---
title: "Requirements for WIMSE Token Translation"
category: info

docname: draft-rosomakho-wimse-tokentranslation-requirements-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Applications and Real-Time"
workgroup: "Workload Identity in Multi System Environments"
keyword:
 - Token Translation
 - Requirements
venue:
  group: "Workload Identity in Multi System Environments"
  type: "Working Group"
  mail: "wimse@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/wimse/"
  github: "yaroslavros/wimse-tokentranslation-requirements"

author:
 -  ins: "Y. Rosomakho"
    fullname: Yaroslav Rosomakho
    organization: Zscaler
    email: yrosomakho@zscaler.com,
 -  ins: "D. Saxe"
    fullname: Dean H. Saxe
    organization: Amazon Web Services
    email: deansaxe@amazon.com
 -  ins: "D. Izumskiy"
    fullname: Dmitry Izumskiy
    organization: Intuit
    email: idimaster@gmail.com

normative:

informative:


--- abstract

This document outlines the requirements for workload token translation within the context of the Workload Identity in Multi System Environments (WIMSE). Token translation may be required for interoperability between workloads or for complying with security requirements of multi-system environments. This requirement document considers various aspects of token translation, such as changes in token format, content encoding, cryptographic properties, and context embedding. Additionally, this document raises security considerations to be addressed by specific token translation implementations, including replay attacks, access control, and privacy concerns.


--- middle

# Introduction

Inter-workload communications rely on tokens for identification, authentication and authorization. These tokens are available in various formats including Oauth 2.0 bearer tokens, X.509 certificates, SPIFFE JWT-SVID and many others. Some of these token formats have encoding variants, offer flexible cryptographic options to address confidentiality and integrity requirements and may embed additional contextual information in various formats. This document outlines the requirements for token translations that can apply within a given token format or across token formats and defines security considerations to be addressed by specific implementations of token translation.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Token Translation Requirements

Token translation involves transforming a token from one format or set of characteristics to another. The following requirements must be considered for effective token translation:

## Token Format Change

The translation service must support converting tokens from one format to another (e.g., from Oauth 2.0 Bearer Token to X.509 client certificate).

## Token Encoding Change

Some token formats support multiple encodings of subject and context. Token translation process must support changes to these encodings were relevant.

## Changes to Cryptographic Properties of the Token

Some token format support various cryptographic algorithms for digital signatures, hashing and encryption. Specific cryptographic requirements can be defined by capabilities of communicating workloads and identity proxies, inherent security of communication channels and relevant regulatory compliance. Token translation process must facilitate changes in the relevant cryptographic algorithms.

## Embedding One Token in Another

Certain token formats have flexibility to embed another token in the same or different format. The translation service must enable such embedding to facilitate nested authentication or delegation.

## Change of Embedded Context in Token

The translation service must support modifications to the embedded context within a token including attestation and assertions.

## Change of Validity Constraint of the Token

The translation service must allow changes to the validity constraints of a token, such as the expiration time, scope or audience.

## Changing or Adding Subjects of the Token

The translation service must support altering or adding subjects within the token to reflect different entities or roles.

## Adding Sender Constraint to the Token

The translation service must enable the addition of sender constraints to restrict who can use or forward the token.

# Token Translation Mechanisms

Token translation can be performed by either the workload itself or an identity proxy. Multiple aspects of translation processes can occur simultaneously or be chained together to meet the needs of complex scenarios.

# Security Considerations

The following considerations must be addressed by the token translation process.

## Replay attacks

Token translation process must address concern of replay attacks to ensure that unauthorised parties cannot steal and reuse workload tokens.

## Access control

Token translation process must have relevant authentication and authorization mechanisms to ensure required level of access control.

## Privilege Escalation

Token translation process must provide required validation and comply to least privilege principles to prevent unauthorized privilege escalation through token translation.

## Prevention of Abuse of Token Translation Service

Token translation process must consider protection of token translation service against denial of service and other abusing attacks.

## Auditability

Token translation process must support detailed logging options of all token translation activities to support auditing and forensic analysis.

## Privacy Considerations

Token translation process performed for cross-domain use cases needs to consider generalization of identity to limit exposure of internal topology of a given domain. In addition to that, token translation process must consider confidentiality of sensitive information such as identity subject and context included in the token.

# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
