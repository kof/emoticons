## Parse text emoticons and replace them by graphics.

This is a pure string based parser and has no dependencies to DOM or jquery.

In order to insert an emoticon code into the textarea or input field you might want to use https://github.com/kof/field-selection

### Features
- copy emotified text together with emoticons, exchangable between skype and other systems
- every emoticon can have different codes, so, when parsing useres emoticons, different styles will be recognized
- fully customizable, define any emoticons yourself
- nodejs ready without dependencies
- tiny and fast

### Get the api

    // Within commonjs
    var emoticons = require('emoticons');

    // Within jquery
    $.emoticons;

    // From global
    window.emoticons;

### emoticons.define(data:Object)

Define a set of emoticons. See the format in skype.json. First code in the codes array will be used as primary one.

Example:

    emoticons.define(
        "smile": {
            "title": "Smile",
            "codes": [":)", ":=)", ":-)"]
        }
    );

### emoticons.replace(text:String, [fn:Function])

Replace text emoticons by html elements which can be then styled with graphics.

Example:

    emoticons.replace(':)');

    If you don't like the generated html, pass your own template builder function.

    emoticons.replace(':)', function(name, code, title) {
        return '<div>' + code + '</div>';
    });

### emoticons.toString([fn:Function])

Get html string with all primary emoticons in order to display an overview. Optionally pass your own template builder function.

### emoticons.tpl(name:String, code:String, title:String)

If you want to overwrite the default template builder function.

Example:

    emoticons.tpl = function(name, code, title) {
        return '<div>' + code + '</div>';
    };


## External components

Thanks to Chris Messina for making this overview http://factoryjoe.com/projects/emoticons

Skype icons included in the package have a special license, which is like BSD but without permission to modify them. See LICENSE file and original blog post.
http://blogs.skype.com/2006/09/01/icons-and-strings
