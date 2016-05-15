VERSION = 0.1.3

OUTDIR = Udapi-$(VERSION)
JAVADIR = $(OUTDIR)/udapi-java
PERLDIR = $(OUTDIR)/udapi-perl

all: clone doc

clone:
	mkdir -p $(OUTDIR)

	cp ../README.md $(OUTDIR)
	cp ../LICENSE.txt $(OUTDIR)

	git clone https://github.com/udapi/udapi-perl.git $(OUTDIR)/udapi-perl
	rm -rf $(OUTDIR)/udapi-perl/.git*

	git clone https://github.com/udapi/udapi-python.git $(OUTDIR)/udapi-python
	rm -rf $(OUTDIR)/udapi-python/.git*

	git clone https://github.com/udapi/udapi-java.git $(OUTDIR)/udapi-java
	rm -rf $(OUTDIR)/udapi-java/.git*

doc:    perldoc pydoc javadoc

pydoc:
	mkdir -p $(OUTDIR)/doc/python
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH && pydoc -w udapi.core.node.Node
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH &&	pydoc -w udapi.core.node.Root
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH &&	pydoc -w udapi.core.node.Bundle
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH &&pydoc -w udapi.core.node.Document
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH && pydoc -w udapi.core.node.Block
	export PYTHONPATH=$(OUTDIR)/udapi-python:$PYTHONPATH && pydoc -w udapi.core.node.Run

	mv udapi.core.node.*.html $(OUTDIR)/doc/python

javadoc:
	mkdir -p $(OUTDIR)/doc/java
	javadoc -d $(OUTDIR)/doc/java -sourcepath $(JAVADIR)/src/main/java -subpackages cz -encoding utf8

perldoc:
	mkdir -p $(OUTDIR)/doc/perl
	# cpanm Pod::ProjectDocs
	pod2projdocs -o $(OUTDIR)/doc/perl -l $(PERLDIR)/lib/

tgz:
	tar -czf $(OUTDIR).tgz $(OUTDIR)

clean:
	rm -rf $(OUTDIR)

