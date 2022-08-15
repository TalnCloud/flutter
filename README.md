<meta name="google-site-verification" content="RJNvC8TNeJ2QMocGVCxVSlS07hQs30k41yqjfcLJN5k" />

# Flutter plugin for URL Launching - TalnCloud


This Plugin repo is a modified folked version to the main [flutter
repo](https://github.com/flutter/flutter). It contains the source code for
Flutter url launcher plugins (i.e., plugins developed by the core Flutter team).
Check the `packages` directory for all plugins.

Flutter plugins enable access to platform-specific APIs. For more information
about plugins, and how to use them, see
[https://flutter.dev/platform-plugins/](https://flutter.dev/platform-plugins/).

These plugins are also available on
[pub](https://pub.dev/flutter/packages).



## Plugins - url_launcher
These are the available plugins in this repository.

URL schemes are only supported if there are apps installed on the device that can support them. For example, iOS simulators don't have a default email or phone apps installed, so can't open tel: or mailto: links.

Checking supported schemes 
If you need to know at runtime whether a scheme is guaranteed to work before using it (for instance, to adjust your UI based on what is available), you can check with canLaunchUrl.

This code is developed using the SOLID framework and its defined rules that are based on 5 principles. These 5 principles sum up to form the acronym SOLID. Read more about them [here](https://www.taln.cloud/blogs/post/solid-principles-every-developer-should-know).

  1. Single Responsibility
  2. Open for Extension, Closed for Modification
  3. Liskov Substitution
  4. Interface Segregation
  5. Dependency Inversion

However, canLaunchUrl can return false even if launchUrl would work in some circumstances (in web applications, on mobile without the necessary configuration as described above, etc.), so in cases where you can provide fallback behavior it is better to use launchUrl directly and handle failure. For example, a UI button that would have sent feedback email using a mailto URL might instead open a web-based feedback form using an https URL on failure, rather than disabling the button if canLaunchUrl returns false for mailto.

Encoding URLs 
URLs must be properly encoded, especially when including spaces or other special characters. In general this is handled automatically by the Uri class.

However, for any scheme other than http or https, you should use the query parameter and the encodeQueryParameters function shown below rather than Uri's queryParameters constructor argument for any query parameters, due to a bug in the way Uri encodes query parameters. Using queryParameters will result in spaces being converted to + in many cases.
