## `document.title` support for [Ember.js](http://emberjs.com/)

This repository serves as a bower installable mirror of [Alex Matchneer's](https://github.com/machty) [original public gist](https://gist.github.com/machty/8413411). Support for `document.title` is on the Ember roadmap, but the API is yet to be determined and will likely differ from the one set out in this plugin. See [this github issue](https://github.com/emberjs/ember.js/pull/3689) for more information.

Install via bower:

```sh
$ bower install ember-document-title
```

### Usage

Start by adding the new `title` hook to your application route:

```javascript
App.ApplicationRoute = Ember.Route.extend({
  // This defines how all collected 'tokens' are put together to create a title
  title: function(tokens) {
    return tokens.join(' ') + ' - My Site';
  }
});
```

Next, add the `titleToken` hook to all routes that want to contribute a token to the title. They can be a static string:

```javascript
App.SomeRoute = Ember.Route.extend({
  titleToken: 'Something'
});
```

Or a function, in which case they are passed the route's current model:

```javascript
App.AnotherRoute = Ember.Route.extend({
  titleToken: function(model) {
    return model.get('name');
  }
});
```
