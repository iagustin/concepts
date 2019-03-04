# JS
careful: pop mutates
```input.split("/").pop()```
https://stackoverflow.com/questions/651563/getting-the-last-element-of-a-split-string-array

```sortArray = [ ...dontMutateMe ].sort(...)```
https://stackoverflow.com/questions/9009879/which-javascript-array-functions-are-mutating

# UI

https://www.nngroup.com/articles/toggle-switch-guidelines/

Summary: Toggle switches are digital on/off switches. They prompt users to choose between two mutually exclusive options and always have a default value. Toggles should provide immediate results, giving users the freedom to control their preferences as needed.

# React enzyme testing

https://github.com/airbnb/enzyme/issues/1002

"I'd generally recommend using only shallow as much as possible, and only making assertions on which components your thing renders - in other words, if A renders B which renders C, your A tests shouldn't know anything about C, and should only be asserting that A renders B with the right props. Your _B_ tests should be asserting things about C." **[ljharb](/ljharb) ** commented [on Jul 26, 2017](#issuecomment-318102035)

# Router
https://stackoverflow.com/questions/49964925/this-props-location-pathname-for-dynamic-urls-in-react
When a route is matched, inside the component you can access props.match.params
You can use matchPath to compare paths

# Redux vs Graphql

https://www.reddit.com/r/javascript/comments/9esh23/can_someone_explain_how_graphql_replaces_redux/

There is some validity to this claim, but in my opinion you still need redux.

The thing is there is less of a need for redux when using GraphQL than when using a traditional REST api. This has nothing to do with Caching, as some people have suggested, but rather due to how GraphQL behaves.

First let’s dispel this notion of caching. Redux is not a cache nor is it primarily used as one. Most applications I see load things into the store on first load, and then request the data from a remote service again, regardless of whether or not it is in state anyway. Maybe they don’t send a loading message the second time around, but most developers don’t really treat redux as a cache.

Rather most logic in redux deals with manipulating the response back from some remote api into something that the application can understand/easier to work with. Things like normalizing the data, or putting chunks of the data into separate parts of the state. Next time you’re in a big application, pay attention to how much of the redux code is dedicated to marshaling an API response into a different format to store in Redux.

You have less of a need to manipulate the response with GraphQL because every request you send to it is already formed to how you would want it anyway. To put it differently, you don’t have as much of a need to take the data you get back from your api and form it to something your application understands. Instead you just send a query that is already formed in a way that your application would want it.

Do I think this gets rid of needing state management? No. There are more benefits to state management than just taking a response and putting it into a different format. Things like sharing data across your components, or having a single place where all network and data interactions take place. But I recognize that it cuts down a lot on the “take the response, normalize it, and take the user’s name and throw it in this part of the state” code.
