# flutter_recaptcha_v2

A Flutter plugin for Google ReCaptcha V2.

## Getting Started

This plugin requires `Webview` to use Google ReCaptcha.
This plugin only supports **Google ReCAPTCHA V2** (not V3)

Obtain your own key & secret here: https://www.google.com/recaptcha

**!!! Remember to add this domain into the reCaptcha setting: recaptcha-flutter-plugin.firebaseapp.com**

Then test your API KEY at: https://recaptcha-flutter-plugin.firebaseapp.com/?api_key=API_KEY

Put `RecaptchaV2` widget into your widget tree (Usually inside `Stack` widget), **make sure it's placed on top of the tree and block all the behind interactions**:

```
RecaptchaV2Controller recaptchaV2Controller = RecaptchaV2Controller();
...
RecaptchaV2(
	apiKey: "YOUR_API_KEY", // for enabling the reCaptcha
	apiSecret: "YOUR_API_SECRET", // for verifying the responded token
	controller: recaptchaV2Controller,
	onVerifiedError: (err){
		print(err);
	},
	onVerifiedSuccessfully: (success) {
		setState(() {
		if (success) {
			// You've been verified successfully.
		} else {
			// "Failed to verify.
		}
		});
	},
),
```

The `RecaptchaV2` widget is hidden by default, you need to attach the `RecaptchaV2Controller` and call `show()` method when needed. Like this:
```
recaptchaV2Controller.show();
```

Manually hide it:
```
recaptchaV2Controller.hide();
```

That's it!

## Upgrades

Now you can change the plugin url or leave it by default: `https://recaptcha-flutter-plugin.firebaseapp.com/`

Example:

```
RecaptchaV2(
	...
	pluginURL: "https://mypersonalurl.com"
	...
	onVerifiedError: (err){
		print(err);
	},
	onVerifiedSuccessfully: (success) {
		setState(() {
		if (success) {
			// You've been verified successfully.
		} else {
			// "Failed to verify.
		}
		});
	},
),

```
If you want the Cancel Button with the captcha controller set the boolean to True, **otherwise it won't show**

bool _visibleCancelBottom = true;
