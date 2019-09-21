# OAuthenticator

OAuth + JupyterHub Authenticator = OAuthenticator

**OAuthenticator** currently supports the following authentication services:

- [Auth0](auth0.py)
- [Azure](#azure-setup)
- [Bitbucket](bitbucket.py)
- [CILogon](cilogon.py)
- [GitHub](#github-setup)
- [GitLab](#gitlab-setup)
- [Globus](#globus-setup)
- [Google](#google-setup)
- [MediaWiki](mediawiki.py)
- [Moodle](#moodle-setup)
- [Okpy](#okpyauthenticator)
- [OpenShift](#openshift-setup)

In addition to OAuthenticators for these services, a
[generic oauthenticator implementation](generic.py), can be used or extended to support
any OAuth provider.

# Usage

## Use as a JupyterHub Authenticator

In its most basic usage, the OAuthenticator may be used instead of JupyterHub's default PAM
Authenticator. The OAuthenticator is used to authenticate a user with JupyterHub using the
OAuth2 protocol. The OAuthenticator simplifies sign-on for users.

## Use in a Docker image
The [examples](examples) directory of this repo provides an example docker image which
uses OAuthenticator. The Dockerfile and a README can be found in the `full` subdirectory. 

## Use as part of a custom Spawner

OAuthenticators can be used in a custom JupyterHub Spawner. 
[DockerSpawner](https://github.com/jupyterhub/dockerspawner/tree/master/examples/oauth)
is an example of using an OAuthenticator, specifically GitHub OAuth, to spawn each user's
server in a separate docker container which a user can access with their GitHub login.

# Installation

Install with pip:

```bash
pip3 install oauthenticator
```

or conda:

```bash
conda install -c conda-forge oauthenticator
```

A development installation requires cloning the source code and
doing a dev install:

```bash
git clone https://github.com/jupyterhub/oauthenticator.git
cd oauthenticator
pip3 install -e .
```

