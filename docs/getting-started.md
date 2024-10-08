# Getting Started

Connect to Cube AI deployed instance on port `:6193`. Login with your username and password. If you can't log in ask the instance administrator to create a new user.

## Create a new user

[This is a demonstration of how to create a new user](https://jam.dev/c/f8d3fa47-7505-4201-b8ca-c0f724826237). You can use the same steps to create a new user.

1. Admin login with their credentials
2. Create a new domain if there is none
3. Login to the new domain or already existing domain
4. Click profile icon and navigate to `Manage Users`
5. Click create
6. Fill in the form
7. Click `Create`

## Login

Get a token from using your login credentials.

```bash
curl -ksSiX POST https://<cube-ai-instance>/users/tokens/issue -H "Content-Type: application/json" -d @- << EOF
{
  "identity": "<your_email>",
  "secret": "<your_password>"
}
EOF
```

The response will look something like this:

```bash
HTTP/2 201
content-type: application/json
date: Wed, 18 Sep 2024 11:13:48 GMT
x-frame-options: DENY
x-xss-protection: 1; mode=block
content-length: 591

{"access_token":"<access_token>","refresh_token":"<refresh_token>"}
```

The access token is the `access_token` field in the response will be used to authenticate with the API.

## VS Code Setup

1. Download and intall [VS Code](https://code.visualstudio.com/)
2. In VS Code download and install the [continue extention](https://www.continue.dev/). This extenstion will help us connect with the Cube AI running models and use them as coding assistance.
3. Open tthe continue extension and click the setting icon `Configure Continue`. This will open the `.continue/config.json` file.
4. Edit the `config.json` file to look something like this:

```json
{
  "models": [
    {
      "title": "Ollama",
      "provider": "ollama",
      "model": "llama3:8b",
      "apiKey": "<access_token>",
      "apiBase": "<cube-ai-instance>/ollama"
    }
  ],
  "tabAutocompleteModel": {
    "title": "Starcoder 2 3b",
    "provider": "ollama",
    "model": "starcoder2:3b",
    "apiKey": "<access_token>",
    "apiBase": "<cube-ai-instance>/ollama"
  },
  "embeddingsProvider": {
    "provider": "ollama",
    "model": "nomic-embed-text",
    "apiKey": "<access_token>",
    "apiBase": "<cube-ai-instance>/ollama"
  },
  "requestOptions": {
    "verifySsl": false
  }
}
```

This is a demonstration of how to connect to Cube AI with the continue extension.

<iframe width="560" height="315" src="https://www.youtube.com/embed/BGpv_iTB2NE?si=2qwUc4p99MYkSROK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
