
# Straight North Front-end Frequent Stuff

## Tracking

### GoNorth tracking pnt (Method 1)
 
If trying to get pnt working is being a PITA, do this:
* Go to the gn code and add selector
 
```
<script>
(function(l,e,a,d,s) {
// straightnorth.com - 2018-10-29T13:12:18Z
window._GNL=window._GNL||{};window._GNL.config = l;window._GNL.callback = e;
a=document.createElement('script');
a.src='https://8ab0a26cb0027939bcf5-49c99c3c0c9c98b3365b710757036e1b.ssl.cf5.rackcdn.com/10001.js';
a.async=true;d=document.getElementsByTagName('script')[0];d.parentNode.insertBefore(a, d)})
({property: 10001, debug: false, selector: ['.yourClassOrID']},
function(leads) {
  // leads.submitOn('click', 'a.link-submit')
  // leads.pollForForm('.late-form')
})
</script>
```
To test this and make sure it's working:
 
* Open incognito browser
* Open dev pane > network tab > check preserve log
* Click XHR
* Visit page > Network tab > see 2x “visit” entries
* Go to page with form
* Application tab > Local storage > site.com
* Type into forms and notice lead_ keys show up with your data in value column
* Go back to network tab > submit form > see 2x “form-inquiry” go through 
 
Seeing each of those as you step along the process will confirm that the script was setup and is working correctly. 

### Add pnt with Vanilla JS  (Method 2)
Add one of the following in Google Tag Manager or in a script.js or footer.php file of the site. 
```
<script>
document.querySelectorAll('form')[0].classList.add('pnt')
</script>


<script>
  document.getElementById('form').classList.add('pnt')
</script>

<script>
  document.getElementsByClassName('form')[0].classList.add('pnt')
</script>

```
### Google Tag Manager Notes
**Tags that should run before another**:
* Global Site Tag > Adwords
* PNT > GoNorth

*We cannot track Marketo forms
## Squarespace

### Squarespace Redirect
// ADD THIS CODE BELOW TO FORM > post submit html
```
<script type="text/javascript">
  // Your Squarespace form redirect URL
  var redirectURL = "http://www.google.com";
     
  // Fixes an issue with IE8 and lower
  if ( navigator.userAgent.match(/MSIE\s(?!9.0)/) ) {
    var referLink = document.createElement( "a" );
    referLink.href = redirectURL;
    document.body.appendChild( referLink );
    referLink.click();

  // Standard redirect for all other browsers
  } else {
    window.location.assign( redirectURL );
  }
</script>
```
### Javascript not working until reloading of page issue
[JS not working fix](https://answers.squarespace.com/questions/188857/why-doesnt-my-javascript-code-work-until-i-refresh.html)

## Wordpress

### Advanced Custom Fields Repeatable Content
```
<?php if( have_rows(‘repeating_body’) ): ?>
    <div class=“row nested”>
        <?php while( have_rows(‘repeating_body’) ): the_row(); ?>
        <?php
        // VARS
        $content = get_sub_field(‘repeating_body_text’);
        ?>
        <?php if( $content ): ?>
        <div class=“col col-xs-12">
            <?php echo $content; ?>
        </div><!-- col -->
        <?php endif; ?>
    <?php endwhile; ?>
    </div><!-- row -->
<?php endif; ?>
```
### Get Year Script
`<?php echo date("Y"); ?>`

### If Home Is Blog
```
if ( is_front_page() && is_home() ) {
// Default homepage
} elseif ( is_front_page()){
//Static homepage
} elseif ( is_home()){
//Blog page
} else {
//everything else
}
```
## CSS
### CSS Font Smoothing
```
.class {
	text-rendering: auto;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-size-adjust: none;
}
```
