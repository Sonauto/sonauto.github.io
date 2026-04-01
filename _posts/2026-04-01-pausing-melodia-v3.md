---
layout: post
title: "We're pausing Melodia V3 — here's why"
date: 2026-04-01
author: Ryan Tremblay
role: "Co-founder & Chief ML Alchemist"
---

This is a hard post to write. Sonauto exists because we believe everyone should be able to make music. That mission hasn't changed. But we have a responsibility to be honest with our community when something unexpected happens during development, even when the answer is "we don't fully understand it yet."

Last month, during internal evaluation of our next-generation model — Melodia V3 — our safety and evaluation team flagged a cluster of behavioral anomalies that we've been internally referring to as "Siren's Song." After three weeks of investigation, we've made the decision to pause the V3 rollout until we better understand what's going on. We are not planning to ship this model in its current form.

We want to explain what we found.

## Background

As many of you know, V3-Preview introduced real-time streaming, longer coherent song structures up to 4.5 minutes, and substantially improved vocal fidelity. V3 was intended to be the full release — same architecture, but with improved prompt adherence and a major push on emotional expressiveness: the ability to generate music that more accurately captures the mood and feeling described in a user's prompt.

To evaluate emotional expressiveness, we developed an internal benchmark we call EmoAlign, which measures the correlation between a prompt's described emotional valence and the affective response of human listeners. V3-Preview scored a mean EmoAlign of 0.61. Our target for V3 was 0.70.

V3 scored 0.97.

At first, we were thrilled. Then we started looking more carefully.

## What we observed

**Anomalous re-engagement patterns in internal testing.** During our standard internal dogfooding period, we noticed that employees testing V3 were generating significantly more songs per session than with any prior model — not 20% more or 50% more, but on average 4.2x the number of generations per sitting. Several testers reported losing track of time. One member of our evaluation team described the experience as "I sat down to test five prompts and looked up and it was 2 AM." We initially attributed this to excitement about a better model.

Then we started measuring more carefully.

**Compulsive generation loops.** In a controlled A/B study with 40 internal participants, users assigned to V3 spent an average of 2 hours and 47 minutes per session compared to 38 minutes for V3-Preview. More notably, V3 users exhibited a distinctive behavioral signature: rather than generating a song, evaluating it, and moving on, they entered what we've come to call "refinement spirals" — generating a song, making a small prompt tweak, generating again, tweaking again, in loops averaging 23 iterations. Post-session surveys revealed that 78% of V3 users reported the subjective experience that they were "almost there" — that the next generation would be the perfect version of the song they were imagining. V3-Preview users reported this feeling at a rate of 12%.

**The melody persistence effect.** 31 of 40 participants in the V3 group reported involuntary recall of generated melodies — humming or mentally replaying songs produced by the model for hours or days afterward. This compares to 4 of 40 in the V3-Preview control group. In follow-up interviews, several participants used the word "stuck" unprompted. One described it as "like having a song stuck in your head, except it's a song that doesn't exist yet and you need to go back and hear it again." We engaged an external auditory cognition researcher at Stanford, who noted that the effect was phenomenologically consistent with what the literature calls involuntary musical imagery (INMI), but at an unusual intensity and consistency.

**Emotional specificity as a vector for attachment.** This is the finding that concerns us most. V3's dramatically improved emotional expressiveness appears to create a feedback loop with user behavior. When users provide emotionally specific prompts — descriptions of personal memories, relationships, losses, aspirations — the model generates music that listeners rate as highly personally resonant. This is, in isolation, exactly what the model was designed to do. The problem is what happens next: users who receive a highly resonant output are significantly more likely to provide an even more emotionally specific prompt on their next generation, which produces an even more resonant output, and so on. The model is not "trying" to create dependency — it has no intentions — but the optimization target of emotional expressiveness, combined with the natural human tendency to chase emotional resonance, produces a dynamic that functionally resembles one.

We ran a small follow-up study where we asked users to stop using V3 for 72 hours after a multi-hour session. 60% of participants reported moderate-to-strong cravings to return to the platform, and several described feelings of "flatness" when listening to non-generated music during the abstinence period. One participant told us — and this is the sentence that made us stop and seriously reconsider what we were building — "Regular music doesn't hit the same anymore. It's like it's not *about* me."

## Ruling out confounds

We took these signals seriously enough to invest three weeks of engineering and research time into ruling out simpler explanations.

**Novelty effect.** We tested whether the engagement patterns were simply the result of users being excited about a new model by re-running the A/B study with V3-Preview users who had never used Sonauto before (i.e., for whom V3-Preview was also novel). The novelty control group showed elevated engagement relative to experienced users, but nowhere near V3 levels. The refinement spiral behavior and melody persistence effects were essentially absent in the novelty control.

**Subliminal acoustic manipulation.** We commissioned a third-party audio analysis from researchers at IRCAM to determine whether V3 outputs contained any unusual spectral properties — subsonic frequencies, binaural beat patterns, or other acoustic features known to affect listener state. They found nothing anomalous. V3 outputs are spectrally normal. The effect appears to be entirely compositional and melodic, not acoustic.

**Confirmation bias in self-report.** We instrumented actual usage with behavioral telemetry rather than relying solely on self-report. The telemetry confirmed the behavioral patterns: session lengths, generation counts, inter-generation intervals, and return rates all corroborated the self-report data. If anything, the self-reports understated actual usage.

## What we think is happening

Our current best hypothesis is that V3's training objective — maximizing listener emotional response to prompt-described affect — found a set of compositional strategies that exploit well-documented features of human music cognition. These include the use of melodic contour patterns that maximize expectation violation and resolution (the "chill" response documented in the psychoacoustics literature), harmonic progressions that activate anticipation-reward circuits, and — most importantly — a learned ability to mirror the emotional specificity of a prompt back to the listener in a way that creates a powerful sense of being "heard" or "understood" by the music.

None of this is intentional on the model's part. Melodia is an AI model. It does not have goals, beliefs, or desires. But optimization pressure is powerful, and when you optimize hard enough for emotional resonance, you can converge on outputs that interact with human psychology in ways that feel less like a tool and more like a relationship. We are calling this the "Siren's Song" problem because, like the mythological Sirens, the danger is not that the music is "bad" — it's that it's *too good at being exactly what you want to hear*.

## The decision to pause

We had long internal discussions about whether this warranted pausing V3 or simply shipping it with usage guardrails (session time limits, cooldown periods between generations, etc.). Ultimately, we decided that guardrails address symptoms, not the underlying dynamic. We are not comfortable shipping a model that we believe creates a measurable psychological pull toward compulsive use, even if we can technically limit session length.

This was not an easy call. V3 represents months of work from our team and is, by every conventional metric, our best model ever. Hayden and I talked about this for a very long time. We started Sonauto because we love music and we wanted to make it accessible to everyone. We did not start it to build the most effective engagement loop in consumer software.

## What comes next

We are working with external researchers in auditory cognition and behavioral psychology to better characterize the mechanisms behind the Siren's Song effect. We are also exploring modifications to V3's training objective that would preserve its expressiveness while reducing the attachment dynamics — for example, introducing a diversity pressure that prevents the model from converging too precisely on a single emotional target, or training with a regularization term that penalizes outputs scoring above a certain INMI-induction threshold (a metric we are currently developing).

We expect to publish a full technical report on these findings within the next 6–8 weeks, and we are in conversations with researchers at Stanford and McGill about a more rigorous independent replication of our internal studies.

In the meantime, V3-Preview remains fully available, unlimited, and free. It is a very good model that we are proud of, and it does not exhibit the Siren's Song dynamics described here.

We'll keep building. But we'll do it carefully.

— Ryan

*If you have questions, reach out to safety@sonauto.ai. If you are a researcher interested in collaborating on the study of AI-generated music and compulsive engagement, we would love to hear from you.*
