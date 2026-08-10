# Active Directory Authentication

This page contains my notes on authentication in Windows domain environments, especially Kerberos and NetNTLM.

---

## Windows Domain Authentication

When a user tries to access a service using a domain account, the user's identity is validated through the:

`Domain Controller (DC)`

Windows domain environments commonly use two authentication methods covered in my notes:

- Kerberos
- NetNTLM

A simple way to remember them is:

`Kerberos = Ticket-based authentication`

`NetNTLM = Challenge-response authentication`

---

# Kerberos

Kerberos is the more modern and default authentication method used in newer Windows domain environments.

Instead of sending the user's password directly to every service, Kerberos uses:

`Tickets`

This allows a user to authenticate once and then request access to different services without entering the password again for every service.

---

# Basic Kerberos Flow

The simplified Kerberos authentication flow from my notes is:

1. The user authenticates with the KDC.
2. The KDC gives the user a TGT.
3. When the user wants to access a service, the TGT is used to request a service ticket.
4. The user receives a TGS ticket for the requested service.
5. The user sends the service ticket to the target service.
6. The service validates the ticket and allows access.

Simplified:

`User`

↓

`KDC`

↓

`TGT`

↓

`Request access to a service`

↓

`TGS`

↓

`Target Service`

↓

`Access`

---

# KDC — Key Distribution Center

KDC stands for:

`Key Distribution Center`

The KDC is responsible for issuing Kerberos tickets.

A simple way to remember:

`KDC = Ticket issuer`

The user first communicates with the KDC before accessing domain services through Kerberos.

---

# TGT — Ticket Granting Ticket

TGT stands for:

`Ticket Granting Ticket`

The TGT is the main ticket received after the user's initial authentication.

The TGT can later be used to request service tickets.

A simple way to remember:

`TGT = I have already authenticated`

The TGT does not represent access to one specific service.

Instead, it helps the user request access to other services.

---

# TGS — Ticket Granting Service Ticket

A TGS ticket is used to access a specific service.

For example, after receiving a TGT, the user may request a ticket for a specific domain service.

A simple way to remember:

`TGS = I can access this specific service`

---

# TGT vs TGS

The difference is important:

| TGT | TGS |
|---|---|
| Received after initial authentication | Requested when accessing a specific service |
| Used to request other tickets | Used to access the target service |
| General authentication ticket | Service-specific ticket |

The easiest way to remember:

`TGT = I already proved who I am`

`TGS = I have permission to access this service`

---

# SPN — Service Principal Name

SPN stands for:

`Service Principal Name`

An SPN identifies the service and server that the user wants to access.

Kerberos needs to know which service the requested ticket is intended for.

Conceptually:

`User wants service`

↓

`SPN identifies service`

↓

`Kerberos issues the appropriate service ticket`

---

# krbtgt

`krbtgt`

is a special domain account used by Kerberos.

According to my notes, it is used in relation to the encryption of TGTs.

This makes the `krbtgt` account an important part of Kerberos authentication in the domain.

A simple way to remember:

`krbtgt = Special Kerberos domain account associated with TGTs`

---

# Why Kerberos Uses Tickets

Without tickets, a user might need to send credentials again every time a different service is accessed.

With Kerberos:

`Initial Authentication`

↓

`Receive TGT`

↓

`Use TGT to request service tickets`

↓

`Access multiple services`

The user does not need to enter the password again for every service.

---

# NetNTLM

NetNTLM uses a different authentication model.

Instead of tickets, it uses:

`Challenge-Response`

A simple way to remember:

`NetNTLM = Challenge → Response`

---

# NetNTLM Authentication Flow

The simplified flow from my notes is:

1. The client sends a login request to the server.
2. The server generates a random challenge.
3. The client creates a response using its NTLM hash information and the challenge.
4. The server sends this response to the Domain Controller.
5. The Domain Controller performs the same calculation.
6. If the results match, the user is authenticated.

Simplified:

`Client`

↓

`Login Request`

↓

`Server sends Challenge`

↓

`Client calculates Response`

↓

`Server sends Response to DC`

↓

`DC verifies`

↓

`Authentication succeeds or fails`

---

# Challenge

The server sends a random value called a:

`Challenge`

The challenge is used as part of the authentication calculation.

The user is therefore not simply sending the same reusable value to the server each time.

---

# Response

The client uses the challenge and its authentication information to calculate a:

`Response`

The response is sent back to the server.

The server then uses the Domain Controller to verify whether the response is correct.

---

# Role of the Domain Controller in NetNTLM

The server does not need to directly know the user's password.

Instead:

`Server`

↓

`Sends authentication information to DC`

↓

`Domain Controller verifies`

↓

`Valid / Invalid`

This allows domain authentication to remain centralized.

---

# Password Transmission

An important point from my notes is:

The user's actual password is not directly sent across the network.

The password hash itself is also not directly transmitted as the authentication response.

Instead, the challenge-response calculation is used.

---

# Kerberos vs NetNTLM

The comparison from my notes is:

| Kerberos | NetNTLM |
|---|---|
| Modern and default | Older / mainly supported for compatibility |
| Uses tickets | Uses challenge-response |
| Uses TGT and TGS | Uses challenge and response |
| Uses KDC | Domain Controller verifies the response |

---

# Easy Memory Trick

The easiest way to remember the difference is:

`Kerberos = Tickets`

`NetNTLM = Challenge-Response`

For Kerberos:

`TGT → TGS → Service`

For NetNTLM:

`Challenge → Response → Verification`

---

# Why Authentication Matters in Cybersecurity

Authentication determines whether an identity is allowed to prove who it claims to be.

In an Active Directory environment, authentication is especially important because the same domain identity may be used to access multiple systems and services.

Understanding the authentication process helps explain:

- How domain users log in
- How services verify identities
- Why Domain Controllers are important
- How enterprise authentication is centralized

---

# Authentication vs Authorization

Authentication answers:

`Who are you?`

Authorization answers:

`What are you allowed to access?`

For example:

A user may successfully authenticate to the domain.

That does not automatically mean the user has permission to access every resource.

Simplified:

`Authentication`

↓

`Identity verified`

then:

`Authorization`

↓

`Permissions checked`

---

# Quick Reference

| Term | Meaning |
|---|---|
| Authentication | Verifying an identity |
| Domain Controller | Validates domain identities |
| Kerberos | Ticket-based authentication |
| KDC | Key Distribution Center |
| TGT | Ticket Granting Ticket |
| TGS | Service-specific Kerberos ticket |
| SPN | Identifies a service and server |
| `krbtgt` | Special Kerberos domain account related to TGTs |
| NetNTLM | Challenge-response authentication |
| Challenge | Random value sent by the server |
| Response | Value calculated by the client for authentication |

---

## Key Takeaway

The main authentication concepts are:

`Kerberos → Ticket System`

and:

`NetNTLM → Challenge-Response`

For Kerberos:

`Authenticate → TGT → TGS → Service`

For NetNTLM:

`Challenge → Response → Domain Controller Verification`

Kerberos is the modern default approach in Windows domain environments, while NetNTLM remains supported mainly for compatibility.
