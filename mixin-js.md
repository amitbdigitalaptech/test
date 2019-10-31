## Code
**file Path:** `app/code/{vendorName}/{Modulename}/view/frontend/requirejs-config.js`

**Code**

```js
var config = {
    config: {
        mixins: {
            'mage/menu':{
                 '{vendorName}_{Modulename}/js/menu-mixin': true
            }
        }
    }
};
```

**file Path:** `app/code/{vendorName}/{Modulename}/view/frontend/web/js/menu-mixin.js`

**Code**
```js
define(['jquery'], function (jQuery) {

    return function (originalWidget) {

        jQuery.widget(
                'mage.menu',
                jQuery['mage']['menu'], {

            _toggleMobileMode: function () {
                console.log("Calling Mobile Menu");
                var parrentCall = this._super();
                subMenus = this.element.find('.level-top');
                console.log(subMenus);
               jQuery.each(subMenus, jQuery.proxy(function (index, item) {
                    var category = jQuery(item).find('> a span').not('.ui-menu-icon').text(),
                        categoryUrl = jQuery(item).find('> a').attr('href'),
                        menu = jQuery(item).find('> .ui-menu');



     

                    if (menu.find('.all-category').length > 0) {
                        menu.find('.all-category').css("background-color","#ff5501")
                    }

                }, this));
                return parrentCall;

            },
            _toggleDesktopMode: function () {
                 console.log("Calling Destop Menu");
                 return this._super();
            }
            
            

        });

        return jQuery['mage']['menu'];


    };
});


```
