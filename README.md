# No User Enumeration Plugin
Stop user enumeration for security.

# Description
In many WordPress installations is possible enumerate usernames through the author archives:

```bash
curl -s http://wpsite/?author=1
curl -s http://wpsite/?author=1/
curl -s http://wpsite/?bypass=1&author%00=1
curl -s http://wpsite/?author%00=%001
curl -s http://wpsite/?%61uthor=1
```

And recently wordpress since 4.7 comes with a rest api integrated that allow list users:

```bash
curl -s http://wpsite/wp-json/wp/v2/users/
curl -s http://wpsite/?rest_route=/wp/v2/users
curl http://wpsite/?_method=GET -d rest_route=/wp/v2/users
```

Know the username of a administrator is the half battle, now an attacker only need guest the password.
This plugin stop it.

Also, is possible get usernames from the post entries.
This plugin, hide the name of the author in a post entry if he is not using a nickname.
Also, hide the url page link of an administrator author.

The main goal is hide the administrators usernames.
Obviously, is better not choose "admin" as the username because is easiliy guessable.

# Installation
1. Upload `no-user-enumeration` to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress

# Changelog
1.3.2 : Using WP_DEBUG not emit undefined index notice.

1.3.1 : Minor changes.

1.3.0 : Fix bypass protection using this:
```bash
curl http://wpsite/?_method=GET -d rest_route=/wp/v2/users
```

1.2.0 : Disallow list users using the rest api. Compatibility with plugin WP All Import.

1.1.0 : Hide admin usernames in post replies. Improved security.

1.0.0 : First version.
