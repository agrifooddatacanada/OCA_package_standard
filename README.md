# Proposal for OCA specification governance
Overlays Capture Architecture is a standardized language for describing data schemas.

Overlays Capture Architecture is optimized for overlays, where the community can improve the functionalities of a schema to meet their needs while maintaining interoperability.

OCA_bundles MAY be collected together with an OCA package and they can also exist independently.

![OCA package](https://github.com/carlyh-micb/OCA_package/blob/main/package.png)

Figure: example OCA Package structure
 
There are multiple levels of overlays that can be incorporated into OCA syntax, Community, Recognized and Core.

# OCA Core overlays
The overlays are contained in the oca_bundle object. There should be widest support for core overlays, they do not change frequently as they may introduce breaking changes, and any software which claims to support OCA MUST support all core overlays plus capture_base.
Core overlays are governed by HCF, incorporated into OCA Repo implementation and include the OCA File documentation and support.
OCA core overlays are the only overlays that can appear within the oca_bundle (in addition to capture_base). The SAID of the oca_bundle when calculated only includes capture_base and OCA core overlays. Dependencies also only include capture_base and OCA core overlays of respective oca_bundles.
Overlays within the core are no longer individually versioned. They version together with each bundle specification release.

# Extension overlays
Extension overlays include Recognized overlays and Community overlays.

## Recognized Overlays
Recognized overlays are governed by HCF which hosts the official source of overlay syntax and documentation. 

## Community Overlays
Community overlays are governed by their communities and outside of the governance of the oca-specification. However, when present in an oca package community overlays will have specific requirements. Community overlays should follow the OCA Overlay Design and Documentation Standard as best practice.

Note that Community overlays can be a community of one individual which could be implemented in a single project and addressing a single need.

# Promotion of Overlays
## Promotion from Community to Recognized: 
Community overlays are first developed in the community and supported by specific use cases. Then, when popular enough, community overlays may be proposed to the OCA standard as Recognized Overlays. Recognized overlays are accepted from the community when they follow the OCA Overlay Design and Documentation Standard.

Community overlays are proposed to the DSWG for a change in status. The DSWG seeks input from the Technology Council on the suitability of the overlay. Approval to Recognized overlay is the resonsibility of the DSWG. The DSWG is responsible for the timely addition of the new Recognized overlay specification to the official standard with input from the Technology Council. 

## Promotion from Recognized to Core: 
HCF maintains the official tool repository for working with OCA. They also maintain the official implementation of working with OCA Core (OCA Repo). To become a Core overlay, the Recognized overlay must be supported by the official HCF OCA Repo and follow the OCA Overlay Documentation Standard.

Community overlays are proposed to the DSWG for a change in status. The DSWG together with the Technology Council approves the acceptance of the overlay as a Core overlay. The DSWG is responsible for the timely addition of the new Core overlay specification to the official standard with required approval from the Technology Council. 

# OCA Standard Documentation
The HCF MUST maintain the official standard specification for oca_bundle, oca_package and OCA Overlay Design and Documentation Standard. OCA Core overlays and Recognized overlays MUST follow the OCA Overlay Design and Documentation Standard. Community overlays MAY follow the OCA Overlay Design and Documentation Standard.

# OCA Capture Base 
TODO Description of syntax of capture base.

# OCA Core Overlays
TODO Description of syntax of Core overlays following the OCA Overlay Design and Documentation Standard.

# OCA Recognized Overlays
TODO Description of syntax of Recognized overlays following OCA Overlay Design and Documentation Standard.

Note: SAID calculations will reference official version 0.9 release of ACDC, but also include a non-normative and helpful description of how SAIDs are calculated as well as reference libraries that will calculate SAIDs.

# OCA Overlay Design and Documentation Standard
The documentation standard outlines the different sections of documentation for each overlay. Core and Required overlays MUST follow this documentation standard, Community overlays SHOULD use this documentation standard. Test cases for each overlay MAY be documented in a separate section collecting all test cases together. OCA File Syntax MAY be documented in a separate section collecting all OCA File syntax together.

1.	Description (MUST: Core and Recognized):
 - Summarize the functionality of the overlay, what needs the overlay is addressing and descriptions of components of the overlay. Any references to community standards belong in this section.
3.	OCA File description (MUST: Core, MAY: Recognized): 
 - If there is an implementation of OCA File syntax used to generate the overlay include a description of the syntax here.
 - Add meta-grammar rules about OCA File here (if OCA File is present MUST: Core and Recognized).
4.	Example (MUST: Core and Recognized): 
 - Provide at least one example of the overlay in fully canonicalized, serialized (in JSON) format including a correctly calculated SAID value. 
 - The capture_base SAID does not need to reference a specific capture_base but MUST be well formed. 
 - The capture_base example SAID is used in the calculations of the overlay SAID. 
 - The example MAY be formatted with line breaks and indentations for readability.
 - Core overlays MUST use Type= “core/overlay/name/” where name is the name of the overlay.
 - Recognized overlays MUST use Type= “recognized/overlay/name/vX.X where name is the name of the overlay and versioning MUST follow semantic versioning recommendations.
 - Community overlays MUST use Type= “community/overlay/name/vX.X” where name is the name of the overlay and versioning MUST follow Semantic Versioning recommendations when part of the OCA Package.
5.	OCA File source example (MUST: Core, MAY: Recognized): 
 - For at least one overlay example given provide the complete OCA File syntax.
6.	Canonicalization rules (MUST: Core and Recognized): (TODO: adapt this content)
 - Canonicalization rules MUST be documented for all objects.
 - All sections of the overlay must be explicitly specified if they are insertion ordered or lexigraphical ordered. Lexicographical sorting is based on the character Unicode values in ascending order, starting with the first character and proceeding through the string.
 - Overlays MUST have at the beginning: SAID (d), type, optional language, then capture base. This order is insertion ordered. `"d"="", "type"="", "language"="" (optional), "capture_base"=""`
 - If multiple languages are present within an overlay object, each language overlay MUST be ordered lexigraphically.
 - After the  properties that would apply to the entire overlay (or data). This order MUST be lexigraphical ordered.
 - If an attributes object is present it MUST follow lexigraphical ordering.
7.	Rules summary (MUST: Core and Recognized): 
 - Summarize all the requirements (MUST and MAY) for the overlay.
8.	Test case: (MUST: Core and Recognized): 
 - Provide at least one fully worked example that (MUST: Core, MAY (MUST?): Recognized) include OCA File. 
 - The worked example MUST be a fully canonicalized, JSON serialized schema bundle with SAIDs calculated. 
 - The fully worked example MUST include a capture_base and any other overlays that the documented overlay depends on. 
 - The example MUST exclude any transformations made for readability that would interfere with the reproducible calculation of the SAID.

# OCA Bundle 
TODO Description of syntax of OCA Bundle

# OCA Package
TODO Description of syntax of OCA Package






