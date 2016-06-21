根据AMD规范写插件
```javascript
;(function () {
	'use strict';
	function pluginName(layer, options) {
		var something;
		options = options || {};
		this.layer = layer;
		this.param1 = options.param1||'';
	}
	var privateField = '';
	pluginName.prototype.fun1 = function(){
	
	}
	/**
	 * Factory method for creating a object
	 */
	pluginName.attach = function(layer, options) {
		return new pluginName(layer, options);
	};
    if (typeof define === 'function' && typeof define.amd === 'object' && define.amd) {

		// AMD. Register as an anonymous module.
		define(function() {
			return pluginName;
		});
	} else if (typeof module !== 'undefined' && module.exports) {
		module.exports = pluginName.attach;
		module.exports.pluginName = pluginName;
	} else {
		window.pluginName = pluginName;
	}
}());
```