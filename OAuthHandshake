# Authorization Handshake 

The authorization handshake assumes that there is already a resource owner who has stored a resource on a resource server.

``` mermaid

%%{
  init: {
    'themeVariables': {
      'nodeBorder': '#00467F',
      'primaryColor':'#B2292E',
      'lineColor': '#007078'
    }
  }
}%%

flowchart LR

A["Resource Owner/
End User"] -- creates --> B["Resource 
(Data)"] -- stored on --> C[("Resource 
Server")] 

```

In this example, the resource owner is an angler who uses Fish Online. Their resource is their Fish Online account, which they create when they enter their profile information and upload their documents. The resource server is a database operated by GARFO, which is where the usernames, passwords, addresses, vessel permit numbers, and other information is stored.

``` mermaid

sequenceDiagram
    participant A as Resource Owner<br/>End User<br/>e.g. Angler
    participant B as Client application <br/>with third-party login<br/>e.g. Bluefin Data app <br/>with FishOnline Login
    participant C as Authorization Server <br/>Resource Server <br/>OpenID Provider<br/>e.g.FishOnline Server

A->>B: 1. User clicks third-party login.
B->>C: 2. Client requests authentication.
C->>A: 3. Server requests authorization.
A->>C: 4. Grants authorization.
C->>B: 5. Sends authorization code.
B->>C: 6. Requests access token.
C->>B: 7. Sends access token. 



```

1. To initiate the authorization handshake, the end user visits the client and uses the third-party login feature. For example, the angler uses the Bluefin Data app and clicks the "Log In With Fish Online" button.
2. The client makes an authentication request on behalf of the user to the authorization server. In this case, the authorization server is the OpenID provider implemented by GARFO. 
3. The authorization server requests authorization from the user. The user is redirected to an authorization endpoint, where they log in using their Fish Online credentials. They must already be a Fish Online user, or they must create an account at this step (see above).
4. If the user successfully enters their username and password and consents to sharing their information (e.g. by clicking an "I agree" checkbox), authorization is granted. 
An authorization code is created by the OpenID provider. At the same time, a JSON Web Token (JWT) is also created, and the authorization code is used as the name of the JWT. The authorization code is sent to the client (Bluefin Data). This authorization code lets the client know that the user has authorized their access, but it does not grant them permission yet.
The client uses the authorization code to request the access token from the OpenID provider. 
The OpenID provider checks the client's credentials against the authorization code. If there isn't a match, the flow stops. If there's a match, the OpenID provider finds the matching access token (see step 5) and gives it to the client. The access token is a JSON Web Token (JWT, pronounced "jot") whose name matches the authorization code. The JWT includes the user's Client ID.
The client decrypts the token using the public key provided at the JWKS endpoint. The access token has various claims (JSON properties). The client validates the standard claims in the access token and gets the resources (custom claims) from the JWT which consist of information about the user. The resources include clientID, humanName, clientEmail and user (i.e. username). The user's Client ID is used to submit vessel trip reports on their behalf.
The user is logged in to Bluefin Data without Bluefin Data ever seeing their Fish Online username and password. Bluefin Data may use the Client ID number to pre-populate the user's profile information. 
