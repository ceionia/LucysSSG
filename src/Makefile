# ---------- OUTPUT FILES ----------
# Add new files for the final site here!
# The build & template rules will try to create them

files = index.html

# ----------------------------------


# If the OUTDIR variable does not exist, create it with a default
ifeq ($(OUTDIR),)
OUTDIR=out
endif

# Construct the full output list 
LIST=$(addprefix $(OUTDIR)/, $(files))

# Just `make` should build our whole output list
all: $(LIST)

# Automatic directory creation
# https://ismail.badawi.io/blog/automatic-directory-creation-in-make/
.PRECIOUS: $(OUTDIR)/. $(OUTDIR)%/. 
$(OUTDIR)/:		; mkdir -p $@
$(OUTDIR)%/:	; mkdir -p $@
.SECONDEXPANSION:

# `make clean` just removes our OUTDIR
clean:
	rm -rf $(OUTDIR)


# ---------- BUILD & TEMPLATE RULES ----------

# Default template - .html (base-start.html + content + base-end.html)
$(OUTDIR)/%.html: src/%.html | $$(@D)/
	cat templates/base-start.html $< templates/base-end.html > $@

# Bare template - .bare.html (just copy)
$(OUTDIR)/%.html: src/%.bare.html | $$(@D)/
	cp $< $@

# Create .html from .md using kramdown
src/%.html: src/%.md | $$(@D)/
	kramdown $< > $@

# Other files - just copy
$(OUTDIR)/%: src/% | $$(@D)/
	cp $< $@

# --------------------------------------------
