# Public vs Private

ProtocolWarden explicitly separates public-facing knowledge from private
operational truth.

## Public

Public-safe material may include:

- public repo identities
- public protocol descriptions
- public-safe topology
- stable public documentation
- sanitized diagrams
- public examples

## Private

Private material may include:

- internal topology
- private managed project details
- internal paths and endpoints
- private runtime or deployment assumptions
- restricted relationship edges

## Core Rule

Public knowledge should be a projection of private truth when those surfaces are
related. This avoids documentation drift and privacy leakage.
