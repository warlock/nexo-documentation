# Data Models

ALERT: **Reactive is under construction &gt; 0.0.44**

You can relate models to a component if they are passed as data.

When a model receives a change, the rendering of related components automatically triggers.

```javascript
n.render('listComponent', 'main_div', n.model.get('clients'))
```

Create a new model \(automatic render on update model\)

```javascript
n.model.set('clients', { name : 'Eudald', age : 18, country : 'china' })
```

Add element in model \(automatic render on update model\)

```javascript
n.model.push('clients', { name : 'Josep', age : 18, country : 'spain' })
```

Return array data from model\(is array\)

```javascript
n.model.get('clients')
```

Pop element in model \(automatic render on update model\)

```javascript
n.model.pop('clients')
```

Shift element in model \(automatic render on update model\)

```javascript
n.model.shift('clients')
```

Reverse elements in model \(automatic render on update model\)

```javascript
n.model.reverse('clients')
```

Count elements in model

```javascript
n.model.size('clients')
n.model.length('clients')
```

Clear data in model \(automatic render on update model\)

```javascript
n.model.clear('clients')
```

Delete element in model with index \(automatic render on update model\)

```javascript
n.model.remove('clients' , 5)
```

Delete element in model with attributte \(automatic render on update model\)

```javascript
n.model.remove('clients' , { name : 'josep' })
```

Delete model \(automatic render on update model\)

```javascript
n.model.delete('clients')
```

Filter data in model for search systems\(automatic render on update model\) without destroy data in model

```javascript
n.model.filter('clients', { age : 18, name : 'os' })
```

Automatic render on update models

```javascript
n.render('listClients', 'main_div', n.model.get('clients'))

setTimeout(() => {
  n.model.push('clients', { name : 'Simon' })
} ,5000);
```

