---
layout: doc
title: Kohana Module - Codeception - Documentation
---

# Kohana Module

**For additional reference, please review the [source](https://github.com/Codeception/Codeception/tree/2.0/src/Codeception/Module/Kohana.php)**


This module provides integration with [Kohana](http://kohanaframework.org/) v3.
Functional tests can be run inside Kohana. All commands of this module are just the same as in other modules that share Framework interface.

### Status

* Maintainer: **Nikita Groshin**
* Stability: **alpha**
* Contact: nike-17@ya.ru

#### Installation

This module sets $_SERVER['KOHANA_ENV'] = 'testing'

1. Fix your bootstrap/index.php [like this](https://gist.github.com/2043592)
2. You need install this module https://github.com/nike-17/codeception-kohana
  or just fix your Cookie class like this https://github.com/nike-17/codeception-kohana/blob/master/classes/cookie.php 
3. if you have some problem pls feel free to ask me nike-17@ya.ru

Module is created by [Nikita Groshin](nike-17@ya.ru)




























#### amHttpAuthenticated
 
Authenticates user for HTTP_AUTH

 * `param` $username
 * `param` $password


#### amOnPage
 
Opens the page.
Requires relative uri as parameter

Example:

{% highlight php %}

<?php
// opens front page
$I->amOnPage('/');
// opens /register page
$I->amOnPage('/register');
?>

{% endhighlight %}

 * `param` $page






















#### attachFile
 
Attaches file from Codeception data directory to upload field.

Example:

{% highlight php %}

<?php
// file is stored in 'tests/_data/prices.xls'
$I->attachFile('input[@type="file"]', 'prices.xls');
?>

{% endhighlight %}

 * `param` $field
 * `param` $filename


#### checkOption
 
Ticks a checkbox.
For radio buttons use `selectOption` method.

Example:

{% highlight php %}

<?php
$I->checkOption('#agree');
?>

{% endhighlight %}

 * `param` $option


#### click
 
Perform a click on link or button.
Link or button are found by their names or CSS selector.
Submits a form if button is a submit type.

If link is an image it's found by alt attribute value of image.
If button is image button is found by it's value
If link or button can't be found by name they are searched by CSS selector.

The second parameter is a context: CSS or XPath locator to narrow the search.

Examples:

{% highlight php %}

<?php
// simple link
$I->click('Logout');
// button of form
$I->click('Submit');
// CSS button
$I->click('#form input[type=submit]');
// XPath
$I->click('//form/*[@type=submit]');
// link in context
$I->click('Logout', '#nav');
// using strict locator
$I->click(['link' => 'Login']);
?>

{% endhighlight %}

 * `param` $link
 * `param` $context






#### dontSee
 
Check if current page doesn't contain the text specified.
Specify the css selector to match only specific region.

Examples:

{% highlight php %}

<?php
$I->dontSee('Login'); // I can suppose user is already logged in
$I->dontSee('Sign Up','h1'); // I can suppose it's not a signup page
$I->dontSee('Sign Up','//body/h1'); // with XPath
?>

{% endhighlight %}

 * `param`      $text
 * `param null` $selector


#### dontSeeCheckboxIsChecked
 
Assert if the specified checkbox is unchecked.
Use css selector or xpath to match.

Example:

{% highlight php %}

<?php
$I->dontSeeCheckboxIsChecked('#agree'); // I suppose user didn't agree to terms
$I->seeCheckboxIsChecked('#signup_form input[type=checkbox]'); // I suppose user didn't check the first checkbox in form.
?>

{% endhighlight %}

 * `param` $checkbox


#### dontSeeCookie
 
Checks that cookie doesn't exist

 * `param` $cookie



#### dontSeeCurrentUrlEquals
 
Checks that current url is not equal to value.
Unlike `dontSeeInCurrentUrl` performs a strict check.

{% highlight php %}

<?php
// current url is not root
$I->dontSeeCurrentUrlEquals('/');
?>

{% endhighlight %}

 * `param` $uri


#### dontSeeCurrentUrlMatches
 
Checks that current url does not match a RegEx value

{% highlight php %}

<?php
// to match root url
$I->dontSeeCurrentUrlMatches('~$/users/(\d+)~');
?>

{% endhighlight %}

 * `param` $uri


#### dontSeeElement
 
Checks if element does not exist (or is visible) on a page, matching it by CSS or XPath
You can also specify expected attributes of this element.

Example:

{% highlight php %}

<?php
$I->dontSeeElement('.error');
$I->dontSeeElement('//form/input[1]');
$I->dontSeeElement('input', ['name' => 'login']);
$I->dontSeeElement('input', ['value' => '123456']);
?>

{% endhighlight %}

 * `param` $selector


#### dontSeeInCurrentUrl
 
Checks that current uri does not contain a value

{% highlight php %}

<?php
$I->dontSeeInCurrentUrl('/users/');
?>

{% endhighlight %}

 * `param` $uri


#### dontSeeInField
 
Checks that an input field or textarea doesn't contain value.
Field is matched either by label or CSS or Xpath
Example:

{% highlight php %}

<?php
$I->dontSeeInField('Body','Type your comment here');
$I->dontSeeInField('form textarea[name=body]','Type your comment here');
$I->dontSeeInField('form input[type=hidden]','hidden_value');
$I->dontSeeInField('#searchform input','Search');
$I->dontSeeInField('//form/*[@name=search]','Search');
$I->seeInField(['name' => 'search'], 'Search');
?>

{% endhighlight %}

 * `param` $field
 * `param` $value


#### dontSeeInTitle
 
Checks that page title does not contain text.

 * `param` $title



#### dontSeeLink
 
Checks if page doesn't contain the link with text specified.
Specify url to narrow the results.

Examples:

{% highlight php %}

<?php
$I->dontSeeLink('Logout'); // I suppose user is not logged in
?>

{% endhighlight %}

 * `param`      $text
 * `param null` $url


#### dontSeeOptionIsSelected
 
Checks if option is not selected in select field.

{% highlight php %}

<?php
$I->dontSeeOptionIsSelected('#form input[name=payment]', 'Visa');
?>

{% endhighlight %}

 * `param` $selector
 * `param` $optionText




#### fillField
 
Fills a text field or textarea with value.

Example:

{% highlight php %}

<?php
$I->fillField("//input[@type='text']", "Hello World!");
$I->fillField(['name' => 'email'], 'jon@mail.com');
?>

{% endhighlight %}

 * `param` $field
 * `param` $value










#### grabAttributeFrom
 
Grabs attribute value from an element.
Fails if element is not found.

{% highlight php %}

<?php
$I->grabAttributeFrom('#tooltip', 'title');
?>

{% endhighlight %}


 * `param` $cssOrXpath
 * `param` $attribute
 * `internal param` $element


#### grabCookie
 
Grabs a cookie value.

 * `param` $cookie



#### grabFromCurrentUrl
 
Takes a parameters from current URI by RegEx.
If no url provided returns full URI.

{% highlight php %}

<?php
$user_id = $I->grabFromCurrentUrl('~$/user/(\d+)/~');
$uri = $I->grabFromCurrentUrl();
?>

{% endhighlight %}

 * `param null` $uri

 * `internal param` $url


#### grabTextFrom
 
Finds and returns text contents of element.
Element is searched by CSS selector, XPath or matcher by regex.

Example:

{% highlight php %}

<?php
$heading = $I->grabTextFrom('h1');
$heading = $I->grabTextFrom('descendant-or-self::h1');
$value = $I->grabTextFrom('~<input value=(.*?)]~sgi');
?>

{% endhighlight %}

 * `param` $cssOrXPathOrRegex



#### grabValueFrom
 
 * `param` $field

@return array|mixed|null|string








#### resetCookie
 
Unsets cookie

 * `param` $cookie




#### see
 
Check if current page contains the text specified.
Specify the css selector to match only specific region.

Examples:

{% highlight php %}

<?php
$I->see('Logout'); // I can suppose user is logged in
$I->see('Sign Up','h1'); // I can suppose it's a signup page
$I->see('Sign Up','//body/h1'); // with XPath
?>

{% endhighlight %}

 * `param`      $text
 * `param null` $selector


#### seeCheckboxIsChecked
 
Assert if the specified checkbox is checked.
Use css selector or xpath to match.

Example:

{% highlight php %}

<?php
$I->seeCheckboxIsChecked('#agree'); // I suppose user agreed to terms
$I->seeCheckboxIsChecked('#signup_form input[type=checkbox]'); // I suppose user agreed to terms, If there is only one checkbox in form.
$I->seeCheckboxIsChecked('//form/input[@type=checkbox and @name=agree]');
?>

{% endhighlight %}

 * `param` $checkbox


#### seeCookie
 
Checks that cookie is set.

 * `param` $cookie



#### seeCurrentUrlEquals
 
Checks that current url is equal to value.
Unlike `seeInCurrentUrl` performs a strict check.

{% highlight php %}

<?php
// to match root url
$I->seeCurrentUrlEquals('/');
?>

{% endhighlight %}

 * `param` $uri


#### seeCurrentUrlMatches
 
Checks that current url is matches a RegEx value

{% highlight php %}

<?php
// to match root url
$I->seeCurrentUrlMatches('~$/users/(\d+)~');
?>

{% endhighlight %}

 * `param` $uri


#### seeElement
 
Checks if element exists on a page, matching it by CSS or XPath.
You can also specify expected attributes of this element.

{% highlight php %}

<?php
$I->seeElement('.error');
$I->seeElement('//form/input[1]');
$I->seeElement('input', ['name' => 'login']);
$I->seeElement('input', ['value' => '123456']);

// strict locator in first arg, attributes in second
$I->seeElement(['css' => 'form input'], ['name' => 'login']);
?>

{% endhighlight %}

 * `param` $selector
 * `param array` $attributes
@return


#### seeInCurrentUrl
 
Checks that current uri contains a value

{% highlight php %}

<?php
// to match: /home/dashboard
$I->seeInCurrentUrl('home');
// to match: /users/1
$I->seeInCurrentUrl('/users/');
?>

{% endhighlight %}

 * `param` $uri


#### seeInField
 
Checks that an input field or textarea contains value.
Field is matched either by label or CSS or Xpath

Example:

{% highlight php %}

<?php
$I->seeInField('Body','Type your comment here');
$I->seeInField('form textarea[name=body]','Type your comment here');
$I->seeInField('form input[type=hidden]','hidden_value');
$I->seeInField('#searchform input','Search');
$I->seeInField('//form/*[@name=search]','Search');
$I->seeInField(['name' => 'search'], 'Search');
?>

{% endhighlight %}

 * `param` $field
 * `param` $value


#### seeInTitle
 
Checks that page title contains text.

{% highlight php %}

<?php
$I->seeInTitle('Blog - Post #1');
?>

{% endhighlight %}

 * `param` $title



#### seeLink
 
Checks if there is a link with text specified.
Specify url to match link with exact this url.

Examples:

{% highlight php %}

<?php
$I->seeLink('Logout'); // matches <a href="#">Logout</a>
$I->seeLink('Logout','/logout'); // matches <a href="/logout">Logout</a>
?>

{% endhighlight %}

 * `param`      $text
 * `param null` $url


#### seeOptionIsSelected
 
Checks if option is selected in select field.

{% highlight php %}

<?php
$I->seeOptionIsSelected('#form input[name=payment]', 'Visa');
?>

{% endhighlight %}

 * `param` $selector
 * `param` $optionText



#### seePageNotFound
 
Asserts that current page has 404 response status code.


#### seeResponseCodeIs
 
Checks that response code is equal to value provided.

 * `param` $code



#### selectOption
 
Selects an option in select tag or in radio button group.

Example:

{% highlight php %}

<?php
$I->selectOption('form select[name=account]', 'Premium');
$I->selectOption('form input[name=payment]', 'Monthly');
$I->selectOption('//form/select[@name=account]', 'Monthly');
?>

{% endhighlight %}

Can select multiple options if second argument is array:

{% highlight php %}

<?php
$I->selectOption('Which OS do you use?', array('Windows','Linux'));
?>

{% endhighlight %}

 * `param` $select
 * `param` $option


#### sendAjaxGetRequest
 
If your page triggers an ajax request, you can perform it manually.
This action sends a GET ajax request with specified params.

See ->sendAjaxPostRequest for examples.

 * `param` $uri
 * `param` $params


#### sendAjaxPostRequest
 
If your page triggers an ajax request, you can perform it manually.
This action sends a POST ajax request with specified params.
Additional params can be passed as array.

Example:

Imagine that by clicking checkbox you trigger ajax request which updates user settings.
We emulate that click by running this ajax request manually.

{% highlight php %}

<?php
$I->sendAjaxPostRequest('/updateSettings', array('notifications' => true)); // POST
$I->sendAjaxGetRequest('/updateSettings', array('notifications' => true)); // GET


{% endhighlight %}

 * `param` $uri
 * `param` $params


#### sendAjaxRequest
 
If your page triggers an ajax request, you can perform it manually.
This action sends an ajax request with specified method and params.

Example:

You need to perform an ajax request specifying the HTTP method.

{% highlight php %}

<?php
$I->sendAjaxRequest('PUT', /posts/7', array('title' => 'new title');


{% endhighlight %}

 * `param` $method
 * `param` $uri
 * `param` $params


#### setCookie
 
Sets a cookie.

 * `param` $cookie
 * `param` $value




#### submitForm
 
Submits a form located on page.
Specify the form by it's css or xpath selector.
Fill the form fields values as array.

Skipped fields will be filled by their values from page.
You don't need to click the 'Submit' button afterwards.
This command itself triggers the request to form's action.

Examples:

{% highlight php %}

<?php
$I->submitForm('#login', array('login' => 'davert', 'password' => '123456'));


{% endhighlight %}

For sample Sign Up form:

{% highlight html %}

<form action="/sign_up">
    Login: <input type="text" name="user[login]" /><br/>
    Password: <input type="password" name="user[password]" /><br/>
    Do you agree to out terms? <input type="checkbox" name="user[agree]" /><br/>
    Select pricing plan <select name="plan"><option value="1">Free</option><option value="2" selected="selected">Paid</option></select>
    <input type="submit" value="Submit" />
</form>

{% endhighlight %}
I can write this:

{% highlight php %}

<?php
$I->submitForm('#userForm', array('user' => array('login' => 'Davert', 'password' => '123456', 'agree' => true)));


{% endhighlight %}
Note, that pricing plan will be set to Paid, as it's selected on page.

 * `param` $selector
 * `param` $params



#### uncheckOption
 
Unticks a checkbox.

Example:

{% highlight php %}

<?php
$I->uncheckOption('#notify');
?>

{% endhighlight %}

 * `param` $option

<p>&nbsp;</p><div class="alert alert-warning">Module reference is taken from the source code. <a href="https://github.com/Codeception/Codeception/tree/2.0/src/Codeception/Module/Kohana.php">Help us to improve documentation. Edit module reference</a></div>
