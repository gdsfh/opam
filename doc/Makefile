OPAM    = ../_obuild/opam/opam.byte
TOPICS  = $(shell $(OPAM) help topics)
HELPFMT = --help=groff

.PHONY: man pdf
all: man pdf

man:
	rm -f man/*
	$(OPAM) $(HELPFMT) > man/opam.1
	for i in $(TOPICS); do\
	  $(OPAM) $$i $(HELPFMT) > man/opam-$$i.1;\
	done
	for i in opam-mk-repo opam-check; do\
	  pandoc -s -t man man-ext/$$i.md -o man/$$i.1;\
	done

pdf:
	$(MAKE) -C tutorials