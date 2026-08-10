# Active Directory Trees, Forests, and Trusts

This page contains my notes on Active Directory trees, forests, domain relationships, and trust relationships.

---

## Why Multiple Domains May Be Needed

As an organization grows, a single domain may not always be enough.

For example, an organization may create separate domains for different countries or regions.

Example:

`thm.local`

↓

`uk.thm.local`

`us.thm.local`

These domains are related because they share the same namespace.

---

# Tree

A Tree is a collection of related Active Directory domains that share the same namespace.

Example:

`thm.local`

↓

`uk.thm.local`

`us.thm.local`

Here:

- `thm.local` → Parent domain
- `uk.thm.local` → Child domain
- `us.thm.local` → Child domain

Together, they form a:

`Tree`

---

## Namespace

A namespace is the naming structure shared by related domains.

For example:

`thm.local`

`uk.thm.local`

`us.thm.local`

all share:

`thm.local`

as part of their name.

Because of this common namespace, they belong to the same tree.

---

# Child Domains

Each child domain can have its own:

- Domain Controller
- Users
- Computers
- Group Policies
- Administrative structure

For example:

`uk.thm.local`

may have its own Domain Controller and users.

`us.thm.local`

may also have its own Domain Controller and users.

This allows different parts of the organization to manage their own domain environments.

---

# Domain Admins

Each domain has its own:

`Domain Admins`

group.

Domain Admins have very high administrative privileges inside their own domain.

For example:

`uk.thm.local Domain Admin`

mainly manages:

`uk.thm.local`

A simple way to remember:

`Domain Admins = One Domain`

---

# Enterprise Admins

Enterprise Admins have broader administrative privileges across the Active Directory structure.

A simple way to remember:

`Domain Admins → Single domain`

`Enterprise Admins → All domains in the organization`

Enterprise Admins are therefore more powerful than normal Domain Admin accounts.

---

# Forest

A Forest is formed when multiple Active Directory trees with different namespaces are combined.

Example:

`Forest`

↓

`thm.local`

- `uk.thm.local`
- `us.thm.local`

and:

`mht.local`

- `asia.mht.local`
- `eu.mht.local`

Here:

`thm.local`

and:

`mht.local`

use different namespaces.

Therefore, they represent different trees.

Together, those trees form a:

`Forest`

---

# Tree vs Forest

The difference can be summarized as:

`Tree`

→ Related domains sharing the same namespace

`Forest`

→ Multiple trees that may use different namespaces

Example:

`thm.local + uk.thm.local + us.thm.local`

→ Tree

while:

`thm.local tree + mht.local tree`

→ Forest

---

# Trust Relationship

A Trust Relationship allows identities from one domain to be recognized by another domain.

This can allow users from one domain to be granted access to resources in another domain.

Important:

`Trust does not automatically mean access.`

It only means that another domain's identity can be recognized and potentially authorized.

---

# Authentication and Authorization

This distinction is important.

Trust helps with the possibility of recognizing users from another domain.

Actual resource access still requires:

`Authorization / Permission`

A simplified idea is:

`Trust`

↓

`I recognize this domain's user`

but then:

`Resource Permission`

↓

`Is this user actually allowed to access the resource?`

---

# One-Way Trust

A One-Way Trust means only one domain trusts the other.

Example from my notes:

`Domain AAA trusts Domain BBB`

In this case, users from BBB can potentially be authorized to access resources in AAA.

This means the trust direction and possible access direction are opposite.

A simple way to remember:

`AAA trusts BBB`

↓

`BBB users may be given access to AAA resources`

---

# Why the Direction Looks Reversed

If AAA says:

`I trust BBB`

AAA is saying:

`I am willing to recognize users authenticated by BBB.`

Therefore, BBB users can potentially be granted access to resources belonging to AAA.

That is why:

`Trust Direction`

and:

`Possible Access Direction`

appear opposite.

---

# One-Way Trust Example

Imagine:

`Company-A.local`

trusts:

`Company-B.local`

This means Company A can recognize identities from Company B.

A user from Company B may then be given permission to access a resource in Company A.

But this does not automatically mean Company A users can access Company B resources.

---

# Two-Way Trust

In a Two-Way Trust:

`Domain A trusts Domain B`

and:

`Domain B trusts Domain A`

Both domains recognize identities from the other domain.

This means users from either domain can potentially be authorized to access resources in the other domain.

---

# Tree and Forest Trusts

When domains are combined under Active Directory tree or forest structures, trust relationships may exist between them.

The important idea from my notes is that these relationships allow users from different domains to be recognized across the Active Directory structure.

However, recognition still does not automatically grant access.

---

# Trust Does Not Equal Permission

This is the most important concept in this section.

A trust relationship means:

`I recognize users from the other domain.`

It does NOT mean:

`All users from that domain can access all of my resources.`

Access still requires explicit permission.

Example:

`BBB User`

↓

`AAA trusts BBB`

↓

`AAA recognizes the user`

but:

`Shared Folder Permission`

↓

`Allow / Deny`

The resource owner still controls authorization.

---

# Example

Imagine:

`uk.thm.local`

and:

`us.thm.local`

have a trust relationship.

A user:

`john@uk.thm.local`

may be recognized by:

`us.thm.local`

However, John still cannot automatically access every shared folder in the US domain.

The resource must give John or one of John's groups permission.

---

# Domain, Tree, Forest, and Trust

The complete hierarchy can be simplified as:

`Domain`

→ One administrative domain environment

`Tree`

→ Multiple related domains sharing a namespace

`Forest`

→ Multiple trees, potentially with different namespaces

`Trust`

→ Relationship that allows identities from another domain to be recognized

---

# Administrative Scope

Another useful way to understand the structure is:

`Domain Admin`

↓

`Controls one domain`

while:

`Enterprise Admin`

↓

`Can manage across the forest`

This reflects the larger administrative scope of a forest.

---

# Why Trees and Forests Matter in Cybersecurity

Large organizations may contain many domains.

Understanding trees, forests, and trusts helps explain:

- How users are organized across domains
- How administrative privileges are separated
- How users from one domain may access another domain's resources
- Why trust relationships can affect security boundaries
- Why permissions still matter after authentication

Trust relationships are therefore important when analyzing enterprise Active Directory environments.

---

# Quick Reference

| Term | Meaning |
|---|---|
| Domain | One Active Directory management area |
| Child Domain | Domain beneath another domain |
| Tree | Related domains sharing the same namespace |
| Namespace | Common naming structure between domains |
| Forest | Collection of one or more trees |
| Domain Admins | Administrators of one domain |
| Enterprise Admins | Administrators across the forest |
| Trust Relationship | Allows identities from another domain to be recognized |
| One-Way Trust | One domain trusts another |
| Two-Way Trust | Both domains trust each other |
| Authorization | Determines actual resource access |

---

## Key Takeaway

The easiest way to remember the structure is:

`Domain → Single management area`

`Tree → Same namespace`

`Forest → Multiple trees / namespaces`

`Trust → Recognize identities from another domain`

And the most important security rule is:

`Trust ≠ Access`

A trust relationship only makes cross-domain authentication possible.

Actual access still depends on:

`Permission / Authorization`
