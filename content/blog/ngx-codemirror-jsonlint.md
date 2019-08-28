+++
categories = ["programming", " angular", "web"]
color_choice = ""
title = "ngx-codemirror jsonlint"

+++
# How I got jsonlint to work with ngx-codemirror

I had a bit of trouble getting jsonlint to work with ngx-codemirror, so ill post my solution here.

in `main.ts` i needed the following imports

    import jsonlint from 'jsonlint';
    window['jsonlint'] = jsonlint;
    import 'jshint';
    
      
    import 'codemirror/mode/javascript/javascript';
    import 'codemirror/mode/yaml/yaml';
    import 'codemirror/addon/lint/lint';
    import 'codemirror/addon/lint/javascript-lint';
    import 'codemirror/addon/lint/json-lint';

The 'Gotcha' moment was when I finally updated my `package.json` to include this browser object

      // name
      // version
      "browser": {
        "fs": false,
        "path": false,
        "os": false,
        "file": false,
        "system": false
      },
      // scripts
      // dependencies
      // etc

of course you gotta make sure you are using all the proper css if you want he nice jsonlint/jshint error messages

    @import "~codemirror/lib/codemirror.css";
    @import "~codemirror/theme/monokai.css";
    @import "~codemirror/addon/lint/lint.css";