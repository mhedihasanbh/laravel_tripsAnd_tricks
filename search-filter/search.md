<?php

namespace App\Http\Controllers;

use App\Models\User;
use Illuminate\Http\Request;

class UserController extends Controller
{
    public function index()
    {
        $users = User::latest()->simplePaginate(20);

        return view('users',compact('users'));
    }

    public function filter(Request $request)
    {
        $users = User::query();

        $name = $request->name;
        $email = $request->email;
        $username = $request->username;
        $age = $request->age;

        if ($name) {
            $users->where('name','LIKE','%'.$name.'%');
        }
        if ($email) {
            $users->where('email','LIKE','%'.$email.'%');
        }

        if ($username) {
            $users->where('username','LIKE','%'.$username.'%');
        }

        if ($age) {
            $users->where('age',$age);
        }

        $data = [
            'age' => $age,
            'email' => $email,
            'name' => $name,
            'username' => $username,
            'users' => $users->latest()->simplePaginate(20),
        ];

        return view('users',$data);
    }
}

==============================================
laravel search filter
=============================================
step1:
            <form action="{{route('code.search')}}" method="get">
         
               <div class="form-group">
                 <input type="text" class="form-control" name="search" id="exampleInputEmail1" placeholder="Search your Problem" aria-describedby="emailHelp">
                 </div>
                 <div class="search_btn ">
                   <button type="submit" class="btn btn-primary  w-50">Search</button>
                 </div>
               
                </form>
				=================================================
				step2:
				Route::get('/search', 'App\Http\Controllers\SearchsController@search')->name('code.search');
				========================================================
				step3:
				public function search(Request $r){
        
        // if($request->isMethod('post')){
        //     $name=$request->get('search');
        //    return $questions=Question::where('title','LIKE','%'.$name.'%');
        //     return view('search.search',['questions'=>$questions]);
           

        // }
        //query for search
             $search_txt = $r->search;
         
              $questionsearchs =Question::orderBy('id', 'desc')
                ->where('title', 'LIKE', '%'.$search_txt.'%')
             ->paginate(3);

            

          
  
        return view('search.search',[
            'questionsearchs'=>$questionsearchs,
            
            
        ]);