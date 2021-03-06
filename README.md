## Filipac CNP - Validare CNP
[![Build Status](https://travis-ci.org/filipac/cnp.svg)](https://travis-ci.org/laravel/framework)[![Latest Stable Version](https://poser.pugx.org/filipac/cnp/v/stable.svg)](https://packagist.org/packages/filipac/cnp) [![Total Downloads](https://poser.pugx.org/filipac/cnp/downloads.svg)](https://packagist.org/packages/filipac/cnp) [![Latest Unstable Version](https://poser.pugx.org/filipac/cnp/v/unstable.svg)](https://packagist.org/packages/filipac/cnp) [![License](https://poser.pugx.org/filipac/cnp/license.svg)](https://packagist.org/packages/filipac/cnp)

![Filipac/CNP](https://raw.githubusercontent.com/filipac/cnp/master/cnp.jpg)

### Cum instalez pachetul?
```
composer require filipac/cnp ~1.0
```
Sau introduceti in sectiunea require din ```composer.json```:
```json
"filipac/cnp": "~1.0"
```
[Instalare (tutorial Youtube)](https://www.youtube.com/watch?v=DlHQKygnd_E)

### Cum folosesc acest pachet?
Clasa ```Cnp``` are 2 metode publice statice: ```valid``` care returneaza un boolean (true, false). Este disponibila si functia
```invalid``` care este practic functia valid, dar negata.
```php
<?php
use Filipac\Cnp\Cnp;
if(Cnp::valid('1930101021162')) #true
	echo 'Cnp-ul este valid';
if(! Cnp::valid('1930101021161')) #false
   echo 'Cnp-ul este invalid';
if(Cnp::invalid('1930101021161')) #true
	echo 'Cnp-ul este invalid';
if(!Cnp::invalid('1930101021162')) #false
	echo 'Cnp-ul este valid';
?>
```
Incepand de la versiune **1.0.3** am introdus si un ServiceProvider pentru Laravel 5 in caz ca vreti sa folositi acest validator la un form. Tot ce trebuie sa faceti este sa puneti in ```app.php``` urmatorul service provider: ```'Filipac\Cnp\Laravel\CnpValidatorProvider',``` dupa care puteti sa folositi validatorul la orice FormRequest sau Validator in felul urmator:
```php
public function rules()
	{
		return [
			'cnp' => 'required|max:13|cnp',
		];
	}
```
sau
```php
Validator::make($data, [
			'cnp' => 'required|max:13|cnp',
		])
```
### Cum sa contribui?
Daca ai idei de imbunatatire a acestui script, da fork acestui repository, fa modificarile necesare si apoi da un pull-request.
Nu uita sa scrii un test (vezi ```tests/CnpTest.php```) pentru ce ai implementat, altfel nu voi accepta request-ul.
Testarea se face cu **PhpUnit**.

### Licenta

Acest script este distribuit sub [licenta MIT](http://opensource.org/licenses/MIT).
