---
name: test-lifecycle
description: Use when planning, introducing, maintaining, reviewing, or retiring tests or their explanatory documentation. Govern their roles and written accountability.
---

# Test Lifecycle

Use settled requirements and product design for expected behavior. When work affects a test or its explanation, apply the rules for its current lifecycle stage, including transfer of documentation ownership and retention or retirement when due.

## Assign written accountability

Give every test a concise written explanation of its purpose, expected result, verification method, and lifecycle classification.
Use the repository's existing document locations and format. Identify the corresponding tests or manual procedures from the documentation side, at the granularity of a case or coherent group whose explanation covers every member.

Before introducing a test, place its explanation and applicable completion or retirement condition in the test plan.
When introducing it, make the test design responsible for the actual verification method, why that method is sufficient, and its correspondence to the implemented test or manual procedure.
Transfer the current explanation to the test design and use references where the plan still needs it; maintain one authoritative explanation for each current test.
Here, test design means documentation of the tests themselves; product design remains the authority for the behavior being tested.

When maintaining an existing test, use its current test design and apply known retirement conditions first. Recover missing explanations for tests whose role continues from settled requirements, design, and the test's actual behavior.
Update the test design with changes to retained tests and remove references to retired tests from current documentation. Existing planning history needs no new deletion record.

## Classify the test's role

Choose the role from the reason verification is needed:

- **Implementation-time verification** establishes facts needed to finish the current implementation, investigation, or transition. Define the concrete completion condition in the plan and delete the test when that condition is met. Running it automatically during development does not make it a continuing CI test.
- **Manual testing** provides verification through deliberate human execution or judgment. Record the execution trigger, prerequisites, procedure, and expected result in the test design. Keep this verification outside automatic CI execution and assess completion from the manual result.
- **CI testing** continually protects against a concrete unintended change. Record the change that could cause the failure, the behavior that would break, how the test detects it, and the contract-preserving variations it accepts.

Classify a defect reproduction by its continuing role using these same criteria.
For staged implementation, give substitute tests an explicit replacement condition and keep the complete verification obligation with its owner until it is satisfied.
Keep manual verification obligations visible when reporting completion; a successful CI run establishes only what its tests check.

## Admit and retain CI tests for concrete risks

Add or retain a CI test only when a concrete mechanism for unintended change warrants continuing protection and its assertions detect the resulting violation.
Use the actual implementation and dependency paths to assess that mechanism. Importance, a coverage target, and hypothetical future usefulness alone do not establish it.
Where unintended change has no identified mechanism, use the verification needed to complete the current work without creating a continuing CI obligation.
Reuse existing tests when they already detect the same violation; add separate coverage for a distinct failure they would miss.

Assess retention by the current risk, even when the product contract continues to exist.
When that protective role ends, retire the test under the retirement rule below.

## Preserve the contract while allowing extension

Make CI assertions reject violations of the protected contract and accept extensions and other changes permitted by it.
Assert the required properties and relationships. Fix complete collections, exact representations, ordering, counts, or wording only when the contract requires them.
For example, a test for required API fields accepts additional optional fields when the contract allows them and fails when a required field disappears or changes meaning.

When an implementation change breaks a test while the contract is unchanged, determine whether the implementation violates the contract or the test fixes an incidental detail.
Repair the violating implementation or narrow the incidental assertion while preserving detection of the intended failure.
Do not rewrite expected results merely to match each new implementation.
When an intentional contract change is settled by its owning workflow, update the test plan or test design according to introduction status, then align the affected verification.

## Retire tests at the end of their role

Once a planned completion or replacement condition is met, delete the test and any support used only by it, and remove obsolete registration and current documentation references.
Apply the same cleanup when reassessment establishes that an existing test's role has ended.
Check the condition and perform the cleanup as fulfillment of the plan. Do not require a deletion rationale, retirement report, or renewed approval.
Do not extend a completed test's lifetime for possible future usefulness.

## Responsibility boundary

This skill owns lifecycle classification, written accountability, CI admission and retention, and retirement conditions.
[Test-evidence planning](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/planning/SKILL.md) owns concrete cases and expected outcomes; [test-evidence implementation](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/implementation/SKILL.md) owns executable tests and their corresponding test design.
Test-evidence review and remediation own evidence sufficiency and repair within the selected lifecycle.
[CI execution efficiency](https://github.com/supersovaa/ci-efficiency/blob/main/skills/execution/SKILL.md) owns execution selection and configuration; [test execution budget](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/execution/SKILL.md) owns necessity and bounded execution of costly verification.
Product requirements, product design, implementation planning, and implementation execution remain with their owning workflows.
