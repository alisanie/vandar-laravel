# vandar-laravel
laravel library for vandar gateway

## Installation  
### step 1  
run this command :  
``composer require rfmhb2/vandar-laravel``  
### step 2  
add this to ``config/services.php``   
```php 
 'vandar' => [
        'api' => '6cc20e798ba30a2f352c0bf7ebfed11158af14b7',
        'test' => false
    ]
```
you can find your api in [vandar dashboard](https://dash.vandar.io).  
## Usage
Before you begin, add this code to  the top of the class
```php
use Vandar\Laravel\Facade\Vandar;
```
Then, you most send payment request like this
```php
$result = Vandar::request($amount, $mobile = null, $factorNumber = null, $description = null, $callback);
```
and save ``$result['token']`` for verify payment.  
now you can redirect user to gateway
```php
Vandar::redirect();
//or 
Vandar::redirectUrl();
```
After user made payment, vandar redirect user to ``$callback`` with a token in url. you can verify payment by pass token to verify method like this
```php
$token=$_GET['token'];
$result = Vandar::verify($token);
```
> you can read more about responses and api [here](https://docs.vandar.io/).
## bug report
if you find a bug add [issue](https://github.com/rfmhb2/vandar-laravel/issues)
