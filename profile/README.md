# 11/11 AI — The Execution Layer for AI

**No action executes without authorization.**

Runtime governance for AI agents: pre-execution authorization, fail-closed
enforcement, and a signed receipt for every decision. The control plane is live
and the proof is public.

## Try it

```bash
npm install @11ai/execution-governance
```

Gate any MCP server's tool calls, no code changes:

```bash
npx @11ai/mcp-gate --help
```

## Verify it yourself

One unauthenticated request returns a real, signed governance decision with its
full EA-11 evidence chain:

```bash
curl https://control.11aiblockchain.com/v1/public/evidence
```

Then check the signature on your own machine, no API key and no account:

```bash
git clone https://github.com/11-11AI/verify-11ai-proof
cd verify-11ai-proof
pip install -r requirements.txt
python verify.py
```

That verifies the **Ed25519** signature with no extra dependencies. The envelope
also carries **ML-DSA-87** and **SLH-DSA** post-quantum signatures, which are
**not** checked by default: the script reports them as skipped rather than
claiming a pass, because the envelope's own "valid" field is the server's claim
and not evidence. To check all three, `pip install liboqs-python` and re-run.

## The stack

| Layer | What it is |
| --- | --- |
| **EA-11** | the arithmetic and evidence core |
| **Execution OS** | runtime enforcement, fail-closed by default |
| **11-Lang** | the policy language |
| **SDKs** | [`@11ai/execution-governance`](https://www.npmjs.com/package/@11ai/execution-governance) and [`@11ai/mcp-gate`](https://www.npmjs.com/package/@11ai/mcp-gate) on npm |

This organisation publishes the SDK, the MCP proxy, the receipt format and the
doctrine. The policy core and the hosted control plane stay closed.

## The record

| | |
| --- | --- |
| SDK and MCP proxy | [execution-governance](https://github.com/11-11AI/execution-governance) — Apache-2.0 |
| Verify a live decision | [verify-11ai-proof](https://github.com/11-11AI/verify-11ai-proof) |
| Doctrine | [execution-governance-doctrine](https://github.com/11-11AI/execution-governance-doctrine) — eight principles, each with its verification path |
| Live proof | [control.11aiblockchain.com/proof](https://control.11aiblockchain.com/proof) · [health](https://control.11aiblockchain.com/health) |
| Research corpus | [DOI-registered records on Zenodo](https://zenodo.org/communities/11-11-ai/records) |
| Contact | [11aiblockchain.com](https://11aiblockchain.com) · quantum@11aiblockchain.com |

Cryptography, named: Ed25519 · SHA3-512 · BLAKE2b-512 · ML-DSA-65 (FIPS 204) ·
SLH-DSA / SPHINCS+ (FIPS 205). Fail-closed by default.

*© 2026 11 AI Blockchain Developments LLC · Apache-2.0 for released code ·
Patent pending*
