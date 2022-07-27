# Timetable.js
Vanilla javascript plugin for building nice responsive timetables. Provides a simple javascript interface to add events and locations which can be rendered to nice HTML. Works on mobile devices as well.

## Just show me the demo
Okay: [**demo**](http://timetablejs.grible.co). Also, have a look at the website: [http://timetablejs.org](http://timetablejs.org).

Load the plugin and styles in your HTML from the `dist` folder:
```html
<link rel="stylesheet" href="timetablejs.css">

<script src="timetable.min.js"></script>
```
Add a timetable placeholder:
```html
<div class="timetable"></div>
```

## Usage
Make a timetable object, optionally set the scope in hours (the visible hours in the timetable):
```javascript
var timetable = new Timetable();
timetable.setScope(9, 17); // optional, only whole hours between 0 and 23
timetable.useTwelveHour(); //optional, displays hours in 12 hour format (1:00PM)
```
Add some locations:
```javascript
timetable.addLocations(['Silent Disco', 'Nile', 'Len Room', 'Maas Room']);
```
Add your events using `addEvent(name, location, startDate, endDate[, options])`:
```javascript
timetable.addEvent('Frankadelic', 'Nile', new Date(2015,7,17,10,45), new Date(2015,7,17,12,30));
```

In addition, you can pass options through an object (optional):
```javascript
var options = {
  url: '#', // makes the event clickable
  class: 'vip', // additional css class
  data: { // each property will be added to the data-* attributes of the DOM node for this event
    id: 4,
    ticketType: 'VIP'
  },
  onClick: function(event, timetable, clickEvent) {} // custom click handler, which is passed the event object and full timetable as context  
};
timetable.addEvent('Jam Session', 'Nile', new Date(2015,7,17,21,15), new Date(2015,7,17,23,30), options);
 ```

Last, render the thing in your previously created timetable placeholder:
```javascript
var renderer = new Timetable.Renderer(timetable);
renderer.draw('.timetable'); // any css selector
```
That's it!
