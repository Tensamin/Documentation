---
title: "Privacy Policy"
lastUpdated: 2025-11-15
---

### 1. Who we are  
Tensamin is an open-source, end-to-end encrypted messaging platform composed of the public web client, the Authentication Server, Omega, Omikron, and Iota nodes described above.

### 2. Data we collect & purpose

| System                | Data elements                                                                                                                                                                  | Purpose & lawful basis                                                                                                                      |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Authentication Server | UUID, username, display name, avatar URL, “about” text, status, public key, hash of private key (never the key itself), subscription tier & expiry, account creation timestamp | Account provisioning, authentication, subscription management (contractual necessity)                                                       |
| Client                | Locally cached profile records, IndexedDB-stored community/chat metadata, call settings, language/theme preferences                                                            | Provide UX offline resilience and personalization (legitimate interest; stored only on user device)                                         |
| Client Calls          | WebRTC SDP blobs, ICE candidates, call state flags, per-user stream status                                                                                                     | Establish peer-to-peer media connections (contractual necessity)                                                                            |
| Omega                 | User UUID ↔ Iota ID ↔ Omikron ID mapping, last reported status                                                                                                                 | Route traffic to the correct Omikron/Iota and show presence (contractual necessity)                                                         |
| Omikron               | Iota IDs, user IDs associated with an Iota session, CommunicationValue payload metadata (message IDs, sender/receiver IDs, timestamps, stream toggles)                         | Broker encrypted payloads between clients/Iotas while hiding IPs (contractual necessity)                                                    |
| Iota                  | Encrypted chat content, community definitions, voice room membership and state, contact lists                                                                                  | Store user-owned content under the operator’s control; content decryption keys remain with end users (contractual necessity / user control) |

We do **not** run analytics or behavioural tracking anywhere in the workspace.

### 3. How we process and transmit data
- All API calls use HTTPS/WSS.  
- Omikron ensures IP anonymisation by relaying communication so that Omega/Iotas only see UUID metadata.  
- WebRTC media flows are encrypted end-to-end between peers.  
- Authentication credentials are never exposed to other users; the client retrieves account data only after authenticated fetches.

### 4. Storage & retention
- Authentication Server data persists until the account is deleted; subscription/grant logs may be retained for billing disputes.  
- Omega’s MySQL table keeps routing/status entries until systems remove an Iota.
- Omikron caches user metadata for 90 days and caps payload history.
- Iota storage belongs to the operator; by design users can self-host or delete their instance to wipe history.  
- Local browser caches live solely on the user’s device; clearing browser storage removes them.

### 5. Sharing & disclosures
- We share profile metadata and routing info internally between Authentication Server, Omega, Omikron, and Iota strictly to deliver the service.  
- We do not monetise or sell personal data.  
- Third-party processors are limited to infrastructure hosts you choose (e.g., your own Iota/Omikron deployment). Any additional processors must provide equivalent safeguards.

### 6. Security measures
- TLS everywhere (client endpoints and WSS).  
- Database credentials isolated via environment files (.env, `Omega/src/main/java/dev/tensamin/config/ConfigManager.java`).  
- CommunicationValue validation and signature checks inside Omikron/Iota modules prevent spoofing (call_connection.rs, `Iota/src/auth/crypto_helper.rs`).  
- Sensitive keys remain client-side; only salted hashes reach servers.

### 7. User rights
Depending on jurisdiction, you may request access, correction, portability, or deletion of Authentication Server data. Because chats are stored on the Iota you or your community controls, deletion requires contacting that operator (or wiping your own node). Requests can be initiated via <a href="mailto:support@tensamin.net" >support@tensamin.net</a> or through community administrators.

### 8. International transfers
Hosting choices (self-hosted Iota or third party operated nodes) determine data locality. When using our infrastructure, data may be processed in the EU; we rely on standard contractual safeguards where applicable.

### 9. Contact
For privacy inquiries, email <a href="mailto:support@tensamin.net" >support@tensamin.net</a>.