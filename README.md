# Welcome to Nashville: Build an itinerary for a day trip to Music City

In this app users can search for four different things to do/visit in Nashville:
* parks -- using the Nashville [Metro Gov API](https://dev.socrata.com/foundry/data.nashville.gov/xbru-cfzi)
* public art collections -- using Nashville [Metro Gov API](https://dev.socrata.com/foundry/data.nashville.gov/eviu-nxp6)
* restaurants -- using the [Zomato API](https://developers.zomato.com/api)
* concerts -- using the [Ticketmaster API](https://developer.ticketmaster.com/products-and-docs/apis/getting-started/)

You will be utilizing all of the skills and concepts that you've learned up to this point in the course.

1. Functions
1. Persistent data storage
1. Github
1. CSS
1. Building DOM components
1. Handling user events
1. Modular code
1. Semantic HTML
1. [Valid HTML5](https://validator.w3.org/)

## Itinerary Builder

When the user searches for any of the four categories of things to do, the results should be listed in the DOM. Each result item should have an affordance to add the item to the current itinerary. Use your awesome new skills to select the text of the search result ( ie "John Mellencamp at the Ryman" ) and add it to the itinerary list. See the wireframe below for a visual cue for how this might look.


## Professional Requirements

1. Only one itinerary needs to exist at a time. If a user selects an item to add to the itinerary, and an item already exists for that category in the itinerary, then you will need to update the corresponding itinerary item in the DOM with the new data.
1. All teammates must be using http-server during development. `json-server` should only be used if you have time to work on the stretch goal (_see below_).
1. Each teammate is responsible for one API module. If your group has five members, one person is responsible for the module that interacts with the DOM and the data from the API modules. In a four-person team, the team will decide how to handle the development of that module.
1. The README for your project should include instructions on how another person can download and run the application. **PRO TIP:** Don't wait until the very end to create the README. [Readme Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
1. DO NOT FORGET to use a `.gitignore` file to keep git from tracking `.DS_Store`, **your API Keys**, and, if necessary, API directory (stretch goal).
1. CSS for structure is part of MVP. CSS for style (animations, colors, fonts) is _secondary_. Do not add any additional visual enhancements until you have a fully functional app. 
1. The goal of every member of the team is to _implement functionality with JavaScript_.

## Visual Feature List

To help you along, here is a wireframe of how your app might look

![welcome wireframe](./welcom-to-nashville-example.png)

## Notes about the APIs

### Ticketmaster API

The Ticketmaster API requires an `apikey` to be included in the url.

For example:
```js
const concertApi = {
  searchForQueen() {
    return fetch("http://app.ticketmaster.com/discovery/v1/events.json?keyword=Queen&apikey=__YOUR_API_KEY_HERE__")
      .then(response => response.json());
  }
};
```

### Zomato API

Here's an example fetch to search restuarants in Nashville.

* 1138 is the `id` for the city of Nashville
* `entity_type` must be set to `city`
* Your API key must be added as an `apikey` query string parameter

```js
return fetch("https://developers.zomato.com/api/v2.1/search?entity_id=1138&entity_type=city&start=first&sort=rating&apikey=__YOUR_API_KEY_HERE__")
    .then(r => r.json())
```

### Nashville Metro Open Data API

This API does not require an API key.

### Keeping track of API Keys

_**NEVER store API Keys in Github!!!**_

You will need to a separate JavaScript module with `const`s to store your API Keys. The module's filename should be added to your `.gitignore` to prevent if from being added to your git repo.

## Stretch Goal

Persist your itinerary with `json-server`. You only need to have a single itinerary. If the user selects a different park, restaurant, etc, use a PUT to update the itinerary with the new data.

To start you off, here's an example of what the itinerary in your API might look like in your database once it's created by the user.

```json
{
  "itinerary":
      {
        "id": 1,
        "park": "Centennial Park",
        "restaurant": "Prince’s Hot Chicken",
        "meetup": "Meeple Mountain Board Game Night",
        "concert": "John Mellencamp at the Ryman"
      }
}
```
## Stretchier Goals

Add a "more info" link to each of the Public Art search result entries. This link should open a new tab. Use the URL from the `page_link` property as the link's `href`.

## Stretchiest Goals
* Add an affordance to finalize an itinerary, and start a new one.
  * Add ability to view one or all of the itineraries
* Instead of displaying all the search fields, search results, and itinerary list at the same time, add a nav bar or other feature(s) for hiding/showing what the user wants to view
