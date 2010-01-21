all: html5.xml fileapi.xml

html5.xml:
	../../webidl-check http://dev.w3.org/html5/spec/Overview.html > $@

fileapi.xml:
	../../webidl-check http://dev.w3.org/2006/webapi/FileAPI/ > $@