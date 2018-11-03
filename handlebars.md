##### handlebars

```
网址：https://tutorialzine.com/2015/01/learn-handlebars-in-10-minutes
```

##### 输出表达式

```
#输出html
{{{}}}
```

##### helper

```
  Handlebars.registerHelper('capitalize', function(str){
    // str is the argument passed to the helper when called
    str = str || '';
    return str.slice(0,1).toUpperCase() + str.slice(1);
  });
```

##### block helper

```
  Handlebars.registerHelper('uppercase', function(options) {

    // "this" is the context that existed when calling the helper.

    // The options object has a special function - fn. This is a
    // compiled version of the template that is contained between the opening and closing
    // blocks of this helper. To get a string, call fn with the context:

    return options.fn(this).toUpperCase();

  });
```

