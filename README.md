# homebrew-nimbus

Official Homebrew tap for **[Renmy](https://renmy.net)** (formerly Nimbus) — run Salesforce Apex tests locally, without an org.

---

## The problem

Running Apex tests requires a connected Salesforce org. That means waiting for scratch org provisioning, managing org pools in CI, debugging shared-org pollution, and spending days onboarding new developers before they can run a single test.

Meanwhile, every other language just runs tests locally.

## What Renmy does

Renmy runs your Apex tests on your machine — no Salesforce connection, no Docker, no setup beyond pointing it at your SFDX project.

```
❯ renmy test "*"

  ✓  AccountServiceTest.testCreateAccount     12ms
  ✓  AccountServiceTest.testBulkInsert         8ms
  ✓  CalculatorTest.testAddition               2ms
  ✓  CalculatorTest.testDivision               3ms
  ✓  AccountTriggerTest.testBeforeInsert       15ms
  ✓  AccountTriggerTest.testAfterInsert        11ms

  6 passed · 0 failed · 51ms total
```

Real SOQL. Real triggers. Real DML. Backed by an embedded PostgreSQL database — not a simulated environment.

## What it supports

| Area | Coverage |
|---|---|
| Language | Classes, interfaces, enums, inheritance, generics, exception handling |
| Data | SOQL, DML (insert, update, delete, upsert), bind variables, aggregates, relationships |
| Automation | Before/after triggers, record-triggered flows, platform event flows |
| Testing | `@isTest`, `@testSetup`, `System.assert`, Test.startTest/stopTest, per-test isolation |

## Why developers use it

- **Instant feedback** — tests run in milliseconds, not minutes
- **No org dependency** — works offline, works on CI without DevHub or scratch org pools
- **JUnit XML + Cobertura coverage** — plug into GitHub Actions, SonarQube, Codecov like any other language
- **AI-agent ready** — fast enough for write-test-fix loops with Claude Code, Cursor, or Copilot

---

## Install

```sh
brew tap renmy-solutions/nimbus
brew install renmy-solutions/nimbus/renmy
```

The tap keeps the repository name `homebrew-nimbus`. The formula installs `renmy` and a `nimbus` link to it, so the `nimbus` command keeps working.

## Upgrade

```sh
brew upgrade renmy
```

An existing install of the `nimbus` formula moves to `renmy` with `brew upgrade nimbus`; the `nimbus` command stays in place.

## Verify

```sh
renmy --version
```

---

[Documentation](https://renmy.net/docs) · [Website](https://renmy.net) · [Releases](https://github.com/renmy-solutions/renmy/releases)
