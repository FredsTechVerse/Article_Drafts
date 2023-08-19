
### USING REACT-QUERY

- There will be painfull tears if you miss the return statement in the useQuery hook if your useCase requires an arrow function that extends to another line other eg ` () => {
  return deleteUser({ userID, role });
},`
- To avoid the painful tears simply define the arrow function in a single line avoiding the need for curly braces which always require a return statement as shown `() => deleteUser({ userID, role })`
- Is amazing how much information we can extract from the axios error body eg instead of repopulating the form again after renewing token because we do not have the global form states , we simply extract the previous values from the axios.config.data object and retry the request. If the data is in this config object , it doesn't even matter if we had been redirected after the request failed , we can still retry the mutation and the data will be there.
- Adding the enabled prop prevents react query from running immediately! Turns out that it was not being triggered by the status check! It is just build to run immediately when spotted!
- Suitable for handling mutation and fetch requests.
- Mutation opertations is broader than a post request in that it can be used to make a put(update ) and a delete request also.
- Found a way to utilize useEffect to update state from either cache or a fresh fetch by migrating onSuccess out of the query and instead populating the data if the query status is successfull and the data exists. Mine is to watch out for a query status change.
- To delete data , I arise the dead when the time to do so comes and invalidate the necessary parties for a fresh refetch.

#### ITS SUPERPOWERS

- Eliminates the need for a try catch statements as it has its own eventHandlers for handling errors and loading states. eg onError , onLoading , onSuccess
- Integrating skeletons has never been easier as we know exactly when our data is loading.
- Error handling has also been simplified where we can use the `onError((error)=>{})`or the `isError` if we are just interested in the current state.
- We also get instant updates when we use it to make a post request.

- Has a one line syntax which i enjoy using when doing my fetches whose syntax( [keys ],function ,additonal props) eg

```js
const courseQuery = useQuery(
  ["courseData", courseID],
  () => fetchCourseData(courseID),
  {
    onError: (error) => {
      handleError(error, updateAlertBoxData);
    },
  }
);
```

