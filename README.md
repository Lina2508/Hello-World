# Hello-World$(document).ready(function(){
	
	$('[href="#"]').click(function(e){
		e.preventDefault();
	});
	
	$('.nav-mobile-btn, .nav-overlay').click(function(){
		$('.nav, .nav-overlay').toggleClass('mobile-show');
	});
	
	$('.slider-items').slick({
		slidesToShow: 3,
		slidesToScroll: 3,
		prevArrow: '<button class="slider-arrow slider-prev"><span class="icon icon-prev"></span></button>',
		nextArrow: '<button class="slider-arrow slider-next"><span class="icon icon-next"></span></button>',
		responsive: [
			{
				breakpoint:768,
				settings: {
					slidesToShow: 2,
					slidesToScroll: 2,
				}
			},
			{
				breakpoint:480,
				settings: {
					slidesToShow: 1,
					slidesToScroll: 1,
				}
			},
		],
	});
	
	$('.top-slider-outer-slider').slick({
		arrows: false,
		swipe: false,
	});
	
	$('.top-slider-inner-slider').slick({
		prevArrow: '<button class="slider-arrow slider-prev"><span class="icon icon-prev"></span></button>',
		nextArrow: '<button class="slider-arrow slider-next"><span class="icon icon-next"></span></button>',
	});
	
	$('a[data-slide-to="0"]').closest('li').addClass('active');
	
	$('.top-slider-inner-slider').on('beforeChange', function(event, slick, currentSlide, nextSlide){
		$(this).closest('.top-slider-outer-slide').find('.top-slider-inner-nav a[data-slide-to="'+nextSlide+'"]').closest('li').addClass('active').siblings().removeClass('active');
	});
	
	$('.top-slider-outer-slider').on('afterChange', function(event, slick, currentSlide, nextSlide){
		var target = $('.top-slider-outer-slide.slick-active').data('slick-index');
		$('.top-slider-outer-nav a[data-slide-to="'+target+'"]').closest('li').addClass('active').siblings().removeClass('active');
	});
	
	
	$('.top-slider-outer-nav a').click(function(){
		var targetSlide = $(this).data('slide-to');
		$('.top-slider-outer-slider').slick('slickGoTo', targetSlide);
		$(this).closest('li').addClass('active').siblings().removeClass('active');
	});
	
	$('.top-slider-inner-nav a').click(function(){
		var targetSlide = $(this).data('slide-to');
		$(this).closest('.top-slider-outer-slide').find('.top-slider-inner-slider').slick('slickGoTo', targetSlide);
	});
	
	$('.image-popup-vertical-fit').magnificPopup({
		type: 'image',
		closeOnContentClick: true,
		mainClass: 'mfp-img-mobile',
		image: {
			verticalFit: true
		}
