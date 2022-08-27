<p><b>1.</b>একটা টেবিল এর সবগুলো ডাটা তুলে আনার জন্য এই কোয়েরি ব্যবহার করা হয়</p>
#####  $persons=person::all();
<p><b>2.</b>এই কোয়েরি টা ব্যবহার করলে ডেটাবেসে এ টেবিল এর শেষ id টা প্রথমে আসবে এবং সবগুলো ডাটা ওঠে আসবে</p>
##### $persons=person::orderBy('id','desc')->get();
<p><b>3.</b>এই কোয়েরি টা ব্যবহার করলে ডেটাবেসে এ টেবিল এর প্রথম যে ডাটা টা আছে তা ওঠে আসবে</p>
##### $persons=person::orderBy('id','asc')->first();
<p><b>4.</b>এই কোয়েরি টা ব্যবহার করলে ডেটাবেসে এ টেবিল এর মনে করেন আপনি প্রথম ৩টা ডাটা বাদে বাকি ২০টা ডাটা আনতে চান আপনি আনতে পারবেন এইভাবে</p>
##### $persons=person::orderBy('id','asc')->skip(3)->take(20)->get(); 
<p><b>5.</b>নিচের এই কোয়েরি টা ব্যবহার করলে ডেটাবেসে এ টেবিল name এর প্রথম অক্ষর ধরে আপনি ডাটা তুলে আনতে পারবেন</p>
##### $persons=person::where('name','torjo')->first(); 
<p><b>6.</b>একটা টেবিল প্রথম row টা তুলে আনার কোয়েরি </p>
##### $persons=Person::first();

==================================

```php
 $customers=DB::table(‘customers’)->where(‘votes’, ’<=’, ‘200’)->get();

Multiple where condition:
$customers=DB::table(‘customers’)
->where(‘votes’, ’>’, ‘150’)
->where(‘votes’, ’<’, ‘250’)
get();
```


<p>1.***যাদের vote ১৫০ এর বেশি এবং ২০০ কম তাদের ডাটা গুলো দেখাবে***</p>
```php
 Multiple where or condition:
$customers=DB::table(‘customers’)
->where(‘votes’, ’>’, ‘150’)
->orwhere(‘name’, ’<’, ‘sajib’)
get();
```

<p>2.**যাদের vote ১৫০ এর বেশি এবং এবং sajib নামে আছে  তাদের ডাটা গুলো দেখাবে***</p>
```php
 Wherte between condition:
$customers=DB::table(‘customers’)
->whereBetween(‘id’,[1,5])
get();

```

<p>3.**যাদের id ১,৫ এর ভিতর তাদের ডাটা শো করাবে***</p>
```php
 Limit condition:
$customers=DB::table(‘customers’)
->orderBy(‘id’,’DESC’)-
>limit(2)
get();


```

<p>4.***২ টা id দেখাবে 
***</p>
```php
 update condition:
$customers=DB::table(‘customers’)
->where(‘vote’,’150’)
->update([‘name’=>’bhuyan’])
```

<p>5.***যাদের ভোট ১৫০ তাদের নাম আপডেট করে bhuyan করে দিবে
***</p>
```php
 Updateor insert condition:
$customers=DB::table(‘customers’)
->updateOrInsert(
[‘email’=>’example@gmail.com’,’name’=>’sajib bhuyan’],
[‘votes’=>’11’]
);

```

<p>6.***যদি প্রথম কন্ডিশন টা খুজে পাই তাহলে পরের  কন্ডিশন টা আপডেট করবে আর যদি খুজে না পাই তাহলে সে প্রথম array  টা ইন্সার্ট করে দিবে
***</p>


