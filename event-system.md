# Event system

## n.on\(event, function\);

Comunicate any component in anyone direction

```javascript
n.ready(() => {

  n.render('eventTest', 'main')

  n.on('sayHi', name => {
    console.log(`Hi ${name}!`)
  })

})
```

## Emit with component click:

```javascript
n.set({
 name: 'eventTest',
 html: n => `
    NAME: <input type="text" id="name">
    <div id="sendEvent">CLICK FOR SEND NAME IN EVENT</div>
 `,
 ready: n => {
    n.on('#sendEvent', 'click', () => {
      n.emit('sayHi', n.id('name').value)
    })
  }
})
```

