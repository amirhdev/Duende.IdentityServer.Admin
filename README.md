![Logo](docs/Images/Skoruba.Duende.IdentityServer.Admin-Logo-ReadMe.png)

🛡️ IdentityServer + Ocelot API Gateway + Sample Api (PKCE | .NET 9)

This project is a customized microservices setup built on top of the Skoruba Duende IdentityServer Admin, extended to support:

- Centralized authentication with Duende IdentityServer

- Routing and access control via Ocelot API Gateway

- A secure, protected Sample API

- OAuth 2.0 with Authorization Code Flow + PKCE

- Modern architecture using .NET 9


📁 Project Structure

/src

├── IdentityServer       # Duende IdentityServer + Skoruba Admin UI (port 44310)

├── ApiGateway           # Ocelot-based gateway (port 6001)

└── SampleApi            # Protected API microservice (port 7111)


🔐 Authentication Flow (Authorization Code + PKCE)
- This project uses the Authorization Code Flow with PKCE, which is secure and recommended for public clients like SPAs and mobile apps.
  
🔁 Flow Overview

1- Client (SPA or mobile app) initiates login
   Sends code_challenge and code_challenge_method=S256 to IdentityServer.

2- User authenticates via IdentityServer (https://localhost:44310).

3- IdentityServer returns an authorization code to the client.

4- The client sends the authorization code + code_verifier to the token endpoint.

5- IdentityServer returns:
  - access_token
  - id_token
  - (optional) refresh_token

6- The client sends the access_token to the API Gateway (https://localhost:6001).

7- Ocelot Gateway validates the token and forwards the request to Sample API (https://localhost:7111).

🌐 Endpoints
- IdentityServer	https://localhost:44310
- API Gateway	https://localhost:6001
- Sample API (MyApi) https://localhost:7111

