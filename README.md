# Coding Standards  
Production coding standards to be followed. Everything in this document is a standard that must be followed by **ALL** production team members. If you have suggestion, you can talk to John or Michael and further discuss.  

#####Purpose  

##Class Names
1. **Always use dashes**  
 
	Correct:  
	```html
	<img class="img-center" />
	```  
	Not:  
	```html
	<img class="imgCenter" />
	```
  
2. **Always lowercase** 

	Correct:  
	```html
	<img class="img-center" />
	```  
    Not:  
	```html
	<img class="img-Center" />
	```
	```html
	<img class="IMG-CENTER" />
	```
  
3. **Custom classes are always after Bootstrap classes**  

	Correct:  
	```html
	<div class="row search-row">
	```  
	Not:  
	```html
	<div class="search-row row">
	``` 

##Naming Conventions
1. **Always use the type of content in the section for the class on the parent tag**  
	
	```php
	<section class="homepage-slideshow">
		<?= $this->componentModules()->reserved1; ?> <? /* Slideshow::responsive1 */ ?>
	</section>
	```
	OR  
	
	```php
	<section class="slideshow-section">
		<?= $this->componentModules()->reserved1; ?> <? /* Slideshow::responsive1 */ ?>
	</section>
	```  
	
2. **For sections that are side-by-side, use both types of content in the parent’s class name. Then for the children, use the type of content within each...**  

	```html
	<section class="homepage-content-google-map">
		<div class="container">
			<div class="row">
				<div class="col-xs-12 col-sm-6 homepage-content"></div>
				<div class="col-xs-12 col-sm-6 homepage-google-map"></div>
			</div>
		</div>
	</section>
	```

3. **Try to avoid ambiguous names:**  

	```html
	<div class="item-1"></div>
	<div class="cm-4"></div>
	```  
4. **Beyond that, make your class names make sense. We are humans and we still like to read in our native language.**  

##Layout
1. **All sections of the homepage will be between a single ```<section>``` tag that has the class of ```com-home-page<?= $this->classPrefix ?>```**  

	Correct  
	```php
	<section class="com-home-page<?= $this->classPrefix ?>">
		// All sections go between here
	</section>
	```
	Not  

	```php
	<section class="com-home-page<?= $this->classPrefix ?>">
		// Slideshow
	</section>
	<section class="com-home-page<?= $this->classPrefix ?>">
		// Google Map
	</section>
	```

2. **All Module placeholders will have a comment next to them with the module name and theme.**

	```php
	<?= $this->componentModules()->reserved1; ?> <? /* Slideshow::responsive1 */ ?>
	<?= $this->componentModules()->reserved2; ?> <? /* GoogleMap::responsive1 */ ?>
	```

 
##CSS
1.	**Use a semicolon after every declaration.**
	- End every declaration with a semicolon for consistency and extensibility reasons.

	```css
	.test {
 		display: block;
  		height: 100px;
	}
	```
	
2. **Indent all block content**
	- Indent all block content, that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

	```css
	@media screen, print {
  		html {
    		background: #fff;
    		color: #444;
  		}
  	}
	```

3. **Use a space after a property name’s colon.**
	- Always use a single space between property and value (but no space between property and colon) for consistency reasons.  

	```css
	h3 {
	  font-weight: bold;
	}
	```

4. **Use a space between the last selector and the declaration block.**
	- Always use a single space between the last selector and the opening brace that begins the declaration block.
	- The opening brace should be on the same line as the last selector in a given rule. 

	```css
	#video {
	  margin-top: 1em;
	}
	```

5. **Use single quotation marks for attribute selectors and property values.**
	- Use single ('') rather than double ("") quotation marks for attribute selectors or property values. Do not use quotation marks in URI values (url()).  
	_**Exception:** If you do need to use the @charset rule, use double quotation marks—single quotation marks are not permitted._   

	```css   
	@import url(//www.google.com/css/maia.css);
	 
	html {
	  font-family: 'open sans', arial, sans-serif;
	}
	```

6. **Group stylesheet sections together by using comments. Separate sections with new lines.**   

	```css   
	/* Header */
	 
	#adw-header {}
	 
	/* Footer */
	 
	#adw-footer {}
	 
	/* Gallery */
	 
	.adw-gallery {}
	```

7. **Use Tabs**
8. **Use shorthand notation where possible.**
9. **Use hex color codes #000 unless using rgba();**
10. **Always provide fallback properties for older browsers.** 

	```css   
	.media {
	  overflow: hidden;
	  color: #fff;
	  background-color: #000; /* Fallback value */
	  background-image: linear-gradient(black, grey);
	}
	 
	.media .img {
	  float: left;
	  border: 1px solid #ccc;
	}
	 
	.media .img img {
	  display: block;
	}
	 
	.media .content {
	  background: #fff url(../images/media-background.png) no-repeat;
	}
	```

11.	**All ids, classes and attributes must be lowercase with hyphens used for separation.** 

	```css   
	/* GOOD */
	.dataset-list {}
	 
	/* BAD */
	.datasetlist {}
	.datasetList {}
	.dataset_list {}
	```

12. **Try keep all selectors loosely grouped into modules where possible and avoid having too many selectors in one declaration to make them easy to override.** 

	```css   
	/* Avoid */
	ul#dataset-list {}
	ul#dataset-list li {}
	ul#dataset-list li p a.download {}
	```

	- Instead here we would create a dataset "module" and styling the item outside of the container allows you to use it on its own e.g. on a dataset page: 

	```css   
	.dataset-list {}
	.dataset-list-item {}
	.dataset-list-item .download {}
	```

##HTML
1. **Use HTML5.**
	- Do not close void elements, i.e. write 
	```html
	<br>
	```  
	Not  
	```html 
	<br />
	```
		- http://www.w3.org/TR/html-markup/syntax.html#syntax-elements 
		- www.colorglare.com/2014/02/03/to-close-or-not-to-close.html  

2. **Use HTML according to its purpose.**
	- Use elements (sometimes incorrectly called "tags") for what they have been created for. For example, use heading elements for headings, p elements for paragraphs, a elements for anchors, etc.

	- Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.  

3. **Omit type attributes for style sheets and scripts.**
	- Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).
	- Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

	```html
	<link rel="stylesheet" href="//www.google.com/css/maia.css">
	```  

4. **Use a new line for every block, list, or table element, and indent every such child element.**  
	- Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.
	- Also, indent them if they are child elements of a block, list, or table element.

	```html
	<blockquote>
	  <p><em>Space</em>, the final frontier.</p>
	</blockquote>
	 
	<ul>
	  <li>Moe</li>
	  <li>Larry</li>
	  <li>Curly</li>
	</ul>
	```

5. **When quoting attributes values, use double quotation marks.**
	- Use double ("") rather than single quotation marks ('') around attribute values.

	```html
	<a class="maia-button maia-button-secondary">Sign in</a>
	```

 
##JavaScript

1. **White Space**
	- Tab must be used for indentation at all times. Unlike in idiomatic whitespace must not be used _inside_ parentheses between the parentheses and their Contents.

	```javascript
	// BAD: Too much whitespace.
	function getUrl( full ) {
	  var url = '/styleguide/javascript/';
	  if ( full ) {
	    url = 'http://okfn.github.com/ckan' + url;
	  }
	  return url;
	}
	 
	// GOOD:
	function getUrl(full) {
	  var url = '/styleguide/javascript/';
	  if (full) {
	    url = 'http://okfn.github.com/ckan' + url;
	  }
	  return url;
	}
	```
2. **Quotes**
	- Single quotes should be used everywhere unless writing JSON or the string contains them. This makes it easier to create strings containing HTML.

	```javascript
	jQuery('<div id="my-div">').appendTo('body');
	```

##Comments
1. **All comments in any .phtml or .php file will use be in PHP**  

	```php
	<? /* Comment */ ?>
	```
