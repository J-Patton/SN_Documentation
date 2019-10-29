# PNT & Form Tracking

### Outline
1. Tracking with Vanilla JS
2. Form Tracking Extended
3. Top 5 Things You Never Knew About Form Tracking
4. jQuery Tracking
5. Form Tracking Testing

## Tracking with Vanilla JS
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

<script>
    document.getElementsByTagName("element")[0].classList.add('pnt');
</script>

<script>
    document.getElementById('form_id').classList.add('pnt')
</script>

<script>
    document.querySelector('firstElement')[0].classList.add('pnt')
</script>

<script>
    document.querySelectorAll('allElementsOfType')[0].classList.add('pnt')
</script>

<script>
    document.querySelectorAll('form')[3].classList.add('pnt')
</script>
```

### Hit all elements of `<form>`
```
<script>
var forms = document.querySelectorAll('form')
for (var i = 0; i < forms.length; i++) {
  forms[i].classList.add('pnt')
}
</script> 

```

## Form Tracking Extended

### Selector, pollForForm, submitOn

**selector: [‘.form-class’]**
>This is used when you're trying to target a form to add pnt. Use this when other methods of adding pnt are not working. 

**leads.pollForForm(‘.late-form’)**
>This is used when the form is not sending data or tracking is not working. You need to target the form's id or class for this to work. Think of this as a loop.

**leads.submitOn(‘click’, ‘a.link-submit’)**
>Use this when form-inquiry isn't being passed or if the submit button is not a standard one. Simply target the submit button, replace `a.link-submit` to class or id of submit button.

**ignoreFields**
>If you want to ignore fields such as password or other personal information

<a href="https://gist.github.com/kolbaba/469b69a69a1422909329631117b03f30" target="_blank">See examples of usage

**_GNL.refreshForms()**
>Trigger the form init handler to rescan the DOM for forms. This is useful in situations where forms are injected into the DOM after the tracker code has initilized.

## Top 5 Things You Never Knew About Form Tracking
1. If it's an iframe, we can't track it
2. In Contact Form 7 you can add `html_class="class-here" html_id="id-here"` to the shortcode
3. In Gravity Forms you can add `pnt` in the form settings
4. Pending
5. Pending

## jQuery Tracking
**Note:** We are no longer tracking with jQuery, this section has been archived. 

[See jQuery Tracking](https://gist.github.com/kolbaba/578aa2db319023e5178c3856e622abed).

## Form Tracking Testing
* Open incognito browser
* Open dev pane > network tab > check preserve log
* Visit page > Network tab > see 2x “visit” entries
* Go to page with form
* Application tab > Local storage > site.com
* Type into forms and notice lead_ keys show up with your data in value column
* Go back to network tab > submit form > see 2x “form-inquiry” go through
