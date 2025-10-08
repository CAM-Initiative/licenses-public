# CAM Initiative Public Licence Registry

This repository is the **public ledger** of custodian licences issued by the CAM Initiative.  Each record in `licenses/` corresponds to a licence that has been issued and published for verification.  The public registry contains only non‑sensitive metadata — full declarations, signatory details and internal notes are stored privately in the companion repository `licenses-private`.

## Repository Structure

```
licenses-public/
├── LICENSE                # Licence for this repository (Apache‑2.0)
├── README.md             # This file
├── SCHEMA.license.json   # JSON schema defining the structure of licence records
├── revocations.json      # List of revoked licences with timestamps and reasons
├── jwks.json             # JSON Web Key Set containing public verification keys
├── licenses/             # Directory of published licence records
│   └── cam-lic-orourke-planetary-2025.json
└── .github/
    └── workflows/
        └── validate.yaml  # GitHub Actions workflow to validate licence records
```

## How to Use

1. **Add or update licences** by creating or editing files in `licenses/`.  Each file must conform to the schema in `SCHEMA.license.json`.
2. **Revoked licences** should have their `revoked` field set to `true` and a corresponding entry added to `revocations.json`.
3. **Public keys** used to sign licence declarations are published in `jwks.json`.  If a new signing key is introduced, append it to this file with a unique `kid`.
4. A GitHub Actions workflow (`validate.yaml`) runs on every pull request to ensure that all licence records are valid JSON and conform to the schema.

For more details on issuance, renewal and revocation procedures, see the documentation in the `licenses-private` repository.