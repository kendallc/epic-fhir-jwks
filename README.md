# Epic FHIR JWKS Hosting

This repository hosts the JSON Web Key Set (JWKS) for Epic FHIR integration.

## Purpose

Epic requires backend OAuth 2.0 applications to provide public keys via a JWK Set URL for JWT signature verification.

## Access

The JWKS is publicly accessible at:
- **Non-Production**: `https://<your-username>.github.io/jwks-hosting/.well-known/jwks.json`

## Security Note

This repository only contains **public keys** - it is safe to host publicly. The corresponding private keys are securely stored and never committed to this repository.

## Key Rotation

When rotating keys:
1. Add the new public key to the `keys` array in `.well-known/jwks.json`
2. Deploy the updated file
3. Wait 5 minutes for Epic to cache the new keys
4. Start using the new private key
5. Remove the old public key after confirming the new key works
