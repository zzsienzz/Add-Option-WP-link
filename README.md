#//ADD Nofollow,title,confirm link (Script by Sien)
add_action( 'after_wp_tiny_mce', function(){
echo '<script>
	var originalWpLink;
	if($("#wp-link-more").length==0){
	$(".wp-link-text-field").append(\'<div id="wp-link-more"><div><label><span>Title </span><input id="wp-link-title" type="text"></label></div><div><label><span>Confirm</span><input id="wp-link-confirm" type="text"></label></div> <div><label><span></span><select id="wp-link-color"><option value="">Color</option><option value="red">Red</option><option value="blue">Blue</option> <option value="green">Green</option> <option value="gray">Gray</option> <option value="hotpink">Pink</option> <option value="yellow">Yellow</option> <option value="black">black</option> <option value="white">White</option></select></label></div>  <div><label><span style="width: 83.5px;"></span><input type="checkbox" id="wp-link-nofollow" /> rel="nofollow"</label></div>   </div>   <style>.has-text-field #wp-link .query-results {top: 250px;}</style>\');
	originalWpLink = _.clone( wpLink );
	wpLink = _.extend( wpLink, {
	getAttrs: function() {
						var attrs = originalWpLink.getAttrs();
						attrs.title = $("#wp-link-title").val();
						attrs.confirm = $("#wp-link-confirm").val();
						attrs.rel = $("#wp-link-nofollow").prop("checked") ? "nofollow" : false;
						attrs.color = $("#wp-link-color").val();
						return attrs;
					},
	buildHtml: function(attrs){
						var html = \'<a href="\' + attrs.href + \'"\';
						if(attrs.target){
							html += \' target="\' + attrs.target + \'"\';
						}
						if(attrs.rel){
							html += \' rel="\' + attrs.rel + \'"\';
						}
						if(attrs.title){
							html += \' title="\' + attrs.title + \'"\';
						}
						if(attrs.confirm){
							html += \' onclick="return confirm(\\\'\'+attrs.confirm+\'\\\')"\';
						}
						if(attrs.color){
							html += \' style="color:\' + attrs.color + \'"\';
						}
						return html + \'>\';
					},
				});
	}
		
	</script>';

});
