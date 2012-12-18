# app.net

See https://github.com/appdotnet/api-spec.

Currently this is only non-authenticated APIs.

Endpoint: https://alpha-api.app.net

# User posts
## Request
````
GET /stream/0/users/{user-id}/posts
    ?[since_id={}]
    &[before_id={}]
    &[count={}]
    &[include_muted=0]
    &[include_deleted=1]
    &[include_directed_posts={}]
    &[include_machine=0]
    &[include_annotations=0]
    &[include_starred_by=0]
    &[include_reposters=0]
    &[include_user=0]
````

# Post
## Request
````
GET /stream/0/posts/{post_id}
````

# Global stream
## Request
````
GET /stream/0/posts/stream/global
    ?[since_id={}]
    &[before_id={}]
    &[count={}]
    &[include_muted=0]
    &[include_deleted=1]
    &[include_directed_posts={}]
    &[include_machine=0]
    &[include_annotations=0]
    &[include_starred_by=0]
    &[include_reposters=0]
    &[include_user=0]
````

# Tagged posts
## Request
````
GET /stream/0/posts/tag/{hashtag}
````

