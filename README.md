# Background and Motivation

In many scenarios, particularly with the rise of Trusted Execution
Environments (TEEs) and the increasing security demands for IoT devices
and confidential workloads, there is a requirement for some use cases that
utilize protocols such as (D)TLS to also ensure that the peer's state 
expressed as Claims (for example about code, data and configurations) is
validated in addition to the verification of identity for conventional authentication.

Remote attestation ([RFC9334](https://datatracker.ietf.org/doc/rfc9334/)) addresses this by allowing an entity to
produce verifiable Evidence about its current state, for example, to
prove that its software and firmware haven't been tampered with, or
that a secure boot method is enabled, or that cryptographic keys are
securely stored within a hardware-protected environment.

The composition of remote attestation and (D)TLS
provides an additional assurance of trustworthiness, helping to
prevent the continued use of a compromised system even if its
conventional credentials remain valid, and enables authorization
policies based on stronger security guarantees.

# Scope

The Secure Evidence and Attestation Layer (SEAL) WG 
will initially deliver a Standards Track protocol that 
enables peer or mutual attestation for (D)TLS using the
extension and/or exporter features of (D)TLS.

Such a protocol would allow an entity to produce Evidence or an
Attestation Result about itself for another party to evaluate.

This protocol will also describe a minimum subset of properties
that the attested remote state must ensure in order to bind the
Evidence and Attestation Results to the TLS connection.

Specific scoping:

* This effort will be restricted to leveraging the (D)TLS 1.3 protocol
and attestation binding to a (D)TLS 1.3 connection. Older versions of (D)TLS will not be supported.
* It will leverage the existing RATS WG documents to ensure
interoperability with existing and future attestation technologies.
* The attested (D)TLS protocol will focus on the composition of remote attestation and (D)TLS,
but will not create new authentication mechanisms.
* The attested (D)TLS protocol will not modify the (D)TLS protocol outside
of adding (D)TLS extensions to support its goals that do not modify the
core (D)TLS specification.
* The attested (D)TLS protocol will support: 

  * Server as Attester
  * Client as Attester
  * Mutual Attestation

In particular, the specification will also support mutual attestation without client authentication.
* The attested (D)TLS protocol will allow per-connection
[freshness](https://www.ietf.org/rfc/rfc9334.html#section-10)
of Evidence or Attestation Results, whichever is applicable.
* The effort will not create a protocol that decreases the privacy
or security properties of generic TLS connections.

The working group will engage with the research community on the
evaluation and formal analysis of the protocol artifacts in parallel
with the specification work.

# Dependencies and Liaisons

* The working group will work closely with the TLS working group, the RATS working group, and the Confidential Computing Consortium's (CCC's) Attestation Special Interest Group (SIG).
* The working group will engage with research groups, such as [IRTF Usable Formal Methods Research Group (UFMRG)](https://www.irtf.org/ufmrg.html), regarding formal analysis of the protocol.

# (Proposed) Milestones

* A Standards Track document defining an attested (D)TLS protocol supporting remote peer and mutual attestation bound to the (D)TLS connection.

# Future work

After the initial Milestones are complete, the WG may recharter to work
on adding attestation to protocols other than (D)TLS, such as IKEv2 or
SSH, provided there is sufficient interest.
