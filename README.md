
## ghw-menu

Github Worlds menu is a visualization toolkit that provides
**Views** into JSON data that comes from the
[Github GraphQL API](https://developer.github.com/v4/).
It is called Github Worlds **menu** because there is also a
**[Github Worlds drawer](https://muitool.github.io/ghw-drawer/)** which displays the same data and views
but with the
**[Drawer](https://material-ui.com/demos/drawers/)**
being the primary navigation element instead of the
**[Menu](https://material-ui.com/demos/menus/)**

### The List of Demos in the Material-UI Tutorial

This demo is an extension of
[mui-menu](https://stormasm.github.io/mui-menu/) and it is assumed that you have already reviewed the concepts and
documentation associated with that repo.

There is an order to the demos in this
**[tutorial series](https://github.com/topics/material-ui-tutorial)**
and this one is the last tutorial to review.  We highly recommend reviewing the other tutorials first so that you get all of the background information you need prior to reviewing this tutorial.

* [mui-drawer](https://stormasm.github.io/mui-drawer/)
* [ghw-drawer](https://muitool.github.io/ghw-drawer/)
* [mui-menu](https://stormasm.github.io/mui-menu/)
* [ghw-menu](https://muitool.github.io/ghw-menu/)

### The Card Views

There are four views present in the Github Worlds drawer and menu demo series. They include in order of View appearance.

* Cards displayed six across in an infinite vertical column
* Cards displayed in a Horizontal Line
* Cards displayed as a function of
[react-autosuggest](https://github.com/moroshko/react-autosuggest)
in concert with
[Material-UI Tables](https://material-ui.com/demos/tables/)
* Cards displayed with no avatars


### High level data flow outline

In all Create-React-App (CRA) applications things kickoff inside **index.js**.  From there you wire up the
[Redux](https://redux.js.org/introduction)
state through a Provider interface inside **Root**.  Next up is the **MenuAppBar** which houses the Icons and Menus along with the
[React-Router](https://reacttraining.com/react-router/core/guides/philosophy)
Route definitions.  Finally, when you select a view inside the menu Views.

**ShowTheLocation** will select the properties that get passed into the **DataViewWrapper** given the repo name and view name as
[props](https://reactjs.org/docs/components-and-props.html#props-are-read-only).

### DataViewWrapper

This component has two important variables defined inside it.

```js
const repoMap = {
  repo1: "material-ui.json",
  repo2: "graphql-js.json",
  repo3: "html5-node-diagram.json",
  repo4: "nodejs-sandboxed-fs.json",
  repo5: "ivy.json"
};
```

The **repoMap** allows one to define their own repositories of
data that they are interested in observing, showing to others,
or using for your open source web site.  Say you have an open
source project on Github, and you want to show the world all of the committers
on the project.  Or provided you don't have too many stars, all of the
developers who starred or forked your repo.  This is the type of view
that might be interesting to you but with your own repositories data
instead of these sample data sets.

```js
const template =
  "https://raw.githubusercontent.com/stormasm/ghdata/master/data1/";
```

The **template** is the location of where your JSON data files live.
You can put them anywhere you want, provided you define the template variable.

#### Fetching Data

Now that you have things defined, its time to go out and
[fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
the data.  For now we are fetching static JSON files from a specific
Github repo defined in the template above, but we could have just as easily fetched the data from the
[Github GraphQL API](https://developer.github.com/v4/), or if you have other custom data views defined, your own GraphQL or REST endpoint.

### DataView

DataView is a switch or set of if statements to grab the selected View from the View Menu in the AppBar.

The actual views themselves are styled any way you like them with
Material-UI's [styling solution](https://material-ui.com/customization/css-in-js/#material-ui-39-s-styling-solution).  

The **View** is the core of the application in that this is where you do your creative work.  Its your canvas so to speak, to create your data visualization. The rest of the framework is there for your use, you just have to be inventive
and come up with interesting views of your data.

The View takes in the prop **tileData** which is the data that was fetched from the API in the DataViewWrapper.  Then the tileData is mapped onto each component that you define in your View.

Any custom view that you define will take in tileData as a prop and then its up to you to build out your own styled component View.

### The Material-UI Tutorial

If you have not already read the **[The Material-UI Tutorial](https://stormasm.github.io/mui-tutorial/)**
you should read it first prior to diving deeply into
this code base.  It will give you all of the background
material you need to better understand the concepts
discussed in this code.
