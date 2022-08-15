# Flutter TalnCloud plugin


This repo is a modified folked version to the main [flutter
repo](https://github.com/flutter/flutter). It contains the source code for
Flutter first-party plugins (i.e., plugins developed by the core Flutter team).
Check the `packages` directory for all plugins.

Flutter plugins enable access to platform-specific APIs. For more information
about plugins, and how to use them, see
[https://flutter.dev/platform-plugins/](https://flutter.dev/platform-plugins/).

These plugins are also available on
[pub](https://pub.dev/flutter/packages).

## Issues

Please file any issues, bugs, or feature requests in the [main flutter
repo](https://github.com/flutter/flutter/issues/new).

Issues pertaining to this repository are [labeled
"plugin"](https://github.com/flutter/flutter/issues?q=is%3Aopen+is%3Aissue+label%3Aplugin).

## Contributing

If you wish to contribute a new plugin to the Flutter ecosystem, please
see the documentation for [developing packages](https://flutter.dev/developing-packages/) and
[platform channels](https://flutter.dev/platform-channels/). You can store
your plugin source code in any GitHub repository (the present repo is only
intended for plugins developed by the core Flutter team). Once your plugin
is ready, you can [publish](https://flutter.dev/developing-packages/#publish) it
to the [pub repository](https://pub.dev/).

If you wish to contribute a change to any of the existing plugins in this repo,
please review our [contribution guide](https://github.com/flutter/plugins/blob/main/CONTRIBUTING.md),
and send a [pull request](https://github.com/flutter/plugins/pulls).

## Plugins - url_launcher
These are the available plugins in this repository.

URL schemes are only supported if there are apps installed on the device that can support them. For example, iOS simulators don't have a default email or phone apps installed, so can't open tel: or mailto: links.

Checking supported schemes 
If you need to know at runtime whether a scheme is guaranteed to work before using it (for instance, to adjust your UI based on what is available), you can check with canLaunchUrl.

This code is developed using the SOLID framework and its defined rules that are based on 5 principles. These 5 principles sum up to form the acronym SOLID. Let's look into them [here](https://www.taln.cloud/blogs/post/solid-principles-every-developer-should-know).

However, canLaunchUrl can return false even if launchUrl would work in some circumstances (in web applications, on mobile without the necessary configuration as described above, etc.), so in cases where you can provide fallback behavior it is better to use launchUrl directly and handle failure. For example, a UI button that would have sent feedback email using a mailto URL might instead open a web-based feedback form using an https URL on failure, rather than disabling the button if canLaunchUrl returns false for mailto.

Encoding URLs 
URLs must be properly encoded, especially when including spaces or other special characters. In general this is handled automatically by the Uri class.

However, for any scheme other than http or https, you should use the query parameter and the encodeQueryParameters function shown below rather than Uri's queryParameters constructor argument for any query parameters, due to a bug in the way Uri encodes query parameters. Using queryParameters will result in spaces being converted to + in many cases.
