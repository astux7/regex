Regex 
=====
http://rubular.com/ tool which helped me :-)
some nice regex to extract info


+ Extract data from HTML list li elements
```ruby
/<li>(.*?)<\/li>/i
```

+ Extracting data from RRS feed (link path, images ...)
```php
  preg_match_all('#<\s*img [^\>]*src\s*=\s*(["\'])((.*?))\1#im', $text, $fromimg);
  $text = preg_replace('/<\s*img[^>]+>/Ui', '', $text);


  /* --- replace a tag which link to image --- */
  preg_match_all('/<a.*href="([^<].*(png|jpg|gif|jpeg))"[^>]*>(.*?)<\/a>/im', $text, $fromlinks);

  for ($i = 0; $i < sizeof($fromlinks[2]); $i++) {
    $mid_text = $fromlinks[2][$i]; // this is the text or other in the middle of link which link to image
    $text_tmp = preg_replace('/<a.*href="([^<]*[\.png|\.jpg|\.jpeg|\.gif]+)"[^>]*>(.*?)<\/a>/im', $mid_text, $text, 1);
    $text = $text_tmp;
  }
  /* --- remove text below image span color #696969 -- */


  $text = preg_replace('/<span.*style="([^<]*696969+)"[^>]*>(.*?)<\/span>/im', "", $text);
```

+ a => b, a => or a=> or b=>k string checker with case insensitive

```
/(^[a-z]{1}\s?)(=>)(\s?[a-z]{1}?)/i
```
