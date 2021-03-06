---
layout: page
title: "JavaScript sql_regcase function"
comments: true
sharing: true
footer: true
sidebar: false
alias:
- /functions/view/sql_regcase:787
- /functions/view/sql_regcase
- /functions/view/787
- /functions/sql_regcase:787
- /functions/787
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's sql_regcase

{% codeblock pcre/sql_regcase.js lang:js https://raw.github.com/kvz/phpjs/master/functions/pcre/sql_regcase.js raw on github %}
function sql_regcase (str) {
  // http://kevin.vanzonneveld.net
  // +   original by: Brett Zamir (http://brett-zamir.me)
  // -    depends on: setlocale
  // *     example 1: sql_regcase('Foo - bar.');
  // *     returns 1: '[Ff][Oo][Oo] - [Bb][Aa][Rr].'
  this.setlocale('LC_ALL', 0);
  var i = 0,
    upper = '',
    lower = '',
    pos = 0,
    retStr = '';

  upper = this.php_js.locales[this.php_js.localeCategories.LC_CTYPE].LC_CTYPE.upper;
  lower = this.php_js.locales[this.php_js.localeCategories.LC_CTYPE].LC_CTYPE.lower;

  for (i = 0; i < str.length; i++) {
    if (((pos = upper.indexOf(str.charAt(i))) !== -1) || ((pos = lower.indexOf(str.charAt(i))) !== -1)) {
      retStr += '[' + upper.charAt(pos) + lower.charAt(pos) + ']';
    } else {
      retStr += str.charAt(i);
    }
  }
  return retStr;
}
{% endcodeblock %}

 - [view on github](https://github.com/kvz/phpjs/blob/master/functions/pcre/sql_regcase.js)
 - [edit on github](https://github.com/kvz/phpjs/edit/master/functions/pcre/sql_regcase.js)

### Example 1
This code
{% codeblock lang:js example %}
sql_regcase('Foo - bar.');
{% endcodeblock %}

Should return
{% codeblock lang:js returns %}
'[Ff][Oo][Oo] - [Bb][Aa][Rr].'
{% endcodeblock %}


### Other PHP functions in the pcre extension
{% render_partial _includes/custom/pcre.html %}
