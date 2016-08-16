## XMLHttpRequest [Back](./../web_api.md)

**XMLHttpRequest**, also called XHR is designed firstly by MicroSoft, which is **used to request resources from a url**. Although it's named with XML, but it can request all types of resources, with HTTP, FTP protocol and so on.

#### 1. new an object

```js
var xhr = new XMLHttpRequest();
```

### 2. create a AJAX request with XHR

```js
function createXHR() {
    if (XMLHttpRequest) {
        /** not IE 6 */
        return new XMLHttpRequest();
    } else if (ActiveXObject) {
        /** IE 6 */
        var version = [
            'MSXML2.XMLHttp.6.0',
            'MSXML2.XMLHttp.3.0',
            'MSXML2.XMLHttp'
        ];
        
        for (var i = 0; i < versions.length; i++) {
            try {
                return new ActiveXObject(version[i]);
            } catch (e) {
                /** ignore */
            }
        }
    } else {
        throw new Error('Failed to create XHR');
    }
}

function param(obj) {
    var arr = [];
    
    for (var i in data) {
        arr.push(encodeURIComponent(i) + "=" + encodeURIComponent(data[i]));
    }
    
    return arr.join('&');
}

function ajax(obj) {
    var xhr = creatXHR();
    
    /** clear cache */
    obj.url = obj.url.indexOf('?') > 0 ? obj.url + '&_=' + new Date().getTime() : obj.url + '?_=' + new Date().getTime();
    
    /** escape parameters */
    obj.data = param(obj.data);
    
    /** whether it's GET */
    if (obj.type === 'GET') {
        obj.url += '&' + obj.data;
    }
    
    /** whether it's sync */
    
}
```