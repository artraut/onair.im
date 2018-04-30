Thanks to:
* https://github.com/zhukov
* https://github.com/tecknojock

## [ONAIR.IM](https://onair.im) — is uncensored Telegram Web App, — [Webogram](https://github.com/zhukov/webogram). 

Telegram offers great [apps for mobile communication](https://www.telegram.org). It is based on the [MTProto protocol](https://core.telegram.org/mtproto) and has an [Open API](https://core.telegram.org/api). I personally like Telegram for its speed and cloud-support (that makes a web app possible, unlike in the case of WA and others).

MTProto data can be carried over HTTP (SSL is also supported), so this project is my take at creating one.

That said, I'm using this app myself and I'd like to share its sources, so anyone can contribute to the development. Any help is welcome!


### Interface


Here are some screenshots of the interface:


![Sample screenshot 1](/app/img/screenshot1.png)
![Mobile screenshot 2](/app/img/screenshot2.png)
![Mobile screenshot 3](/app/img/screenshot3.png)


### Unsupported at the moment

* Secret chats
* Black list
* ...


### Maintained locations


| Description        | URL           | Type  |
| ------------- |-------------| -----:|
| Online Web-version (hosted on Telegram servers)      | https://web.telegram.org/ | hosted
| Online Web-version (hosted on GitHub pages)      | https://zhukov.github.io/webogram | hosted
| Chrome Web Store      | [https://chrome.google.com/webstore/detail/telegram/ clhhggbfdinjmjhajaheehoeibfljjno](https://chrome.google.com/webstore/detail/telegram/clhhggbfdinjmjhajaheehoeibfljjno) |   packed
| Firefox & FirefoxOS Marketplace | https://marketplace.firefox.com/app/telegram |    packed



**Hosted version**: the app is downloaded via HTTPS as a usual website. Will be available offline due to application cache.

**Packed version**: the app is downloaded at once in a package via HTTPS. The package is updated less frequently than the Web-version.

All of the apps above are submitted and maintained by [@zhukov](https://github.com/zhukov), so feel free to use them and report bugs [here](https://github.com/zhukov/webogram/issues). Please do not report bugs which are only reproducible in different locations.


## Technical details

The app is based on the AngularJS JavaScript framework, and written in pure JavaScript. jQuery is used for DOM manipulations, and Bootstrap as the CSS-framework.


### Running locally


The project repository is based on angularjs-seed and includes gulp tasks, so it's easy to launch the app locally on your desktop.
Install [node.js](http://nodejs.org/) and run the following commands in the project directory

```
sudo npm install -g gulp
npm install
```

This will install all the needed dependencies.


#### Running web-server


Just run `gulp watch` to start the web server and the livereload task.
Open http://localhost:8000/app/index.html in your browser.



#### Running as Chrome Packaged App

To run this application in Google Chrome as a packaged app, open this URL (in Chrome): `chrome://extensions/`, then tick "Developer mode" and press "Load unpacked extension...". Select the downloaded `app` folder and Webogram should appear in the list.

Run `gulp watch` to watch for file changes and automatically rebuild the app.


#### Running as Firefox OS App

To run this application in Firefox as a packaged app, open "Menu" -> "Developer" -> "WebIDE" (or hit `Shift + F8`). Choose "Open packaged app" from the Project menu and select the `app` folder.

Run `gulp watch` to watch for file changes and automatically rebuild the app.

#### Running in production

Run `gulp clean`, then `gulp publish` to build the minimized production version of the app. Copy `dist` folder contents to your web server. Don't forget to set `X-Frame-Options SAMEORIGIN` header ([docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options)).

### NGINX settings
Edit your Nginx config file to include the following locations:

```
location ^~ /pluto/apiw1/ {
            proxy_pass https://pluto.web.telegram.org/apiw1/;
}
location ^~ /venus/apiw1/  {
            proxy_pass https://venus.web.telegram.org/apiw1/;
}
location ^~ /aurora/apiw1/ {
            proxy_pass https://aurora.web.telegram.org/apiw1/;
}
location ^~ /vesta/apiw1/ {
            proxy_pass https://vesta.web.telegram.org/apiw1/;
}
location ^~ /flora/apiw1/ {
            proxy_pass https://flora.web.telegram.org/apiw1/;
}
location ^~ /pluto-1/apiw1/ {
            proxy_pass https://pluto-1.web.telegram.org/apiw1/;
}
location ^~ /venus-1/apiw1/  {
            proxy_pass https://venus-1.web.telegram.org/apiw1/;
}
location ^~ /aurora-1/apiw1/ {
            proxy_pass https://aurora-1.web.telegram.org/apiw1/;
}
location ^~ /vesta-1/apiw1/ {
            proxy_pass https://vesta-1.web.telegram.org/apiw1/;
}
location ^~ /flora-1/apiw1/ {
            proxy_pass https://flora-1.web.telegram.org/apiw1/;
}
location ^~ /DC1/ {
            proxy_pass http://149.154.175.10:80/;
}
location ^~ /DC2/ {
            proxy_pass http://149.154.167.40:80/;
}
location ^~ /DC3/ {
            proxy_pass http://149.154.175.117:80/;
}
location ^~ /DC4/ {
            proxy_pass http://149.154.175.50:80/;
}
location ^~ /DC5/ {
            proxy_pass http://149.154.167.51:80/;
}
location ^~ /DC6/ {
            proxy_pass http://149.154.175.100:80/;
}
location ^~ /DC7/ {
            proxy_pass http://149.154.167.91:80/;
}
location ^~ /DC8/ {
            proxy_pass http://149.154.171.5:80/;
}
```


### Third party libraries

Besides the frameworks mentioned above, other libraries are used for protocol and UI needs. Here is the short list:

* [JSBN](http://www-cs-students.stanford.edu/~tjw/jsbn/)
* [CryptoJS](https://code.google.com/p/crypto-js/)
* [zlib.js](https://github.com/imaya/zlib.js)
* [UI Bootstrap](http://angular-ui.github.io/bootstrap/)
* [jQuery Emojiarea](https://github.com/diy/jquery-emojiarea)
* [nanoScrollerJS](https://github.com/jamesflorentino/nanoScrollerJS)
* [gemoji](https://github.com/github/gemoji)
* [emoji-data](https://github.com/iamcal/emoji-data)

Many thanks to all these libraries' authors and contributors. A detailed list with descriptions and licenses is available [here](/app/vendor).


### Licensing

The source code is licensed under GPL v3. License is available [here](/LICENSE).


### [Contribute](CONTRIBUTING.md)
