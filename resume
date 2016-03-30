---
layout: page
title: "简历"
---

<script>
;(function($){
var p = 'simo',//prompt('Password:'),
    u = 'http://resume.onrd.net/resume.php?jsoncallback=?',
    n = 1;
console = console || {};
console.log = console.log?console.log:function(){};
function getResume(){
	$.ajax({
		url: u,
		dataType: 'json',
		data: {},
		timeout : 3000,
		beforeSend : function(){console.log(n, arguments)},
		success: function(d){
			console.log(status);
			$('#loading').remove();
			$('.page').append(d);
		},
		error: function(XMLHttpRequest, textStatus, errorThrown) {
			if(n++<5) {
				getResume()
			} else {
				$('#loading').remove();
				$('.page').append('<p>简历飘在墙外，此刻无法翻越，请稍后重试或翻墙查阅。给您造成的不便，请见谅</p>')
			}
		},
	})
}
if(p==='simo') {
	$('.page').append('<p id="loading">正在读取简历，请稍等...</p>');
	getResume();
} else {
	location.replace('http://im.onrd.net');
}
})(jQuery);
</script>

