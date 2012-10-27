Stradlin
========

Severely minimal PHP routing microframework inspired by Sinatra that is specially useful for prototyping RESTful APIs.

Usage example:

```php

require_once('stradlin.php');

route('/hello/(?P<name>\w+)/?', all_verbs(), function($params) {
  $name = $params['name'];
  if (is_numeric($name)) {
    set_status_code(400); /* Bad Request */
    $doc = array(
      "status" => "error",
      "errors" => array(
        "Come on! Your name can't be numeric! Are you a clone trooper or what?"
      )
    );
  } else {
    $doc = array(
      "status" => "ok",
      "data" => array(
        "greeting" => "Hello Mr. or Mrs. $name!!! Welcome to Stradlin :)"
      )
    );
  }
  serve_json($doc, JSON_PRETTY_PRINT);
});
```

In order to have the clean URLs working please use the provided .htaccess file for Apache and write/include your controllers from index.php or simple adapt it to suit your needs.

Speaking of controllers, this microframework should have been called 'Axl', that's a real control freak! :)

For more information please read the freaking sources and please stay tuned.

(c) 2012 - Bit Zeppelin S.A.C. - Developed by Antonio Ognio a.k.a @gnrfan
