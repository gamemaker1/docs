# Resume as a Verifiable Presentation

This project enables users to create verifiable presentations (VPs) from verifiable credentials (VCs)
or certificates previously issued to them.

## Process Breakdown

#### Programmatic retrieval of VCs from various sources

For example, retrieving certificates and proofs for a user from their DigiLocker account.

#### Parsing of VCs to retrieve the claim and their presentation.

This involves verifying and reading the VC for a list of claims, and how to render them in the VP.

For example, a birth certificate is a VC that stores the claim that they are of a certain age. The
presentation of that claim could be in various forms:

- JSON: `{ "age": 29 }`
- HTML: `<p> I am <strong>29</strong> years old. </p>`
- Text: `I am 29 years old.`

#### UI for creation of a VP from retrieved VCs

A GUI that allows users to pick claims from a list of their VCs, and create a VP from them. The template
for the VP could be user created too.

#### Signing and storage of VPs

This involves cryptographically signing and then storing the VP as a stream on a CORD chain, and embedding
the stream ID in a QR code that anyone can scan to verify the VP.
