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

The projection boundary is not a manual copy step. RepoGraph defines the
projection rules, the private-truth layer generates boundary artifacts from
private truth, and Custodian verifies public surfaces against those artifacts.

The public site is current-only. It does not catalog private-truth repos as
first-class browseable pages.
