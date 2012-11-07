phonegap-ratchet-demo
=====================

This is a demo that shows [Ratchet](https://github.com/maker/ratchet) working with (PhoneGap)[http://phonegap.com]. It's meant to be used with [PhoneGap Build](http://build.phonegap.com).

In order to get Ratchet to work with PhoneGap I had to make a small change to `rachet.js`. In that file replace:

`if (xhr.readyState == 4) xhr.status == 200 ? success(xhr, options) : failure(options.url);`

with

`      if (xhr.readyState == 4) xhr.status == 200 || (xhr.status == 0 && options.url.indexOf('file:///') != -1) ? success(xhr, options) : failure(options.url);`

By also allowing for an XMLHttpRequest status of 0 when we're working with the filesystem, PhoneGap can work with push.js that Ratchet uses. (Thanks to [@macdonst](https://twitter.com/macdonst) for the tip).