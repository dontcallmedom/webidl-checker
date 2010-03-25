
# based on ISO schematron implementation in XSLT1
# http://www.schematron.com/implementation.html
webidl-schematron.xsl: webidl-schematron.xml
	xsltproc ~/data/2010/01/iso_dsdl_include.xsl webidl-schematron.xml > webidl-schematron1.xml
	xsltproc ~/data/2010/01/iso_abstract_expand.xsl webidl-schematron1.xml > webidl-schematron2.xml
	xsltproc ~/data/2010/01/iso_svrl_for_xslt1.xsl webidl-schematron2.xml > $@

# Generates widlproc XML out of IDLs
IDLS := $(wildcard tests/idl/*.idl)
XML_IDLS := $(patsubst tests/idl/%.idl,tests/idl/%.xml,$(wildcard tests/idl/*.idl))

generate-xml-idls: $(XML_IDLS) $(IDLS)

tests/idl/%.xml: tests/idl/%.idl
	widlproc $< > $@

TESTS_OUTPUT := $(patsubst tests/idl/%.xml,tests/output/%.txt,$(wildcard tests/idl/*.xml))

generate-test-output: generate-xml-idls $(TESTS_OUTPUT) $(XML_IDLS) webidl-schematron.xsl

tests/output/%.txt: webidl-schematron.xsl tests/idl/%.xml
	xsltproc --novalid $^ |grep svrl:text|sed -e "s/^.*>\([^<]*\)<.*/\1/" > $@

test: webidl-schematron.xsl $(XML_IDLS)
	for i in $(XML_IDLS) ; do xsltproc --novalid webidl-schematron.xsl $$i |grep svrl:text|sed -e "s/^.*>\([^<]*\)<.*/\1/" |diff - tests/output/`basename $$i .xml`.txt ; done