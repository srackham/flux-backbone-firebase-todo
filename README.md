# Flux Backbone Firebase Todos Example

This is the [Flux Backbone Todos
app](https://github.com/srackham/flux-backbone-todo) with minor
modifications to add [Firebase](https://www.firebase.com/)
persistance.

The changes are minimal, largely amounting to replacing the Backbone
Todo Collection with a
[BackboneFire](https://github.com/firebase/backbonefire)
Collection. The remaining changes replaced node modules with
`<script>` tags because Firebase JavaScript modules are not (as of
November 2014) distributed via npm -- this in turn does away with the
need to bundle the app for distribution using Webpack.

**IMPORTANT**: You will need to create your own Firebase account to
run or deploy the application **and** you will need to:

1. Edit `firebase.json` and change the `"firebase"` property to your
   Firebase name.
2. Edit `./app/app.jsx` change the Collection `url` property to your
   Firebase URL.


## Lessons learnt
- If the BackboneFire Collection `autoSync` property is `true` (the
  default value) then do not use Backbone Model/Collection
  `fetch`/`save`/`destroy` syncing functions --  BackboneFire does
  that for you.

- The app does not use
  [ReactFire](https://www.firebase.com/docs/web/libraries/react/),
  there's no need because the app does not use component State
  properties.

- Firebase Hosting is HTTPS by default, this means that you need to
  load external content via HTTPS otherwise you will get browser
  _Mixed Content_ errors.  If you leave the protocol prefix off a URL
  the browser treats it as a relative URL and so it will use the same
  protocol as it used to load the page e.g.

        src="//cdn.firebase.com/js/client/2.0.5/firebase.js"></script>

