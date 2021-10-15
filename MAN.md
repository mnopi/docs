# MAM 

##[Ascii](https://docs.asciidoctor.org/asciidoctor/latest/manpage-backend/)
Minimum structure with :doctype: 
1. Document Header 
2. Document Attributes 
3. The NAME Section 
4. The SYNOPSYS Section 

[syntax-quick-reference](https://docs.asciidoctor.org/asciidoc/latest/syntax-quick-reference/)

#### Code highlighters 
1. [:source-highlighter: highlight.js](https://docs.asciidoctor.org/asciidoctor/latest/syntax-highlighting/highlightjs/)
   :highlightjs-languages: rust, swift
2. [rouge supports](https://github.com/rouge-ruby/rouge/tree/master/spec/lexers)
   :source-highlighter: rouge 
   :rouge-style: monokai
   [source%linenums,ruby]
3. :source-highlighter: coderay
4. [pygments support](https://pygments.org/languages/)
   :source-highlighter: pygments.rb
   :pygments-style: manni
   :pygments-linenums-mode: inline
   [source%linenums,ruby]

````Makefile
RONN := ronn -W
PAGES := x-code-path.1 bats.7
ORG := bats-core
MANUAL := 'Bash Automated Testing System'
ISOFMT := $(shell date -I)
RM := rm -f

.PHONY: all clean

all: $(PAGES)

bats.1: bats.1.md
	$(RONN) --date=$(ISOFMT) --manual=$(MANUAL) --organization=$(ORG) --roff $<

x-code-path.1: xcode-path.adoc
	@asciidoctor -b manpage $<

bats.7: bats.7.md
	$(RONN) --date=$(ISOFMT) --manual=$(MANUAL) --organization=$(ORG) --roff $<

clean:
	$(RM) $(PAGES)
````
