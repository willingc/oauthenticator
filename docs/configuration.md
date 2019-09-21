# Basic Configuration

**OAuthenticator** currently supports a variety of OAuth authentication services.
This section describes:
- choosing an OAuthenticator and its basic naming for an OAuth provider
- adding an OAuthenticator to the JupyterHub configuration file
- setting a callback URL for the OAuth provider
- setting up a client and its secret

## Choose an OAuthenticator for an OAuth provider

The first step is to tell JupyterHub to use your chosen OAuthenticator. Each
OAuth provider's authenticator is provided in a submodule of `oauthenticator`.
For example, the GitHub OAuth service has `GitHubOAuthenticator`.
A variant of the provider's authenticator exists to map OAuth usernames to 
local system usernames by prefixing the authenticator with 
`Local` (e.g. `LocalGitHubOAuthenticator`),

## Add OAuthenticator to JupyterHub config file

In `jupyterhub_config.py`, add these lines to the configuration file:

```python
from oauthenticator.github import GitHubOAuthenticator
c.JupyterHub.authenticator_class = GitHubOAuthenticator
```

## Set callback URL, client ID, and client secret

All OAuthenticators require setting a callback URL, client ID, and client
secret. You will generally get these when you register your OAuth application
with your OAuth provider. 

When registering your oauth application (in this case JupyterHub) with your
OAuth provider, you will probably need to specify a callback URL.
The callback URL should look like:

`http[s]://[your-host]/hub/oauth_callback`

where `[your-host]` is the server where JupyterHub will be running, such as
`example.com:8000`.

When JupyterHub runs, the callback URL, client id, and client secret values will
be retrieved from the **environment variables**:

```bash
$OAUTH_CALLBACK_URL
$OAUTH_CLIENT_ID
$OAUTH_CLIENT_SECRET
```

You can also set these values in your **configuration file**, `jupyterhub_config.py`:

```python
# Replace MyOAuthenticator with your selected OAuthenticator class (e.g. c.GithubOAuthenticator)

c.MyOAuthenticator.oauth_callback_url = 'http[s]://[your-host]/hub/oauth_callback'
c.MyOAuthenticator.client_id = 'your-client-id'
c.MyOAuthenticator.client_secret = 'your-client-secret'
```

## Summary

This section explained the basic setup and configuration of an OAuthenticator:

- add the OAuthenticator to JupyterHub's config file
- set up the provider's callback URL, client ID, and client secret
- store this provider information as **environment variables** or in the **JupyterHub config file**.

Please refer to provider specific OAuthenticator sections for additional settings and
deployment instructions.
