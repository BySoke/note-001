# 一.JQuery插件

## 1.Multiple Select-多选/搜索下拉框

- [官网地址](https://multiple-select.wenzhixin.net.cn/index.html?locale=zh_CN)

> 使用示例:

- 引入multiple-select.css及multiple-select.js
- select元素添加multiple="multiple"属性

- DOM渲染之前初始化

  ```javascript
  $(function () {
  //初始化select支持多选
  $('select').multipleSelect();
  }
  ```

- 设置默认选中(支持默认多选,传参数组)

  ```javascript
  $("#selectCode").multipleSelect('check', codeId);
  $("#select").multipleSelect('setSelects', '[' + arrYear.toString() + ']');
  ```

  

- 其他取值、刷新option等方法见官网文档

## 2.jquery.nicescroll-滚动条

- [官网地址](https://nicescroll.areaaperta.com/)

- [Github地址](https://github.com/inuyaksa/jquery.nicescroll)

## 3.xlsx.js-excel预览导出

- [官网地址](https://sheetjs.com/)
- [Github地址](https://github.com/sheetjs/sheetjs)

> 使用示例:

  ```javascript
function Export(title) {
	var blob = sheet2blob(XLSX.utils.table_to_sheet($('#'+ title +'')[0]));
	//设置链接
	var link = window.URL.createObjectURL(blob);
	//创建a标签
	var a = document.createElement("a");
	//设置被下载的超链接目标（文件名）
	a.download = "年度审查结论情况汇总.xlsx";
	//设置a标签的链接
	a.href = link;
	//a标签添加到页面
	document.body.appendChild(a);
	//设置a标签触发单击事件
	a.click();
	//移除a标签
	document.body.removeChild(a);
}

// 将一个sheet转成最终的excel文件的blob对象，然后利用URL.createObjectURL下载
function sheet2blob(sheet, sheetName) {
	sheetName = sheetName || 'sheet1';
	var workbook = {
		SheetNames: [sheetName],
		Sheets: {}
	};
	workbook.Sheets[sheetName] = sheet;
	// 生成excel的配置项
	var wopts = {
		// 要生成的文件类型
		bookType: 'xlsx',
		// 是否生成Shared String Table，官方解释是，如果开启生成速度会下降，但在低版本IOS设备上有更好的兼容性
		bookSST: false,
		type: 'binary'
	};
	var wbout = XLSX.write(workbook, wopts);
	var blob = new Blob([s2ab(wbout)], {type: "application/octet-stream"});

	// 字符串转ArrayBuffer
	function s2ab(s) {
		var buf = new ArrayBuffer(s.length);
		var view = new Uint8Array(buf);
		for (var i = 0; i != s.length; ++i) view[i] = s.charCodeAt(i) & 0xFF;
		return buf;
	}
	return blob;
}
  ```

## 4.jquery.wordexport-导出为word

- [FileSaver地址](https://github.com/eligrey/FileSaver.js)

- [jquery.wordexport.js地址](https://github.com/Jasmine1227/jquery.wordexport.js)
- [jQuery-Word-Export地址](https://github.com/markswindoll/jQuery-Word-Export)

> 使用示例:

- 该插件依赖于JQuery与FileSaver,需先引入依赖插件

  ```javascript
  function exportInfo() {
		//wordExport()可填参数为导出的文件名
		var personName = $("#authorName").val();
		$("#export").wordExport(personName + "-项目统计信息");
  }
  ```
  
  

## 5.JQuery从1.4.2升级至3.5.1

> 由于JQuery从1.9版本后移除了$.browser的支持,高版本如何去兼容低版本?

- 引入jQuery Migrate,是应用迁移辅助插件，是用于高级版本兼容低级版本辅助插件。例如jQuery版本用的是1.x，计划升级到3.x，就可以在页面删除1.x版本，换成3.x版本，如果有脚本错误，就引入jquery-migrate插件用于兼容低版本，同时也显示低版本方法替换成新版本方法的方案。

- [官网地址](https://plugins.jquery.com/migrate/)

- [Github地址](https://github.com/jquery/jquery-migrate)

- 在jquery中添加兼容代码

  ```javascript
   jQuery.browser={};
  (function(){
      jQuery.browser.msie=false; 
      jQuery.browser.version=0;
      if(navigator.userAgent.match(/MSIE ([0-9]+)./)){ 
          jQuery.browser.msie=true;
          jQuery.browser.version=RegExp.$1;
      }
  })();	
  ```

  

