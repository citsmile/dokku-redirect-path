# dokku-redirect-path

dokku-redirect-path is a plugin for [dokku][dokku] that gives the ability to set simple redirects within an application.

This plugin redirects paths to other paths of a specific domain. When the changes are applied, the nginx config is reloaded but the server is not restarted.

## Installation

```sh
# dokku 0.37+
$ sudo dokku plugin:install https://github.com/citsmile/dokku-redirect-path
```

## Commands
Usage: `dokku redirect-path[:command] [<app>]`

```
    redirect-path:list <app>                      Display the redirects set on app
    redirect-path:add <app> <src> <dest> [<code>] Add a new redirect from <src> path to <dest> path
    redirect-path:delete <app> <src>              Delete the redirect from the <src> path
    redirect-path:apply <app>                     Generates redirect.conf in nginx.conf.d and applies it
```

## Redirect Codes

| Code | Name               | Behavior                                           |
| ---- | ------------------ | -------------------------------------------------- |
| 301  | Moved Permanently  | __(Default)__ Permanent, preserves method          |
| 302  | Found              | Temporary, may change method to GET                |
| 303  | See Other          | (HTTP/1.1) Temporary, changes method to GET        |
| 307  | Temporary Redirect | (HTTP/1.1) Temporary, preserves method             |

## Usage

Check redirects on my-app
```shell
$ dokku redirect-path:list app

SOURCE   DESTINATION  CODE
old-url  new-url      301
```

## License

This plugin is released under the MIT license. See the file [LICENSE](LICENSE).

[dokku]: https://github.com/progrium/dokku
