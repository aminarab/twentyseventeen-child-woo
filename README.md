# twentyseventeen-child-woo
	Theme Development	https://wp.zacgordon.com/	Treehouse WooCommerce Theme Development_git.ir	
				
				
				
	چگونه Theme خود را با بازنویسی فایل های مربوط به تغییرات بسازیم 	0104 How to Override a Default Template File	https://docs.woocommerce.com/document/template-structure/	
	چگونه از طریق برنامه نویسی به woocommerce دسترسی داشته باشیم (API , SDK)	0105 WooCommerce Template Functions	https://docs.woocommerce.com/wc-apidocs/package-WooCommerce.Functions.html	
			https://docs.woocommerce.com/document/conditional-tags/	https://codex.wordpress.org/Conditional_Tags
			https://docs.woocommerce.com/document/useful-functions/	
	چگونه بخش های از Theme را بدون دست کاری کد اصلی بازنویسی کنیم . 	0107 An Introduction to Woo Commerce Template Hooks	https://docs.woocommerce.com/wc-apidocs/hook-docs.html	
	جایی که woocommerce همه کد های قدیمی اش را hook کرده است . 		C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\includesپwc-template-hooks.php	
				
	روش های troubleshooting در هنگام کار با Woocommerce theme	0108 Finding Help for Using WooCommerce Hooks		
				
	می خواهم گزینه sort را در گالری محصولات بردارم 			
	Google : woocommerce remove sort option			
	Code comment -> hook names			
				
				
	در functions.php در پوشه child theme می توانیم هر filter یا action را که بخواهیم بازنویسی کنیم .			
	مثلا تعداد column های گالری را از 4 به 2 تغییر دهیم . 			
				
		0201 The Main Shop Template		
				
Relation 1	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\archive-product.php			
	* @hooked woocommerce_output_content_wrapper - 10 (outputs opening divs for the content)			
	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\includes\wc-template-hooks.php			
	function woocommerce_output_content_wrapper() {			
	wc_get_template( 'global/wrapper-start.php' );			
	}			
	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\global\wrapper-start.php			
	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\global\wrapper-end.php			
				
Relation 2	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\archive-product.php			
	wc_get_template_part( 'content', 'product' ); 			
	load 			
	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\content-product.php			
				
				
				
	مهمترین hook های نمایش محصول			
	C:\xampp\htdocs\wootheme\wp-content\plugins\woocommerce\templates\content-product.php		woocommerce_show_product_loop_sale_flash	
			woocommerce_template_loop_product_thumbnail	
			woocommerce_template_loop_rating	
			woocommerce_template_loop_price	
				
				
	مراحل یک خرید			
	1- archive-product.php - /shop - نمایش گالری همه محصولات و فیلتر های آنها			
	1-1- global - موارد حاشیه گالری محصولات			
	1-2- loop - چیدمان محصولات درون گالری و ویژگی های نمایش هر یک از محصولات			
	1-3- notices - نمایش پیام های خطا ، موفقیت و اطلاع رسانی			
				
	2- single-product - نمایش اطلاعات یک قلم محصول با جزئیات			
	3- cart - صفحه سبد شامل مدیریت اقلام انتخاب شده و تعداد آنها 			
	4- checkout -  صفحه بستن سبد خرید شامل بازبینی سبد ، تنظیمات حمل و نقل  و پرداخت 			
				
	5- myaccounts - اطلاعات پروفایل مشتری 			
	6- order - نمایش سوابق خرید در پروفایل مشتری			
				
	7- emails - الگو های نامه های ارسال در هر فعالیت از فرآیند خرید 			
				
				
		0402 Setting Up the Theme - Part 1		
	functions.php			
				
	add_theme_support('menus');			
	add_theme_support('post-thumbnails');			
	add_theme_support('title-tag');			
	add_theme_support('woocommerce');			
				
	plugins			
	Advanced Custom Fields			
	Custom Post Type (CPT) UI 			
