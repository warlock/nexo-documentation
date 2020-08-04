# Project demo

## Demo project using Webpack && Expressjs and Nexo:

[https://github.com/warlock/nexoDemo](https://github.com/warlock/nexoDemo)

### Webpack configuration:

```javascript
var path = require("path")
module.exports = {
  entry: {
    app: ["./src/main.js"]
  },
  output: {
    path: path.resolve(__dirname, "assets/js"),
    publicPath: "/assets/",
    filename: "bundle.js"
  }
}
```

### src/index.html

```markup
<html>
  <head>
    <script src="/assets/js/bundle.js"></script>
    <title>nexo demo</title>
  </head>
  <body>
    <div id="filters"></div>
    <div id="main"></div>
  </body>
</html>
```

### src/main.js

```javascript
const n = require('nexo')
const clients = [
  { userId: 0, userName: 'Name', type: 'OPEN' },
  { userId: 1, userName: 'Name2', type: 'CLOSE' },
  { userId: 2, userName: 'Name3', type: 'CLOSE' }
]

n.load([
  require('./list/list.js'),
  require('./client/client.js'),
  require('./filters/filters.js')
])

n.ready(() => {
  n.render('list', 'main', { element: '#main', data: clients })
  n.render('filters', { element: '#filters' })
})
```

## Component list \('src/list/list.js'\)

```javascript
module.exports = {
  name: 'list',
  html: n => {
    if (n.empty(n.data)) return "NOT FOUND CLIENTS"
    var text = `<table>`
    n.data.forEach(client => {
      text += n.render('client', { data: client })
    })
    text += `</table>`
    return text
  }
}
```

## Component client \('src/client/client.js'\)

```javascript
module.exports = {
  name: 'client',
  html: n => `
    <tr id="client-${n.data.id}">
      <td>
        ${n.data.userId}
      </td>
      <td>
        ${n.data.userName}
      </td>
      <td>
        ${n.data.type}
      </td>
    </tr>`,
  ready : n => {
    n.on(`#client-${n.data.id}`, 'click', () => {
      console.log(`click client: ${n.data.userName}`)
    })
  }
}
```

## Component filter \('src/filter/filter.js'\)

```javascript
module.exports = {
  name: 'filters',
  html: n => `
    Filter name: <input type="text" id="name">
    Filter STATUS:
    <select id="type">
      <option value="">ALL</option>
      <option value="OPEN">OPEN</option>
      <option value="CLOSE">CLOSE</option>
    </select>
    `,
  ready : n => {
    const filter = () => {
      n.model.filter('clients', { userName : n.id('nombre').value type : n.id('type').value })
    }

    n.on('#name', 'keyup', filter)
    n.on('#type', 'change', filter)
  }
}
```

