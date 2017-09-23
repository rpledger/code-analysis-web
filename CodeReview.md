# Code Review Notes:

## Update NameGame API
Include commit from feature branch to update to latest NameGame API: https://willowtreeapps.com/api/v1.0/profiles.

## Add Boostrap and modify CSS
Updating the UI helps make the application much easier to use. Using Bootstrap, the UI can be easily update to achieve a friendlier look and feel. I updated to Bootstrap v3.3.7 using CDN link in html and made some modifications to CSS. I made the following modifications to the UI:

* Add Boostrap classes to buttons and table to add Bootstrap styling
* Add spacing in between objects, such as buttons and table, to make the UI more friendly
* Change width to 50% to be more responsive (app size will update with page resize)

## Sorting
The functionality for first name sorting works correctly, but last name sorting does not work properly. Instead of reversing the first name sort, called the sortObjListByProp() function with the last name prop. The slice(1) commands is supposed to copy the full array, but it does not include the element at index 0. Changing this to slice(0) allows the code to include element 0. I also added a new feature for sorting which allows an optional tiebreaker prop for breaking a tie in the comparator when the primary prop is equal. I used this by calling the function with firstName as the primary prop and lastName as the tie breaker prop. Below is a summary of the changes:

* Fix last name sort with sortObjListByProp()
* Copy full array with slice(0) instead of slice(1)
* Add tie breaker feature to break ties when primary prop is equal

## Searching
Add regular expression for searching at the start of a string to implement real-time searching. Before, the search function would not return results until the full first name or last name was entered. Now it is updated with search results each time a character is typed. I decided to search at the start of first name OR the start of last name, which seemed like an intuitive way for someone to go about searching for names. Below is a summary of the changes:

* Create regex for searchForName at start of string
* Filter on start of first name or start of last name

## Upgrde React
Update to lastest versions of React and React.Dom.
* React v15.6.1
* React.Dom v 15.6.1

## Shuffle
One React best practice to not mutate date used as props or state. Not mutating props or state data also improves the performance of the application. In the shuffle function, a copy is made of the list prop using the slice(1) command. However, similarly to in sorting, slice(1) must be changed to slice(0) in order to copy full array (including element 0). The result variable (copy of list prop) was created, but was not actually used in the shuffle algorithm. In order to not mutate the list data, the result variable must also be used in the shuffle algorithm for loop. Below is a summary of the changes:

* Change slice(1) to slice(0) to include index 0
* Use result variable in shuffle for loop for swap

## getLastName consistency
Use latest ES6 Javascript notation for getFirstName function, which also makes it consistent with the getFirstName function. It is a good practice to maintain consistency in syntax even if both are accepted. 