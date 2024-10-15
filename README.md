# OCA Package

Overlays Capture Architecture is a standardized language for describing data schemas.

Overlays Capture Architecture is optimized for overlays, where the community can improve the functionalities of a schema to meet their needs while maintaining interoperability.

The OCA specification describes OCA_bundles which collect a capture base and associated overlays into a single object. OCA Package describes how additional overlays outside of the official specification can be added to an OCA Schema without altering the OCA_bundle object. OCA_bundles MAY be collected together within an OCA package and they can also exist independently.

OCA Package exists as a JSON serialized version of [OCA specification v1.0.1](http://oca.colossi.network/specification/). It formalizes a way to develop, test, and publish overlays that are outside of the Core of the OCA specification.

![OCA package](https://github.com/carlyh-micb/OCA_package/blob/main/package.png)

Figure: example OCA Package structure
 

# OCA Core overlays
The overlays are contained in the oca_bundle object of an OCA Package. These overlays are governed by the Human Colossus Foundation and documented into the official [OCA Specification](http://oca.colossi.network/specification/).
Core overlays are governed by HCF and outside of the governance of OCA Package.

OCA core overlays are the only overlays that can appear within the oca_bundle (in addition to capture_base). The SAID of the oca_bundle when calculated only includes capture_base and OCA core overlays. Dependencies also only include capture_base and OCA core overlays of respective oca_bundles.

# Extension overlays
Extension overlays include Recognized overlays and Community overlays. These overlays are outside of the governance of the Human Colossus Foundation and can be created by members of the community to meet their needs.

## Recognized Overlays
Recognized overlays are governed by the OCA Package governance body which hosts the official source of overlay syntax and documentation.

## Community Overlays
Community overlays are governed by their respective communities. When present in an oca package community overlays MUST follow the OCA Overlay Design and Documentation Standard as best practice.

Note that Community overlays can be a community of one individual which could be implemented in a single project and addressing a single need.

# Promotion of Overlays
## Promotion from Community to Recognized: 
Community overlays are first developed in the community and supported by specific use cases. Then, when popular enough, community overlays may be proposed to the OCA Package governance body as Recognized Overlays. Recognized overlays are accepted from the community when they follow the OCA Overlay Design and Documentation Standard.

Community overlays are proposed to the OCA Package governance body for a change in status. Approval to Recognized overlay is the resonsibility of the OCA Package governance body. The OCA Package governance body is responsible for the timely addition of the new Recognized overlay specification to the official standard. 

## Promotion from Recognized to Core: 
HCF maintains the official implementation of working with OCA Core (OCA Repo). To become a Core overlay, any overlay must go through the [official RFC process](https://github.com/the-human-colossus-foundation/oca-spec/blob/master/README.md).


# OCA Standard Documentation
The OCA Package governance body MUST maintain the official standard specification for oca_package and the OCA Overlay Design and Documentation Standard. OCA Recognized overlays MUST follow the OCA Overlay Design and Documentation Standard. Community overlays MAY follow the OCA Overlay Design and Documentation Standard.

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






