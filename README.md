# OCA Package version 1.0 DRAFT

Overlays Capture Architecture is a standardized language for describing data schemas.

Overlays Capture Architecture is optimized for overlays, where the community can improve the functionalities of a schema to meet their needs while maintaining interoperability.

## Components of an OCA Package

OCA Package formalizes a way to develop, publish and use overlays that are outside of the OCA specification. 

The OCA specification describes oca_bundle which collects a capture base and associated overlays into a single object. OCA Package describes how additional overlays outside of the official specification can be added to an OCA Schema without altering the oca_bundle object.

![OCA package](https://github.com/carlyh-micb/OCA_package/blob/main/package.png)

Figure: example oca_package structure

### OCA Bundle
The overlays and capture base of the [OCA Specification](http://oca.colossi.network/specification/) are contained in the oca_bundle object of an oca_package. The contents of oca_bundle are governed by the Human Colossus Foundation and documented into the official [OCA Specification](http://oca.colossi.network/specification/).

The SAID of the oca_bundle when calculated only includes capture_base and OCA overlays documented by the official specification. Additional oca_bundles which are dependencies are collected in the object Dependencies. Dependencies only include official specification oca_bundles.

### Extension overlays
Extension within oca_package contains overlays developed by various communities. These overlays are outside of the governance of the Human Colossus Foundation and can be created by members of the community to meet their needs.
Community overlays are governed by their respective communities. A community can consist of one individual implementing a single project addressing a single need. A community can also be a large consortium of partners with their own governance structure for determining composition, versioning and acceptance of their community overlays. When present in an oca_package community overlays MUST follow the OCA Package Design Requirements.  

## Governance of OCA Package

The oca_package is under the governance of the OCA Package governance body.

The OCA Package governance body MUST maintain the official standard specification for oca_package and the OCA Package Design Requirements. OCA Community overlays MUST follow the OCA Package Design Requirements.

### Promotion of overlays to official OCA Specification: 
HCF maintains the official implementation the OCA specification. To become become part of the official OCA specification any overlay must go through the [official RFC process](https://github.com/the-human-colossus-foundation/oca-spec/blob/master/README.md).

## Technical Implementation of an OCA Package
Technical implementation of the OCA package is outside of the scope of the OCA Package governance body. Communities are expected to develop their own implementations.

# OCA Package Design Requirements
1. Community overlays MUST follow OCA Package Syntax Requirements
2. Documentation for Community overlays MUST be published publically and follow the OCA Package Overlay Documentation Requirements. 
4. SAID calculations of the oca_package contents (excluding oca_bundle) follow requirements documented in [CESR Specification](https://weboftrust.github.io/ietf-cesr/draft-ssmith-cesr.html). This non-normative post [documents the process and design choices of the calculations of SAIDs](https://kentbull.com/2024/09/22/keri-series-understanding-self-addressing-identifiers-said/) and includes links to libraries implementing the SAID calculation which can be used by overlay developers. The author Kent Bull is officially contributing documentation to the ongoing work of the [latest CESR specification](https://trustoverip.github.io/tswg-cesr-specification/).
5. Lexicographical sorting follows the requirements documented in section [3.2.3 Sorting of Object Properties](https://www.rfc-editor.org/rfc/rfc8785#section-3.2.3)

## OCA Package Syntax Requirements
- oca_package MUST include the following objects in this specific order (canonicalization):
	- `d` where the package MUST use "d= _SAID value of entire oca_package_"
	- `type` where the the package MUST use type="oca_package/1.0".
	- `oca_bundle` which MUST contain two objects:
 		- `bundle` which MUST contain overlays and capture_base as specified by the [OCA specification v1.0.1](http://oca.colossi.network/specification/) and be canonicalized and serialized according to that specification.
		- `dependencies` which MAY contain additional oca_bundles that are referenced by the OCA_package `oca_bundle` and meet the same `oca_bundle` requirements.
	- `extensions` which MAY contain Community overlays which are ordered lexicographically according to: [3.2.3 Sorting of Object Properties](https://www.rfc-editor.org/rfc/rfc8785#section-3.2.3)
- Extension overlay contents MUST follow [3.2.3 Sorting of Object Properties](https://www.rfc-editor.org/rfc/rfc8785#section-3.2.3)
- Community overlays MUST use type= "community/community_name/overlay/name/vX.X" where name is the name of the overlay, community_name is the name of the community and versioning MUST follow semantic versioning.

## OCA Package Overlay Documentation Requirements
This section outlines the different sections of published documentation for each overlay. Each header must be present in a publically documented overlay description.

**Title**: _overlay name_ by _community name_: version: _version_

**Authors**: _overlay author names_

**Date released**: _date of version release_

This overlay follows official OCA Package requirements documented at _(link to OCA Package source)_

**Description**:
 - Describe the functionality of the overlay, what needs the overlay is addressing and complete descriptions of components of the overlay. Any references to community standards belong in this section.

**Example**: 
 - Provide at least one example of the overlay which has been fully canonicalized and serialized (in JSON) for calculating the correct overlay SAID value. 
 - The capture_base SAID does not need to reference a specific capture_base but MUST be well formed. 
 - The capture_base example SAID is used in the calculations of the overlay SAID. 
 - The example MAY be formatted with line breaks and indentations, including reorganizing objects for readability after the SAID has been calculated.

**Rules summary**: 
 - Summarize all the requirements (MUST and MAY) for the overlay.

**Test case**: 
 - At least one fully worked example MUST be provided.
 - The worked example MUST be a fully canonicalized, JSON serialized oca_package with SAIDs calculated. 
 - The fully worked example MUST include at least a minimal set of capture_base and any other overlays that the documented overlay depends on. 
 - The example MUST exclude any transformations made for readability that would interfere with the reproducible calculation of the SAID.

## Normative references
- [OCA specification v1.0.1](http://oca.colossi.network/specification/) 
- [3.2.3 Sorting of Object Properties](https://www.rfc-editor.org/rfc/rfc8785#section-3.2.3)
- [CESR Specification](https://weboftrust.github.io/ietf-cesr/draft-ssmith-cesr.html) for SAID calculations
