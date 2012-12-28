# imgur

[Official documentation](http://api.imgur.com/)

Endpoint: https://api.imgur.com/3

# Authorization header

The value of the `Authorization` header should be the string
`"Client-ID <YOUR-CLIENT-ID>"`.


------------------------------------------------------------------------------
<!-- Account -->

# Current Account

To make requests for the current account, you may use `me` as the
`{username}` parameter. For example,
`https://api.imgur.com/3/account/me/images` will request all the
images for the account that is currently authenticated.

# account

Request standard user information. If you need the username for the
account that is logged in, it is returned in the request for an
[access token](/oauth2/#token).

## Request:
````
GET /account/{username}
Authorization: {}
````


# account-create

Create a new user on Imgur.

Note: You </strong> you **MUST** send recaptcha information with this
request.

Use this as the public captcha key:
`6Lf7R8USAAAAAIkTcbhc8Di49orfHUuExshF9z8I`.

## Request:
````
POST /account/{username}
Authorization: {}
````


# account-delete

Delete a user account, you can only access this if you're logged in as
the user.

## Request:
````
DELETE /account/{username}
Authorization: {}
````


# account-likes

Return an array of images that have been upvoted by the user.

## Reqest:
````
GET /account/{username}/likes
Authorization: {}
````


# account-submissions

Return the images a user has submitted to the gallery.

## Request:
````
GET /account/{username}/submissions/{page}
Authorization: {}
````


# account-settings

Returns the account settings, only accessible if you're logged in as the user.

## Request:
````
GET /account/{username}/settings
Authorization: {}
````


# account-stats

Return the statistics about the account.

## Request:
````
GET /account/{username}/stats
Authorization: {}
````


# account-profile

Returns the totals for the gallery profile.

## Request:
````
GET /account/{username}/gallery_profile
Authorization: {}
````


# account-albums

Get all the albums associated with the account. Must be logged in as
the user to see secret and hidden albums.

## Request:
````
GET /account/{username}/albums/{page}
Authorization: {}
````

### Parameters
<table>
  <tbody><tr class="header">
      <td>Key</td>
      <td>Required</td>
      <td>Description</td>
    </tr>
    <tr>
      <td>page</td>
      <td>optional</td>
      <td>integer - allows you to set the page number so you don't have to retrieve all the data at once.</td>
    </tr>
</tbody></table>


# account-get-album

Get additional information about an album, this endpoint works the
same as the Album endpoint. You can also use any of the additional
routes that are used on an album in the Album endpoint.

## Request:
````
GET /account/{username}/album/{id}
Authorization: {}
````


# album-ids

Return an array of all of the album IDs.

## Request:
````
GET /account/{username}/albums/ids
Authorization: {}
````


# album-count

Return the total number of albums associated with the account.

## Request:
````
GET /account/{username}/albums/count
Authorization: {}
````


# account-album-delete

Delete an Album with a given id.

## Request:
````
DELETE /account/{username}/album/{id}
Authorization: {}
````


# comments

Return the comments the user has created.

## Request:
````
GET /account/{username}/comments
Authorization: {}
````


# comment

Return information about a specific comment. This endpoint works the
same as the Comment endpoint. You can use any of the additional
actions that the comment endpoint allows on this end point.

## Request:
````
GET /account/{username}/comment/{id}
Authorization: {}
````


# comment-ids

Return an array of all of the comment IDs.

## Request:
````
GET /account/{username}/comments/ids
Authorization: {}
````


# comment-count

Return a count of all of the comments associated with the account.

## Request:
````
GET /account/{username}/comments/count
Authorization: {}
````


# account-comment-delete

Delete a comment. You are required to be logged in as the user whom
created the comment.

## Request:
````
DELETE /account/{username}/comment/{id}
Authorization: {}
````


# images

Return all of the images associated with the account. You
can page through the images by setting the page, this
defaults to 0.

## Request:
````
GET /account/{username}/images/{page}
Authorization: {}
````


# account-image

Return information about a specific image. This endpoint works the
same as the Image Endpoint.  You can use any of the additional actions
that the image endpoint with this endpoint.

## Request:
````
GET /account/{username}/image/{id}
Authorization: {}
````


# image-ids

Returns an array of Image IDs that are associated with the account.

## Request:
````
GET /account/{username}/images/ids
Authorization: {}
````


# image-count

Returns the total number of images associated with the account.

## Request:
````
GET /account/{username}/images/count
Authorization: {}
````


# account-image-delete

Deletes an Image. This requires a delete hash rather than an ID.

## Request:
````
DELETE /account/{username}/image/{deletehash}
Authorization: {}
````


# account-notifications

Return all of the notifications associated with the account.  Defaults
to return only new notifications, however you can set the GET
variable, new, to false to return all of the notifications. You're
required to be logged in as the user to view this information.

## Request:
````
GET /account/{username}/notifications
    ?[new=true]
Authorization: {}
````

### Parameters
<table>
  <tbody><tr class="header">
      <td>Key</td>
      <td>Required</td>
      <td>Value</td>
    </tr>
    <tr>
      <td>new</td>
      <td>optional</td>
      <td>boolean - false for all notifications, true for only non-viewed notification. Default is true.</td>
    </tr>
</tbody></table>


# account-messages

Returns all messages sent to the user, formatted as a
notification. Required to be logged in to view this information.

## Request:
````
GET /account/{username}/notifications/messages
    ?[new=true]
Authorization: {}
````

### Parameters
<table>
  <tbody><tr class="header">
      <td>Key</td>
      <td>Required</td>
      <td>Value</td>
    </tr>
    <tr>
      <td>new</td>
      <td>optional</td>
      <td>boolean - false for all notifications, true for only non-viewed notification. Default is true.</td>
    </tr>
</tbody></table>

# messages-send

Send a message to the user in the URL from the user that's currently
logged in.  Set the variables subject (the subject of the message) and
body (the body of the message) accordingly.  A user must be logged in
to send a message to another user.

## Request:
````
POST /account/{username}/message
    ?body={}
    &[subject={}]
    &[parent_id={}]
Authorization: {}
````

### Parameters
<table>
  <tbody><tr class="header">
      <td>Key</td>
      <td>Required</td>
      <td>Value</td>
    </tr>
    <tr>
      <td>body</td>
      <td>required</td>
      <td>The text of the message. Similar to the body of an email.</td>
    </tr>
    <tr>
      <td>subject</td>
      <td>optional</td>
      <td>The subject of the message</td>
    </tr>
    <tr>
      <td>parent_id</td>
      <td>optional</td>
      <td>The ID of the first message in the thread, by setting this, the message will be threaded to the given message.</td>
    </tr>
</tbody></table>

# replies

Returns all of the reply notifications for the user.  Required to be
logged in as that user.

## Request:
````
GET /account/{username}/notifications/replies
    ?[new=true]
Authorization: {}
````

### Parameters
<table>
  <tbody><tr class="header">
      <td>Key</td>
      <td>Required</td>
      <td>Value</td>
    </tr>
    <tr>
      <td>new</td>
      <td>optional</td>
      <td>boolean - false for all notifications, true for only non-viewed notification. Default is true.</td>
    </tr>
</tbody></table>

------------------------------------------------------------------------------
<!-- Album -->

# album-get

Get information about a specific album.

## Request:
````
GET /album/{id}
Authorization: {}
````

# album-images

Return all of the images in the album</p>

## Request:
````
GET /album/{id}/images
Authorization: {}
````

# album-image

Get information about an image in an album, any additional actions
found in `Image Endpoint` will also work.

## Request:
````
GET /album/{id}/image/{id}
Authorization: {}
````

# album-upload

Create a new album. optional parameter of ids[] is an array of image
ids to add to the album.

## Request:
````
POST /album/
    ?[ids={}]
    &[title={}]
    &[description={}]
    &[cover={}]
Authorization: {}
````

## Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>ids[]</td>
        <td>optional</td>
        <td>The image ids that you want to be included in the album.</td>
      </tr>
      <tr>
        <td>title</td>
        <td>optional</td>
        <td>The title of the album</td>
      </tr>
      <tr>
        <td>description</td>
        <td>optional</td>
        <td>The description of an album</td>
      </tr>
      <tr>
        <td>cover</td>
        <td>optional</td>
        <td>The ID of an image that you want to be the cover of the album</td>
      </tr>
  </tbody></table>
</div>

# album-update

Update the information of an album.</p>

## Request:
````
PUT /album/{id}
    ?[ids={}]
    &[title={}]
    &[description={}]
    &[cover={}]
Authorization: {}
````

## Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>ids[]</td>
        <td>optional</td>
        <td>The image ids that you want to be included in the album.</td>
      </tr>
      <tr>
        <td>title</td>
        <td>optional</td>
        <td>The title of the album</td>
      </tr>
      <tr>
        <td>description</td>
        <td>optional</td>
        <td>The description of an album</td>
      </tr>
      <tr>
        <td>cover</td>
        <td>optional</td>
        <td>The ID of an image that you want to be the cover of the album</td>
      </tr>
  </tbody></table>
</div>

# album-delete

Delete an album with a given ID.  You are required to be logged in as
the user to delete the album.

## Request:
````
DELETE /album/{id}
Authorization: {}
````

# album-set-to

Sets the images for an album, removes all other images and only uses the images in this request.

## Request:
````
POST /album/{id}/
    ?ids={}
Authorization: {}
````

## Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>ids[]</td>
        <td>required</td>
        <td>The image ids that you want to be added to the album.</td>
      </tr>
  </tbody></table>
</div>

# album-add-to

Takes parameter, ids[], as an array of ids to add to the album.

## Request:
````
POST /album/{id}/add
    ?ids={}
Authorization: {}
````

## Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>ids[]</td>
        <td>required</td>
        <td>The image ids that you want to be added to the album.</td>
      </tr>
  </tbody></table>
</div>

# album-remove-from

Takes parameter, ids[], as an array of ids and removes from the labum.

## Request:
````
DELETE /album/{id}
    ?ids={}
Authorization: {}
````

## Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>ids[]</td>
        <td>required</td>
        <td>The image ids that you want to be added to the album.</td>
      </tr>
  </tbody></table>
</div>

------------------------------------------------------------------------------
<!-- Comment -->

# comment" class="textbox">

Get information about a specific comment.

## Request:
````
GET /comment/{id}
Authorization: {}
````

# comment-create

Creates a new comment, returns the ID of the comment.

## Request:
````
POST /comment
    ?image_id={}
    &comment={}
    &[parent_id={}]
Authorization: {}
````

  <span>Parameters</span>
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>image_id</td>
        <td>required</td>
        <td>The ID of the image in the gallery that you wish to comment on</td>
      </tr>
      <tr>
        <td>comment</td>
        <td>required</td>
        <td>The comment text, this is what will be displayed</td>
      </tr>
      <tr>
        <td>parent_id</td>
        <td>optional</td>
        <td>The ID of the parent comment, this is an alternative method to create a reply.</td>
      </tr>
  </tbody></table>


# comment-delete

Delete a comment by the given id.

## Request:
````
DELETE /comment/{id}
Authorization: {}
````


# comment-replies

Get the comment with all of the replies for the comment.

## Request:
````
GET /comment/{id}/replies
Authorization: {}
````


# comment-vote

Vote on a comment. The {vote} variable can only be set as "up" or "down".

## Request:
````
POST /comment/{id}/vote/{vote}
Authorization: {}
````


# comment-report

Report a comment for being inappropriate.

## Request:
````
POST /comment/{id}/report
Authorization: {}
````


# comment-reply-create

Create a reply for the given comment.

## Request:
````
POST /comment/{id}
    ?image_id={}
    &comment={}
Authorization: {}
````

  <span>Parameters</span>
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>image_id</td>
        <td>required</td>
        <td>The ID of the image in the gallery that you wish to comment on</td>
      </tr>
      <tr>
        <td>comment</td>
        <td>required</td>
        <td>The comment text, this is what will be displayed</td>
      </tr>
  </tbody></table>

------------------------------------------------------------------------------
<!-- Gallery -->

# gallery

Returns the images in the gallery. For example the main gallery is
`https://api.imgur.com/3/gallery/hot/viral/0.json`.

## Request:
````
GET /gallery/{section}/{sort}/{page}
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>section</td>
        <td>optional</td>
        <td>viral | score | time - defaults to viral</td>
      </tr>
      <tr>
        <td>sort</td>
        <td>optional</td>
        <td>hot | top | new - defaults to hot</td>
      </tr>
      <tr>
        <td>page</td>
        <td>optional</td>
        <td>integer - the data paging number</td>
      </tr>
  </tbody></table>
</div>

# subreddit

View gallery images for a sub-reddit

## Request:
````
GET /gallery/r/{subreddit}/{sort}/{page}
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>subreddit</td>
        <td>required</td>
        <td>pics - A valid sub-reddit name</td>
      </tr>
      <tr>
        <td>sort</td>
        <td>optional</td>
        <td>hot | new - defaults to hot</td>
      </tr>
      <tr>
        <td>page</td>
        <td>optional</td>
        <td>integer - the data paging number</td>
      </tr>
  </tbody></table>
</div>

# gallery-serach

Search the gallery with a given query string.

## Request:
````
GET /gallery/search
    ?q={}
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>q</td>
        <td>required</td>
        <td>Query string</td>
      </tr>
  </tbody></table>
</div>

# to-gallery

Add an Album or Image to the Gallery.

## Request:
````
POST /gallery/image/{id}
    ?title={}
    &[terms={}]
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>title</td>
        <td>required</td>
        <td>The title of the image. This is required.</td>
      </tr>
      <tr>
        <td>terms</td>
        <td>optional</td>
        <td>If the user has not accepted our terms yet, this endpoint will return an error. To by-pass the terms in general simply set this value to 1.</td>
      </tr>
  </tbody></table>
</div>


# album

Get additional information about an album in the gallery.

## Request:
````
GET /gallery/album/{id}
Authorization: {}
````

# gallery-image

Get additional information about an image in the gallery.

## Request:
````
GET /gallery/image/{id}
Authorization: {}
````

# gallery-reporting

Report an Image in the gallery

## Request:
````
POST /3/gallery/{id}/report
Authorization: {}
````

# gallery-votes

Get the vote information about an image

## Request:
````
GET /gallery/album/{id}/votes
Authorization: {}
````

# gallery-voting

Vote for an image, up or down vote

## Request:
````
POST /gallery/album/{id}/vote/{vote}
Authorization: {}
````

# gallery-comments

Comment on an image in the gallery.

## Request:
````
GET /gallery/album/{id}/comments
Authorization: {}
````

# gallery-comment

Information about a specific comment.  This action also allows any of
the additional actions provided in the `Comment Endpoint`.

## Request:
````
GET /gallery/album/{id}/comment/{id}
Authorization: {}
````

# gallery-comment-creation

Create a comment for an image.

## Request:
````
POST /gallery/album/{id}/comment
    ?comment={}
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>comment</td>
        <td>required</td>
        <td>The text of the comment.</td>
      </tr>
  </tbody></table>
</div>

# gallery-comment-reply

Reply to a comment that has been created for an image.

## Request:
````
POST /gallery/album/{id}/comment/{id}
    ?comment={}
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>comment</td>
        <td>required</td>
        <td>The text you want to use as the reply.</td>
      </tr>
  </tbody></table>
</div>

# gallery-comment-ids

List all of the IDs for the comments on an image.

## Request:
````
GET /gallery/album/{id}/comments/ids
Authorization: {}
````

# gallery-comment-count

The number of comments on an Image.

## Request:
````
GET /gallery/album/{id}/comments/count
Authorization: {}
````

------------------------------------------------------------------------------
<!-- Image -->

# image

Get information about an image.

## Request:
````
GET /image/{id}
Authorization: {}
````

# image-delete

Delete an image with the deletehash that is returned to image owners.

## Request:
````
DELETE /image/{deletehash}
Authorization: {}
````
  
# image-upload


Upload a new image.

## Request:
````
POST /image
    ?image={}
    &[album_id={}]
    &[type={}]
    &[name={}]
    &[title={}]
    &[description={}]
Authorization: {}
````

### Parameters:
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>image</td>
        <td>required</td>
        <td>A binary file, base64 data, or a URL for an image</td>
      </tr>
      <tr>
        <td>album_id</td>
        <td>optional</td>
        <td>The id of the album you want to add the image to</td>
      </tr>
      <tr>
        <td>type</td>
        <td>optional</td>
        <td>The type of the file that's being sent; file, base64 or URL</td>
      </tr>
      <tr>
        <td>name</td>
        <td>optional</td>
        <td>The name of the file, this is automatically detected if uploading a file with a POST and multipart / form-data</td>
      </tr>
      <tr>
        <td>title</td>
        <td>optional</td>
        <td>The title of the image.</td>
      </tr>
      <tr>
        <td>description</td>
        <td>optional</td>
        <td>The description of the image.</td>
      </tr>
  </tbody></table>
</div>

# image-update

Updates the title or description of an image. You can only update an
image you own and is associated with your account.

## Request:
````
PUT /image/{id}
    ?[title={}]
    &[description={}]
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>title</td>
        <td>optional</td>
        <td>The title of the image.</td>
      </tr>
      <tr>
        <td>description</td>
        <td>optional</td>
        <td>The description of the image.</td>
      </tr>
  </tbody></table>

------------------------------------------------------------------------------
<!-- Message -->

# messages

Get one message from every thread the user has received.  For example
if a user has 5 messages, but 3 of them are on the same thread there
will be 3 messages returned.

## Request:
````
GET /messages
Authorization: {}
````


# messages-ids

Returns an array of the message ids, this also limited and is
paged.

## Request:
````
GET /messages/ids/{page}
Authorization: {}
````


# messages-count

Return the total count of messages for the user.

## Request:
````
GET /messages/count
Authorization: {}
````


# message

Get information about a specific message

## Request:
````
get /message/{id}
Authorization: {}
````


# message-thread

Get a specific message and the rest of the conversation with that
message. The message ID sent needs to be the parent id.  This is the
same id as the first message in the thread.

## Request:
````
GET /message/{id}/thread
Authorization: {}
````


# message-create

Create a new message.

## Request:
````
POST /message
    ?recipient={}
    &body={}
    &[subject={}]
    &[parent_id={}]
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Description</td>
      </tr>
      <tr>
        <td>recipient</td>
        <td>required</td>
        <td>The recipient username, this person will receive the message</td>
      </tr>
      <tr>
        <td>body</td>
        <td>required</td>
        <td>The message itself, similar to the body of an email.</td>
      </tr>
      <tr>
        <td>subject</td>
        <td>optional</td>
        <td>The subject of the message, this is not required</td>
      </tr>
      <tr>
        <td>parent_id</td>
        <td>optional</td>
        <td>If this message is in reply to another message set the parent_id to message id of the initial message.</td>
      </tr>
  </tbody></table>
</div>

# message-delete

Delete a message by the given ID.

## Request:
````
DELETE /message/{id}
Authorization: {}
````


# message-report

Report a user for sending messages that are against the Terms of
Service.

## Request:
````
POST /message/report/{username}
Authorization: {}
````


# message-block

Block the user from sending messages to the user that is logged in.

## Request:
````
POST /message/block/{username}
Authorization: {}
````

------------------------------------------------------------------------------
<!-- Notification -->

# notifications

Get all notifications for the user that's currently logged in.

## Request:
````
GET /notification
    ?[new={}]
Authorization: {}
````

### Parameters
  <table>
    <tbody><tr class="header">
        <td>Key</td>
        <td>Required</td>
        <td>Value</td>
      </tr>
      <tr>
        <td>new</td>
        <td>optional</td>
        <td>boolean - false for all notifications, true for only non-viewed notification. Default is true.</td>
      </tr>
  </tbody></table>


# notification

Returns the data about a specific notification</p>

## Request:
````
GET /notification/{id}
Authorization: {}
````


# notification-viewed

Marks a notification as viewed, this way it no longer shows up in the
basic notification request.

## Request:
````
PUT /notification/{id}
Authorization: {}
````

------------------------------------------------------------------------------

# credits

Check your rate limits.

## Request:
````
GET /credits
Authorization: {}
````
