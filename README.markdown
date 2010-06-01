# Gritter for jQuery

This is a fork of the gritter jQuery plugin by [jboesch](http://boedesign.com/blog/2009/07/11/growl-for-jquery-gritter/). We forked this plugin to make a few changes to the original version as follows:

- Dropped IE6 support
- Moved close button to top right corner
- Restyled window background using CSS3 instead of images
- Changed callback events to determine whether close button was clicked
- Added additional option to allow hiding of close button


## Dropped IE6 support
It seems IE6 has almost had it’s day now so we’ve dropped support for this dog of a browser on our [production application](http://smoothcontract.com). The original gritter plugin has some additional CSS hacks to work with this browser but we frankly didn’t think it was worth bothering so removed ~20 lines of CSS. In addition, this allows the CSS to be validated correctly.

## Moved close button
We moved the close button to the top right corner (previously it was in the top left) to avoid it clashing with the image in the notification window. Purely subjective, but we think it looks better.

## Restyled using CSS3
The original gritter plugin looks gorgeous but relies on large images to provide the notification background. We found a problem with this on slow connections as the gritter notification would be shown and disappear before the background image had time to load leading to white text on a white background!

On newer browsers with early CSS3 support (Firefox, Safari and Chrome) we managed to replicate the exact look of the original using almost pure CSS (only one image is used for the close button). On IE the notification window is still functional but looks a bit basic (an opaque rectangle) - we can live with that though.

## Callback changes
The original gritter plugin fires a before_close callback when the user manually clicks the close button or the notification times out and fades automatically. Unfortunately there’s no way to tell which of those events fired the callback so we changed this to only fire when the close button is clicked.

## Hiding close button
In some cases we wanted to display the notification without allowing the user to close the window (primarily because we don’t want to allow a notice to be ignored as described above) so added an option to hide the close button as shown in this example:

	$.gritter.add({
		title: ‘Look, no close button’,
		text: ‘This notification has no close button’,
		hide_close: true
	});


You can see a demonstration of these changes at [http://smoothcontract.com](http://smoothcontract.com) - Click the DEMO link.