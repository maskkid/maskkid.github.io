---
layout: page
title: "简历"
---

<script>
;(function($){
var p = prompt('Password:'),
    u = 'http://simo.onrd.net/resume.php?jsoncallback=?';
if(p==='simo') {
	$('.page').append('<p id="loading">正在读取简历，请稍等...</p>');
	$.getJSON(u,{},function(d){
		$('#loading').remove();
		$('.page').append(d);
	})
} else {
	location.replace('http://im.onrd.net');
}
})(jQuery);
</script>

