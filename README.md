# PhalconPHP Debug Assets

This repository allows developers to pull the debug page assets locally, especially useful for projects:

 - requiring a secure environment with no remote assets
 - local development with no internet connection (developing on the move/commuting)

## Installation

Example composer file:

```
{
    "name": "vendor/example-project",
    "description": "Example Composer File.",
    "authors": [
        {
            "name": "example",
            "email": "email@example.com"
        }
    ],
    "minimum-stability": "dev",
    "config" : {
        "optimize-autoloader": true,
        "sort-packages": true
    },
    "require" : {
        "php" : ">=7.2",
        "ext-phalcon" : "^3.4",
        "zvps/phalcon-validation" : "dev-master",
        "fabfuel/prophiler": "~1.5",
        "phalcon/incubator": "3.4.x"
    },
    "require-dev": {
        "phalcon/devtools": "~3.4",
        "phalcon/ide-stubs": "*",
        "ralouphie/getallheaders": "2.0.5",
        "zvps/phalconphp-debug-assets": "4.x-dev"
    },
    "repositories": [
        {
            "type": "vcs",
            "url":  "git@github.com:zVPS/phalconphp-debug-assets.git"
        }
    ],
    "scripts": {
        "post-install-cmd": [
            "SlowProg\\CopyFile\\ScriptHandler::copy"
        ],
        "post-update-cmd": [
            "SlowProg\\CopyFile\\ScriptHandler::copy"
        ]
    },
    "extra": {
        "copy-file-dev": {
            "vendor/zvps/phalconphp-debug-assets/debug/": "public/debug/"
        }
    }
}
```

If your project has a different location for assets / webroot then change `public/debug/` to the correct path relative to the project root.