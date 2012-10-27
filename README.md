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

In order to have the clean URLs working please use the provided .htaccess file for Apache and write/include your controllers from index.php or simply adapt it to suit your needs.

By the way, PHP 5.3+ is going to be needed to run this code since it uses lambda functions and closures.

<p align="center">
  <img src="http://stradlin.bitzeppelin.com/images/izzy-and-axl.jpg" alt="Izzy Stradlin' and Axl Rose" />
</p>

Speaking of controllers, this microframework should have been called 'Axl', that's a real control freak! :)

For more information please read the freaking sources and please stay tuned.

(c) 2012 - Bit Zeppelin S.A.C. - Developed by Antonio Ognio a.k.a @gnrfan
