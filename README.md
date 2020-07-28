# User centric advertising network

## Introduction
Personalized advertising aims at fostering users' awareness of brands, products and services that match their interests in ways that foster positive engagement and brand recognition — By funding content providers and publishers, personalized advertising enables free access to content and services ranging from social media platforms to news, investigation journalism or weather forecasts. . As of today, it is impractical for users to assess how the media they consume is brought to them and to what extent this consumption comes at odds or not with their privacy preferences. 

This proposal adopts the viewpoint that users should benefit from a vast, open and mostly free internet ecosystem in ways that cater to their individual preferences in terms of level of personalized services they seek to enjoy online, from each of the businesses they engage with.

This document presents a proposal for a user-centric advertising network that makes the open web ecosystem durable while empowering users to control their online privacy profile.

## Design Principles
We propose a design which grants full and easy control to the user to manage a revocable, enforceable and auditable online privacy profile.

As of today, identity management and resolution is decentralized and generates fragmentation of the user data and lack of controls. 

As such, the following principles guide our design:

Centralization of user privacy preferences: the users’ privacy profile is cross-browser/device/environment/OS.
Ubiquity for accessing & altering user preferences: any and every online touchpoint can provide controls for users to manage their preferences.
Auditability: in the way user data is managed by vendors.
Limitation of purpose: the identifier is dedicated to advertising use case and should not be used for any other purpose (say as a login to a social media app) which ensures clean separation of data used for advertising purposes with those leveraged to power other types of online services.

Multiple designs were studied to enforce those principles, all of them relying on a unique identifier representing the end user.

Nonetheless, each design has i) its own way of storing the user identifier and ii) pros and cons:
| Design options  | Identifier storage location | Description | Pros | Cons |
|---|---|---|---|---|
| #1 | Browser | Identifier is generated, stored and shared by browsers to publishers/advertisers/SSPs/DSPs | <ul><li>Centralization of user privacy preferences</li><li>Limitation of purpose</li><li>Auditability</li><li>Great user experience for end-users</li></ul> | <ul><li>Require support from all browser vendors to manage an Identifier</li></ul> |
| #2 | Browser plugin | Identifier is generated, stored and shared by a browser's plugin installed manually by the end user | <ul><li>Centralization of user privacy preferences</li><li>Limitation of purpose</li><li>Great user experience for end-users</li><li>Auditability</li></ul> | <ul><li>Capacity to scale (require plugin-install)</li></ul> |
| #3 (current state) | Advertiser/Publisher/Vendors | Identifier is collected, stored and shared by each advertiser/publisher/vendors and based on PII | <ul><li>Great user experience for end-users</li></ul> | <ul><li>No centralization of user privacy preferences</li><li>No clear limitation of purpose</li><li>Capacity to scale (PII-only)</li><li>Few auditability</li></ul> |
| #4 | Identity providers | Identifier is generated, stored and shared by Identity Providers and is linked to PII | <ul><li>Great user experience for end-users</li><li>Clear limitation of purpose</li><li>Auditability</li></ul> | <ul><li>Requirement support from all identity providers to manage an Identifier</li><li>Requirement for advertisers/publishers to adopt SSOs as login provider</li><li>Capacity to scale (PII-only)</li></ul> |
| #5 | Third-party entity | Identifier is generated and stored by a third-party independent entity at user sign-up time or consent time and is shared across advertisers, publishers and tech vendors | <ul><li>Centralization of user privacy preferences</li><li>Ubiquity for accessing & altering user preferences</li><li>Clear limitation of purpose
</li><li>Auditability</li></ul> | <ul><li>User experience</li></ul> |

Options 2, 3 and 4 seems difficult to scale and are therefore not detailed in this proposal.

Even if option 1 has both significant alignements with our design principles, they require strong support from browser vendors which is uncertain at this time.

So, in the mean time, we believe that option 5 is a valuable option worth investigating and focus the rest of the document on it.
## Proposal

## Benefits

## About the Network Governance

## Additional considerations