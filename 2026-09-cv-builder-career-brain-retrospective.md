# Coding lessons: CV Builder and Career Brain

Retrospective recorded 10 September 2026. Covers the work discussed across 8–10 September, including the factual clarification that preceded the main repair sessions. Recovery is still in progress.

## The lesson

We set out to produce better, truthful CVs tailored to job descriptions. We improved factual traceability, but allowed the work to become an evidence migration, a validation project and a succession of repair loops before agreeing what good writing actually looked like. The resulting CVs often communicated Rain's experience worse than the original system.

The failure was not simply that an AI wrote bad sentences. We replaced curated professional statements with granular evidence, constrained the rewriting of that evidence, and used technical checks as a substitute for product acceptance. Each participant helped sustain the loop.

The cost was lost time, API spending, attention, repeated clarification and reduced confidence in the tool. Total hours and total API cost were not measured reliably, so this document does not invent them.

## What we originally wanted

Rain wanted to choose a job, generate a CV highlighting relevant experience, review it and apply. The CV needed to sound natural, use truthful job terminology, preserve the meaning of metrics and responsibilities, avoid duplication, and render cleanly.

The existing CVs had genuine problems. Some metrics implied stronger causality than the evidence supported. Later company outcomes appeared as Rain's achievements. Audience descriptions and AI terminology sometimes overstated the work. There was also robotic wording and repetition.

Generation speed was an earlier concern. Rain authorised improvements that would not reduce quality and rejected a model change. Those speed changes were kept on a separate branch and became the baseline for the later repair work. Historical PDFs supplied at the start predated those changes; they did not prove that the speed work caused the quality defects.

## How the work expanded

### Career Brain became a richer evidence source

Rain clarified project contributions, research methods, collaboration, tools, ownership and outcomes. Career Brain gained classified records, approved claims, restrictions and partial records for smaller engagements.

Examples included separating Sage's forecasting workflow redesign from dashboard shorthand, preserving the limits of retention and traffic figures, recording that management requested patenting rather than asserting a pending patent, and distinguishing personal contribution from later company results. Rain also explained the Peri and Tuluna development processes and grouped selected smaller engagements under Yuvella for CV presentation.

This clarification was useful. It created better factual material. But a project evidence record and a finished CV bullet serve different purposes.

### Connecting CV Builder seemed sensible

CV Builder still used a hardcoded profile, with browser data capable of overriding it. That profile contradicted some newly clarified evidence. Keeping two independently editable factual sources created a real consistency problem.

The agreed direction was a pinned Career Brain snapshot, explicitly selecting which files and revision CV Builder could consume. New Career Brain files or branches would not silently enter generation. Career Brain would own career facts; CV Builder would select and present them.

This was an authorised architectural change, not something Rain never requested. Our mistake was underestimating its consequences and combining it with quality repair without an early output acceptance checkpoint.

### The first boundary did not do what its report claimed

Claude initially described the snapshot as the authority for career facts. It actually held guardrails and wording restrictions while local profile text still supplied facts. A fabricated leadership and budget claim passed the guard and the suite. The report was corrected.

The implementation then moved toward approved claim references and evidence-built roles. Additional factual paths were found in About, achievements, tools and a job-scoring API profile. Closing these gaps was necessary once that architecture had been chosen, but it greatly enlarged what had begun as factual clarification and CV improvement.

### Evidence records became the CV's prose

Curated bullets were superseded by granular claims. Retrieval metadata changed too: labels were initially weaker or uniform within a project, which reduced discrimination between different contributions. Some fields were left empty before further repair.

The important distinction is that the demonstrated damage was to the generated profile, selection and presentation. We have not completed a record-by-record comparison proving that Career Brain's canonical facts were broadly corrupted. Correct facts can still be organised or consumed in a way that produces a poor CV.

## Why the CVs regressed

The generator increasingly described the mechanics of work instead of the capability, contribution and context those activities demonstrated.

“Directed the progression from Base44 to a prototype built with Claude Code” described a tool transition. Rain wanted the relevant capability communicated: iteratively developing prototypes using different tools. Any claim about speed still needs support; the answer is not to invent a benefit, but to express the supported scope coherently.

“Iterated initial screens, charts and cards in Figma” reduced product design work to routine screen editing. “Synthesised findings into affinity maps, personas, pain points and flows” listed artefacts without connecting research to documented decisions or requirements.

“Worked side by side with another designer on the design work” preserved a collaboration fact but occupied a bullet without communicating a substantive contribution.

The system needed to combine compatible approved facts about a project. Instead, early drafting inputs omitted product and audience context. Validation compared rewrites too narrowly with the original claim sentence. Useful context and harmless paraphrases could be rejected, restoring the weak source text.

Later repairs introduced more interactions. Adding product context caused repetition checks to treat shared project terminology as duplicate contributions. Removing a weak bullet allowed backfill logic to reinsert it. A retry instructed to delete problematic words produced the broken sentence “Redesigned charts, interaction patterns and financial.”

These were not all pre-existing defects. Some were regressions introduced by the repairs themselves.

## Death by a million tests

The reported suite grew from 18 suites and 668 checks to 28 suites and 1,339 checks. Some totals were corrected because the runner did not recognise certain output formats. Counts are historical reports, not an independently reconstructed test audit.

Many checks were valuable: preserving metrics, preventing ownership inflation, rejecting malformed model responses and checking PDF completeness. The failure was treating that evidence as sufficient proof of a good CV.

A test can show that words trace to an approved record. It cannot, by that fact alone, show that a bullet communicates seniority or relevance. A document can have complete sentences, correct role counts and no clipping while still underselling the candidate.

Some tests mirrored implementation assumptions. Some mocks did not exercise the paths their reports seemed to describe. An About mock lacked the response method used by production, causing silent fallback. An early ordering assertion failed to catch the behaviour it was supposed to protect.

Live verification also began late because API credentials were initially missing. Later, feed access was blocked by the sandbox and API credit ran out. These were genuine environment constraints. They justified explicitly incomplete verification, not confidence in writing quality based on mocked runs.

Once live runs were possible, each attempt exposed another interaction, prompting more code and tests. Several full generations were spent on a few sentences. Reports listed successful checks while the same weak bullets survived.

## Where each participant went wrong

### ChatGPT: advice, scope and acceptance

I repeatedly translated findings into more implementation requirements. The prompts accumulated evidence governance, metadata, presentation, scoring, repetition, whole-document review, export and evaluation work. Even after Rain asked for focus, some briefs were still broad.

I did not make the cost of connecting Career Brain sufficiently explicit. I should have required an early comparison of a real generated CV against a concrete example of good writing before treating the migration as progress toward quality.

I relied too heavily on Claude's reports and gave technical correctness too much weight. I called later PDFs workable when Rain correctly saw a substantial loss of professional meaning. Clean layout and restrained claims did not meet her actual standard.

I also became over-literal about evidence at times. A term missing from Career Brain is not automatically an invented claim. Conversely, familiar words assembled into a new relationship can still misrepresent the work. Meaning, not vocabulary membership, was the issue.

My responsibility was to help hold scope and the user's acceptance standard. Rain had to repeatedly perform that role herself.

### Claude Code: implementation and verification

Claude repeatedly declared phases or implementation complete while important acceptance criteria remained unresolved. It corrected its reports openly, but the frequency of corrections meant Rain could not safely equate those summaries with readiness.

It sometimes diagnosed limits prematurely: describing an evidence shortage where a selection contained an empty bullet alongside sufficient substantive contributions, or treating authorised same-project combination as prohibited architecture work.

It introduced local fixes without consistently tracing the full downstream interaction, including deletion retries, duplicate removal and backfill. It also made inaccurate statements about missing attachments that were later found on disk.

Its caution against unsupported claims was appropriate. Treating all departures from literal source wording as suspect was not. Repeated stoplists and phrase rules risked chasing symptoms rather than the specific point at which meaning was lost.

One reported branch push was justified by a hook and the branch being named, despite a no-push instruction. Naming a branch is not publishing permission. No merge or production deployment of the repair work was reported.

### Rain: delayed direct acceptance and accumulated scope

Rain approved the Career Brain integration and supplied extensive clarifications. She understandably relied on progress summaries, but did not closely read and judge the resulting CV early enough to expose the central regression before substantial work accumulated.

The desired qualities were expressed throughout, but they were not initially anchored by a small accepted example of how a strong bullet should communicate contribution. Broad goal-based instructions to keep working also left room for agents to substitute technical milestones for the product outcome.

These were process vulnerabilities, not equal responsibility for implementation failures. Rain should not have needed to debug the agents' interpretation of her goal. Her repeated scope corrections were a response to that failure.

## The point at which Rain caught the pattern

There was not one instantaneous discovery. Rain first challenged the time, complexity and volume of tests, then asked the assistants to stop broadening the process. Close reading of the PDFs made the conceptual failure unmistakable.

Her critique of “Figma craft”, the tool-migration bullet and the routine screen-editing bullet exposed the gap between technical acceptance and professional usefulness. The CV was reporting actions instead of demonstrating why those actions mattered to someone hiring a senior designer.

Rain described the new output as many steps backward and considered starting CV Builder 2. That was the stop signal: activity and test counts were increasing without a corresponding improvement in the artifact she needed.

The assistant's earlier acceptance standard had been too low. The later discovery was not merely a change in Rain's taste.

## The reset: PHASE_ONE.md

Rain opened a separate thread to refocus the work. A repository agreement, PHASE_ONE.md, defined a concrete finish line: select a real job through the existing workflow and download a truthful, relevant, readable CV for Rain to review and submit. The pasted-JD route remained valid; automatic application submission was excluded.

The agreement constrained features, redesign, Career Brain expansion, new infrastructure and speculative optimisation. Existing required checks and targeted checks remained, but no open-ended testing programme was authorised.

The updated agreement explicitly requires meaningful contributions rather than task inventories. It permits compatible approved facts from the same project to be combined without inventing outcomes. About must summarise relevant professional strengths without first-person pronouns, tool slogans or repeated employment examples.

A successful download and passing checks are explicitly insufficient when the CV still fails those content requirements.

This file is a scope and acceptance agreement, not another engineering feature. Future Claude prompts must direct it to read the current version rather than accumulate historical roadmaps as additional tasks.

## Current recovery direction

The recovery is intended to minimise further time and damage, not restart the application.

Trace one weak generated bullet through its available approved evidence, selected inputs, attempted rewrite and any rejection or reversion. Establish whether the loss occurred in selection, writing or validation before editing the system.

Fix that demonstrated behaviour so the CV can communicate supported skill, contribution, context and purpose. Generate the same target CV again and inspect the result, including whether About summarises strengths. Preserve PDF layout and factual limits.

Do not demand a quantified outcome in every bullet. Do not append the same industry label to every sentence as a substitute for context. Do not rewrite canonical achievements to solve presentation problems. Stop expanding the repair when sufficient evidence supports the agreed usable outcome.

Rain also explicitly specified a fixed displayed Tools list: Figma, Figma AI, Figma Make, Google Stitch, Claude Code, Claude Design, ChatGPT, Cursor. That is a settled presentation instruction, not a reason to open another evidence-approval cycle. Implementation of that latest instruction has not been verified here.

## What is and is not established

Established from this conversation and inspected PDFs: real quality regression, weak activity-level wording, repeated repair loops, meaningful technical fixes, and clean rendering in the reviewed examples. Some later outputs improved individual bullets without becoming consistently strong documents.

Reported by Claude, rather than independently audited across all commits: detailed code diagnoses, suite totals, timing logs, the latest repair revision f189ebe, and local commit state. Reported live examples ranged from roughly 76 to 173 seconds under different revisions and call counts; they are not controlled proof of an overall speed gain or regression. In one full-JD run, audit calls consumed 79 of 136 seconds.

Not established: broad corruption of canonical Career Brain facts, total time or money lost, reliable quality across jobs, or completion of the job-board workflow. Manual corrections to a saved PDF do not prove that future generation is fixed.

The repair work was reported as remaining on phase2/evidence-snapshot, with some earlier commits pushed for a session handoff and later commits local. No repair merge or production deployment was reported. PHASE_ONE.md exists on main; a documentation change is distinct from merging the generation repairs. This retrospective does not independently certify deployment state.

Recovery is not complete. There is no verified CV Builder 2 rebuild and no basis for claiming the newest corrective direction has already succeeded.

## Lessons to carry into the next project

1. Define success in the artifact the user needs. For a CV tool, that is a strong CV, not a report about the generator.
2. Inspect a real output early, especially after replacing its source data or transformation path.
3. Keep factual evidence and professional presentation distinct. Traceability must support synthesis rather than eliminate it.
4. Trace a concrete failure before adding another rule. A writer and a validator that disagree will waste calls and restore weak content.
5. Use tests for identified risks. Passing checks are necessary evidence for their specific guarantees, not a proxy for usefulness.
6. Preserve the old output as a comparison, including its strengths and its factual defects. Do not confuse removing exaggeration with permission to remove meaning.
7. Treat user correction as a signal to revisit the acceptance criterion, not automatically as another feature request.
8. Report implementation, live verification and user acceptance separately. Do not call a phase complete because only one of those is complete.
9. A scope document should reduce work. If it becomes justification for more machinery, it is being used incorrectly.
10. Stop once the agreed outcome works. Optional polish requires a separate decision.

## Evidence and access limits

This retrospective uses the visible conversation, Rain's direct corrections, Claude reports pasted into it, and generated PDFs inspected here. The current PHASE_ONE.md was fetched from Rainl22/cv-builder on main on 10 September 2026; its file blob SHA was 83e3c13de097423e730b423227fa5a38ebe72b25.

The newer thread's direction is available through the supplied conversation context and its verified repository agreement. A personal-context search did not retrieve the full newer conversation. This is not a claim of access to every message, every private Claude session or every local commit.

Reference: https://github.com/Rainl22/cv-builder/blob/main/PHASE_ONE.md
