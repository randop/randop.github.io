---
layout: post
title:  "Find function declaration in PHP"
date:   2018-08-31 10:00:00 +0800
categories: php debug debugging programming
---
This is a simple way to find where the function is defined on your script

```php
<?php
$reflFunc = new ReflectionFunction('function_name');
print $reflFunc->getFileName() . ':' . $reflFunc->getStartLine();
```