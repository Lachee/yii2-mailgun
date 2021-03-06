# Mailgun Extension for Yii 2

This extension provides a [Mailgun](https://www.mailgun.com/) mail solution for [Yii framework 2.0](http://www.yiiframework.com).

[![Latest Stable Version](https://poser.pugx.org/boundstate/yii2-mailgun/v/stable)](https://packagist.org/packages/boundstate/yii2-mailgun)
[![Total Downloads](https://poser.pugx.org/boundstate/yii2-mailgun/downloads)](https://packagist.org/packages/boundstate/yii2-mailgun)
[![Build Status](https://travis-ci.com/boundstate/yii2-mailgun.svg?branch=master)](https://travis-ci.com/boundstate/yii2-mailgun)

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

```
composer require boundstate/yii2-mailgun
```

The [Mailgun API Client](https://github.com/mailgun/mailgun-php) is not hard coupled to Guzzle, Buzz or any other library that sends
HTTP messages. You must also install the [PSR-7 implementation and HTTP client](https://packagist.org/providers/php-http/client-implementation)
you want to use.

If you just want to get started quickly you should install [Buzz](https://github.com/kriswallsmith/Buzz) and [nyholm/psr7](https://github.com/Nyholm/psr7):

```bash
composer require kriswallsmith/buzz nyholm/psr7
```

## Usage

To use this extension, simply add the following code in your application configuration:

```php
return [
    //....
    'components' => [
        'mailer' => [
            'class' => 'boundstate\mailgun\Mailer',
            'key' => 'key-example',
            'domain' => 'mg.example.com',
        ],
    ],
];
```

You can then send an email as follows:

```php
Yii::$app->mailer->compose('contact/html', ['contactForm' => $form])
    ->setFrom('from@domain.com')
    ->setTo($form->email)
    ->setSubject($form->subject)
    ->send();
```

For further instructions refer to the [related section in the Yii Definitive Guide](http://www.yiiframework.com/doc-2.0/guide-tutorial-mailing.html).