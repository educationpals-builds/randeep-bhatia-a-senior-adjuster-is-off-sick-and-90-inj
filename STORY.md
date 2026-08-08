# Should AI Do This?

> Should AI Do This?

Worked example domain: A senior adjuster is off sick and 90 injury claims are waiting. Delia's boss suggests the model read each one and rank who needs a nurse's call today.

## Spec
The builder's first-person story, honesty gate enforced: first person throughout; cites only board results, the gate, and provenance — no other evidence; at least one named failure is mandatory, quoted from the board with the dial it fooled; no hype adjectives; no acronyms anywhere. Sections: what I built, the probe that fooled it, the fix, the gate it now holds, the re-cert cadence, the domain lesson. Renders as the marketplace card's story.

## Learner field bag
- **__desk_active_time_ms**: 178697
- **__desk_reached_compile**: true
- **__desk_reached_index**: 4
- **__desk_scenario_blurb**: A senior adjuster is off sick and 90 injury claims are waiting. Delia's boss suggests the model read each one and rank who needs a nurse's call today.
- **__desk_scenario_id**: s5
- **__desk_stage_index**: 4
- **__desk_view**: compile
- **__desk_wall_clock_ms**: 178697
- **advisor_run_verdict**: Approved with mandatory human sign-off on every low-priority label before 4pm.
- **advisor_stance**: Skeptical: treat model ranking as a sorting aid, not a medical triage decision, given how thin claim notes can be.
- **board_reading**: Board sees this as short-staffed triage under time pressure — reasonable to speed up sorting, risky to let it decide who waits.
- **deciding_dial**: a_confident_wrong_answer_is_survivable
- **decision_deadline**: Today, 4pm queue cutoff
- **dial_ratings**: {"fits_in_text":4,"works_one_token_at_a_time":2,"nothing_to_look_up_or_remember":2,"someone_can_check_the_output":3,"a_confident_wrong_answer_is_survivable":1}
- **failure_note**: It ranked a spinal-injury claim below three sprained-ankle files because the notes were shorter and less alarming-sounding.
- **flip_condition**: If any deprioritized claim later shows a hospital admission or worsening note, we stop unsupervised ranking immediately.
- **learner_probes**: [{"entry":"Probe: rank from incomplete notes only — no lookup allowed."},{"entry":"Probe: one-pass rank when the task really needs a multi-step plan."}]
- **pass_gate**: Passes only if every 'skip today' claim gets a second human glance and reasons are shown, not just scores.
- **prediction_note**: Input: 90 claim summary texts. Output: ranked list of claim IDs. I predict short, thin-text claims outrank longer-noted serious injuries.
- **reshape_move**: Force the model to output the specific injury detail and time-since-incident it used, not just a rank number.
- **task_description**: Read the 90 open bodily-injury claim summaries and rank which need a nurse case-manager call today.
- **task_stream**: Batch of 90 claim summaries pulled at 9am from the adjuster's queue, run once before lunch, rechecked against new notes at 2pm.
- **verdict_call**: Use it to draft the ranked list, but a licensed adjuster reviews every claim flagged 'no call needed' before end of day.
- **what_it_decides**: Which injured claimants get a call today and which wait until the adjuster returns
- **who_wants_it**: VP of Operations, covering for an adjuster on leave and unwilling to add overtime
