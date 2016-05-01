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

### To get the content-description out of an element

You use elementByAccessibilityId

```javascript
  .elementById('id')
  .getAttribute('name') //this get the content-desc of that element
```

### Taking a screenshot and storing it in a file

```javascript
 let base64Img = require('base64-img');
 let res = await driver.takeScreenshot();
 filePath = await base64Img.imgSync('data:image/png;base64,' + res, directory,filePath);
```

### Debugging techniques

#### To view page source at any point

dumps out UITree at that point
```javascript
  driver.source() 
```

### Wait for something to disappear/appear

#### Example of waiting for a progressbar to disappear (using async/await and modifying timeouts)
```javascript
async function waitTillProgressBarDisappears(max_attempts=10){
  await this.setImplicitWaitTimeout(LONG_WAIT_TIME);
  let cond = await this.hasElementByClassName('android.widget.ProgressBar');
  //Loop till element is not found or till attempts have been finished
  while(max_attempts > 0 && cond == true){
    await Q.delay(MODERATE_WAIT_TIME);
    cond = await this.hasElementByClassName('android.widget.ProgressBar');
    max_attempts--;
  }
  await this.setImplicitWaitTimeout(MOCHA_IMPLICIT_TIMEOUT);
}
```
