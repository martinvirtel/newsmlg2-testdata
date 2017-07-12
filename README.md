# newsml g2 test data

This repository contains some test data so that you can familiarize yourself with
what to expect when you get news from dpa.

The authoritative copy of this repository lives at https://github.com/dpa-newslab/newsmlg2-testdata


## How to start

1. Read [IPTC.org's Quick Start PDF](https://www.iptc.org/std/NewsML-G2/latest/QuickStart-NewsML-G2-ItemBasics). 

2. Search for clues to fill in the blanks. For any instance of a hard-to-understand XML metadata attribute, there is 

 - either a NewsML G2 definition available in the [NewsML G2 catalog](https://www.iptc.org/std/catalog/). 

 - or a definition in dpa's controlled vocabularies, included in this repository under `controlled-vocabularies`.


The definitions are sometimes hard to find. But it is possible. Example:

```xml
 <subject qcode="medtop:20000538" rank="1" type="dpatype:dpasubject">
               <name xml:lang="de">Freizeit</name>
               <sameAs qcode="dpasubject:553">
                  <name xml:lang="de">Freizeit</name>
               </sameAs>
               <broader qcode="subj:10010000">
                  <name xml:lang="de">Freizeit</name>
               </broader>
               <broader qcode="medtop:10000000">
                  <name xml:lang="de">Freizeit, Modernes Leben</name>
               </broader>
            </subject>
```

- `dpatype:dpasubject` - is defined in the controlled vocabulary file in this repository: `controlled-vocabularies/g2.dpa.com/cv/type.xml`
- `medtop:200000538` - Leisure - is defined in the IPTC Media Topics controlled vocabulary http://cv.iptc.org/newscodes/mediatopic/20000538
- `medtop:10000000` - Lifestyle and Leisure - is defined in the IPTC Media Topics controlled vocabulary: http://cv.iptc.org/newscodes/mediatopic/10000000
- `subj:10010000` - leisure (general) - is defined in the IPTC Subject Codes controlled vocabulary: http://cv.iptc.org/newscodes/subjectcode/10010000
- `dpasubject:553`  - Freizeit - is defined in the controlled vocabulary file in this repository: `controlled-vocabularies/g2.dpa.com/cv/subject.xml`.


The most important controlled vocabularies are:

  - `controlled-vocabularies/g2.dpa.com/cv/category.xml` - what the dpa newsroom calls "Ressort".
  - `controlled-vocabularies/g2.dpa.com/cv/country.xml` - countries
  - `controlled-vocabularies/g2.dpa.com/cv/geosubject.xml` - geographical names
  - `controlled-vocabularies/g2.dpa.com/cv/subject.xml` - the "first keyword" ("Erststichwort") that has to be chosen from this vocabulary


The `<narrower>` and `<broader>` characterizations in the XML sometimes defy common logic. For most purposes, we have found it best to ignore this information. 


## Links


[NewsML G2 page at IPTC.org](https://iptc.org/standards/newsml-g2/)


Jump into the documentation: [IPTC.org's Quick Start PDF](https://www.iptc.org/std/NewsML-G2/latest/QuickStart-NewsML-G2-ItemBasics)

Versions of the IPTC's controlled vocabulary [XML Catalog](https://www.iptc.org/std/catalog/).

## Files in this repo

| path | description|
| ----- | ----------|
| data/20170629-dpa-sample.tar.xz | 100 files from Basisdienst dated June 29th, 2017, 2.8 MB unpacked |
| controlled-vocabularies/g2.dpa.com/ | Controlled vocabularies defined by dpa, as of November 10th 2016 |
| experiments/jex-classifier-result.xml | Result of a classification of the documents in data/20170629-dpa-sample.tar.xz with the JRC EuroVoc Indexer JEX (see below) | 


## Experiment in classification with the JRC EuroVoc Indexer JEX

The EU's Joint Research Center in Ispra has published a pre-trained elassifier that classifies texts in 22 languages according to [Eurovoc](http://eurovoc.europa.eu), a multilingual thesaurus used by EU institutions. This classifier is called *JRC EuroVoc Indexer JEX*, it looks a bit dated but it is [free to download](https://ec.europa.eu/jrc/en/language-technologies/jrc-eurovoc-indexer), and you can download a paper discribing it [here](https://ec.europa.eu/jrc/sites/jrcsh/files/2012_LREC-JEX_Steinberger-et-al.pdf). 

The news articles present in `data/20170629-dpa-sample.tar.xz` have been classified using version 1.0 (dated May 2012) of the german version. The results are stored in `experiments/jex-classifier-result.xml`. The concept IDs can be looked up on the eurovoc website: [5462](http://eurovoc.europa.eu/drupal/?q=request&view=pt&termuri=http://eurovoc.europa.eu/219244&language=en) stands for "Animal Welfare", for example. 

Here's how to read `experiments/jex-classifier-result.xml`:

```xml
<document id="urn:newsml:dpa.com:20090101:170629-99-46001.xml">
    <category code="5563" weight="0.202473011089883 "/>
    <category code="5898" weight="0.15730123744644367 "/>
    <category code="5931" weight="0.09492841717389104 "/>
```


This means document `urn:newsml:dpa.com:20090101:170629-99-46001.xml` (title:
Slowenien erringt Erfolg im bitteren Grenzstreit mit Kroatien) has been classified with [5564](http://eurovoc.europa.eu/5563) - Croatia and [5898](http://eurovoc.europa.eu/5898) - Slovenia and [5931](http://eurovoc.europa.eu/5931) - former yugoslav republic (which is considered obsolete by now). The thesaurus has been updated several times since  2012, while the classifier remains at its 2012 version. 



