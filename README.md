![Logo](https://privacysafe.locker/img/privacysafe_locker_logo.svg)

PrivacySafe Locker &ndash; Private Files &amp; Memos
===

PrivacySafe Locker is a fork of [Up1](https://github.com/Upload/Up1) with some additional changes on the server to treat the app more like a temporary locker that self-destructs. The PrivacySafe Locker application has zero knowledge of the contents of a locker (aka the encrypted file or memo) and uses client-side cryptography to encrypt images, text, and other data. The server software and server administrators cannot read the contents of any files created by end-users, and these encrypted blobs are what we call a "locker". The app can load a variety of files on the client-side for viewing by the recipient of a PrivacySafe Locker URL, such as images, text with syntax highlighting, and short videos. The creator of the PrivacySafe Locker can easily delete the locker after they have confirmed receipt of the contents with their intended recipient, or they can wait a short amount of time (6 hours by default) and the locker will self-destruct.

Free Public Server
---
Browse to https://privacysafe.locker to try this software for free. Files on that instance are deleted every 24 hours and filesize limit is 15MB

#### Client Utilities:
* [upclient](https://github.com/Upload/upclient), a command-line tool for uploading to Up1 servers

Quick start
---
To install and run the server with default settings:

    apt install nodejs
    git clone https://github.com/seandiggity/privacysafe-locker/
    cd privacysafe-locker
    cp server/server.conf.example server/server.conf
    cp client/config.js.example client/config.js
    cd server
    npm install
    node server.js

Server configuration is done through the [`server.conf`](https://github.com/Upload/Up1/server.conf.example) file. For a quick start, simply move `server.conf.example` to `server.conf`.

`listen` is an `address:port`-formatted string, where either one are optional. Some examples include `":9000"` to listen on any interface, port 9000; `"127.0.0.1"` to listen on localhost port 80; `"1.1.1.1:8080"` to listen on 1.1.1.1 port 8080; or even `""` to listen on any interface, port 80.

`api_key` is a very basic security measure, requiring any client making an upload to know this key. This doesn't seem very useful and should be revamped; replace it with HTTP auth maybe?

`delete_key` is a key used to secure the deletion keys. Set this to something that only the server knows.

`maximum_file_size` is the largest file, in bytes, that's allowed to be uploaded to the server. The default here is a decimal 50MB.

There are three additional sections in the configuration file: `http`, `https` and `cloudflare-cache-invalidate`. The first two are fairly self-explanitory (and at least one must be enabled).

`cloudflare-cache-invalidate` is disabled by default and only useful if you choose to run the Up1 server behind Cloudflare. When this section is enabled, it ensures that when an upload is deleted, Cloudflare doesn't hold on to copies of the upload on its edge servers by sending an API call to invalidate it.

For the web application configuration, a [`config.js.example`](https://github.com/Upload/Up1/config.js.example) file is provided. Make sure the `api_key` here matches the one in `server.conf`.

External Tools
---

Currently, there is a command-line program that works with Up1: ~~[ShareX](https://github.com/ShareX/ShareX) ([relevant code](https://github.com/ShareX/ShareX/pull/751))~~, and [upclient](https://github.com/Upload/upclient).

Upclient is a CLI tool which can send files or data to Up1 servers either via unix pipe (`ps aux | up`), or via argument (`up image.png`), and returns a URL to the uploaded file on stdout. It runs on nodejs and uses SJCL for the crypto.

How it works
---

Before an image is uploaded, a "seed" is generated. This seed can be of any length (because really, the server will never be able to tell), but has a length of 25 characters by default. The seed is then run through SHA512, giving the AES key in bytes 0-256, the CCM IV in bytes 256-384, and the server's file identifier in bytes 384-512. Using this output, the image data is then encrypted using said AES key and IV using SJCL's AES-CCM methods, and sent to the server with an identifier. Within the encryption, there is also a prepended JSON object that contains metadata (currently just the filename and mime-type). The (decrypted) blob format starts with 2 bytes denoting the JSON character length, the JSON data itself, and then the file data at the end.

Image deletion functionality is also available. When an image is uploaded, a delete token is returned. Sending this delete token back to the server will delete the image. On the server side, `HMAC-SHA256(static_delete_key, identifier)` is used, where the key is a secret on the server.

Technologies
---

The browser-side is written in plain Javascript using SJCL for the AES-CCM encryption, with entropy obtained using the WebCrypto APIs and encryption performed within a Web Worker. The video and audio players just use the HTML5 players hopefully built into the browser. The paste viewer uses highlight.js for the syntax highlighting and line numbers.

Additionally, the repository copy of SJCL comes from the source at https://github.com/bitwiseshiftleft/sjcl, commit `fb1ba931a46d41a7c238717492b66201b2995840` (Version 1.0.3), built with the command line `./configure --without-all --with-aes --with-sha512 --with-codecBytes --with-random --with-codecBase64 --with-ccm`, and compressed using Closure Compiler. If all goes well, a self-built copy should match up byte-for-byte to the contents of `static/deps/sjcl.min.js`.

The server-side is written in Node, although we also have a Go server which uses no dependencies outside of the standard library. The only cryptography it uses is for generating deletion keys, using HMAC and SHA256 in the built-in `crypto/hmac` and `crypto/sha256` packages, respectively.

Caveats
---

* **Encryption/Decryption are not streamed or chunked.** This means that (at the time) any download must fit fully in memory, or the browser may crash. This is not a problem with sub-10MB images, but may be a problem if you want to share a long gameplay video or recorded meeting minutes. We would love help and contributions, even if they break backwards compatibilty.

* **CCM is kinda slow.** Compared to other authenticated encryption modes out there such as GCM or OCB, CCM is considered one of the slower modes (slightly slower than GCM, and almost twice as slow as OCB), isn't parallelizable and [didn't make the best design decisions](http://crypto.stackexchange.com/a/19446). The reason that we chose this algorithm, however, is twofold: primarily, this is the most-audited, oldest and most commonly used algorithm contained in SJCL; as this is used for viewing data, security there is important - and secondly, the other two mentioned algorithms in SJCL were actually *slower* than CCM. There are other crypto libraries which may be allegedly faster, such as [asmcrypto.js](https://github.com/vibornoff/asmcrypto.js/), but it seems new, we don't know anything about it and currently prefer SJCL for its familiarity. With an audit from a trusted party, we may take a second look at asmcrypto.js.

* **By its very nature, this uses cryptography in Javascript.** There are reasons as to why it's bad to use cryptography in Javascript. We're working on browser extensions to mitigate some of these reasons (and non-Javascript clients are always welcome!), however by the very nature of how Up1 works, cryptography in the browser is required. In the event of a breach of trust on the server, the client code could still be modified to read your decryption keys.

* **As a new project, this code hasn't been audited by a trusted party.** There have been (to date) very few eyes on the code that we're aware of, and even fewer trusted eyes on the code. While we've put as much effort as possible into offloading the hard crypto stuff to SJCL, we still might have made a mistake somewhere (reading over `static/js/encryption.js` and letting us know if you find issues would be very helpful to us!), and so for that reason, using this software is at your own risk.

* **The server will, in most cases, receive referrer headers.** If a server decides to log requests, they will also be able to receive `Referer` headers. For private/protected websites and direct links sent via IM or email, this isn't a big deal. If the link is on a public website however, it means the server owner might be able to find the original image. We've added some mitigations for some scenarios, however unfortunately there's nothing that the software or server owner can do about this (apart from hosting behind a CDN and offloading the Referer header to the edge), however when posting a link you have a couple of options:
  1. Put `rel="noreferrer"` into any `<a>` links that are directed at the Up1 server.
  2. If you don't have control over the link attributes, you can use a referrer breaker such as https://anon.click/ or https://href.li/, amongst many.

Contributing
---
Any contributions, whether to our existing code or as separate applications, are very welcome!

We don't ask for any CLAs - you don't have to give up copyright on your code - however we prefer that you contribute under the MIT license, just for consistency.

If you find serious security issues, please email us at `security@privacysafe.net`.

Thank you for you contributions!

License
---

The Up1 server and browser code are both licensed under MIT.

ShareX's base code is licensed under GPLv2, however the modifications (namely, the C# encryption code) is licensed under MIT.

Upclient is licensed fully under MIT.
