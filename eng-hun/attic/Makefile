FREEDICT_TOOLS ?= ../../tools
hedir ?= ../hun-eng
VPATH += $(hedir)
DISTFILES = eng-hun.tei.header Makefile ChangeLog
supported_phonetics =
include $(FREEDICT_TOOLS)/mk/dicts.mk

dbview_in_path := $(shell which dbview 2>/dev/null)

$(hedir)/SZOTAR.DBF:
	$(MAKE) -C "$(hedir)" SZOTAR.DBF

eng-hun.tei: eng-hun.tei.header $(hedir)/SZOTAR.DBF szotar-dbf2tei.pl
ifeq ($(dbview_in_path),)
	@echo "To get the data out of the dBase database, we require the tool"
	@echo "\`dbview' from Martin Schulze aka Joey."
	@echo "Try to get it from http://packages.debian.org/stable/misc/dbview"
	@false
else
	cp $(hedir)/SZOTAR.DBF .
	cp $< $@
	$(hedir)/szotar-dbf2tei.pl -v --reverse >> $@
endif

