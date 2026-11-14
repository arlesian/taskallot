# Shared writing profile

This profile governs TaskAllot proposals, messages, reports, status text, and generated documentation. It implements the user's preference for approximately 80% ASD-STE100 adherence.

That preference means selective, practical adoption of STE principles. It is not a compliance score, measured percentage, or certification. [Source notes](../../docs/design-sources.md#writing-and-engineering) identify the reference and access limits.

## Reviewable rules

| Area | Rule |
| --- | --- |
| Instructions | Aim for at most 20 words per sentence. Give one instruction per sentence. |
| Descriptions | Aim for at most 25 words per sentence. Keep one main subject per sentence. |
| Actors | Use active voice and identify who acts. |
| Terms | Use consistent terms with one intended meaning. Follow the [shared vocabulary](../../controller/task-assessment.md). |
| Prose | Use complete sentences where prose requires them. Compact table cells and labels may be fragments. |
| Technical fidelity | Keep technical names, commands, paths, code, and identifiers exact. |
| Relevance | Include only information that supports a decision, action, or assessment. |
| Presentation | Prefer compact tables for assignments, estimates, and status. Link detailed evidence. |
| Tone | Remove filler, praise, repeated conclusions, and routine narration. |
| Material facts | Preserve risks, failed checks, blockers, and uncertainty. Concision must not hide them. |

Review long sentences and ambiguous terms manually. Do not invent an automatic “80% compliance” measure. A longer sentence is acceptable when splitting it would change meaning.

## Fidelity exceptions

Preserve exact errors, quotations, code, and structured data. Do not rewrite their contents to meet sentence or vocabulary targets. Put explanations beside the preserved material.

An exact identifier can use words outside an STE dictionary. Quoted source text needs attribution. Source accuracy and required technical meaning take precedence over stylistic targets.

## Short software glossary

| Term | Intended meaning |
| --- | --- |
| Patch | A proposed source change tied to an artifact reference. |
| Check | An observation compared with an explicit expected result. |
| Self-check | A developer's check of its own work. |
| Blocker | A condition that prevents the next required action. |
| Replay | Another delivery or attempt of the same logical operation. |
| Token | A provider-accounted text or reasoning unit; category visibility depends on the host. |
| Reservation | Budget held for estimated remaining work, as defined in [scheduling](../../controller/session-scheduling.md). |

Add project-specific terms only when ambiguity affects decisions. Keep the glossary short. Repository-specific instructions take precedence over generic guidance.
