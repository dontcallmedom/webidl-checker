This is the source code for the [W3C on-line WebIDL
checker](http://www.w3.org/2009/07/webidl-check), a tool verify the
correctness of [WebIDL](http://dev.w3.org/2006/webapi/WebIDL/) fragments
embedded in HTML documents.

It defines a Python-based CGI interface on top of
[widlproc](https://github.com/dontcallmedom/widlproc), with additional semantic checks done
through a [Schematron analysis](widlproc-schematron/) of the resulting
XML file.

Some of these analysis rely on knowing which WebIDLs are well-known in
the Web platform: this list of well-known WebIDLs are maintained in the
[Web platform sub-directory](web-platform/).
