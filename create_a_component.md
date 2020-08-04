# Components

## Create a simple component

**n.set\(component\_name, function\_run\_when\_load, function\_return\_html, function\_run\_when\_component\_ready\)**

```javascript
n.set({
    name: 'button',
    html: n => `<b id="click_now">Clickme!</b>`,
    ready: n => {
        n.on('#click_now', 'click', () => {
          console.log("Hi!")
        })
    }
})
```

**Using components in other components**

```javascript
n.set({
  name: 'news',
  html: n => {
    var text = ""
    articles.forEach(article => {
      text += n.render("articleComp", { data : article })
    })
    return text
  }
})
```

### Load Function:

**Asyncronous operations before render**

```javascript
n.set({
  name: 'fetchNews',
  load: (n, render) => {

    console.log(`Fetch data from url: ${n.data}`)
    setTimeout(() => {
      var receivedArticles = [
        { title : "Title 1"},
        { title : "Title 2"}
      ]
      render(receivedArticles)
    }, 2000)

  },
  html : n => {
    var text = `<div>LATEST NEWS(${n.data.length}):</div>`
    n.data.forEach(article => {
      text += `<div>${article.title}<br></div>`
    })
    return text
  },
  ready : (n, data) => {
    console.log(`Fetch ${n.data.length} articles.`)
  }
})

n.render('fetchNews', { element : 'main4', data : 'http://url' })
```

## Create a importable component width require

```javascript
module.exports = {
  name: 'showName',
  html: n => `YOUR NAME IS ${n.data}`
}
```

## Import component from file

```javascript
n.load(require('component.js'))
```

## Import multiple components from files

```javascript
n.load([
  require('component1.js'),
  require('component2.js')
})
```

#### Render component

**n.render\(component\_name, object\_options\)**

```javascript
n.render('news', { element : '#main_page' })
```

**Render component with data**

```javascript
var news_data = [
  { title : 'TITLE 1', 'content' : 'CONTENT 1' },
  { title : 'TITLE 2', 'content' : 'CONTENT 2' }
]

n.render('news', { element: '#main_page', data: news_data })
```

#### Destroy component and clean div

**n.destroy\(element\_id\)**

```javascript
n.destroy('#main_div')
```

