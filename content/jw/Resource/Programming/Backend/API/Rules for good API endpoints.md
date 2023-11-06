## Introduction
Naming your [[API]] properly is the first step in designing a good API. When the API name follows a convention, it provides lots of information about the API and its purposes.
## ✅ Rule 1: In lowercase, with hyphens and not abridged
The URI of your API rules are:
- should always be lowercase.
- Separate multiple words using [[hyphens]], not underscores.
- Do not keep abridged, or shortened, words in your URI.
- If your API accepts a variable, you should always represent it in camelCase, and wrap it inside a set of `{}`.

Examples:

| 👎 Bad | 👍 Good |
|:---- | :---------|
|`/Customers`|`/customers`|
| `/generalMembers` | `/general-members` |
| `/MenuItems` | `/menu-items` |
| `/customers/15/tel-no` | `/customers/15/telephone-number` |
| `/customers/13/phone_number` | `/customers/13/phone-number` |
| `/customers/13/phonenumber` | `/customers/13/phone-number` |
| `/users/{user-id}` | `/users/{userId}` |
## ✅ Rule 2: Use a forward slash to indicate a hierarchical relationship
In your API [[URI]], always use the forward slash to indicate a hierarchical relationship.

Example scenarios:
- A store can have customers who have placed many orders and each of these orders can have delivery addresses, menu items and bills.
	- `/store/customers/{customerId}/orders`
	- `/store/orders/{orderId}`
	- `/store/orders/{orderId}/menu-items`
- A library can have books from many authors. ISBN number for each book.
	- `/library/authors/books
	- `/library/book/{bookId}/isbn`

## ✅ Rule 3: Use nouns for resource names, not verbs
One of the most prominent features of [[ReST]] APIs is that it uses __nouns__ to indicate resources, not __verbs__. You should also use plural nouns to indicate a collection.

Examples:

| 👎 Bad | 👍 Good |
|:---- | :---------|
| `/order` | `/orders` |
|`/getOrder`| `/orders`|
| `/getUser/{userId}` | `/users/{userId}`|

## ✅ Rule 4: Avoid special characters
You should always avoid special characters in your API endpoints. They can be confusing and technically complex for your users.
Examples:

| 👎 Bad | 👍 Good |
|:---- | :---------|
|`/users/12:24:25/address` | `/users/12,23,24/address`|
| `/orders/16/menu^items`||

## ✅ Rule 5: Avoid file extensions in URI

| 👎 Bad | 👍 Good |
|:---- | :---------|
| `/sports/basketball/teams/{teamId}.json` | `/sports/basketball/teams/{teamId}?format=json`|
| `/sports/basketball/teams/{teamId}.xml` | `/sports/basketball/teams/{teamId}?format=xml` |

If your API is serving a static file, such as CSS or JavaScript files, you should use endpoints like the followings:
- `/assets/js/jquery/3.12/min`
- `/assets/js/jquery/3.12/source`
- `/assets/js/jquery/3.12/?format=min`
- `/assets/js/jquery/3.12/?format=source`
- `/menu-items?format=json`

## ✅ Use query parameters to filter when necessary
When designing your API, you should always perform data filtering using a query string. This is the same when you expect some extra parameters, like the number of items per page and page number.

| 👎 Bad | 👍 Good |
|:---- | :---------|
| `/users/{userId}/locations/USA` | `/users/{userId}/locations?country=USA`|
| `/articles/page/2/items-per-page/10` | `/articles?page=2&per-page=10` |

## ✅ No trailing slash

| 👎 Bad | 👍 Good |
|:---- | :---------|
| `/users/{userId}/` | `/users/{userId}`|
| `/articles/{articleId}/author/` | `/articles/{articleId}/author` |

