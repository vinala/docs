## Translator

[![alt return](https://gitlab.com/lighty/Art/raw/master/Resources/signs.png) Main Menu](https://gitlab.com/lighty/Docs/tree/3.3/#index)

- [Introduction](#introduction)

----

### Introduction

Vinala's Translator Surface provide a convenient way to retrieve strings in various languages, allowing you to easily support multiple languages within your application. Language strings are stored in files within the `resources/translator` directory. Within this directory there should be a subdirectory for each language supported by the application:

```
/resources
    /translator
        /en
            /profile.php
        /ar
            /profile.php
```

All language files simply return an array of keyed strings. For example:

```php
<?php

return [
    'hello' => 'Hello World!',
];
```