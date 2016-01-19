# Mvalidate

表单格式验证, 依赖jQuery。

#How to use

Include jQuery and Mvalidate.js;

```html
  <script src="http://cdn.bootcss.com/jquery/1.11.1/jquery.min.js"></script>
  <script src="path/to/Mvalidate.js"></script>
```
Example:
```html
<form>
	<input type="text" data-vali="email" name="email" />
</form>
```

```javascript
var validateForm = new Malidate($("form"));
.....other code .......
    if (validateForm.validate()) {
        // todo something
        // 如果验证通过返回表单数据，可通过validateForm.data获取
        // 否则返回false
    }
...... other code .....
```

#API与使用说明

自带验证规则： number, email, mobile(只验证手机号) ,tel(可通时时验证手机、座机、400、800服务号),password, notNull, url

1. ［data-vali］－－ 验证规则；  
   ［name］－－ 表单键值名， 不设置该属性不影响验证。但是返回的表单数据中将不包含该项。  
2. 验证函数： .validate(option)  
    @option:  null 不传入option时，验证所有项；   
        {array} 传入数组时验证数组中包含项；  
        {string} 传入string时只验证单项;   
3. 添加验证规则： .addValidations(object)  
```javascript
.addValidations({
    IDcard: function(v) {
        // v表单需验证值
        if ( !v.length ) {
            return false;
        }

        var r = /(^\d{15}$)|(^\d{17}([0-9]|X)$)/;
        return r.test(v);
    }
})
```
