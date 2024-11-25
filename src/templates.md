# Templates

### default template

---

`templates/base-start.html` and `templates/base-end.html` are used as the default template, for all .html files (and .html processed from .md).  

when you build your site, the content of `templates/base-start.html` will be added before each page's content, and `templates/base-end.html` after.  
  
to not apply the template to a page, use `.bare.html`/`.bare.md` as the extension.  
  
  
### adding a template

---

to add a template, add a rule to the makefile. you can use the default template as reference:  
```
# Default template - .html (base-start.html + content + base-end.html)
$(OUTDIR)/%.html: src/%.html | $$(@D)/
	cat templates/base-start.html $< templates/base-end.html > $@
```  
  
as an example, to create a new template which will work on all files ending in `.media.html`, add the following rule to the build & template rules section:  
```
$(OUTDIR)/%.html: src/%.media.html | $$(@D)/
	cat templates/media-start.html $< templates/media-end.html > $@
```  
don't forget to create `templates/media-start.html` and `templates/media-end.html`  
note `src/%.media.html` in the first line, this matches any file in `src/` ending with `.media.html`. the output then is `$(OUTDIR)/%.html`, with `.html` instead of `.media.html` - we don't want the template selector in the final output name.  
  
  
### removing a template

---

to remove a template, simply delete its rule from the makefile.  
for example, to delete the default template, remove the following lines:  
```
# Default template - .html (base-start.html + content + base-end.html)
$(OUTDIR)/%.html: src/%.html | $$(@D)/
	cat templates/base-start.html $< templates/base-end.html > $@
```
