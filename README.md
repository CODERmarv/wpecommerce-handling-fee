# wpecommerce-handling-fee
Adding handling fee for wpEcommerce

/*
 * @uses wpsc_cart
 *
 * @return string the total price of the cart, with a currency sign
 */
function wpsc_cart_total( $format_for_display = true ) {
	global $wpsc_cart;
	$total = 0;
	$handling = 2.00;
    $final = 0;

	if ( _wpsc_verify_global_cart_has_been_initialized( __FUNCTION__ ) ) {

		$total = $wpsc_cart->calculate_total_price();
		$final = $total + $handling;
		if ( $format_for_display ) {
			$final = wpsc_currency_display( $final );
		}
