# Guide to Generative Video with **Google Veo 3** & **Flow**

*Last updated: 26 May 2025*

---

## 1. Orientation

Google’s **Flow** platform couples a prompt‑driven interface with Google DeepMind’s most advanced video models.  **Veo 3** is the flagship model (native 1080p, optional audio), while **Veo 2** remains available for lower‑cost iterations and specialist tools such as camera‑path control and object removal.  Flow is not a linear editor; think of it as an idea generator that outputs **8‑second clips** you later assemble into longer scenes.([theverge.com](https://www.theverge.com/news/670181/google-deepmind-ai-videos-app-flow-veo-3-2-imagen-4-io-2025))

### Plan Tiers & Monthly Allowances

| Plan                | Included generations                         | Veo version access                  | Typical monthly credit pool\* |
| ------------------- | -------------------------------------------- | ----------------------------------- | ----------------------------- |
| **Google AI Pro**   | \~100 Flow generations                       | Veo 2 (default) & time‑shared Veo 3 | 12 500 credits                |
| **Google AI Ultra** | Highest limits, priority Veo 3, native audio | Veo 3 (priority) + Veo 2            | 12 500 + bonus\*              |

> \*Google currently prices each Veo 3 generation at **150 credits**. Credits and allowances are revised periodically—check the *Google AI Plans* dashboard before budgeting.([datacamp.com](https://www.datacamp.com/tutorial/veo-3), [theverge.com](https://www.theverge.com/news/670181/google-deepmind-ai-videos-app-flow-veo-3-2-imagen-4-io-2025))

---

## 2. Working in 8‑Second Building Blocks

1. **Think in Shots, not Scenes.**  Every Flow render is exactly eight seconds.  Write prompts that *begin* and *end* cleanly—hard cuts, camera whip‑pans, or a natural pause help you stitch clips later.
2. **Continuity Costs Credits.**  Character appearance can drift between clips.  Budget extra iterations for key characters (“character studies”) in a neutral space; reuse frames from these studies as visual references in subsequent prompts.
3. **Interview Formats Are Easy Wins.**  Talking‑head or street‑vox‑pop setups avoid cross‑clip continuity because each clip is self‑contained.

---

## 3. Prompt Architecture

Veo 3 responds best when a prompt reads like a *tight, hyper‑specific screenplay.* Combine Dave Clark’s “cinematic hook” approach with our **S‑C‑A‑S‑M‑C** scaffold for maximum control.

| Section           | Purpose                                                                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **S Subject**     | Character(s), props, wardrobe, distinctive traits.                                                                                        |
| **C Context**     | Time, place, atmosphere, genre.                                                                                                           |
| **A Action**      | On‑screen events in linear order; include dialogue in quotes.                                                                             |
| **S Style**       | Mood, colour palette, film stock, era references.                                                                                         |
| **M Motion**      | **(i) Subject motion** – what the actors or objects do.  **(ii) Camera motion** – dolly, pan, handheld, crash‑zoom. *Keep them distinct.* |
| **C Composition** | Shot size & framing (close‑up, medium, wide), rule‑of‑thirds, leading lines, depth‑of‑field instructions.                                 |

### Dave Clark’s Prompt Rules (integrated)

1. **Lead with a Cinematic Hook.**  One sentence that nails *mood + primary shot type*: e.g. *“A tense, noir‑lit close‑up of a detective’s trembling hands under flickering neon.”*  This primes Veo’s look‑up tables.
2. **State Shot Size Early.** *Close‑up / medium / wide / aerial.*  Veo obeys better if the camera’s starting vantage is explicit.
3. **Write What the Lens Sees & Feels.**  Assume your AI cinematographer has *zero* implicit context.  Spell out lighting ("chiaroscuro side‑light"), colour temps ("sodium‑orange rim"), and implied sound beds ("distant siren wailing").
4. **Separate Motion Channels.**  Describe subject movement and camera movement in distinct clauses to avoid unintended shake or drift.
5. **Embed Composition Language.**  Phrases like *"rule‑of‑thirds placement, horizon on upper third, leading lines converge centre‑frame"* guide Veo’s internal layout engine.
6. **Use Strong Verbs, No Filler.**  “Slams,” “glides,” “billows” outperform “is,” “seems,” or vague adverbs. Aim for concise, evocative sentences.
7. **Avoid Temporal Connectors in Stand‑Alone Clips.**  Words like “then,” “after that,” can confuse isolated generations.  Keep each eight‑second prompt self‑contained.
8. **Re‑establish Visual Anchors Each Clip.**  Because Veo lacks memory, restate critical details (wardrobe colour, lighting scheme) at the top of every prompt to maintain continuity across shots.

> **Tip:** Draft in blocks, then collapse to one paragraph for Flow. Veo’s parser respects punctuation more than line breaks.

**Prompt Template Example (final one‑paragraph form)**

```
A tense, noir‑lit close‑up of a detective’s trembling hands under flickering pink‑blue neon strip lights. Rain‑speckled trench‑coat sleeves, cigarette smoke curling upward. Context: midnight alley behind a 24‑hour diner, puddles reflecting signage. Action: hands fumble a .38 revolver, thumb pulls back the hammer, detective whispers "one last chance"; raindrops patter loudly. Style: Blade‑Runner‑esque retro‑futurist melancholy, palette of desaturated cyans and magentas. Subject motion: subtle tremor; Camera motion: locked‑off tripod with 5% micro‑jitter handheld feel. Composition: rule‑of‑thirds left‑hand placement, shallow f/1.4 depth, neon bokeh halos.
```

---

## 4. Practical Workflow

1. **Storyboard Early.**  Sketch beats in a traditional storyboard or generate stills with Imagen 4 or any image model; Flow’s SceneBuilder lets you drop placeholders before you spend video credits.
2. **Character Studies.**  Render 2–3 eight‑second loops of each main character walking, turning, or speaking neutral phrases.  Screenshot representative frames; paste those frames into later prompts with *“match appearance to reference frame”* language.
3. **Pre‑Upscale Trick.**  If you plan to start a clip from a still image (for example, a book on a shelf), run that still through **Magnific** or another upscaler *before* feeding it into Flow.  Higher‑resolution seed frames translate into sharper motion footage downstream—Javi Lopez used this tactic for the dragon‑in‑7‑Eleven scene.
4. **Frames‑to‑Video Interpolation (Veo 2).**  When audio is non‑critical, drop to Veo 2 and supply a start‑frame and end‑frame; Flow will interpolate motion.  This is cheaper (≈ 60 credits) but outputs silent clips and may soften detail.
5. **One Render at a Time.**  Flow offers 1–4 variations per prompt.  Generating four clips costs 4× the credits; unless you need ideation breadth, stick to one and iterate.
6. **Download & Edit Externally.**  SceneBuilder is convenient but limited.  Stitch clips, add titles, or stabilise footage in Resolve, Premiere, **CapCut** (Lopez’s choice), or even iMovie.

---

## 5. Audio, Music & Subtitles

* **Audio is Veo 3‑only.**  You may receive silent clips if demand on GPUs is high; click the muted‑speaker icon first—Flow often ships audio but defaults to mute.  If audio is truly missing, re‑queue the job.
* **Persistent Subtitles Glitch.**  Veo currently insists on burning English subtitles into many dialogue clips.  Workaround: append *“without subtitles, cinematic clean frame”* in the Composition block and re‑render.  Success rate ≈ 60 %.
* **Score Your Clips.**  Lopez generated a Back‑to‑the‑Future‑style synth score in **Udio** after testing **Suno**.  Prompt example:

  > Epic cinematic orchestral and synthesizer piece with a nostalgic 1980s sci‑fi vibe … mystery inside a Seven Eleven at night.
  > Export the audio (WAV/MP3) and lay it under your video in CapCut or your NLE of choice.
* **Supplemental SFX.**  Veo 3 embeds basic ambiences, but you can top up footstep or dragon‑roar layers from free libraries such as **Pixabay** or **Freesound**.

---

## 6. Cost‑Saving Checklist

* Drop the render count to **1** until near‑final.
* Prototype in Veo 2; switch to Veo 3 only when audio or higher fidelity is required.
* Cancel mid‑queue jobs you no longer need—credits refund immediately if the render has not begun.
* Share Ultra seats across the team; only the logged‑in user burns credits.

---

## 7. Troubleshooting Cheatsheet

| Symptom                                                                  | Likely Cause                                         | Quick Fix                                                                            |
| ------------------------------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **“Switching you to a compatible model” error** when clicking **Extend** | The Extend tool is Veo 2‑only; current clip is Veo 3 | Re‑render base clip in Veo 2 or start a fresh clip and stitch externally.            |
| Characters drift (hair colour, outfit) across clips                      | Prompt too vague or continuity heavy                 | Use character study frames; add colour hex codes & fabric textures in Subject block. |
| Mute icon with no audio toggle                                           | Backend error or high load                           | Resubmit job; consider off‑peak hours (early morning UTC)                            |
| Sudden credit drain                                                      | Generated 4‑render variants by mistake               | Switch **Renders per prompt** to 1 in Advanced pane.                                 |

---

## 8. Further Resources

1. Google Keyword Blog—*“Meet Flow: AI‑powered filmmaking with Veo 3”* (20 May 2025).
2. DataCamp Tutorial—*“Veo 3: A Guide With Practical Examples”* (22 May 2025).
3. Javi Lopez X‑thread—*7‑Eleven, Dragon & AI Workflow Breakdown* (25 May 2025).
4. Dave Clark X‑thread—*Effective Cinematic Prompt Structure for Veo 3* (25 May 2025).
5. Reddit r/aivideo thread—*“Interdimensional Cable (Veo 3)”* (community walk‑through).

---

### 9. Case Study Snapshot: *7‑Eleven & Dragon* (Javi Lopez)

| Phase         | Tool & Settings                                              | Key Takeaway                                                    |
| ------------- | ------------------------------------------------------------ | --------------------------------------------------------------- |
| Prompting     | Veo 3 via Freepik; 150‑word prompt with rich physical detail | Veo 3 parses long, cinematic prose—no need to trim.             |
| Quality Boost | Magnific upscale *before* generation                         | High‑res seed frames yield crisper video.                       |
| Music         | Udio (synth‑orchestral score)                                | Custom score in minutes; think era‑appropriate instrumentation. |
| Assembly      | CapCut + minor SFX                                           | Fast, phone‑friendly NLE for <1‑hour turnaround.                |

The entire 50‑second scene rendered in under two hours for ≈ 900 credits: a concrete example of how modest budgets can deliver polished, narrative video.

---

### Final Thoughts

Veo 3 is closer to a digital cinematography assistant than a point‑and‑shoot camera.  Invest prep time—character studies, structured prompts, quality seed frames, and disciplined budgeting—so every eight‑second clip moves you toward the story you want to tell.

Happy rendering!
