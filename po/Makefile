all:
.PHONY: update-po update-js update-pot
.PHONY: FORCE

LINGUAS := cs de el es fr it ja ko nl pl pt_BR ru sv tr zh_CN zh_TW

VERSION := $(shell grep '"version"' ../package.json | cut -d '"' -f 4)

POFILES := $(addsuffix .po,$(LINGUAS))
JSONFILES := $(addprefix ../app/locale/,$(addsuffix .json,$(LINGUAS)))

update-po: $(POFILES)
update-js: $(JSONFILES)

%.po: FORCE
	msgmerge --update --lang=$* $@ jerVNC.pot
../app/locale/%.json: FORCE
	./po2js $*.po $@

update-pot:
	xgettext --output=jerVNC.js.pot \
		--copyright-holder="The jerVNC Authors" \
		--package-name="jerVNC" \
		--package-version="$(VERSION)" \
		--msgid-bugs-address="novnc@googlegroups.com" \
		--add-comments=TRANSLATORS: \
		--from-code=UTF-8 \
		--sort-by-file \
		../app/*.js \
		../core/*.js \
		../core/input/*.js
	./xgettext-html --output=jerVNC.html.pot \
		../vnc.html
	msgcat --output-file=jerVNC.pot \
		--sort-by-file jerVNC.js.pot jerVNC.html.pot
	rm -f jerVNC.js.pot jerVNC.html.pot
