SimpleReactPlayer
===========

A react audio component for playing a variety of URLs, including file paths.
This is a modified version of react player (http://cookpete.com/react-player) for a dj app i built. I stripped down react-player to a basic audio element, but retains the props from the original react-player. I have also added a crossOrigin prop (works with SoundCloud SDK)

### Polyfills

If you are using `npm` and need to support [browsers without `Promise`](http://caniuse.com/#feat=promises) you will need a [`Promise` polyfill](https://github.com/stefanpenner/es6-promise). To support `Streamable` or `Vidme` videos you will also need a [`fetch` polyfill](https://github.com/github/fetch) for [browsers without `fetch`](http://caniuse.com/#feat=fetch)

### Usage

```bash
npm install simple-react-player --save
```

```js
import React, { Component } from 'react'
import ReactPlayer from 'react-player'

class App extends Component {
  render () {
    return <ReactPlayer url='https://www.youtube.com/watch?v=ysz5S6PUM-U' playing />
  }
}
```

### Props

Prop | Description | Default
---- | ----------- | -------
`url` | The url of a video or song to play
`playing` | Set to `true` or `false` to pause or play the media | `false`
`loop` | Set to `true` or `false` to loop the media | `false`
`controls` | Set to `true` or `false` to display native player controls<br />*Note: Vimeo player controls are not configurable and will always display* | `false`
`volume` | Sets the volume of the appropriate player | `0.8`
`playbackRate` | Sets the playback rate of the appropriate player | `1`
`width` | Sets the width of the player | `640`
`height` | Sets the height of the player | `360`
`hidden` | Set to `true` to hide the player | `false`
`className` | Pass in a `className` to set on the root element
`style` | Add [inline styles](https://facebook.github.io/react/tips/inline-styles.html) to the root element
`progressFrequency` | The time between `onProgress` callbacks, in milliseconds | `1000`

#### Callback props

Callback props take a function that gets fired on various player events:

Prop | Description
---- | -----------
`onReady` | Called when media is loaded and ready to play. If `playing` is set to `true`, media will play immediately
`onStart` | Called when media starts playing
`onPlay` | Called when media starts or resumes playing after pausing or buffering
`onProgress` | Callback containing `played` and `loaded` progress as a fraction<br />eg `{ played: 0.12, loaded: 0.34 }`
`onDuration` | Callback containing duration of the media, in seconds
`onPause` | Called when media is paused
`onBuffer` | Called when media starts buffering
`onEnded` | Called when media finishes playing
`onError` | Called when an error occurs whilst attempting to play media

#### Config props

These props allow you to override the parameters for the various players:

Prop | Description
---- | -----------
`fileConfig` | Configuration object for the file player.<br />Set `attributes` to apply [element attributes](https://developer.mozilla.org/en/docs/Web/HTML/Element/video#Attributes).

### Methods

To seek to a certain part of the media, there is a `seekTo(fraction)` instance method that will seek to the appropriate place in the media. See `App.js` for an example of this using `refs`.

### Supported media

* [Supported file types](https://github.com/CookPete/react-player/blob/master/src/players/FilePlayer.js#L5-L6) are playing using [`<audio>`](https://developer.mozilla.org/en/docs/Web/HTML/Element/audio) elements

### Thanks

* Anyone who has [contributed](https://github.com/CookPete/react-player/graphs/contributors)
* [gaearon](https://github.com/gaearon) for his [react-transform-boilerplate](https://github.com/gaearon/react-transform-boilerplate), which this repo is roughly based on.
