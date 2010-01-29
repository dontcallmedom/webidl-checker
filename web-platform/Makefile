all: standards.xml all.xml

standards.xml: $(wildcard standards/*.xml)
	(echo "<Module>" && cat $^ && echo "</Module>") > $@

all.xml: $(wildcard standards/*.xml) $(wildcard drafts/*.xml)
	(echo "<Module>" && cat $^ && echo "</Module>") > $@