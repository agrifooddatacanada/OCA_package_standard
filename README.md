# Proposal for OCA specification governance
Overlays Capture Architecture is a standardized language for describing data schemas.
Overlays Capture Architecture is optimized for overlays, where the community can improve the functionalities of a schema to meet their needs while maintaining interoperability.
OCA_bundles MAY be collected together with an OCA package and they can also exist independently.
Figure: example OCA Package structure
 
There are multiple levels of overlays that can be incorporated into OCA syntax, Community, Recognized and Core.
## OCA Core overlays
The overlays are contained in the oca_bundle object. There should be widest support for core overlays, they do not change frequently as they may introduce breaking changes, and any software which claims to support OCA must support all core overlays plus capture_base.
Core overlays are governed by HCF, incorporated into OCA Repo implementation and include the OCA File documentation and support.
OCA core overlays are the only overlays that can appear within the oca_bundle (in addition to capture_base). The SAID of the oca_bundle when calculated only includes capture_base and OCA core overlays. Dependencies also only include capture_base and OCA core overlays of respective oca_bundles.
Overlays within the core are no longer individually versioned. They version together with each bundle specification release.
## Extension overlays
Extension overlays include Recognized overlays and Community overlays.
### Recognized Overlays
Recognized overlays are governed by HCF which hosts the official source of overlay syntax and documentation. 
### Community Overlays
Community overlays are governed by their communities and outside of the governance of the oca-specification. However, when present in an oca package community overlays will have specific requirements. Community overlays should follow the OCA Overlay Design and Documentation Standard as best practice.
## Promotion of Overlays
Promotion from Community to Recognized: Community overlays are first developed in the community and supported by specific use cases. Then, when popular enough, community overlays may be proposed to the OCA standard as Recognized Overlays. Recognized overlays are accepted from the community when they follow the OCA Overlay Design and Documentation Standard.
Promotion from Recognized to Core: HCF maintains the official tool repository for working with OCA. They also maintain the official implementation of working with OCA Core (OCA Repo). To become a Core overlay, the Recognized overlay must be supported by the official HCF OCA Repo and follow the OCA Overlay Documentation Standard.
## OCA Standard Documentation
The HCF MUST maintain the official standard specification for oca_bundle, oca_package and OCA Overlay Design and Documentation Standard. OCA Core overlays and Recognized overlays MUST follow the OCA Overlay Design and Documentation Standard. Community overlays MAY follow the OCA Overlay Design and Documentation Standard.
## OCA Capture Base 
TODO Description of syntax of capture base.
## OCA Core Overlays
TODO Description of syntax of Core overlays following the OCA Overlay Design and Documentation Standard.
## OCA Recognized Overlays
TODO Description of syntax of Recognized overlays following OCA Overlay Design and Documentation Standard.

## OCA Overlay Design and Documentation Standard
The documentation standard outlines the different sections of documentation for each overlay. Core and Required overlays MUST follow this documentation standard, Community overlays SHOULD use this documentation standard. Test cases for each overlay MAY be documented in a separate section collecting all test cases together. OCA File Syntax MAY be documented in a separate section collecting all OCA File syntax together.
1.	Description (MUST: Core and Recognized): 
a.	Summarize the functionality of the overlay, what needs the overlay is addressing and descriptions of components of the overlay. Any references to community standards belong in this section.
2.	OCA File description (MUST: Core, MAY (MUST?): Recognized): 
a.	If there is an implementation of OCA File syntax used to generate the overlay include a description of the syntax here.
b.	Add meta-grammar rules about OCA File here (if OCA File is present MUST: Core and Recognized).
3.	Example (MUST: Core and Recognized): 
a.	Provide at least one example of the overlay in fully canonicalized, serialized (in JSON) format including a correctly calculated SAID value. 
b.	The capture_base SAID does not need to reference a specific capture_base but MUST be well formed. 
c.	The capture_base example SAID is used in the calculations of the overlay SAID. 
d.	The example MAY be formatted with line breaks and indentations for readability.
e.	Core overlays MUST use Type= “core/overlay/name/” where name is the name of the overlay.
f.	Recognized overlays MUST use Type= “recognized/overlay/name/vX.X where name is the name of the overlay and versioning MUST follow semantic versioning recommendations.
g.	Community overlays MAY use Type= “community/overlay/name/v1.0” where name is the name of the overlay and versioning MAY follow Semantic Versioning recommendations.
4.	OCA File source example (MUST: Core, MAY (MUST?): Recognized): 
a.	For at least one overlay example given provide the complete OCA File syntax.
5.	Canonicalization rules (MUST: Core and Recognized): 
a.	Canonicalization rules MUST be documented for all objects.
b.	All sections of the overlay must be explicitly specified if they are insertion ordered or lexigraphical ordered. Lexicographical sorting is based on the character Unicode values, starting with the first character and proceeding through the string in ascending order.
c.	Overlays must have (in this order) at the beginning: SAID (d), type, language if present, then capture base. This order is insertion ordered.
i.	If multiple languages are present within an overlay object, each language overlay MUST be ordered lexigraphically.
d.	Then properties that would apply to the entire overlay (or data). This order MAY be lexigraphical ordered.
e.	If an attributes array is present it follows lexigraphical ordering.
6.	Rules summary (MUST: Core and Recognized): 
a.	Summarize all the requirements (MUST and MAY) for the overlay.
7.	Test case: (MUST: Core and Recognized): 
a.	Provide at least one fully worked example that (MUST: Core, MAY (MUST?): Recognized) include OCA File. 
b.	The worked example MUST be a fully canonicalized, JSON serialized schema bundle with SAIDs calculated. 
c.	The fully worked example MUST include a capture_base and any other overlays that the documented overlay depends on. 
d.	The example MUST exclude any transformations made for readability that would interfere with the reproducible calculation of the SAID.
Note: SAID calculations will reference official version 0.9 release of ACDC, but also include a non-normative and helpful description of how SAIDs are calculated as well as reference libraries that will calculate SAIDs.

## OCA Bundle 
TODO Description of syntax of OCA Bundle

## OCA Package
TODO Description of syntax of OCA Package






