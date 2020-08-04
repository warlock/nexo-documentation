# DOM Event handler

## n.on\(object, event, function\);

Get object from id:

```javascript
n.on(n.id('button'), 'click', () => {
  console.log("Hi button!!")
})
```

Get object from id width string:

```javascript
n.on('#button', 'click', () => {
  console.log("Hi button!!")
})
```

## n.on\(class, event, function\);

Get group objects from class:

```javascript
n.on(n.class('buttons'), 'click', () => {
  console.log("Hi buttons class!!")
})
```

Get object from id width string:

```javascript
n.on('.buttons', 'click', () => {
  console.log("Hi buttons class!!")
})
```

