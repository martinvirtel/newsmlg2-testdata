# newsml g2 test data

This repository contains some test data so that you can familiarize yourself with
what to expect when you get news from dpa.


## How to start

For any piece of hard-to-understand XML, there is 

 - either a NewsML G2 definition available in the [NewsML G2 catalog](https://www.iptc.org/std/catalog/). 

 - or a definition in the dpa's controlled vocabularies in this repository.


They are sometimes hard to find. But it is possible. Example:

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

- `medtop:200000538` - Leisure - is defined in the IPTC Media Topics controlled vocabulary http://cv.iptc.org/newscodes/mediatopic/20000538
- `medtop:10000000` - Lifestyle and Leisure - is defined in the IPTC Media Topics controlled vocabulary: http://cv.iptc.org/newscodes/mediatopic/10000000

- `subj:10010000` - leisure (general) - is defined in the IPTC Subject Codes controlled vocabulary: http://cv.iptc.org/newscodes/subjectcode/10010000

- `dpasubject:553`  - Freizeit - is defined in the controlled vocabulary file in this repository: `controlled-vocabularies/g2.dpa.com/cv/subject.xml`.


## Links


[NewsML G2 page at IPTC.org](https://iptc.org/standards/newsml-g2/)


Jump into the documentation: [IPTC.org's Quick Start PDF](https://www.iptc.org/std/NewsML-G2/latest/QuickStart-NewsML-G2-ItemBasics)

The versions of the controlled vocabulary [XML Catalog](https://www.iptc.org/std/catalog/).

## Files

| path | description|
| ----- | ----------|
| data/20170629-dpa-sample.tar.xz | 100 files from Basisdienst dated June 29th, 2017, 2.8 MB unzpacked |
| controlled-vocabularies/g2.dpa.com/ | Controlled vocabularies defined by dpa, as of November 10th 2016 |




