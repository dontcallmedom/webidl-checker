all: $(patsubst %.idl,%.xml,$(wildcard *.idl))

%.xml: %.idl
	widlproc -no-dtd-ref $<| tail --lines=+2 > $@ # tail for removing XML Decl