PasswordStrength Package
================

This package provides a validator that ensures strong passwords in Laravel 4 applications. It is influenced  a lot by [PasswordStrengthBundle for Symfony 2](https://github.com/jbafford/PasswordStrengthBundle).

It is in a early stage of development but should fulfill its purpose.

This Validations provided include:

- contains alphabetic characters
- contains numeric characters
- contains mixed case characters

#History
- **[0.4.1]** The package works properly now when other extensions of laravel's validator are implemented (like [unique-with](https://github.com/felixkiss/uniquewith-validator)). Unfortunately the implementation of localized response messages didn't work out, so they are english only untill now. If someone has an idea how to solve this problem, just let me know. 
- **[0.3.1]** Fixed: Package validator doesn't overwrite custom validation errror messages any more. Not functional tested though because I have no clue how to set up a test which controls the passing of variables from the password strength package to the native validator INSIDE the package's test folders. Any suggestions?

#Documentation

##Installation

### Get the package

Add the following in your `composer.json`:

``` json
{
    "require": {
        "schuppo/password-strength": "dev-master"
    }
}
```
Notice that you have to set in ```composer.json```
``` json
"minimum-stability": "dev"
```
Because it is in such an early stage it is not a good idea to use it in production environments. Seriously. (By the way, this is my first contribution on GitHub and to Laravel so don't be too harsh.)
If you trust me that the code is unit tested you don't have to download the package's dev dependencies. Updating the application with `composer udate --no-dev` is best choice then.

### Initialize the package

To start using the package, you have to add it to the arraykey ```providers`` in ```app/config/app.php```:

``` php
// app/config/app.php

return array(

    // ...

    'providers' => array(

        // ...

        'Schuppo/PasswordStrength/PasswordStrengthServiceProvider',
    );

    // ...
);
```


##Usage
Now Laravel's native ```Validator``` class is extended by three rules:

- case_diff
- numbers
- letters

### Example
You can apply these rules as described in the [validation section on Laravel's website](http://laravel.com/docs/validation)
``` php

$v = Validator::make(
    'password' => '12345QWERTqwert',
    'password' => 'case_diff|numbers|letters')
);

$v->passes();   // returns true;
```

Notice that you can validate any value with the new rules. This only reason why this package is called "Password Strength Package" is that it describes its foremose purpose.



#License

This package is under the MIT license. See the complete license:

- [LICENSE](https://github.com/schuppo/PasswordStrengthPackage/LICENSE)


##Reporting Issues or Feature Requests

Issues and feature requests are tracked on [GitHub](https://github.com/schuppo/PasswordStrengthPackage/issues).
