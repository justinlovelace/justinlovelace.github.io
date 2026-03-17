---
layout: page
title: SpeechOp Demo
importance: 1
category: research
theme: light
related_publications: false
---

<style>
  .post-header .post-title {
    display: none;
  }

  :root {
    --primary-color: #2563eb;
    --secondary-color: #64748b;
    --success-color: #10b981;
    --background-color: #f8fafc;
    --card-background: #ffffff;
    --border-color: #e2e8f0;
    --text-primary: #1e293b;
    --text-secondary: #64748b;
    --shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06);
    --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  }

  html[data-theme="dark"] {
    --primary-color: #60a5fa;
    --secondary-color: #94a3b8;
    --success-color: #34d399;
    --background-color: #1e1e2e;
    --card-background: #2a2a3c;
    --border-color: #3f3f5c;
    --text-primary: #e2e8f0;
    --text-secondary: #94a3b8;
    --shadow: 0 1px 3px rgba(0, 0, 0, 0.3), 0 1px 2px rgba(0, 0, 0, 0.2);
    --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.3), 0 4px 6px -2px rgba(0, 0, 0, 0.2);
  }

  .demo-header {
    text-align: center;
    margin-bottom: 2rem;
    padding: 1.5rem 0 2rem;
    border-bottom: 1px solid var(--border-color);
  }

  .demo-header h1 {
    font-size: 2rem;
    font-weight: 700;
    margin-bottom: 0.75rem;
    line-height: 1.3;
    color: var(--text-primary);
  }

  .demo-header p {
    color: var(--text-secondary);
    font-size: 1rem;
    margin: 0;
  }

  .demo-header .paper-link {
    display: inline-block;
    margin-top: 0.75rem;
    padding: 0.35rem 1rem;
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    border-radius: 0.375rem;
    text-decoration: none;
    font-size: 0.9rem;
    transition: background 0.2s, color 0.2s;
  }

  .demo-header .paper-link:hover {
    background: var(--primary-color);
    color: #fff;
  }

  .abstract-section {
    background: var(--card-background);
    padding: 2rem;
    border-radius: 0.75rem;
    box-shadow: var(--shadow);
    margin-bottom: 2rem;
    border: 1px solid var(--border-color);
  }

  .abstract-section h3 {
    color: var(--primary-color);
    margin-bottom: 1rem;
    font-size: 1.25rem;
    font-weight: 600;
  }

  .abstract-section p {
    color: var(--text-secondary);
    line-height: 1.8;
    text-align: justify;
  }

  .overview-figure {
    text-align: center;
    margin: 3rem 0;
  }

  .overview-figure img {
    max-width: 100%;
    height: auto;
    border-radius: 0.75rem;
    box-shadow: var(--shadow-lg);
  }

  .demo-section {
    background: var(--card-background);
    margin-bottom: 2rem;
    padding: 2rem;
    border-radius: 0.75rem;
    box-shadow: var(--shadow);
    border: 1px solid var(--border-color);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .demo-section:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg);
  }

  .demo-section h2 {
    color: var(--primary-color);
    font-size: 1.75rem;
    margin-bottom: 1.5rem;
    padding-bottom: 0.75rem;
    border-bottom: 2px solid var(--border-color);
    font-weight: 600;
  }

  .demo-section h3 {
    color: var(--text-primary);
    font-size: 1.25rem;
    margin-top: 2rem;
    margin-bottom: 1rem;
    font-weight: 600;
  }

  .audio-container {
    display: grid;
    gap: 1.5rem;
  }

  .audio-player {
    background: var(--background-color);
    padding: 1rem;
    border-radius: 0.5rem;
    border: 1px solid var(--border-color);
    transition: all 0.2s ease;
  }

  .audio-player:hover {
    background: var(--card-background);
    border-color: var(--primary-color);
    transform: translateX(4px);
  }

  .audio-player label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: var(--text-primary);
    font-size: 0.95rem;
  }

  .audio-player audio {
    width: 100%;
    height: 40px;
    outline: none;
  }

  .audio-player[data-type="original"] label::before,
  .audio-player[data-type="noisy"] label::before,
  .audio-player[data-type="enhanced"] label::before {
    content: '';
    display: inline-block;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    margin-right: 0.5rem;
  }

  .audio-player[data-type="original"] label::before {
    background-color: var(--secondary-color);
  }

  .audio-player[data-type="noisy"] label::before {
    background-color: #ef4444;
  }

  .audio-player[data-type="enhanced"] label::before {
    background-color: var(--success-color);
  }

  @media (min-width: 768px) {
    .audio-container.grid-2 {
      grid-template-columns: repeat(2, 1fr);
    }

    .audio-container.grid-2 .full-width {
      grid-column: 1 / -1;
    }
  }

  .audio-group-label {
    font-size: 0.8rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: var(--secondary-color);
    margin: 0.5rem 0;
    padding-bottom: 0.25rem;
    border-bottom: 1px solid var(--border-color);
  }

  .audio-group-label:first-child {
    margin-top: 0;
  }

  .demo-nav {
    position: sticky;
    top: 0;
    background: var(--background-color);
    padding: 1rem 0;
    margin-bottom: 2rem;
    border-bottom: 1px solid var(--border-color);
    z-index: 100;
  }

  .demo-nav-links {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    justify-content: center;
  }

  .demo-nav-links a {
    color: var(--text-secondary);
    text-decoration: none;
    padding: 0.5rem 1rem;
    border-radius: 0.375rem;
    transition: all 0.2s ease;
    font-size: 0.9rem;
    font-weight: 500;
  }

  .demo-nav-links a:hover {
    background-color: var(--primary-color);
    color: white;
  }

  .section-description {
    color: var(--text-secondary);
    margin-bottom: 1.5rem;
    line-height: 1.6;
    font-size: 0.95rem;
  }
</style>

<div class="demo-header">
  <h1>SpeechOp: Inference-Time Task Composition for Generative Speech Processing</h1>
  <p>Justin Lovelace, Rithesh Kumar, Jiaqi Su, Ke Chen, Kilian Q. Weinberger, Zeyu Jin</p>
  <a href="https://arxiv.org/abs/2509.14298" class="paper-link">Paper (arXiv)</a>
</div>

<nav class="demo-nav">
  <div class="demo-nav-links">
    <a href="#abstract">Abstract</a>
    <a href="#obj1_noisy">Noisy Speech (Example 1)</a>
    <a href="#obj0_noisy">Noisy Speech (Example 2)</a>
    <a href="#f10-script5">Reverberant Speech</a>
    <a href="#librimix-speaker-separation">Speaker Separation</a>
    <a href="#zero-shot-tts">Zero-Shot TTS</a>
    <a href="#real-edit">Speech Editing</a>
  </div>
</nav>

<div class="abstract-section" id="abstract">
  <h3>Abstract</h3>
  <p>While generative Text-to-Speech (TTS) systems leverage vast "in-the-wild" data to achieve remarkable success, speech-to-speech processing tasks like enhancement face data limitations, which lead data-hungry generative approaches to distort speech content and speaker identity. To bridge this gap, we present SpeechOp, a multi-task latent diffusion model that transforms pre-trained TTS models into a universal speech processor capable of performing a wide range of speech tasks and composing them in novel ways at inference time. By adapting a pre-trained TTS model, SpeechOp inherits a rich understanding of natural speech, accelerating training and improving S2S task quality, while simultaneously enhancing core TTS performance. Finally, we introduce Implicit Task Composition (ITC), a novel pipeline where ASR-derived transcripts (e.g., from Whisper) guide SpeechOp's enhancement via our principled inference-time task composition. ITC achieves state-of-the-art content preservation by robustly combining web-scale speech understanding with SpeechOp's generative capabilities.</p>
</div>

<div class="overview-figure">
  <img src="/assets/audio/speechop_demo/figure/speechop_overview.png" alt="SpeechOp Overview Figure" class="img-fluid rounded z-depth-1">
</div>

<p class="section-description">The following examples demonstrate SpeechOp's speech enhancement and foreground/background separation capabilities. Compare the enhancement results with and without TTS guidance (Implicit Task Composition), which uses an ASR-derived transcript to improve content preservation via our TC-CFG inference-time task composition strategy.</p>

<div class="demo-section" id="obj1_noisy">
  <h2>Noisy Speech (Example 1)</h2>
  <div class="audio-container grid-2">
    <div class="audio-player full-width" data-type="noisy">
      <label>Noisy Input</label>
      <audio controls src="/assets/audio/speechop_demo/obj1_noisy/obj1_noisy.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Enhancement</p>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Enhancement</label>
      <audio controls src="/assets/audio/speechop_demo/obj1_noisy/speechop_miipher-obj1.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>Enhancement + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/obj1_noisy/speechop_tts_miipher-obj1.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Foreground / Background Separation</p>
    <div class="audio-player" data-type="enhanced">
      <label>Foreground</label>
      <audio controls src="/assets/audio/speechop_demo/obj1_noisy/speechop_iso-fg_miipher-obj1.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>Background</label>
      <audio controls src="/assets/audio/speechop_demo/obj1_noisy/speechop_iso-bg_miipher-obj1.wav"></audio>
    </div>
  </div>
</div>

<div class="demo-section" id="obj0_noisy">
  <h2>Noisy Speech (Example 2)</h2>
  <div class="audio-container grid-2">
    <div class="audio-player full-width" data-type="noisy">
      <label>Noisy Input</label>
      <audio controls src="/assets/audio/speechop_demo/obj0_noisy/obj0_noisy.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Enhancement</p>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Enhancement</label>
      <audio controls src="/assets/audio/speechop_demo/obj0_noisy/speechop_miipher-obj0.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>Enhancement + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/obj0_noisy/speechop_tts_miipher-obj0.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Foreground / Background Separation</p>
    <div class="audio-player" data-type="enhanced">
      <label>Foreground</label>
      <audio controls src="/assets/audio/speechop_demo/obj0_noisy/speechop_iso-fg_miipher-obj0.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>Background</label>
      <audio controls src="/assets/audio/speechop_demo/obj0_noisy/speechop_iso-bg_miipher-obj0.wav"></audio>
    </div>
  </div>
</div>

<div class="demo-section" id="f10-script5">
  <h2>Reverberant Speech</h2>
  <div class="audio-container grid-2">
    <div class="audio-player" data-type="original">
      <label>Clean Reference (DAPS)</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/daps-mos_Clean-44k_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <div class="audio-player" data-type="noisy">
      <label>Reverberant Input (DAPS)</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/daps-mos_Reverb_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Enhancement</p>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Enhancement</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/speech_op_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>ITC Guided Enhancement</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/speech_op_itc_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <div class="audio-player full-width" data-type="enhanced">
      <label>Personalized Enhancement</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/speech_op_pers_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Foreground Separation</p>
    <div class="audio-player" data-type="enhanced">
      <label>Foreground Separation</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/speechop_iso_f10-script5-ipad-balcony1-00007.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>Foreground Separation + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/f10-script5-ipad-balcony11-00007/speechop_iso_tts_f10-script5-ipad-balcony11-00007.wav"></audio>
    </div>
  </div>
</div>

<div class="demo-section" id="librimix-speaker-separation">
  <h2>Speaker Separation</h2>
  <p class="section-description">SpeechOp separates overlapping speakers from a mixture, using a reference speech sample to identify the target speaker. We show results on LibriMix with both clean and noisy backgrounds, with and without TTS guidance for improved content preservation.</p>

  <h3>Clean Background</h3>
  <div class="audio-container grid-2">
    <div class="audio-player full-width" data-type="noisy">
      <label>Mixture</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_mixture_test2.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Speaker 0</p>
    <div class="audio-player" data-type="original">
      <label>Ground Truth</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_target_test2_0.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Separation</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_speechop-large_test2_0.wav"></audio>
    </div>
    <div class="audio-player full-width" data-type="enhanced">
      <label>SpeechOp Separation + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_speechop-large-tts_test2_0.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Speaker 1</p>
    <div class="audio-player" data-type="original">
      <label>Ground Truth</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_target_test2_1.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Separation</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_speechop-large_test2_1.wav"></audio>
    </div>
    <div class="audio-player full-width" data-type="enhanced">
      <label>SpeechOp Separation + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/librimixclean2/librimixclean_speechop-large-tts_test2_1.wav"></audio>
    </div>
  </div>

  <h3>Noisy Background</h3>
  <div class="audio-container grid-2">
    <div class="audio-player full-width" data-type="noisy">
      <label>Mixture</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_mixture_test0.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Speaker 0</p>
    <div class="audio-player" data-type="original">
      <label>Ground Truth</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_target_test0_0.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Separation</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_speechop-large_test0_0.wav"></audio>
    </div>
    <div class="audio-player full-width" data-type="enhanced">
      <label>SpeechOp Separation + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_speechop-large-tts_test0_0.wav"></audio>
    </div>
    <p class="audio-group-label full-width">Speaker 1</p>
    <div class="audio-player" data-type="original">
      <label>Ground Truth</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_target_test0_1.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Separation</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_speechop-large_test0_1.wav"></audio>
    </div>
    <div class="audio-player full-width" data-type="enhanced">
      <label>SpeechOp Separation + TTS Guidance</label>
      <audio controls src="/assets/audio/speechop_demo/librimixnoise0/librimixnoise_speechop-large-tts_test0_1.wav"></audio>
    </div>
  </div>
</div>

<div class="demo-section" id="zero-shot-tts">
  <h2>Zero-Shot Text-to-Speech</h2>
  <p class="section-description">SpeechOp generates speech in a target speaker's voice given only a short speech prompt. Multi-task training on speech processing tasks actually improves TTS quality compared to a TTS-only baseline.</p>

  <h3>Example 1</h3>
  <div class="audio-container grid-2">
    <div class="audio-player" data-type="original">
      <label>Original Prompt</label>
      <audio controls src="/assets/audio/speechop_demo/zero-shot-tts-1995/zero-shot-tts-mos_prompt_1995-1837-0024.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Result</label>
      <audio controls src="/assets/audio/speechop_demo/zero-shot-tts-1995/zero-shot-tts-mos_speechop-large_1995-1837-0024.wav"></audio>
    </div>
  </div>
  
  <h3>Example 2</h3>
  <div class="audio-container grid-2">
    <div class="audio-player" data-type="original">
      <label>Original Prompt</label>
      <audio controls src="/assets/audio/speechop_demo/zero-shot-tts-61/zero-shot-tts-mos_prompt_61-70970-0000.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Result</label>
      <audio controls src="/assets/audio/speechop_demo/zero-shot-tts-61/zero-shot-tts-mos_speechop-large_61-70970-0000.wav"></audio>
    </div>
  </div>
</div>

<div class="demo-section" id="real-edit">
  <h2>Speech Editing</h2>
  <p class="section-description">SpeechOp edits a specific segment of an utterance while preserving the surrounding speech, maintaining speaker identity and natural prosody across the edit boundary.</p>

  <h3>Example 1</h3>
  <div class="audio-container grid-2">
    <div class="audio-player" data-type="original">
      <label>Original Audio</label>
      <audio controls src="/assets/audio/speechop_demo/edit-116/realedit_original_116-288046-000004-000007.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Edit</label>
      <audio controls src="/assets/audio/speechop_demo/edit-116/realedit_speechop-large_116-288046-000004-000007.wav"></audio>
    </div>
  </div>
  
  <h3>Example 2</h3>
  <div class="audio-container grid-2">
    <div class="audio-player" data-type="original">
      <label>Original Audio</label>
      <audio controls src="/assets/audio/speechop_demo/edit-84/realedit_original_84-121550-000126-000000.wav"></audio>
    </div>
    <div class="audio-player" data-type="enhanced">
      <label>SpeechOp Edit</label>
      <audio controls src="/assets/audio/speechop_demo/edit-84/realedit_speechop-large_84-121550-000126-000000.wav"></audio>
    </div>
  </div>
</div>
