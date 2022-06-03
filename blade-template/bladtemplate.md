```php
@forelse($posts as $post)
<div class="post"> 
  <h2>{{$post->tittle}</h2>}
  <p>{{$post->description}}</p>
</div>
@empty
<h2>No Post Found</h2>
@endforelse
```
<p>***forelse এবং foreach একই কাজ foreach শুধু ডাটা দেখাবে এবং forelse ডাটা দেখাবে তার সাথে যদি ডাটা না পাই তাহলে সে একটা মেসেজ ও দিবে  ***</p>