# Event

A es6 "event" class for publisher and subscriber pattern, message middleware, event bus.

## Install

```cmd
npm install @daybyday/event --save
```

### API

- on(key, fn, isFirst)
- off(key, fn)
- trigger(key, fnParam1, fnParam2, ..., fnParamN)
- once(key, fn)
- destroy()

### Examples

```javascript
import Event from '@daybyday/event';

const event = new Event();
const func0 = (...rest) => {
    console.log(`func0: ${JSON.stringify(rest)}`);
};
const func01 = (...rest) => {
    console.log(`func01: ${JSON.stringify(rest)}`);
};
const func02 = (...rest) => {
    console.log(`func02: ${JSON.stringify(rest)}`);
};
const func03 = (...rest) => {
    console.log(`func03: ${JSON.stringify(rest)}`);
};
const func04 = (...rest) => {
    console.log(`func01: ${JSON.stringify(rest)}`);
};
event.on('click', func0);
event.on('click', func01);
event.on('click', func02);
event.on('click', func03);
event.on('click', func04, true);
event.trigger('click', 1, 3, 5);
event.off('click', func01);
event.trigger('click', 2, 4, 6);
// event.once('click', func04);
event.trigger('click');
event.trigger('click');
event.trigger('event5', 12, 34, 0);
event.on('event5', (a, b, c) => {
    console.log(`Event5: ${a} ${b} ${c}`);
});

event.once('EventOnce', (...rest) => {
    console.log(`EventOnce: ${rest.join(',')}`);
});
event.trigger('EventOnce', 'a', 'b', 'ccc', 'ddd');
event.trigger('EventOnce', 'aaa');
```
