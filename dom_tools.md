# DOM Tools

## Get element with JQuery Style

```javascript
n.get('#element_id')
```

## Get element by Id

```javascript
n.id('element_id')
```

## Get class

```javascript
n.class('class_id')
```

## Ready when loaded

```javascript
n.ready(() => {
  console.log("DOM loaded")
  n.get('#main').innerHTML = "Web is ready"
})
```

