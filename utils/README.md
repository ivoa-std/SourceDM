# Generating the model doc from the VODML

This utility automate as much as possible the transalation of the VODML 
file into a documented Tex file which is inserted into the main Tex file

The process is 3 steps:
- `mango.vo-dml.xml` to `desc.mango.vo-dml.xml` 
  - insert the descriptions located in `vo-dml/desc`intio the vo-dml file
  - description of model elements are like `desc.vodmlid.txt`
  - missing description files are printed out; they can be edited by hand.
  
- `desc.mango.vo-dml.xml` to `doc/model.tex` 
  - XSLT transform
  - style sheet `ivoatex/vo-dml2ivoatex.xslt`

- apply the custom TOC from `toc.json`
  - edit the custom toc (new section must contain the `(added)` word
  - The TEX document is rebuilt following that TOC
  - The head text of the added section is in `vo-dml/sections`
  ) The finlma TEX file is named model_toc.tex `model_toc.tex`
  
```bash
% python -m processVodml
% cd ../doc
xsltproc -o model.tex  ivoatex/vo-dml2ivoatex.xslt ../vo-dml/desc.mango.vo-dml.xml
% make forcetex
```
