# electron-native-notification

[![JavaScript Style Guide](https://img.shields.io/badge/code%20style-ES6-brightgreen.svg)](https://github.com/elierotenberg/coding-styles/blob/master/es6.md)

Easily display native desktop applications from your Electron main process.

Because Notifications use the HTML 5 Notification API, this usually only works
from renderer processes.

However, it's a polyfill from https://developer.mozilla.org/en-US/docs/Web/API/notification .

## Usage

Actually really easy to use:

```javascript
const { app } = require('electron');
const Notification = require('electron-native-notification');

app.on('ready', () => {

  const notification = new Notification('This is a notification!', { body: 'See? Really easy to use!' }, () => {
    console.log('The notification got clicked on!');
  });

  notification.onclick = () => {
    console.log('The notification is be clicked!');
  };

  notification.on('error', () => {
    console.log('Oh no! An error occurred.');
  });

  console.log('What the notification just say? ' + notification.body);

})
```

## Polyfill what?

### Constructor
 - Notification(title, options)

### Properties
 - body (Read-only)
 - data (Read-only)
 - dir (Read-only)
 - icon (Read-only)
 - lang (Read-only)
 - onclick
 - onerror
 - tag (Read-only)
 - timestamp (Read-only)
 - title (Read-only)

### Methods
 - close()

### Events
 - error
 - click
 - close
 - show