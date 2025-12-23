---
title: "PHP Basic Syntax"
---

# Basic Syntax

## PHP tags

When PHP processes a file, it recognizes the opening and closing tags, `<?php` and `?>`, to define the boundaries of PHP code execution. Content outside these tags is ignored by the PHP parser, allowing PHP to seamlessly embed in various document types.

A whitespace character (space, tab, or newline) must follow `<?php` to ensure proper token separation. Omitting this whitespace will result in a syntax error.

PHP also includes the short echo tag `<?=`, which is shorthand for `<?php echo`.

### Example #1 PHP Opening and Closing Tags
```php
1.  <?php echo 'if you want to serve PHP code in XHTML or XML documents,
                use these tags'; ?>

2.  You can use the short echo tag to <?= 'print this string' ?>.
    It's equivalent to <?php echo 'print this string' ?>.

3.  <? echo 'this code is within short tags, but will only work '.
            'if short_open_tag is enabled'; ?>
```
::: details Output of the above example in PHP 8.5.0
1.  if you want to serve PHP code in XHTML or XML documents,
    use these tags
2.  You can use the short echo tag to print this string.
    It's equivalent to print this string.

3.  this code is within short tags, but will only work if short_open_tag is enabled
:::

Short tags (example three) are available by default but can be disabled either via the short_open_tag php.ini configuration file directive, or are disabled by default if PHP is built with the `--disable-short-tags` configuration.

::: info Note
As short tags can be disabled it is recommended to only use the normal tags (`<?php ?>` and `<?= ?>`) to maximize compatibility.
:::

If a file ends with PHP code, it is preferable to omit the PHP closing tag at the end of the file. This prevents accidental whitespace or new lines being added after the PHP closing tag, which may cause unwanted effects because PHP will start output buffering when there is no intention from the programmer to send any output at that point in the script.

### Example #2 PHP Code Only File

```php
<?php
echo "Hello world\n";

// ... more code

echo "Last statement\n";

// the script ends here with no PHP closing tag
```
::: details Output of the above example in PHP 8.5.0
Hello world <br>
Last statement
:::

## Escaping from HTML
Everything outside a pair of opening and closing tags is ignored by the PHP parser which allows PHP files to have mixed content. This allows PHP to be embedded in HTML documents, for example to create templates.


### Example #1 Embedding PHP in HTML
```php
<p>This is going to be ignored by PHP and displayed by the browser.</p>
<?php echo 'While this is going to be parsed.'; ?>
<p>This will also be ignored by PHP and displayed by the browser.</p>
```

::: details Output of the above example in PHP 8.5.0
<p>This is going to be ignored by PHP and displayed by the browser.</p>
While this is going to be parsed.<p>This will also be ignored by PHP and displayed by the browser.</p>
:::

This works as expected, because when the PHP interpreter hits the ?> closing tags, it simply starts outputting whatever it finds (except for the immediately following newline - see instruction separation) until it hits another opening tag unless in the middle of a conditional statement in which case the interpreter will determine the outcome of the conditional before making a decision of what to skip over. See the next example.

Using structures with conditions

### Example #2 Advanced escaping using conditions
```php
<?php if ($expression == true): ?>
This will show if the expression is true.
<?php else: ?>
Otherwise this will show.
<?php endif; ?>
```

In this example PHP will skip the blocks where the condition is not met, even though they are outside of the PHP open/close tags; PHP skips them according to the condition since the PHP interpreter will jump over blocks contained within a condition that is not met.
For outputting large blocks of text, dropping out of PHP parsing mode is generally more efficient than sending all of the text through echo or print.

::: info Note
If PHP is embeded within XML or XHTML the normal PHP `<?php ?>` must be used to remain compliant with the standards.
:::

## Instruction Separation
As in C or Perl, PHP requires instructions to be terminated with a semicolon at the end of each statement. The closing tag of a block of PHP code automatically implies a semicolon; you do not need to have a semicolon terminating the last line of a PHP block. The closing tag for the block will include the immediately trailing newline if one is present.

### Example #1 Example showing the closing tag encompassing the trailing newline

```php
<?php echo "Some text"; ?>
No newline
<?= "But newline now" ?>
```

::: details Output of the above example in PHP 8.5.0
Some textNo newline
But newline now
:::

### Example #2 Examples of entering and exiting the PHP parser

```php
<?php
    echo "This is a test\n";
?>

<?php echo "This is a test\n" ?>

<?php echo "We omitted the last closing tag\n";
```
::: details Output of the above example in PHP 8.5.0
This is a test <br>
This is a test <br>
We omitted the last closing tag
:::

::: info Note
The closing tag of a PHP block at the end of a file is optional, and in some cases omitting it is helpful when using include or require, so unwanted whitespace will not occur at the end of files, and you will still be able to add headers to the response later. It is also handy if you use output buffering and would not like to see added unwanted whitespace at the end of the parts generated by the included files.
:::

## Comments
PHP supports 'C', 'C++' and Unix shell-style (Perl style) comments. For example:

### Example #1 Comments
```php
<?php
// This is a single-line comment
# This is also a single-line comment
/* This is a multi-line comment */
```
