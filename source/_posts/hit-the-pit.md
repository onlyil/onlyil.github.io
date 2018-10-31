---
title: Hit the Pit
date: 2018-09-14 00:51:21
tags: pit
icon: fa-blind
---

# Hit the Pit

## Common

### 1. Download blob file

- Download file with window.URL API and element <a\>.

- In firefox, element <a\> must be appened to <body\>.

- In IE 11, not support for download attribute of 'a', we need use `navigator.msSaveBlob(blob, filename)`.

```javascript
function downloadBlobFile(blob, filename) {
  const objUrl = window.URL.createObjectURL(blob)
  const a = document.createElement('a')
  if ('download' in a) {
    document.body.appendChild(a)
    a.style.display = 'none'
    a.href = objUrl
    a.download = filename
    a.click()
    window.URL.revokeObjectURL(objUrl)
    document.body.removeChild(a)
    return
  }
  // IE
  navigator.msSaveBlob(blob, filename)
}
```

### 2. `new Date()` in Safari and ios(include mini program)

In Safari, `new Date('2018-10-16')` return `Invalid Date`.

```javascript
date = date.replace(/-/g, '/')
```

Tip: Safari 12.0 support `new Date('2018-10-16')`, found it recently.

## WX Mini program

## Fucking IE

### 1. `<input type="number">` no input restriction

The attribute type="number" of input tag is invalid in even IE 11, we can also type characters "@, #, ...".

### 2. `<input type="file">` clear selected file

In IE 10, can not clear selected file via:

```javascript
fileInput.value = ''
```

Need `form.reset()`:

```html
<form ref="fileForm">
  <input type="file">
</form>
```

```javascript
this.$refs.fileForm.reset()
```
