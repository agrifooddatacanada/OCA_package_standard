# OCA Package version 1.0

Overlays Capture Architecture is a standardized language for describing data schemas.

Overlays Capture Architecture is optimized for overlays, where the community can improve the functionalities of a schema to meet their needs while maintaining interoperability.

## Components of an OCA Package

The OCA specification describes OCA_bundles which collect a capture base and associated overlays into a single object. OCA Package describes how additional overlays outside of the official specification can be added to an OCA Schema without altering the OCA_bundle object. OCA_bundles MAY be collected together within an OCA package and they can also exist independently.

OCA Package exists as a JSON serialized version of [OCA specification v1.0.1](http://oca.colossi.network/specification/). It formalizes a way to develop, test, and publish overlays that are outside of the Core of the OCA specification and included in an OCA Package in Extensions.

![OCA package](https://github.com/carlyh-micb/OCA_package/blob/main/package.png)

Figure: example OCA Package structure

### OCA_bundle
The overlays and capture base of OCA Core are contained in the oca_bundle object of an OCA Package. These overlays are governed by the Human Colossus Foundation and documented into the official [OCA Specification](http://oca.colossi.network/specification/).

The SAID of the oca_bundle when calculated only includes capture_base and OCA core overlays. Dependencies also only include capture_base and OCA core overlays of respective oca_bundles.

### Extension overlays
Extension contains overlays and include Recognized overlays and Community overlays. These overlays are outside of the governance of the Human Colossus Foundation and can be created by members of the community to meet their needs.

#### Recognized Overlays
Recognized overlays are governed by the OCA Package governance body which hosts the official source of overlay syntax and documentation.

#### Community Overlays
Community overlays are governed by their respective communities. When present in an oca package community overlays MUST follow the OCA Package Design Requirements as best practice.

Note that Community overlays can be a community of one individual which could be implemented in a single project and addressing a single need.

## Governance of OCA Package

The OCA Package is under the governance of the OCA Package governance body.

The OCA Package governance body MUST maintain the official standard specification for oca_package and the OCA Package Design Requirements. OCA Recognized overlays MUST follow the OCA Package Design Requirements. Community overlays MUST follow the OCA Package Design Requirements when they are part of an OCA Package.

### Promotion of Overlays
#### Promotion from Community to Recognized overlays: 
Community overlays are first developed in the community and supported by specific use cases. Then, when popular enough, community overlays may be proposed to the OCA Package governance body as Recognized Overlays. Recognized overlays are accepted from the community when they follow the OCA Package Design Requirements.

Community overlays are proposed to the OCA Package governance body for a change in status. Approval to Recognized overlay is the resonsibility of the OCA Package governance body. The OCA Package governance body is responsible for the timely addition of the new Recognized overlay specification to the official OCA Package standard. 

#### Promotion of overlays to Core: 
HCF maintains the official implementation of working with OCA Core (OCA Repo). To become become part of the official OCA specification any overlay must go through the [official RFC process](https://github.com/the-human-colossus-foundation/oca-spec/blob/master/README.md).

# OCA Package Design Requirements
This section outlines the different sections of published documentation for each overlay. 

1. Required and Community overlays MUST follow OCA Package Overlay Documentation Requirements when they are included in an OCA Package.
2. Documentation for Required and Community overlays MUST be published publically. 
3. Technical implementation of the Recognized and Community overlays is the responsibilities of the respective communities.
4. SAID calculations of the OCA Package follow requirements documented in [OCA Specification](http://oca.colossi.network/specification/), which in term references an expired version of the [SAID specification](https://datatracker.ietf.org/doc/html/draft-ssmith-said). Until this documentation is updated, OCA Package SAID calculations will follow this article which fully [documents the process and design choices of the calculations of SAIDs](https://kentbull.com/2024/09/22/keri-series-understanding-self-addressing-identifiers-said/) and includes links to libraries implementing the SAID calculation which can be used by overlay developers. The author Kent Bull is officially contributing documentation to the [CESR specification](https://trustoverip.github.io/tswg-cesr-specification/) which is the origin of the SAID specification.
5. Lexicographical sorting follows the requirements documented in section [3.2.3 Sorting of Object Properties](https://www.rfc-editor.org/rfc/rfc8785#section-3.2.3)

## OCA Package Syntax Requirements
- OCA Package MUST include the following objects in this specific order:
	- object information `d` and `type` in this order. `d` contains the SAID value of the fully canonicalized, JSON serialized OCA_package. The package MUST use Type="oca_package/1.0".
	- `oca_bundle` which contains overlays and capture_base as specified by the [OCA specification v1.0.1](http://oca.colossi.network/specification/).
	- `Dependencies` which MAY contain additional oca_bundles that are referenced by `oca_bundle` and meet `oca_bundle` requirements.
	- `Extensions` which contain Recognized and Community overlays which are ordered lexicographically according to the `d` attribute.
- Recognized overlays MUST use Type= "recognized/overlay/name/vX.X" where name is the name of the overlay and versioning MUST follow semantic versioning recommendations.
- Community overlays MUST use Type= "community/overlay/name/vX.X" where name is the name of the overlay and versioning MUST follow Semantic Versioning recommendations when part of the OCA Package.


## OCA Package Overlay Documentation Requirements
1.	Description:
 - Summarize the functionality of the overlay, what needs the overlay is addressing and descriptions of components of the overlay. Any references to community standards belong in this section.
2.	Example: 
 - Provide at least one example of the overlay in fully canonicalized, serialized (in JSON) format including a correctly calculated SAID value. 
 - The capture_base SAID does not need to reference a specific capture_base but MUST be well formed. 
 - The capture_base example SAID is used in the calculations of the overlay SAID. 
 - The example MAY be formatted with line breaks and indentations for readability.
3.	Canonicalization rules:
 - Canonicalization rules MUST be documented for all parts of the overlay indicating when insertion ordered or lexigraphical ordered. 
 - Overlays MUST have at a header at the beginning which contains: SAID (d), type, optional language, then capture base. This order is insertion ordered. `"d"="", "type"="", "language"="" (optional), "capture_base"=""`
 - If multiple languages are present within an overlay object, each language overlay MUST be ordered lexigraphically according to the language value.
 - Following the header content MUST be ordered lexigraphically. 
4.	Rules summary: 
 - Summarize all the requirements (MUST and MAY) for the overlay.
5.	Test case: 
 - At least one fully worked example MUST be provided.
 - The worked example MUST be a fully canonicalized, JSON serialized OCA Package with SAIDs calculated. 
 - The fully worked example MUST include a minimal set of capture_base and any other overlays that the documented overlay depends on. 
 - The example MUST exclude any transformations made for readability that would interfere with the reproducible calculation of the SAID.



