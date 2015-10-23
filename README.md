# wd-appium-cheatsheet
Some of the learnings that I got through working through wd and appium

### A within search - subtree of another element

 You use >
 ```javascript
   .elementById('parent element id')
   .elementById('>','sub element id')
```

### To grab the value of an element
You use text()
```javascript
  .elementById('element id')
  .text().should.become('intended value')
```

### To find an element by content descriptions(android)

You use elementByAccessibilityId

```javascript
  .elementByAccessibilityId('list')
```

### To get to the first element in list of elements use first() (from _) not [0]

You use elementByAccessibilityId

```javascript
  .elementsByAccessibilityId('row').first()
```
