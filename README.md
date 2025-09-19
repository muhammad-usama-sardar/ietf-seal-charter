# Background and Motivation

In many scenarios, particularly with the rise of Trusted Execution
Environments (TEEs) and the increasing security demands for IoT devices
and confidential workloads, there is a requirement for some use cases that
utilize protocols such as (D)TLS to also ensure that the peer's state is
validated in addition to conventional authentication (verification of identity).

Remote attestation ([RFC9334](https://datatracker.ietf.org/doc/rfc9334/)) addresses this by allowing an entity to
produce verifiable Evidence about its current state. For example, to
prove that its software and firmware haven't been tampered with. Or
that a secure boot method is enabled. Or that cryptographic keys are
securely stored within a hardware-protected environment.

This provides an additional assurance of trustworthiness, helping to
prevent the continued use of a compromised system even if its
conventional credentials remain valid, and enables authorization
policies based on richer security guarantees.

# Scope

The Secure Evidence and Attestation Layer (SEAL) WG will document a
set of use cases that protocols such as (D)TLS should be able to support.
It will initially deliver a Standards Track protocol that meets these
use cases and enables peer or mutual attestation for (D)TLS using the
extension and/or exporter features of D(TLS).

Such a mechanism would allow an entity to produce Evidence or an
Attestation Result about itself for another party to evaluate.

Specific scoping:

* This effort will be restricted to leveraging the (D)TLS 1.3 protocol
and a potential attestation binding to a (D)TLS 1.3 session.
* It will leverage the existing RATS WG documents to ensure
interoperability with existing and future attestation technologies.
* The (D)TLS protocol solution will focus on attestation and authenticated
attestation, but will not create new authentication mechanisms.
* The (D)TLS protocol solution will not modify the (D)TLS protocol outside
of adding (D)TLS extensions to support its goals that do not modify the
core (D)TLS specification.
* The (D)TLS protocol solution will allow per-connection
[freshness](https://www.ietf.org/rfc/rfc9334.html#section-10).
* The effort will not create solutions that decrease privacy
or security properties of generic TLS sessions.

The working group will engage with the research community on the
evaluation and formal analysis of the protocol artifacts in parallel
with the specification work.

# Dependencies and Liaisons

* The working group will work closely with the TLS working group, the RATS working group, and the Confidential Computing Consortium's (CCC's) Attestation Special Interest Group (SIG).
* The working group will engage with research groups regarding formal analysis of the working groups's resulting work.
* The working group will work closely with the WIMSE working group to ensure its deliverables are usable for common WIMSE deployments and have taken into account any Operational Considerations that apply.

# (Proposed) Milestones

* A use cases document describing the scenarios that this working group will be targeting in its specification document. This document need not be published as an RFC.
* A Standards Track document defining a (D)TLS protocol solution supporting remote peer and mutual attestation bound to the (D)TLS session.

# Future work

After the initial Milestones are complete, the WG may recharter to work
on adding attestation to protocols other than D(TLS), such as IKEv2 or
SSH, provided there is sufficient interest.
