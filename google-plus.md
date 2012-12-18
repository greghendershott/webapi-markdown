# Google+

See <https://developers.google.com/+/api/>.

Endpoint: https://www.googleapis.com

# Get person

Get a person's profile.

If using the userId value "me", this method requires authentication
using a token that has been granted the OAuth scope
https://www.googleapis.com/auth/plus.me. Read more about
[OAuth](https://developers.google.com/+/api/oauth.html).

## Request:

````
GET /plus/v1/people/{userId}
    ?key={}
    &[maxResult=20]
    &[pageToken={}]
    &[calalback={}]
    &[fields={}]
    &[prettyPrint=true]
    &[userIp={}]
````

# Search people

## Request

````
GET /plus/v1/people
    ?key={}
    &query={}
    &[language={}]
    &[maxResults=10]
    &[pageToken={}]
    &[prettyPrint=true]
````

## Response

If successful, this method returns a response body with the following
structure:

    {
      "kind": "plus#peopleFeed",
      "etag": etag,
      "selfLink": string,
      "title": string,
      "nextPageToken": string,
      "items": [
        people Resource
      ]
    }

`kind` `string`: Identifies this resource as a collection of
people. Value: "plus#peopleFeed".

`selfLink` `string`: Link to this resource.

`title` `string`: The title of this collection of people.

`nextPageToken` `string`: The continuation token, used to page through
large result sets. Provide this value in a subsequent request to
return the next page of results.

`items[]` `list`: The people in this page of results. Each item will
include the id, displayName, image, and url for the person. To
retrieve additional profile data, see the people.get method.

`etag` `etag`: ETag of this response for caching purposes.


# People activity

List all of the people in the specified collection for a particular
activity.

The collection parameter specifies which people to list, such as
people who have +1'd or reshared this activity. For large collections,
results are paginated.

Each item in the response of this method contains basic fields of a
person resource, including id, displayName, image, and url. To get a
full person resource, use `Get person`.

## Request

````
GET /plus/v1/activities/{activityId}/people/{collection}
    ?key={}
    &[maxResults=10]
    &[pageToken={}]
    &[prettyPrint=true]
````

- `activityId` `string`: The ID of the activity to get the list of
  people for.

- `collection` `string`: The collection of people to list. Acceptable
  values are:

  - `"plusoners"` - List all people who have +1'd this activity.

  - `"resharers"` - List all people who have reshared this activity.

## Response

Response

If successful, this method returns a response body with the following
structure:

    {
      "kind": "plus#peopleFeed",
      "etag": etag,
      "selfLink": string,
      "title": string,
      "nextPageToken": string,
      "items": [
        people Resource
      ]
    }

# Activity list

List all of the activities in the specified collection for a
particular user.

The collection parameter specifies which activities to list, such as
public activities. For large collections, results are paginated.

If using the userId value "me", this method requires authentication
using a token that has been granted the OAuth scope
https://www.googleapis.com/auth/plus.me. Read more about
[OAuth](https://developers.google.com/+/api/oauth.html).

## Request
````
GET /plus/v1/people/{userId}/activities/{collection}
    ?key={}
    &[maxResults=10]
    &[pageToken={}]
    &[prettyPrint=true]
````

`collection` `string` The collection of activities to list. Acceptable
values are: `"public"` - All public activities created by the specified
user.

`userId` `string` The ID of the user to get activities for. The
special value `"me"` can be used to indicate the authenticated user.
