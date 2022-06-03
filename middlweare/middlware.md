<p>কাস্টম middleware তৈরি করার নিয়ম </p>
<p> step 1: প্রথমে একটা middleware তৈরি করতে হবে 
```php
 artisan make:middleware ExampleMiddlware
```
<p>Step2: app->http->kernel.php ফাইল এ গিয়া  middleware রেজিস্ট্রেশন করতে হবে। </p>
```php
 'test'=>\App\Http\Middleware\ExampleMiddlware::class
```
<p>middleware কল করতে হবে <p>
<p>****গ্রুপ middleware তৈরি করার ****</p>
```php
 Route::middleware()->group(function(){
     ///
 })
```

