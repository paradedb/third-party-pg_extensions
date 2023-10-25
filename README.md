# ParadeDB Third-Party PostgreSQL Extensions "Package Manager"

At ParadeDB, we build many PostgreSQL extensions. All our extensions come pre-installed on ParadeDB, and can installed on self-hosted PostgreSQL deploments as well. For the ParadeDB extensions, please refer to our [main repository](https://github.com/paradedb/paradedb).

We also aim to support as many open-source PostgreSQL extensions as possible. In order to avoid constantly re-compiling extensions, we created this repository to serve as a mini "package manager" of sort, where we store compiled third-party extensions to easily retrieve and install onto ParadeDB for both development and production workflows.

## Disclaimer

This repository was built for ParadeDB, and does not aim to be a full-fleged package manager. It does not support every version of an extension or every open-source PostgreSQL extensions, but rather only the ones we use and couldn't find pre-packaged somewhere else. The repository is left public to facilitate our own development, and to benefit the community if they'd like to easily install some PostgreSQL extensions that might not be shipped to package managers like `apt` without compiling manually.

And needless to say, ParadeDB does not claim any ownership nor liability for the extensions listed here.

## Usage

Every extension pre-compiled and upload here is uploaded as its own GitHub Release with tag `<name>-v<semVer>-<arch>`, for instance `pgvector-v0.5.1-arm64`. Within each release, many possible versions of PostgreSQL might be supported. As of writing, we only support PostgreSQL 15. The extensions *might* work with different versions, but they were only compiled and tested against PostgreSQL 15. Every extension is built on Ubuntu 22.04 and packaged as a `.deb`.

To download and install an extension, you can simply do:

```bash
PGVECTOR_VERSION=0.5.1
PG_VERSION_MAJOR=15
TARGETARCH=arm64

curl -L "https://github.com/paradedb/third-party-pg_extensions/releases/download/pgvector-v${PGVECTOR_VERSION}-$TARGETARCH/pgvector-v${PGVECTOR_VERSION}-pg${PG_VERSION_MAJOR}-$TARGETARCH-linux-gnu.deb" -o /tmp/pgvector.deb

sudo apt-get install -y /tmp/pgvector.deb
```

For an example of how this is done at scale at ParadeDB, see [our Dockerfile](https://github.com/paradedb/paradedb/blob/dev/docker/Dockerfile#L186).
