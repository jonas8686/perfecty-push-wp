# Perfecty Push WP Plugin ⚡️

[![tests](https://github.com/perfectyorg/perfecty-push-wp/workflows/Tests/badge.svg)](https://github.com/perfectyorg/perfecty-push-wp/actions?query=workflow%3ATests)
[![deployment](https://github.com/perfectyorg/perfecty-push-wp/workflows/Deployment/badge.svg)](https://github.com/perfectyorg/perfecty-push-wp/actions?query=workflow%3ADeployment)
[![License](https://img.shields.io/badge/license-GLPv2-blue.svg)](./LICENSE.txt)
[![PHP compatibility](https://plugintests.com/plugins/wporg/perfecty-push-notifications/php-badge.svg)](https://plugintests.com/plugins/wporg/perfecty-push-notifications/latest)
[![WP compatibility](https://plugintests.com/plugins/wporg/perfecty-push-notifications/wp-badge.svg)](https://plugintests.com/plugins/wporg/perfecty-push-notifications/latest)

Self-hosted Push Notifications from your Wordpress server for free! 🥳

![Perfecty Push for Wordpress](assets/banner-1544x500.png)

**Perfecty Push WP** is an Open Source plugin for WordPress
that allows you to send web Push Notifications directly from your server:
No hidden fees, no third-party dependencies and you own your data. 👏

**Install it now:**
[https://wordpress.org/plugins/perfecty-push-notifications/](https://wordpress.org/plugins/perfecty-push-notifications/)

**More information about the project:** [https://perfecty.org/](https://perfecty.org/)

## Features ✨

- **Open Source**, send Push Notifications **from your server for free!**
- 10.000 notifications/minute in a 2 GB, 1vCPU host. Can achieve better performance with better specs.
- PWA compatible / AMP (Transitional)
- Can be called by other plugins using the `Perfecty_Push_Integration` class
- No third-party dependencies
- Migrate users from other push services like OneSignal
- Send push notifications on posts publishing
- Customize the public widget
- The user authorization tokens stay in your server
- Offline browser notifications through [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API) (Safari is not supported yet)
- Built-in Push Server based on [web-push-php](https://github.com/web-push-libs/web-push-php)

## Requirements 🧩

- `PHP >= 7.2`
- `gmp` extension for message encryption (optional)

**Note**: The `gmp` extension is optional and recommended
for better performance.

## Documentation

[https://docs.perfecty.org/](https://docs.perfecty.org/)

## External integrations 🛸

You can use and extend Perfecty Push Notifications from third party plugins or your own code.

### Send notifications through Perfecty Push

You can use the `Perfecty_Push_Integration` class to send Push Notifications from other plugins:

- `Perfecty_Push_Integration::notify( $wp_user_id, $message, $title = '', $image_url = '', $url_to_open = '' )` Send a notification to a registered WordPress user. If the user has multiple devices, it will send the notification to all the devices the user has subscribed.

- `Perfecty_Push_Integration::broadcast( $message, $title = '', $image_url = '', $url_to_open = '' )` Schedule a broadcast notification that will be sent to all the Push Notifications users.

### Hooks

- `perfecty_push_broadcast_scheduled($payload)` executed when a broadcast notification has been scheduled. You have access to the provided payload.
  
- `perfecty_push_wp_user_notified($payload, $wp_user_id)` executed when a notification has been sent to a WordPress user. You have access to the provided payload and WP User ID.

### Filters

- `perfecty_push_custom_payload($payload)` use this filter to customize the `$payload` array content. More information about the payload array [here](https://github.com/perfectyorg/perfecty-push-wp/blob/master/lib/class-perfecty-push-lib-payload.php).

## Local development 👨🏻‍💻

To see it in action in your local development environment, you need a set of
services which Wordpress relies on. You start off by creating the docker image:

```
docker build -t custom-wordpress:5.8-php7.3-apache .
```

Then start all the services and run the setup:

```
make up
make setup
```

You can now go to https://localhost/wp-login.php > Plugins > Activate the
**Perfecty Push** plugin.

## Available commands 👾

```
# start the service containers
make up

# stop de service containers
make down

# remote console
make console

# run the unit tests
make test

# run the formatter
make format

# setup all: make wordpress, make composer, make phpunit and make sdk
make setup

# setup wordpress and plugins
make wordpress

# install all the composer dependencies
make deps

# setup wordpress as a testing environment for phpunit
make phpunit

# generates the redistributable bundle in dist/perfecty-push-notifications.zip
make bundle
```
## Demo 🎭

### Admin Dashboard

![Dashboard](assets/screenshot-1.png)

### Public view

![Screenshot preview](.github/assets/perfecty.gif "Preview")


## Testing ✅

This project relies on automated tests as in the [Wordpress Core](https://make.wordpress.org/core/handbook/testing/automated-testing/writing-phpunit-tests/) guidelines.

Run all the test suites:

```
make test
```

Run a single test:

```
make console
cd wp-contents/plugins/perfecty-push/
phpunit --filter test_schedule_broadcast_async
```

## Troubleshooting 🛠

**Not intended for production:** In case the plugins cannot be installed on your local installation do:

```
make console
chown -R www-data wp-content
```

## License 👓

The WordPress Plugin is an Open Source project licensed under [GPL v2](./LICENSE.txt).

The bell icon SVG code is a Font Awesome icon, a MIT License.

<span>Banner photo by <a href="https://unsplash.com/@nasa?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">NASA</a> on <a href="https://unsplash.com/s/photos/world?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>

## Contributing 🚀

If you're interesting on contributing to this project, feel free to submit your
suggestions as a PR or an issue directly to any of the projects repos.
Remember to read the [Code of Conduct](./CONDUCT) and the license information
of each project, which in general use the MIT license, except the WordPress plugin (GPL v2).

## Open Source contributors 🔥

[<img src="https://avatars3.githubusercontent.com/u/691521?s=460&u=ceab22655f55101b66f8e79ed08007e2f8034f34&v=4" width="117">](https://github.com/rwngallego) | [<img src="https://avatars.githubusercontent.com/u/26635356?s=460&v=4" width="117">](https://github.com/MocioF) |
:---: | :---: |
[Rowinson Gallego](https://github.com/rwngallego) | [MocioF](https://github.com/MocioF) |

## Special Thanks

[<img alt="Jetbrains" src="https://github.com/perfectyorg/perfecty-push-wp/raw/master/.github/assets/jetbrains-logo.svg" width="120">](https://www.jetbrains.com/?from=PerfectyPush)

Thanks to Jetbrains for supporting this Open Source project with their magnificent tools.