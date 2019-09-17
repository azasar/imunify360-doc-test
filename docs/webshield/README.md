# WebShield
## Captcha

The CAPTCHA is a feature intended to distinguish human from machine input and protect websites from the spam and different types of automated abuse. Imunify360 uses [reCAPTCHA](https://www.google.com/recaptcha/intro/invisible.html) service.

There are two layers in CAPTCHA behavior:

1. If a user of a website is added to the <span class="notranslate">Grey List</span> (the access is blocked), then the CAPTCHA allows him to unblock himself. When he tries to get to the website he is redirected to the Captcha Server by ipset, where he can see the protection page asking to confirm that he is not a robot by ticking a checkbox.

![](/images/captcha.jpg)

::: tip Note
The IP address on the screenshot above is given as an example.
:::

If successful, a user is redirected to the website, which means that the access is unblocked and the IP address of this user is removed from the <span class="notranslate">Grey List</span>.

It is also possible to enable the invisible reCAPTCHA via the Imunify360 [<span class="notranslate">Settings</span> page](/dashboard/#settings). With the invisible reCAPTCHA enabled, a human user is not required to go through human confirmation - the process will pass under the hood and a user will be redirected to the website. In case if invisible reCAPTCHA failed to detect if a user is a human or not, then visible reCAPTCHA appears.

2. The CAPTCHA is always on guard of the websites and checks the activity of each IP. With the help of reCAPTCHA it blocks bots and protects websites from spam and abuse. To learn more about reCAPTCHA follow the [link](https://www.google.com/recaptcha/intro/).

The reCaptcha supports localization. Depending on user’s browser settings, reCaptcha will use the browser default language and allow to change it:

![](/images/local.jpg)

### Captcha page customization

To modify footer, header or body of the CAPTCHA use the templates in <span class="notranslate">`/usr/share/imunify360-webshield/captcha/templates/`</span>.

There are three files:

* <span class="notranslate">`head.tpl`</span> – this file goes inside <span class="notranslate">`<head></head>`</span> tags. So you can add JavaScript, CSS styles, etc.

* <span class="notranslate">`body.tpl`</span> – the main template file, modify it as you wish. CAPTCHA goes above all the layers.

* <span class="notranslate">`static`</span> – here you can place images, CSS, JavaScript, etc. and access these files as <span class="notranslate">`/static/<filename>`</span>.

To find information on supported browsers follow this link [https://support.google.com/recaptcha/answer/6223828](https://support.google.com/recaptcha/answer/6223828).

### Update Captcha localizations
::: tip Note
Custom Captcha localization is available starting from Imunify360 version 2.6.0 and later.
:::

A user can change the text of captcha messages for the supported languages. Note that adding custom language is not supported.

To change the text of the Imunify360 Captcha and update the localizations text, please do the following:

1. Locate appropriate Captcha localization files by running:

    <div class="notranslate">

   ```
   ls /usr/share/imunify360-webshield/captcha/translations/locale/{lang}/LC_MESSAGES/messages.po
   ```

   </div>
   For example for Polish language the catalog looks like this: 
   
    <div class="notranslate">

   ```
   /usr/share/imunify360-webshield/captcha/translations/locale/pl/LC_MESSAGES/messages.po
   ```

   </div>

2. Update Captcha localization files by editing <span class="notranslate">`msgstr "my customization or translation"`</span> for appropriate <span class="notranslate">`msgid “original plain english text"`</span>.

   Where <span class="notranslate">`msgstr`</span> contains text that is shown to user and <span class="notranslate">`msgid`</span> contains Captcha original English text.

   For example:

    <div class="notranslate">

   ``` HTML
   #: templates/index.html:154
   msgid ""
   "We have noticed an unusual activity from your <b>IP {client_ip}</b> and "
   "blocked access to this website."
   msgstr ""
   "Zauważyliśmy nietypową aktywność związaną z twoim adresem <b>IP "
   "{client_ip}</b> i zablokowaliśmy dostęp do tej strony internetowej"
   ```

   </div>
3. To add Polish translation edit text in the <span class="notranslate">`msgstr`</span> field. To change the text for a default English translation, edit text in the <span class="notranslate">`msgid`</span> field.
4. Save files.
5. When translation in <span class="notranslate">`messages.po`</span> files is finished, restart <span class="notranslate">imunify360-webshield</span> service:

<div class="notranslate">

```
service imunify360-webshield restart
```

</div>
6. Block yourself (remove your IP from <span class="notranslate">Imunify360 White List</span> and try to log in to the server via ssh with wrong password until it blocks you). Then go to website and log in. Captcha should appear. Set Polish language and assert that new text is displayed.

## CDN Support <sup>3.8+</sup>
	
Starting from version 3.8 Imunify360 correctly graylists and blocks IPs behind Cloudflare and other CDNs (see [here](/webshield/#supported-cdn-providers) for the full list).
	
Imunify360 passes all requests from CDN through <span class="notranslate">WebShield</span>, and uses <span class="notranslate">CF-Connecting-IP</span> and <span class="notranslate">X-Forwarded-For</span> headers to identify real IPs.
	
The feature is disabled by default in Imunify360 version 3.8 but will be enabled in the future versions.
	
To enable it now, add the following section to the Imunify360 config file (<span class="notranslate">_/etc/sysconfig/imunify360/imunify360.config_</span>):
	
<div class="notranslate">

```
WEBSHIELD:
 known_proxies_support: true
```

</div>
And restart <span class="notranslate">WebShield</span>
For EL6:
<div class="notranslate">

```
service imunify360-webshield restart
```

</div>
For other systems:
<div class="notranslate">

```
systemctl restart imunify360-webshield
```
</div>

::: tip Note
If you are using cPanel/EasyApache3, Imunify360 will not automatically deploy _mod_remoteip_, and log files will show local server IP for visitors coming from CDN. EasyApache 3 is EOL in December 2018, and we don't plan to add automated _mod_remoteip_ setup and configuration for it.
:::
:::tip Note
For cPanel/EasyApache 4, Plesk, DirectAdmin and LiteSpeed _mod_remoteip_ will be automatically installed and configured.
:::
	
#### Supported CDN providers:

* Cloudflare
* MaxCDN
* StackPath CDN
* KeyCDN
* Dartspeed.com
* QUIC.cloud CDN

### SplashScreen for Chinese customers

Imunify360 Captcha isn't available in some countries due to certain restrictions, for example, in China. To alleviate this, Chinese customers can use Imunify360 SplashScreen as Captcha.

To enable SplashScreen, add the following line: 

<div class="notranslate">

```
wscheck_splashscreen_as_captcha= on
```
</div>

to the <span class="notranslate">`/etc/imunify360-webshield/webshield-http.conf.d/wscheck.conf`</span> and run the following command.

**For Ubuntu:**

<div class="notranslate">

```
service imunify360-websheld reload
```
</div>

**For CentOS:**

<div class="notranslate">

```
systemctl reload imunify360-webshield
```
</div>


The graylisted visitors will see such screen for 5 seconds before redirecting to their initial destination.

![](/images/splash_as_captcha.png)





