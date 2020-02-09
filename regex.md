### Regex

__preceding more then one e__
    
    /e+/
__e or a // before question mark is optional__

    /ea?/
__* is the combination of ? and +__

    /re*/

__dot is can be any character, preceding or at__

    /.at/
    /an../
__to select dot__

    /\./
__match any word character__

    /\w/
__match any white space__

    /\s/
__select continuos three character__
```js
    /\w{3}/
    /\w{3, 5}/  //three to five character
```

```js
    /[a-z]at/  //between a-z and 'at' // cat, bat
    /(t|T)he/   // capital T or small t // the, The
```

__^ paragraph first character, $ paragraph last character__
```js
    /^The/
    /\.$/   
```