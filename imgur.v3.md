# imgur

[Official documentation](http://api.imgur.com/)

Endpoint: https://api.imgur.com/3

# Authorization header

The value of the `Authorization` header should be the string
`"Client-ID <YOUR-CLIENT-ID>"`.


# Image
Get information about an image.

## Request:
````
GET /image/{id}
Authorization: {}
````

# Image Deletion
Delete an image with the deletehash that is returned to image owners.

## Request:
````
DELETE /image/{deletehash}
Authorization: {}
````

# Image Upload
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

### Parameters
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

# Update Image Information
Updates the title or description of an image. You can only update an
image you own and is associated with your account.

## Request:
````
PUT /image/{id}
    ?[key={}]
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
