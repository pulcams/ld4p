## The Project

During 2016-2018, Princeton was a partner in the Mellon-funded Linked Data for Production ([LD4P](https://wiki.duraspace.org/display/LD4P)) project, aimed at exploring workflows and extensions to BIBFRAME to cover specific domains.


Princeton worked with the [W3C Web Annotation model](https://www.w3.org/TR/annotation-model/) to encode dedications in books from Jacques Derrida’s personal library, acquired by the University in March, 2015. Out of the 19,000 volumes of Derrida’s library, 6,770 have personal dedications to him. Of these, a group of 450 items was ultimately selected to be the basis of our dataset. 


The goal was to go from static textual notes to structured data, identifying the people, places and events in the inscriptions and to provide identifiers and standard coding to enable researchers (eventually) to explore Derrida’s intellectual and social network in new and surprising ways. This project marks an important milestone -- and in many ways the most difficult one -- toward this goal: a preliminary linked dataset.  

## The Data
Available here is a preliminary 'dump' of encoded dedications in [turtle](https://en.wikipedia.org/wiki/Turtle_(syntax)) format, provided as a primary deliverable of our project. This dataset is at a respectable stopping point, but it is not "done and dusted". We anticipate that it will continue to evolve (see _Future plans / Exciting Possibilities_ below).    

## Data Modelling

### BIBFRAME
Bibliographic records were pulled from our local catalog (Voyager), and, if not found there, from OCLC. OCLC accession numbers were used to harvest work IDs ([OWIs](https://www.oclc.org/developer/develop/linked-data/worldcat-entities/worldcat-work-entity.en.html)). The records were then converted into BIBFRAME 2.0 using the [MARC to BIBFRAME2 converter](https://github.com/lcnetdev/marc2bibframe2) from Library of Congress. 

### W3C Web Annotation
The Web Annotation data model was used to create links between connected resources: the dedication inscribed in a book (`body`), and the page on which the dedication is written (`target`), which, in turn, is part of a particular item (`scope`). The model allowed us describe the nature of that relationship (`purpose`) and why annotations were created (`motivation`). It also permitted us to isolate, identify, and describe specific segment of interest of the dedications (`TextQuoteSelector`), which we used to tag names and places and create semantic equivalences (`sameAs`). The tagging was done using a makeshift [annotation editor](https://github.com/pulcams/annotation_editor). 

### Data Model Limitations and Local Extensions

This model is typically used to represent born-digital, user-generated annotations, and does not address the semantics of manuscript annotations, nor the relation between original and transcribed annotations. We created local extensions to the data model and borrowed from other ontologies to address some of these issues. 

Local properties:

* `ex:inscribing`
  * Label: Inscribing
  * URI: `<http://example.org/inscribing>`
  * Description: motivation for writing words, texts, lettering, or symbols on a resource


Besides BIBFRAME and the Web Annotation model, we used properties from: 
* [ARM](https://github.com/LD4P/arm)
* [DCMI Metadata Terms](http://dublincore.org/documents/dcmi-terms/)
* [OWL](https://www.w3.org/OWL/)
* [RDA Registry](http://www.rdaregistry.info/Elements/) (item and unconstrained properties)
* [RDF](https://www.w3.org/RDF/)
* [schema.org](https://schema.org/)

### Overview of the Data
Every dedication will have at least one annotation, a “meta-annotation” defining Princeton as the creator of the metadata, motivated by describing annotations. Every other annotation is motivated by `oa:tagging` and will describe entities named in the dedications: personal and corporate names, places, works, and conferences.

Dedicators, dedicatees and other personal names were reconciled against VIAF, as were corporate and conference names. Works mentioned in the dedications were reconciled against OCLC work IDs wherever possible. Place names were reconciled against Geonames. All entities are characterized by a `schema.org` class.

Each body is defined as an inscription that has the content of the dedication as its value.

## Future plans / Exciting Possibilities
* Add encoding for: images, color content, concepts, events or dates (besides date of creation of dedication), formatting of dedication (line breaks, indents, etc.), or multiple languages
* Identifying confidence level of transcription or relationships
* Define the type of insertion (postcard, letter, etc.)
* Establish relationships between separate dedications in the same item
* Create interactive visualizations and/or network graphs
* Establish user-friendly interface(s) for data
* Expand project to all 6,770 books with inscriptions (those given to Derrida)
* Allow non-rectangular annotations around regions of images (based on `oa:exact` data or fragment selectors)
* Upload dedicators signatures to Wikidata, and link to them
* Invite scholars to participate by contributing their own annotations for illegible text, etc. (enable crowdsourcing)
* Collaborate with Princeton's own Center for Digital Humanities on their related [Derrida's Margins](https://derridas-margins.princeton.edu/) project.

### Princeton's LD4P Core Group
* Joyce Bell
* Jennifer Baxmeyer
* Lidia Santarelli (from Feb. 2017)
* Luiza Wainer (from Jan. 2018)
* Peter Green
* Regine Heberlein
* Tim Thompson (until Mar. 2017)

### More details
* [LD4P wiki](http://ld4p.org/)
  * [Project proposal](https://wiki.duraspace.org/display/LD4P/Princeton+Project+Proposal)
  * [Project page](https://wiki.duraspace.org/display/LD4P/Princeton+-+Derrida%27s+library)
  * [Presentations](https://wiki.duraspace.org/display/LD4P/LD4P+Presentations+and+Publications)
* [Local project page](https://library.princeton.edu/cams/ld4p)
* [In-house annotation editor](https://github.com/pulcams/annotation_editor)
