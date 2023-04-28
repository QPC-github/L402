# L402: Lightning HTTP 402 Protocol

L402 is a standard to support the use case of charging for services and authenticating users in distributed networks. Developed by [Lightning Labs](https://lightning.engineering/), it combines the strengths of Macaroons, for better authentication, and the strengths of the Lightning Network, for better payments. L402 API credentials invigorate the HTTP error code _402 Payment Required_ by combining the fine-grained authentication capabilities of Macaroons with Lightning Network payments, making it easy to charge amounts of any size for an API request, web page or resource.

This repository outlines the open source design for L402, formerly published under the name LSAT. We welcome contributions to this repository.

An L402 is created like a [Macaroon](macaroons.md). It combines the advantages of bearer and identity-based authentication systems that can quickly be issued and verified without requiring access to a central database.

In addition to a regular Macaroon, an L402 includes a payment hash, which is presented to the user with a Lightning Network invoice. The user can prove their successful payment if the preimage matches the payment hash.

A valid L402, meaning a Macaroon issued by the service and the preimage obtained by the user, is easy to verify by distributed systems. Instead of looking up cookies or payment details using centralized databases, an L402 can be verified using minimal information and basic cryptography.

This system allows users to automate pricing on the fly and enables a number of novel constructs such as automated tier upgrades. L402 get its name from the HTTP status code 402: Payment Required. They can be viewed as a global HTTP 402 reverse proxy at the load balancing level for all services.

Today, L402 is implemented in [Aperture](https://github.com/lightninglabs/aperture) and used for authentication in Lightning Lab’s [Loop](https://github.com/lightninglabs/loop) and [Pool](https://github.com/lightninglabs/pool) services for authentication.

* [Introduction](introduction.md)
* [Authentication flow](authentication-flow.md)
* [Protocol Specification](protocol-specification.md)
* [Macaroon Minting & Verification](macaroons.md)

## Implementations

* [Aperture: A gRPC/HTTP authentication reverse proxy using L402s](https://github.com/lightninglabs/aperture)
* [A utility library for working with L402s](https://github.com/Tierion/lsat-js)
* [boltwall: Nodejs middleware-based authentication using L402s](https://github.com/tierion/boltwall)

## External links / References

* [Builder's Guide Documentation](https://docs.lightning.engineering/the-lightning-network/l402)
* [L402 Playground](https://lsat-playground.bucko.now.sh/)
* [Macaroons: Cookies with Contextual Caveats](https://research.google/pubs/pub41892/)
* [HTTP/1.1 RFC, Section 6.5.2: 402 Payment Required](https://tools.ietf.org/html/rfc7231#section-6.5.2)

