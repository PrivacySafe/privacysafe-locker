<div align="center">
  <a href="https://privacysafe.locker">
    <img src="img/privacysafe_locker_logo.svg" width="300" height="300" />
  </a>
  
  # PrivacySafe Locker &ndash; Private Files &amp; Memos
</div>

PrivacySafe Locker is a privacy-first, temporary storage solution for securely sharing encrypted files and memos. PrivacySafe Locker ensures that **all encryption happens on your device**, making it zero-knowledge — the server cannot read or access the content.

## Features
- **Self-Destructing Files & Memos:** Files automatically expire after a period of time (24 hours by default) or can be manually removed earlier.
- **End-to-End Encryption:** All data is encrypted on your device before uploading, ensuring only the intended recipient can access it.
- **Bypass Email Attachment Limits:** Share files (up to 25MB by default) without relying on email attachments or long-term cloud storage.

## How It Works
1. **Upload a File or Memo:** Drag & drop a file or type a memo.
2. **Create a Private Address:** Your encrypted content creates a unique locker address URL.
3. **Share Securely:** Send the URL through an encrypted chat or other secure channels.
4. **Auto-Deletion:** The file vanishes after a set period of time, leaving no trace.

## Free Public Server
- Browse to [https://privacysafe.locker](https://privacysafe.locker) to try this software for free.
- **Files are deleted every 24 hours** and the file size limit is **25MB**.
- Tor Hidden Service: ohcaaq74kscfpdamfkvafdz24gmyo27debz64vjltvx34pze6meb5rqd.onion

## Installation & Self-Hosting
PrivacySafe Locker can be self-hosted. To install and run the server with default settings:
```bash
apt install nodejs
git clone https://github.com/PrivacySafe/privacysafe-locker/
cd privacysafe-locker
cp server/server.conf.example server/server.conf
cp client/config.js.example client/config.js
cd server
npm install
node server.js
```
For detailed **server configuration**, see [`server.conf.example`](server.conf.example).

## External Tools=
- **Command-Line Uploading:** PrivacySafe Locker is the successor to Up1 so you can use [upclient](https://github.com/Upload/upclient) to upload files programmatically.
- **Desktop GUI Uploading:** The [ShareX](https://github.com/Upload/ShareX) graphical application can send files to PrivacySafe Locker.

## Contributing
Contributions are welcome! Please fork, remix, and create pull requests. Happy Hacking :)

Never send sensitive info about you or other users via direct message or email.

* **Bugs &amp; Security Issues:** See [SECURITY.md](SECURITY.md) for more information.

* **Report Abuse:** Email <a href="mailto:abuse@privacysafe.net" target="_blank">abuse@privacysafe.net</a> (<a href="https://psafe.ly/xSpQhF" target="_blank">PGP</a>)

## License
© 2024-present PrivacySafe Services LLC. This project is dedicated to ethical <a href="https://fsf.org" target="_blank" rel="noreferrer noopener">Free and Open Source Software</a> and <a href="https://oshwa.org" target="_blank" rel="noreferrer noopener">Open Source Hardware</a>. PrivacySafe® is a registered trademark.

Released under the [MIT/Expat License](LICENSE). See [LICENSE](LICENSE) for more information. PrivacySafe Link is modified from [Up1](https://github.com/Upload/Up1) by Andre Drapeau and Keith Morrow.
