# Structure
- Backend
  - Holder Backend (ZK generator)
  - Issuer Backend (DB)
- Contract
  - Issuer Contract (Registry)
  - Verifier Contract (ZK verifier)
- Example Contract (RP)
- Frontend

## Backend
### Holder Backend
- [x] Endpoint to generate proofs
### Issuer Backend
- [ ] small db
- [ ] endpoint to add/remove entries
- [ ] sync every once in a while to the registry (or on change)

## Contract
- [x] Type `AcIssuer = AcRP = AcHolder = AccountId`
- [x] Type `CredentialSchema = string` (_JSON schema_)
### Issuer Contract
- [x] Var credentialSchemata: `Record<AcIssuer, HashSet<CredentialSchema>>`, 
- [x] Var credentialHashes: `Record<(AcIssuer, CredentialSchema), HashSet<CredentialHashes>>`
- [x] func `addCredentialSchema(credentialSchema: CredentialSchema)` (_predecessor becomes issuer_)
- [x] func `modifyCredentialHashes(schemaId: CredentialSchemaId, add: CredentialHashes[], remove: CredentialHashes[])`

### Verifier Contract
- [ ] func `cred_call(receiver: AcRP, proof: ZKProof, usedSchemata: (AcIssuer, CredentialSchemaId)[]): CrossContractCall`

## Example Contract (RP)
- [ ] Var `trustedCredentials: HashSet<(AcIssuer, CredentialSchemaId)>`
- [ ] func `on_cred_call(holder: AcHolder, journal: ZKPJournal)`
  - Type `ZKPJournal` (_Struct_)
- [ ] view func `get_script(schemataUsed: (AcIssuer, CredentialSchemaId)[])`

## Frontend
- [ ] Select script to use
- [ ] Select crendential schema to use
- [ ] Supply credentials
- [ ] Evoke local backend
### BOS integration component
- [ ] Script selection is abstracted away 

# If we have time
- [ ] public/private key verification to verify the credentialholder is the rightful holder.
