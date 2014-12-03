# Flux Backbone Firebase Todos Example

This is the [Flux Backbone Todos
app](https://github.com/srackham/flux-backbone-todo) with minor
modifications to add [Firebase](https://www.firebase.com/)
persistance.

The changes are minimal, largely amounting to replacing the Backbone
Todo Collection with a
[BackboneFire](https://www.firebase.com/docs/web/libraries/backbone/quickstart.html)
Collection. The remaining changes replaced node modules with
`<script>` tags because Firebase JavaScript modules are not
distributed via npm -- this in turn does away with the need to bundle
the app for distribution using Webpack.


## Building and Running
You need a Firebase account to deploy the application.

      firebase deploy


## Lessons learnt
- If the BackboneFire Collection `autoSync` property is `true` (the
  default value) then do not use Backbone Model/Collection
  `fetch`/`save`/`destroy` syncing functions --  autoSync does that
  for you.

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

