Requests which require authentication assume that you have enqueued the client-js and therefore the following variables are localized:
WP_API_Settings.root
WP_API_Settings.nonce


### Get Recent Posts
```

    $.ajax({
            type: 'GET',
            url: WP_API_Settings.root + '/posts,
            dataType: 'json',
            success: function(posts){
                $.each( posts, function(index, post) {
                   //do something with each post
                });        
            },
            error: function(error){
                console.log(error);
            }
    });

```

### Get A Specific Post
```
    $.ajax({
            type: 'GET',
            url: WP_API_Settings.root + '/posts/42,
            dataType: 'json',
            success: function(post){
               //do something with posts       
            },
            error: function(error){
                console.log(error);
            }
    });

```

### Create A Post

```
    //create post data
    var post = array(
        'title' : 'Lord of the Rings',
        'post_type' : 'book',
        'content_raw' : 'Best book ever.'
    );
    
    //prepare data
    var data = JSON.stringify( post );
    
    
    $.ajax({
          type:"POST",
          url: WP_API_Settings.root + '/posts,
          dataType : 'json',
          data: data,
          beforeSend : function( xhr ) {
              xhr.setRequestHeader( 'X-WP-Nonce', JP_POST_EDITOR.nonce );
          },
          success: function(response) {
              alert( 'Post created. ID is ' + response.ID );
          },
          failure: function( response ) {
              alert( 'FAIL!' );
          }
    });
```

### Edit A Post

```
    //post data to edit
    var post = array(
        'title' : 'The Lord Of The Rings, Being the third part of the Lord of the Rings'
    );
    
    //prepare data
    var data = JSON.stringify( post );
    
    $.ajax({
          type:"POST",
          url: WP_API_Settings.root + '/posts/42,
          dataType : 'json',
          data: data,
          beforeSend : function( xhr ) {
              xhr.setRequestHeader( 'X-WP-Nonce', JP_POST_EDITOR.nonce );
          },
          success: function(response) {
              alert( 'Post ' + response.ID ' + ' updated succesfully.' );
          },
          failure: function( response ) {
              alert( 'FAIL!' );
          }
    });
```
