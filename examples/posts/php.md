Requests to the API, from within WordPress, or any other HTTP request should use [the WordPress HTTP API](http://codex.wordpress.org/HTTP_API).

All URLs should be constructed using either the function `json_url()` or `get_json_url()` when using multisite. These functions will return the root URL for the API, according to the current permalink structure. In addition, they will take into account the current value of the 'json_url' filter, which can be used to change the root url for the API.

The URL for the simplest request to the posts route, which would return the most recent posts, would be constructed with `json_url( 'posts' );`

### Get Most Recent Posts
* Number of posts will equal the posts_per_page option
``` php
    //create url
    $url = json_url( 'posts' );
    
    //Make request via the WordPress HTTP API
    $response = wp_remote_get( $url );
 
  
    //Check for error
    if ( ! is_wp_error( $response ) ) {
         //get just the body
         $data = wp_remote_retrieve_body( $response );
         
         //decode
         $data = json_decode( $data );
    }
    
 
}
```

### Get A Post By ID
* In this case post ID 42 will be retrieved.

``` php
    //create url
    $url = json_url( 'posts/42' );
    
    //Make request via the WordPress HTTP API
    $response = wp_remote_get( $url );
 
  
    //Check for error
    if ( ! is_wp_error( $response ) ) {
         //get just the body
         $data = wp_remote_retrieve_body( $response );
         
         //decode
         $data = json_decode( $data );
    }
    
 
}
```

### Use filters
In order to add filters to the request URL, use `add_query_args()` to generate the query string. In this 8 posts, in descending order, whose author has the username "fry" are returned:
``` php

    //build array of args
    $args = array( 
        'filter[author_name]' => 'fry',
        'filter[posts_per_page]' => 8,
        'filter[order]' => 'DESC'
    );
    
    $url = add_query_arg( $args, json_url( 'posts' ) );
    
    //Make request via the WordPress HTTP API
    $response = wp_remote_get( $url );
  
    //Check for error
    if ( ! is_wp_error( $response ) ) {
         //get just the body
         $data = wp_remote_retrieve_body( $response );
         
         //decode
         $data = json_decode( $data );
    }
```

### Create Post
* This example uses basic authentication. A more secure authentication method should be used in production environments:

    //set up post data
    $post = array(
        'title' => 'The Lord Of The Rings',
        'post_type' => 'book',
        'content' => 'Best book ever.'
    );
    //encode as JSON
    $post = json_encode( $post );
    
    //URL for posts route
    $url = json_url( 'posts' );
    
    //prepare headers with basic authentication
    $headers    = array (
        'Authorization' => 'Basic ' . base64_encode( 'admin' . ':' . 'password' ),
    );
    
    //prepare args for request
    $arg = array (
           'method'      => 'POST',
           'timeout'     => 45,
           'headers'     => $headers,
           'body'        => $post
    );
    
    //create post
    $response = wp_remote_post( $url, $args );
 
    if ( is_wp_error( $response ) ) {
       //it failed
       $id = false;
    }
    else {
        //success! get the ID of new post
        $post = json_decode( wp_remote_retrieve_body( $response ) );
        $id = $post[ 'id' ];
    }
```

### Update A Post
* Change the title of an existing post, in this case, post ID 42

``` php

//set up post data
    $post = array(
        'title' => 'The Lord Of The Rings, Being the third part of the Lord of the Rings',
    );
    //encode as JSON
    $post = json_encode( $post );
    
    //URL for this post
    $url = json_url( 'posts/42' );
    
    //prepare headers with basic authentication
    $headers    = array (
        'Authorization' => 'Basic ' . base64_encode( 'admin' . ':' . 'password' ),
    );
    
    //prepare args for request
    $arg = array (
           'method'      => 'POST',
           'timeout'     => 45,
           'headers'     => $headers,
           'body'        => $post
    );
    
    //create post
    $response = wp_remote_post( $url, $args );
 
    if ( is_wp_error( $response ) ) {
       //it failed
       $id = false;
    }
    else {
        //success! get the ID of new post
        $post = json_decode( wp_remote_retrieve_body( $response ) );
        $id = $post[ 'id' ];
    }
```


