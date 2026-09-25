# Security Policy

This repository is XION's fork of
[`cosmos/ibc-go`](https://github.com/cosmos/ibc-go). The current XION mainnet
release uses upstream `github.com/cosmos/ibc-go/v10@v10.7.0` directly and does
not replace it with this Burnt Labs fork. This repository is therefore not a
current-mainnet asset in the
[Blockchain / DLT bug bounty program](https://github.com/burnt-labs/bug-bounty/blob/0cf55eb5b021116c884193c8a1aafac61f00697c/programs/blockchain.md).

This file summarizes repository-specific terms. Until the same terms are
published on [`burnt-labs/bug-bounty` `main`](https://github.com/burnt-labs/bug-bounty),
the canonical program for this repository is the
[pinned blockchain policy revision](https://github.com/burnt-labs/bug-bounty/blob/0cf55eb5b021116c884193c8a1aafac61f00697c/programs/blockchain.md);
where the documents differ, that revision governs.

## Reporting a Vulnerability

**Do not open a public GitHub issue for a security vulnerability.** Because
this repository is not named in the current canonical program asset list,
report it by email at [security@burnt.com](mailto:security@burnt.com).

We acknowledge receipt within **5 business days** and provide a triage decision
within **14 days**. Active exploitation, or confirmed attacker awareness of an
unpatched vulnerability, escalates the issue to Critical **response handling**
— prioritization, coordination, and disclosure timing — regardless of its
original classification. That escalation does not change the finding's
severity assessment or reward eligibility.

## Fork Scope

There is no Burnt Labs `ibc-go` fork delta in the current XION mainnet release.
If a future mainnet release reintroduces this fork, the pinned canonical
program revision above must list the deployed fork version and exact upstream
base before that delta is eligible. A finding that reproduces on the upstream
IBC code used by current mainnet belongs to the upstream project and is not
eligible under this program, regardless of its impact on XION. Report those
findings through the
[Interchain Stack security policy](https://hackerone.com/cosmos?type=team&view_policy=true)
or [security@interchain.io](mailto:security@interchain.io).

Reports about this repository may still be submitted privately by email to
[security@burnt.com](mailto:security@burnt.com), but doing so does not create
bounty eligibility or authorize production testing while the fork is absent
from current mainnet.

## Proof of Concept

An end-to-end proof of concept is required. Unit tests or keeper harnesses that
bypass transaction encoding, routing, the ante handler chain, or block execution
do not demonstrate on-chain exploitability on their own.

Run the proof of concept against a locally running XION node configured with
mainnet parameters and execute the attack through standard transaction
broadcast. Broadcast acceptance alone is not sufficient: show inclusion in a
block, the successful execution result, and the resulting state change or
security impact. For chain-halt or consensus-failure findings, instead show the
triggering transaction or input sequence, the height or round at which progress
stops or diverges, and the observed halt or failure condition; block inclusion
and successful execution are not required when the failure prevents them.

## Privileged Actor Policy

Findings are classified at **Medium at most** when the attack must begin with
control of governance, a module authority, validator or operator credentials,
or another privileged role — or requires that holder to cooperate — and the
demonstrated impact depends on that holder acting self-destructively, outside
normal operation, or in collusion while using authority the role already has.

The cap does not apply when a flaw lets an attacker who starts without that
privilege obtain it or bypass its authorization check, or lets a legitimately
held limited role exercise authority that role was not granted. Those
findings are assessed by demonstrated impact. This policy does not authorize
researchers to acquire or exercise production privileges they do not
legitimately control, or to test with production privileges they do control.

## Rewards and Severity

This repository is not currently reward eligible because the current mainnet
release does not build against it. If a future release and the canonical
program bring the fork back into scope, only **High** and **Critical** findings
will be reward eligible under the canonical terms.

## Responsible Disclosure and Safe Harbor

Do not test against XION mainnet or other production systems. Use a local
environment or infrastructure you control, do not access, modify, or disclose
user data, do not disrupt services, and keep the finding private until
disclosure is coordinated.

This policy does not authorize active testing against a production deployment.
Good-faith research in a local or researcher-controlled environment may be
reported privately by email, but bounty eligibility and safe harbor are
governed by the canonical program's current asset list. Reporting a
vulnerability encountered incidentally is always welcome.
