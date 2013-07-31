Opauth for Yii Framework with the use of Composer
=================================================

What is Opauth for Yii Framework?
-------------------

Opauth for Yii Framework is a wrapper for [Opauth](https://github.com/uzyn/opauth) by U-Zyn. The bundled Opauth may not be the latest, please add the latest opauth packages and add them into your main application `composer.json`.

Opauth provides a standardized way to interface with 3rd-party authentication providers. Unlike many current authentication frameworks, Opauth does not deal with database, so developers are not forced to adhere to predetermined database schema.

You can include strategies from the [Packagist](https://packagist.org/search/?q=opauth).

How to make it work
-------------------
Add into your main application composer.json the yii-opauth package, also add any other opauth package you need from [Packagist](https://packagist.org/search/?q=opauth) that you want to implement
```js
	...
	"require" {
		...
		"kahwee/yii-opauth": "dev-master",
		"opauth/facebook": "dev-master"
		...
	},
	...

```

Update your composer packages
```
#> php composer.phar update
```

Add the composer autoloader into Yii. (If you haven't already)
edit the `yiic.php` and `index.php` and add the following lines
```php
<?php
...
$compsetClassLoader = require_once __DIR__ . '/path/to/vendor/autoload.php';
$compsetClassLoader->register();

// Before the creation of the Yii application
...

```

Edit your config and add the `vendor` alias into your import aliases in you config files.
(`config/main.php` and `config/console.php` probably)

```php
<?php
...
	'aliases'=>array(
		'vendor'=>__DIR__ . '/path/to/vendor/'
	)
...

```

And in your `./protected/config/main.php`, add `opauth` to begin:

```php
<?php
return array(
	...
	'modules' => array(
		'class'=>'vendor.kahwee.yii-opauth.OpauthModule',
		'opauth' => array(
			'opauthParams' => array(
				'Security.salt' => 'LDFmiilYf8Fyw5W10rx4W1KsVrieQCnpBzzpTBWA5vJidQKDx8pMJbmw28R1C4m',
				'Strategy' => array(
					'facebook' => array(
						'app_id' => 'YOUR_FACEBOOK_APP_ID',
						'app_secret' => 'YOUR_FACEBOOK_APP_SECRET',
					)
				),
			),
		),
	),
	...
);
```

Issues?
-------

If you have any issues, please highlight them in [yii-opauth's GitHub issues](https://github.com/kahwee/yii-opauth/issues).
