# Web Tools

## Add cookie and set 2 day expiration

```javascript
n.cookies.set('key', 'value', 2); // Expiration in 2 days
```

## Get cookie value

```javascript
n.cookies.get('key') // Returns 'value'
```

## n.params object contains a URL parsed data

### Example: [http://localhost/index.html?key=value&key2=value2](http://localhost/index.html?key=value&key2=value2)

```javascript
console.log(n.params)
```

```bash
-> {"key":"value","key2":"value2"}
```

