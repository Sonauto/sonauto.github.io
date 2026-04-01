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

V3-Preview introduced real-time streaming and longer coherent structures up to 4.5 minutes. V3 was intended to be the full release, with a major push on emotional expressiveness — the ability to generate music that more accurately captures the mood described in a user's prompt.

To measure this, we developed an internal benchmark called EmoAlign, which scores the correlation between a prompt's described emotion and the affective response of human listeners. V3-Preview scored 0.61. Our target for V3 was 0.70.

V3 scored 0.97.

At first, we were thrilled. Then we started looking more carefully.

## What we observed

In a controlled A/B study with 40 internal participants, V3 users spent an average of 2 hours and 47 minutes per session compared to 38 minutes for V3-Preview. They entered what we've come to call "refinement spirals" — generate, tweak the prompt, generate again — averaging 23 iterations per session. 78% reported the persistent feeling that they were "almost there," that the next generation would be the perfect version of the song they were imagining.

31 of 40 V3 participants reported involuntary recall of generated melodies for hours or days afterward — humming songs that don't exist. An external auditory cognition researcher at Stanford noted the effect was consistent with involuntary musical imagery (INMI), but at unusual intensity.

Most concerning: V3's emotional expressiveness creates a feedback loop. Users who provide emotionally specific prompts — personal memories, relationships, losses — receive highly resonant output, which makes them provide *even more* emotionally specific prompts next time. The model isn't "trying" to create dependency. But when you optimize hard enough for emotional resonance, you converge on outputs that interact with human psychology in ways that feel less like a tool and more like a relationship.

We asked users to stop using V3 for 72 hours after a multi-hour session. 60% reported cravings to return to the platform. Several described "flatness" when listening to non-generated music. One participant told us — and this is the sentence that made us stop — "Regular music doesn't hit the same anymore. It's like it's not *about* me."

We commissioned third-party audio analysis from IRCAM to check for unusual spectral properties — subsonic frequencies, binaural patterns, anything acoustic. They found nothing. V3 outputs are spectrally normal. The effect is entirely compositional and melodic.

## The decision to pause

We discussed whether guardrails — session time limits, cooldown periods — would be sufficient. We decided they address symptoms, not the underlying dynamic. We're not comfortable shipping a model that creates a measurable psychological pull toward compulsive use.

This was not an easy call. V3 is, by every conventional metric, our best model ever. Hayden and I started Sonauto because we love music and wanted to make it accessible to everyone. We did not start it to discover that the line between 'personalized' and 'addictive' is thinner than anyone in this industry wants to admit.

V3-Preview remains fully available, unlimited, and free. We'll publish a full technical report once our investigation is complete.

We'll keep building. But we'll do it carefully.

— Ryan

<p><img src="{{ '/madeforme.png' | relative_url }}" alt="Made For Me"></p>
