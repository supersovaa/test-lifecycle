# Test Lifecycle

A lightweight skill for managing why tests exist, how long they remain useful, and which document explains them.

## Core idea

Every test has a written purpose and a useful lifetime.
The test plan owns that explanation before introduction; the test design owns it after introduction.
CI protects against concrete unintended changes while allowing extensions permitted by the governing contract.

## When to use

Use this skill when planning, introducing, maintaining, reviewing, or retiring tests and their explanatory documentation.

## Responsibility

`test-lifecycle` owns test classification, written accountability, CI admission and retention, and retirement conditions.
It applies to implementation-time verification, manual tests, and CI tests within the existing work scope.
The operational rules are in [SKILL.md](SKILL.md).

## Adjacent responsibilities

- [requirement-driven-testing](https://github.com/supersovaa/requirement-driven-testing) owns concrete test cases, executable evidence, evidence review and repair, and the execution budget for costly verification. Its workflows apply this skill for lifecycle decisions and documentation ownership.
- [ci-execution-efficiency](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md) owns CI execution selection and configuration for admitted tests.
- Requirement and design workflows own the product contracts that tests verify.
- Implementation workflows own production changes and their completion conditions.

## Installation

Place this repository's `SKILL.md` at `<skills-root>/test-lifecycle/SKILL.md` in the target agent's skill directory, or install the repository through that skill system's repository installation mechanism.

For repository-specific routing, link [SKILL.md](https://github.com/supersovaa/test-lifecycle/blob/main/SKILL.md) from the existing guidance for test planning, implementation, maintenance, and review. Keep the detailed rules in this public definition.
