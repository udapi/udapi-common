VERSION = 0.1.1111

OUTDIR = Udapi-$(VERSION)
JAVADIR = udapi-java

all: clone doc

clone:
	mkdir -p $(OUTDIR)

	git clone https://github.com/udapi/udapi-perl.git $(OUTDIR)/udapi-perl
	rm -rf $(OUTDIR)/udapi-perl/.git

	git clone https://github.com/udapi/udapi-python.git $(OUTDIR)/udapi-python
	rm -rf $(OUTDIR)/udapi-python/.git

doc:    perldoc pydoc javadoc

pydoc:
	mkdir -p $(OUTDIR)/doc/python
	pydoc -w udapi.core.node.Node
	pydoc -w udapi.core.node.Root
	pydoc -w udapi.core.node.Bundle
	pydoc -w udapi.core.node.Document
	pydoc -w udapi.core.node.Block
	pydoc -w udapi.core.node.Run

	mv udapi.core.node.*.html $(OUTDIR)/doc/python

javadoc:
	mkdir -p $(OUTDIR)/doc/java
	javadoc -d $(OUTDIR)/doc/java -sourcepath $(JAVADIR)/src/main/java -subpackages cz

tgz:
	tar -czf $(OUTDIR).tgz $(OUTDIR)

clean:
	rm -rf $(OUTDIR)

