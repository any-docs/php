---
title: "What is PHP?"
lang: en-US
---

# What is PHP?
PHP (Hypertext Preprocessor) is a popular server-side scripting language that's especially well-suited for web development. It's been around since 1995 and powers a huge portion of the web, including platforms like WordPress, Facebook, and Wikipedia.

Here are some key things that make PHP useful:

**Server-side processing**: Unlike JavaScript which runs in the browser, PHP runs on the web server. This means it can interact with databases, handle file uploads, process forms, and generate dynamic content before sending HTML to the user's browser.

**Easy to learn**: PHP has a relatively gentle learning curve, especially if you already know HTML. You can embed PHP directly into HTML files, which makes it straightforward to add dynamic features to static pages.

**Database integration**: PHP works seamlessly with databases like MySQL, PostgreSQL, and others, making it ideal for creating data-driven websites.

**Wide hosting support**: Nearly every web hosting provider supports PHP, making it easy to deploy your applications.

Here's a simple example to give you a taste:

::: code-group
```php [hello-world.php]
<?php
// This is a PHP comment
$name = "World";
echo "Hello, " . $name . "!";

// You can also work with arrays
$fruits = array["Apple", "Banana", "Orange"];
foreach ($fruits as $fruit) {
    echo $fruit . " ";
}
?>
```

PHP can handle everything from simple contact forms to complex e-commerce systems. It's also free and open-source, with extensive documentation and a large community.