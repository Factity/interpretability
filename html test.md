
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interpretability — Visual Representations</title>

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Newsreader:ital,opsz,wght@0,6..72,200..800;1,6..72,200..800&family=Plus+Jakarta+Sans:wght@200..800&display=swap" rel="stylesheet">

    <style>
        /* ─── CSS Variables (Dark Theme) ─────────────────────────── */
        :root {
            --font-size: 16px;
            --background: #070b14;
            --foreground: #dde3ed;
            --card: #0d1220;
            --card-foreground: #dde3ed;
            --popover: #0d1220;
            --popover-foreground: #dde3ed;
            --primary: #8b9fff;
            --primary-foreground: #070b14;
            --secondary: #141c2e;
            --secondary-foreground: #dde3ed;
            --muted: #141c2e;
            --muted-foreground: #6e7d99;
            --accent: #e2a44b;
            --accent-foreground: #070b14;
            --destructive: #e05a5a;
            --destructive-foreground: #ffffff;
            --border: rgba(255, 255, 255, 0.07);
            --input: transparent;
            --input-background: #141c2e;
            --switch-background: #2a3550;
            --font-weight-medium: 500;
            --font-weight-normal: 400;
            --ring: #8b9fff;
            --chart-1: #8b9fff;
            --chart-2: #e2a44b;
            --chart-3: #6ee7b7;
            --chart-4: #f472b6;
            --chart-5: #60a5fa;
            --radius: 0.375rem;
            --sidebar: #0d1220;
            --sidebar-foreground: #dde3ed;
            --sidebar-primary: #8b9fff;
            --sidebar-primary-foreground: #070b14;
            --sidebar-accent: #141c2e;
            --sidebar-accent-foreground: #dde3ed;
            --sidebar-border: rgba(255, 255, 255, 0.07);
            --sidebar-ring: #8b9fff;
            --text-2xl: 1.5rem;
            --text-xl: 1.25rem;
            --text-lg: 1.125rem;
            --text-base: 1rem;
        }

        /* ─── Reset & Base ──────────────────────────────────────── */
        *,
        *::before,
        *::after {
            box-sizing: border-box;
            border-color: var(--border);
            outline-color: color-mix(in srgb, var(--ring) 50%, transparent);
        }

        html {
            font-size: var(--font-size);
            scroll-behavior: smooth;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        body {
            margin: 0;
            background: var(--background);
            color: var(--foreground);
            font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
            line-height: 1.6;
            min-height: 100vh;
        }

        ::-webkit-scrollbar {
            width: 0;
            height: 0;
        }

        /* ─── Typography ────────────────────────────────────────── */
        .display {
            font-family: 'Newsreader', Georgia, serif;
        }
        .mono {
            font-family: 'DM Mono', 'Courier New', monospace;
        }

        h1 {
            font-size: var(--text-2xl);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
        }
        h2 {
            font-size: var(--text-xl);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
        }
        h3 {
            font-size: var(--text-lg);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
        }
        h4 {
            font-size: var(--text-base);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
        }
        label {
            font-size: var(--text-base);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
        }
        button {
            font-size: var(--text-base);
            font-weight: var(--font-weight-medium);
            line-height: 1.5;
            cursor: pointer;
            font-family: inherit;
        }
        input {
            font-size: var(--text-base);
            font-weight: var(--font-weight-normal);
            line-height: 1.5;
            font-family: inherit;
        }

        /* ─── Prose Styles ──────────────────────────────────────── */
        .prose p {
            color: #a0aec0;
            line-height: 1.8;
            font-size: 0.97rem;
            font-weight: 300;
            margin-bottom: 1.1em;
        }
        .prose h2 {
            font-family: 'Newsreader', Georgia, serif;
            font-size: 1.75rem;
            font-weight: 300;
            color: #dde3ed;
            line-height: 1.25;
            margin: 2.5rem 0 0.75rem;
        }
        .prose h3 {
            font-family: 'Newsreader', Georgia, serif;
            font-size: 1.2rem;
            font-style: italic;
            font-weight: 300;
            color: #c4cfe6;
            margin: 2rem 0 0.5rem;
        }
        .prose strong {
            color: #c4cfe6;
            font-weight: 500;
        }
        .prose code {
            font-family: 'DM Mono', monospace;
            font-size: 0.82em;
            background: rgba(139, 159, 255, 0.1);
            color: #a5b4fc;
            padding: 0.1em 0.4em;
            border-radius: 3px;
        }
        .prose blockquote {
            border-left: 2px solid rgba(139, 159, 255, 0.35);
            padding-left: 1.25rem;
            margin: 1.5rem 0;
            color: #8892a4;
            font-style: italic;
        }
        .prose figure {
            margin: 2rem 0;
        }
        .prose figcaption {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            color: #6e7d99;
            margin-top: 0.6rem;
            text-align: center;
        }
        .prose em {
            font-style: italic;
        }

        /* ─── Layout ────────────────────────────────────────────── */
        .page-container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 1.5rem;
            padding-top: 5rem;
            padding-bottom: 6rem;
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
        }

        @media (min-width: 1024px) {
            .page-container {
                grid-template-columns: 200px 1fr;
                gap: 4rem;
            }
        }

        /* ─── Nav ───────────────────────────────────────────────── */
        .nav-bar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 50;
            border-bottom: 1px solid var(--border);
            background: rgba(7, 11, 20, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            height: 52px;
        }
        .nav-inner {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 1.5rem;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .nav-links {
            display: flex;
            gap: 1.5rem;
        }
        .nav-links a {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            color: var(--muted-foreground);
            text-decoration: none;
            transition: color 0.15s;
        }
        .nav-links a:hover {
            color: var(--foreground);
        }

        /* ─── TOC Sidebar ───────────────────────────────────────── */
        .toc-sidebar {
            display: none;
        }
        @media (min-width: 1024px) {
            .toc-sidebar {
                display: block;
            }
        }
        .toc-sticky {
            position: sticky;
            top: 6rem;
        }
        .toc-heading {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            color: var(--muted-foreground);
            margin-bottom: 1rem;
            letter-spacing: 0.1em;
            text-transform: uppercase;
        }
        .toc-link {
            font-family: 'DM Mono', monospace;
            font-size: 0.72rem;
            color: #6e7d99;
            display: block;
            padding: 0.35rem 0;
            transition: color 0.15s;
            text-decoration: none;
            border-left: 2px solid transparent;
            padding-left: 0.75rem;
        }
        .toc-link:hover {
            color: #dde3ed;
        }
        .toc-link.active {
            color: #8b9fff;
            border-left-color: #8b9fff;
        }
        .toc-meta {
            margin-top: 2.5rem;
            padding-top: 2rem;
            border-top: 1px solid var(--border);
        }
        .toc-meta-label {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            color: var(--muted-foreground);
            margin-bottom: 0.25rem;
        }
        .toc-meta-value {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            color: var(--foreground);
        }
        .toc-meta-value+.toc-meta-label {
            margin-top: 0.75rem;
        }

        /* ─── Card / Demo Containers ────────────────────────────── */
        .demo-card {
            border-radius: 0.5rem;
            border: 1px solid var(--border);
            overflow: hidden;
            background: #0a0f1e;
        }
        .demo-card-header {
            padding: 1rem 1.25rem;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        .demo-card-body {
            padding: 1.25rem;
            display: flex;
            gap: 1.5rem;
            align-items: flex-start;
            flex-wrap: wrap;
        }
        @media (min-width: 768px) {
            .demo-card-body {
                flex-wrap: nowrap;
            }
        }

        /* ─── Buttons ───────────────────────────────────────────── */
        .pill-btn {
            font-family: 'DM Mono', monospace;
            font-size: 0.75rem;
            padding: 0.25rem 0.75rem;
            border-radius: 0.25rem;
            border: 1px solid transparent;
            background: transparent;
            color: #6e7d99;
            transition: all 0.15s;
            cursor: pointer;
            white-space: nowrap;
        }
        .pill-btn:hover {
            color: #dde3ed;
        }
        .pill-btn.active {
            border-color: rgba(139, 159, 255, 0.4);
            background: rgba(139, 159, 255, 0.15);
            color: #8b9fff;
        }

        /* ─── Animations ────────────────────────────────────────── */
        .fade-up {
            animation: fadeUp 0.5s ease both;
        }
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: none;
            }
        }

        /* ─── Utility ───────────────────────────────────────────── */
        .text-accent {
            color: var(--accent);
        }
        .text-muted {
            color: var(--muted-foreground);
        }
        .text-primary {
            color: var(--primary);
        }
        .text-foreground {
            color: var(--foreground);
        }
        .border-border {
            border-color: var(--border);
        }
        .tracking-widest {
            letter-spacing: 0.1em;
        }
        .uppercase {
            text-transform: uppercase;
        }
        .italic {
            font-style: italic;
        }
        .font-light {
            font-weight: 300;
        }
        .leading-relaxed {
            line-height: 1.7;
        }
        .leading-tight {
            line-height: 1.25;
        }
        .mt-2 {
            margin-top: 0.5rem;
        }
        .mt-10 {
            margin-top: 2.5rem;
        }
        .mt-16 {
            margin-top: 4rem;
        }
        .mb-1 {
            margin-bottom: 0.25rem;
        }
        .mb-2 {
            margin-bottom: 0.5rem;
        }
        .mb-4 {
            margin-bottom: 1rem;
        }
        .mb-5 {
            margin-bottom: 1.25rem;
        }
        .mb-6 {
            margin-bottom: 1.5rem;
        }
        .mb-12 {
            margin-bottom: 3rem;
        }
        .pt-8 {
            padding-top: 2rem;
        }
        .py-4 {
            padding-top: 1rem;
            padding-bottom: 1rem;
        }
        .gap-1 {
            gap: 0.25rem;
        }
        .gap-2 {
            gap: 0.5rem;
        }
        .gap-3 {
            gap: 0.75rem;
        }
        .gap-6 {
            gap: 1.5rem;
        }
        .flex {
            display: flex;
        }
        .flex-col {
            flex-direction: column;
        }
        .flex-wrap {
            flex-wrap: wrap;
        }
        .items-center {
            align-items: center;
        }
        .items-start {
            align-items: flex-start;
        }
        .justify-between {
            justify-content: space-between;
        }
        .flex-1 {
            flex: 1;
        }
        .flex-shrink-0 {
            flex-shrink: 0;
        }
        .self-start {
            align-self: flex-start;
        }
        .ml-auto {
            margin-left: auto;
        }
        .space-y-1\.5>*+* {
            margin-top: 0.375rem;
        }
        .space-y-3>*+* {
            margin-top: 0.75rem;
        }
        .rounded-lg {
            border-radius: 0.5rem;
        }
        .rounded-full {
            border-radius: 9999px;
        }
        .w-2 {
            width: 0.5rem;
        }
        .h-2 {
            height: 0.5rem;
        }
        .h-1\.5 {
            height: 0.375rem;
        }
        .h-full {
            height: 100%;
        }
        .w-full {
            width: 100%;
        }
        .text-xs {
            font-size: 0.75rem;
        }
        .text-sm {
            font-size: 0.875rem;
        }
        .text-xl {
            font-size: 1.25rem;
        }
        .transition-all {
            transition: all 0.2s;
        }
        .transition-colors {
            transition: color 0.15s, background-color 0.15s;
        }
        .transition-opacity {
            transition: opacity 0.15s;
        }
        .hover\:opacity-70:hover {
            opacity: 0.7;
        }
        .hover\:text-foreground:hover {
            color: var(--foreground);
        }
        .no-underline {
            text-decoration: none;
        }
        .relative {
            position: relative;
        }
        .absolute {
            position: absolute;
        }
        .inset-0 {
            inset: 0;
        }
        .overflow-hidden {
            overflow: hidden;
        }
        .cursor-pointer {
            cursor: pointer;
        }
        .grid {
            display: grid;
        }
        .grid-cols-2 {
            grid-template-columns: repeat(2, 1fr);
        }
        @media (min-width: 768px) {
            .md\:grid-cols-4 {
                grid-template-columns: repeat(4, 1fr);
            }
        }
        @media (min-width: 768px) {
            .md\:flex-nowrap {
                flex-wrap: nowrap;
            }
        }

        /* ─── Specific component tweaks ─────────────────────────── */
        .saliency-grid-cell {
            position: absolute;
            width: 17px;
            height: 17px;
            border-radius: 2px;
            transition: background 0.06s;
        }
        .attention-grid-cell {
            width: 36px;
            height: 36px;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'DM Mono', monospace;
            font-size: 10px;
        }
        .jspace-legend-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
        }
        .jspace-legend-dot {
            width: 0.5rem;
            height: 0.5rem;
            border-radius: 9999px;
            flex-shrink: 0;
        }
    </style>
</head>
<body>

    <!-- ─── Nav ──────────────────────────────────────────────────── -->
    <nav class="nav-bar">
        <div class="nav-inner">
            <div style="display:flex;align-items:center;gap:0.5rem;">
                <span class="display" style="font-size:0.875rem;font-weight:300;color:var(--foreground);">Interpretability</span>
                <span style="color:var(--border);margin:0 0.25rem;">/</span>
                <span class="mono" style="font-size:0.75rem;color:var(--muted-foreground);">Visual Representations</span>
            </div>
            <div class="nav-links">
                <a href="#">Archive</a>
                <a href="#">About</a>
            </div>
        </div>
    </nav>

    <!-- ─── Page Layout ──────────────────────────────────────────── -->
    <div class="page-container">

        <!-- TOC Sidebar -->
        <aside class="toc-sidebar">
            <div class="toc-sticky">
                <div class="toc-heading">Contents</div>
                <nav id="toc-nav">
                    <a href="#saliency" class="toc-link" data-section="saliency">Interpretability</a>
                    <a href="#jspace" class="toc-link" data-section="jspace">Types of interpre5tability</a>
                    <a href="#attention" class="toc-link" data-section="attention">Traditional techniques</a>
                    <a href="#maxact" class="toc-link" data-section="maxact">Deep learning based techniques</a>
                </nav>
                <div class="toc-meta">
                    <div class="toc-meta-label">Published</div>
                    <div class="toc-meta-value">July 2025</div>
                    <div class="toc-meta-label">Reading time</div>
                    <div class="toc-meta-value">~12 min</div>
                </div>
            </div>
        </aside>

        <!-- Article -->
        <article class="prose" style="max-width:none;">

            <!-- Header -->
            <header class="fade-up" style="margin-bottom:3rem;">
                <div class="mono text-xs text-accent tracking-widest uppercase mb-5">Chapter 5 Interpretability and Explainability</div>
                <h1 class="display font-light leading-tight mb-5" style="font-size:2.8rem;color:#dde3ed;">
                    Understanding the Internals of the <br>
                    <em class="italic" style="color:#8b9fff;">AI models</em>
                </h1>


                <div style="display:flex;gap:1.5rem;border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:1rem 0;">
                    <div>
                        <div class="mono text-xs" style="color:var(--muted-foreground);">Author</div>
                        <div class="mono text-xs" style="color:var(--foreground);margin-top:0.125rem;">Research Notes</div>
                    </div>
                    <div>
                        <div class="mono text-xs" style="color:var(--muted-foreground);">Topic</div>
                        <div class="mono text-xs" style="color:var(--foreground);margin-top:0.125rem;">Interpretability · ViT · CNNs</div>
                    </div>
                </div>
            </header>

<section>
  <blockquote>
    “The mind, once stretched by a new idea, never returns to its original dimensions.” — Ralph Waldo Emerson
  </blockquote>

  <p>
    So I had this conversation about AI once, a strange but small encounter. I was asked to explain  simply: <strong>“How does AI work?”</strong> I was overwhelmed, possibly so that I have spent the last couple of years studying it. There is simply way too much and I could not get myself to a point where I could start.
    
   <br><br>I do <em>selective speak</em>, which I often consider to be  one of my traits — whether it is positive or negative, I am really not sure. I talk with my audience in mind. I simply was so overwhelmed that I simply said, “<strong>AI just works</strong>.” I did not give a good impression for sure; with some awkward stares we moved on.
   
   <br> <br>A long, long time ago I read some of <strong>Feynman’s</strong> work. Whenever I encounter the problem of breaking down a subject and doing selective speak, I often find myself going back to his work and try to understand how would he have explained it. Now, I am not no Feynman, nothing but an <em>average Joe</em>. I did what I can to break down everything I learnt about <em>“How AI works”</em> — the question of <strong>why</strong>, although <strong>what</strong> is another behemoth on its own. In this chapter we will stick with why.
  </p>

  <p>
    I started digging, curious as I was. There are simply way too many fields, way too much stuff; condensing it all is simply not possible. And the best part about this is the people who are actually building this technology have very little grasp on the field themselves. With the ever-increasing size of the models, the use cases, the sheer scale alone should make it almost impossible to study these. Humans as we are, with the indefinite amount of grit, we started chipping away at these with our chisel.
  </p>

  <p>
    In the spirit of 
    <strong><u><a href="https://calteches.library.caltech.edu/51/2/CargoCult.htm" target="_blank" rel="noopener noreferrer" style="color: white;">Feynman’s Cargo Cult Science lecture</a></u></strong>, in his words:
  </p>

  <blockquote>
    “When you study only what results you get, you never build a deeper understanding. When you study <strong>why</strong> something happens, you can refine your methods, discard dead ends, and make genuine progress.”
  </blockquote>

<section>
  <p>
    Any rigorous scientific study or a method should have a clear, reproducible basis. A fundamental axiom will be that <strong>ML models are no different than classical models, except in size</strong>.
  </p>

  <p>
    Certainly, classical models like Newton’s Laws, the Standard Model, or General Relativity feel different than ML models, owing to the fact that these models are determined by physical principles, even though they may still contain parameters that need to be calibrated from data. By “<strong>classical</strong>”, we mean models created by scientists without using ML techniques. Related terms that are often used are <em>intelligibility</em> and <em>understandability</em>.
  </p>

  <p>
    We will consider <strong>interpretability</strong> and <strong>explainability</strong> to be the primary axes of interest in understanding the <em>why</em> of the model. <strong>Interpretability</strong> concerns the ability to understand, or approximate, the inner workings of a model and how it reaches its output. <strong>Explainability</strong> concerns the ability to map the model onto existing knowledge in the relevant scientific domain.
  </p>

  <p>
    The key difference is how we classify it. Are we able to <em>explain</em> the model? What is <em>happening</em> inside it? <strong>Interpretability</strong> is the degree to which a human can understand the cause of a decision.
  </p>

  <blockquote>
    “A method is interpretable if a user can correctly and efficiently predict the method’s results.”
  </blockquote>

  <p>
    The more interpretable a machine learning model, the easier it is for someone to understand why certain decisions or predictions were made. A particular model is <em>more interpretable</em> than another model if its decisions are easier to understand than the other model’s. Knowing the ‘why’ can help you learn more about the problem, the data, and the reason why a model might fail.
  </p>


<p>
    In some of the cases we might not just need interpretability. In cases like reccomendation systems for movies. well researched technqiuies like ocr does not warrant the use of interpretability techniques. As you will see in the below section explaining a model is often a very compute intensive , tideous and most inmpotantly it is largely a manual task. One of the argument presented by 
</p>




<p>Doshi-Velez and Kim (2017), is that **the need for interpretability and explainability arises from an incompleteness in problem formalization**. This means that for many real-world tasks, the formal objective function we optimise (e.g., classification accuracy) does not capture everything that matters.A single metric like classification accuracy gives us the <strong>“what”</strong> – the prediction.
- But it does not tell us the <strong>“why”</strong> – how the model arrived at that prediction.

one of the most important benefit of doing interpretability and explainability it lets us use these systems in mission critcial scenarios. Most real world tasks are incompletely formalised, have strong ethical and moral concerns and contextual factors associated with them. Any slight error can lead to catastrophic consequenxces. 

One of the important application of explanaibility and interpretability is in ai safety. It helps us avoid plothera of problems. Machine learning models deployed in real contexts have life altering decisions and with the current rate of progress they will fundamentally shape our lives. A oracle that simply gives you answers to anything but doesnt tell you how will distrupt humanity and it is deeply unsettling. 

Reasons for investing in interpretability 

<div style="background:rgba(255,255,255,0.03); border:1px solid rgba(255,255,255,0.08); border-radius:8px; padding:1.5rem; margin:2rem 0;">
  <p style="margin-top:0;"><strong>Fairness:</strong> Ensuring predictions do not implicitly or explicitly discriminate against underrepresented groups. Without interpretability, detecting and correcting bias is nearly impossible.</p>
  <p><strong>Privacy:</strong> Verifying that sensitive information in the training data is not being inadvertently memorised and leaked through predictions.</p>
  <p><strong>Reliability / Robustness:</strong> Confirming that the model does not produce drastically different outputs for minimally perturbed inputs (a phenomenon adversarial examples exploit). Interpretability can reveal whether the model relies on brittle features.</p>
  <p><strong>Causality:</strong> Ensuring the model picks up only genuine causal relationships, not mere correlations that might fail under distribution shift. A model relying on non-causal features is likely to fail in the real world.</p>
  <p style="margin-bottom:0;"><strong>Trust:</strong> Humans find it easier to trust a system that can explain its decisions. Trust is built when an explanation aligns with or respectfully challenges a user’s prior knowledge, rather than being an opaque oracle.</p>
</div>
<p>
Interpretability and explanability would also allow us to analyse a prediction in counter factual terms we can analyse why a particular prediction is generated we can also elimiate why this did not.

By studying these it lets us look at abnormalities, what are the influential factors etc. These explanations should also not be misrepresentataive if a particular reson reson is plusible is it transferable, generalizable etc should also be studied with the help of interpretrability 
</p>
</p>
  <p>
    from a practical stand point you should also look at when to use interpretability if you are looking to increase the model accuracy or finding a causal explanation for a particular case. The anology goes like this a particular resercher when trying to mitigate bias used various complicated interpretability techniques to find the exact reason and solved it but a simple and the optimal method is simply using the more higher quality data which is much cheaper readily avaialble and saves a lot of time.

    
    
    Imagine a scenario where an AI is extremely intelligent and has derived a <strong>novel proof</strong>. When we try to understand the internals of the model we find a particular <strong>x</strong> (an internal element of the model) that is responsible for it. Now we know that to solve the proof, the model should have developed its own forms of, let’s say, <strong>y laws</strong>. Here the <strong>y laws</strong> are the <em>explanation</em> — they connect the model’s behaviour to existing scientific knowledge. The <strong>x</strong> is the <em>interpretable</em> element — it reveals what inside the model caused that behaviour. <strong>Y is for explainability, and x is for interpretability.</strong>

    - Validate that the model is solving the problem in a reasonable way.
- Detect when the model relies on **non-causal features** for prediction, which can lead to catastrophic failures under distribution shift.
- Find **wrong encodings or sub‑par feature engineering** that degrade performance or introduce bias.
- In a specific case, understand **why this particular prediction was made**; if the explanation conflicts with domain knowledge, the decision-maker might question the forecast and initiate an investigation, potentially averting a harmful decision.

  </p>
</section>
</section>

<section id="Different types of interpretability">

<!--   different types of interpretability and explanability 
   
I will now take each of the formal definitions you provided and add a plain‑language explanation along with practical usage contexts.

---

### Global interpretability

**Definition (as provided)**  
Let \(f: \mathcal{X} \to \mathcal{Y}\) be a model and \(P_X\) a distribution over inputs. A global explanation is a function \(G[f] \in \mathcal{E}_G\) such that  

\[
\mathbb{E}_{x \sim P_X}\bigl[ \mathcal{L}\bigl( f(x),\, \hat{f}_{G}(x) \bigr) \bigr] \le \epsilon,
\]  

where \(\hat{f}_{G}\) is the prediction implied by the global explanation and \(\mathcal{L}\) is a loss.

**Explanation**  
Global interpretability summarises **how the model behaves on average across all possible inputs**. Instead of explaining a single prediction, it describes the overall relationships the model has learned—for example, which features are generally important, how a feature influences the output (on average), or a simplified set of rules that mimic the whole model. The formal condition ensures that the summary (a surrogate, a set of rules, a feature‑importance vector) reproduces the model’s predictions with high expected fidelity over the entire input distribution.

**Where they are used**  
- **Regulatory compliance and auditing:** showing that a model does not rely on prohibited features globally.  
- **Model documentation and transparency reports:** giving stakeholders a high‑level understanding of a model’s behaviour.  
- **Feature selection and scientific discovery:** identifying which variables truly drive the model’s decisions (e.g., in medicine or credit scoring).  
- **Model debugging:** checking if the model has learned sensible patterns (e.g., a partial dependence plot revealing a non‑monotonic relationship that contradicts domain knowledge).

---

### Local interpretability

**Definition (as provided)**  
For a fixed instance \(x_0 \in \mathcal{X}\), a local explanation is a map \(\Phi_{x_0}[f] \in \mathcal{E}_L\) that approximates \(f\) in a neighbourhood \(N_\delta(x_0)\):

\[
\Phi_{x_0}[f] \;=\; \arg\min_{e \in \mathcal{E}_L} \; \int_{x \in N_\delta(x_0)} \!\! \ell\bigl( f(x), \, \hat{f}_e(x) \bigr) \, d\mu(x) \;+\; \Omega(e),
\]  

where \(\hat{f}_e\) is the local surrogate prediction, \(\ell\) is a fidelity loss, and \(\Omega(e)\) is a complexity penalty.

**Explanation**  
Local interpretability explains **why a specific prediction was made for a single input**. It builds a simple, interpretable model that is valid only in a small region around that input. The optimisation trades off fidelity to the original model (how well the simple model matches the black‑box output nearby) against the simplicity of the explanation (e.g., a sparse linear model). The result is an easy‑to‑grasp explanation tailored to one individual case.

**Where they are used**  
- **Individual decision support:** explaining to a loan applicant why their application was denied.  
- **Medical diagnosis:** interpreting why an image was classified as malignant for a particular patient.  
- **Model debugging at the instance level:** investigating a single misclassification or suspicious output.  
- **Legal and ethical justification:** providing case‑specific reasons that can be contested or validated.

---

### Intrinsic interpretability

**Definition (as provided)**  
A model \(f \in \mathcal{F}_{\text{int}}\) is intrinsically interpretable if there exists a representation mapping \(\mathcal{R}: \mathcal{F}_{\text{int}} \to \mathcal{H}\), where \(\mathcal{H}\) is a set of human‑understandable descriptions, such that for any \(x\),  

\[
f(x) = \mathcal{R}(f)(x) \quad \text{(perfect fidelity)},
\]  

and the cognitive complexity \(C(\mathcal{R}(f)) \le K\) for some fixed small constant \(K\).

**Explanation**  
Instead of applying an external explanation tool to a black‑box model, **the model itself is simple enough to be read and understood directly**. The learned structure (a small tree, a short rule list, a sparse linear model) is the explanation. There is no approximation; the model’s own parameters form a human‑interpretable description with limited cognitive load.

**Where they are used**  
- **High‑stakes domains where trust is mandatory:** medical scoring systems (e.g., APACHE, SOFA), credit underwriting models that must be justified to regulators.  
- **When explainability must be guaranteed:** safety‑critical systems where a black‑box explanation could be wrong.  
- **Rapid prototyping and baseline modeling:** understanding data patterns through a transparent model before moving to more complex ones.  
- **Settings with limited computational resources for post‑hoc explainers.**

---

### Post‑hoc explainability

**Definition (as provided)**  
Given a trained model \(f: \mathcal{X}\to\mathcal{Y}\), a post‑hoc explainer is a function \(\Psi\) that produces an explanation \(E = \Psi(f, \mathcal{D}, \mathcal{A})\) where \(\mathcal{D}\) is (optionally) a dataset and \(\mathcal{A}\) is an auxiliary algorithm. Crucially, \(\Psi\) does **not** modify \(f\) and treats \(f\) as a black‑box oracle. The explanation \(E\) may only approximate \(f\):

\[
\exists\, \hat{f}_E \in \mathcal{E} \quad \text{s.t.} \quad \hat{f}_E \approx f.
\]

**Explanation**  
Post‑hoc explainability means **we leave the model untouched and, after training, apply a separate algorithm to generate explanations**. The model is treated as an opaque function; we only need its inputs and outputs (or sometimes gradients). The explanation is always an approximation of the model’s true behaviour, and it does not change how the model makes predictions.

**Where they are used**  
- **The overwhelming majority of real‑world explainability needs:** most deployed models are complex (deep nets, ensembles) and cannot be replaced by intrinsically interpretable ones without sacrificing accuracy.  
- **Standard toolkit for data scientists:** SHAP, LIME, permutation importance are all post‑hoc.  
- **Compliance when the model cannot be changed:** e.g., a legacy credit‑scoring system that must be explained without modification.  
- **Model‑agnostic comparisons:** evaluating feature importance across different black‑box model types.

---

### Model‑specific explainability

**Definition (as provided)**  
An explainability method is model‑specific for a model family \(\mathcal{M}\) if it requires access to the internal structure (parameters \(\theta\), gradients, architecture). Formally,  

\[
\Psi_{\mathcal{M}}: \Theta_{\mathcal{M}} \times \mathcal{X} \to \mathcal{E},
\]  

where \(\Theta_{\mathcal{M}}\) is the parameter space of models in \(\mathcal{M}\), and \(\Psi_{\mathcal{M}}\) explicitly uses \(\theta\).

**Explanation**  
These methods **exploit the inner workings of a particular model type** (e.g., neural network weights or tree splits) to produce explanations. They cannot be applied to an arbitrary model; they are tailor‑made for one family. Because they see inside the model, they are often faster and more precise than model‑agnostic methods for that architecture.

**Where they are used**  
- **Deep learning interpretability:** Integrated Gradients, DeepLIFT, and Grad‑CAM require gradients and layer activations.  
- **Tree ensembles:** TreeSHAP uses the tree structure to compute exact SHAP values in polynomial time.  
- **Attention‑based NLP models:** attention weight visualisation (though debated).  
- **When you have full access to model internals** and need a computationally efficient, tightly integrated explanation.

---

### Model‑agnostic explainability

**Definition (as provided)**  
An explainer \(\Psi\) is model‑agnostic if it relies only on query access to \(f\), i.e., for any \(f \in (\mathcal{X} \to \mathcal{Y})\),

\[
\Psi(f, x) = \Phi\bigl( \{(x_i, f(x_i))\}_{i=1}^N, x \bigr),
\]  

where \(\Phi\) is a procedure that uses only the input‑output pairs (no internal parameters or gradients).

**Explanation**  
Model‑agnostic methods **work for any model**, regardless of how it was built. They treat the model as a black box that can be queried for predictions. This makes them universally applicable, but they often require sampling many predictions and may be less precise than model‑specific techniques.

**Where they are used**  
- **Explaining proprietary or external models** where you cannot see the code or parameters (e.g., an API).  
- **Comparing explanations across different model types** (linear vs. random forest vs. neural network) on the same dataset.  
- **Regulated industries where the model is a vendor‑supplied black box.**  
- **Rapid prototyping of explanations** without needing to understand the model architecture.

---

### Feature‑attribution methods

**Definition (as provided)**  
A feature attribution for input \(x\) is a vector \(\phi(x) \in \mathbb{R}^d\) that assigns an importance score to each feature. Many methods impose an additive decomposition:

\[
f(x) = \phi_0 + \sum_{j=1}^d \phi_j(x), \qquad \phi_0 = \mathbb{E}[f(X)].
\]  

SHAP values are the Shapley values of a cooperative game with payoff \(v(S;x) = \mathbb{E}[f(X) \mid X_S = x_S]\).

**Explanation**  
Feature‑attribution methods answer: **“How much did each input feature contribute to this prediction?”** They assign a number (positive/negative) to each feature, summing to the difference between the model’s output and a baseline. They are the most common form of local explanation, giving a clear, quantitative breakdown of influence.

**Where they are used**  
- **Consumer‑facing explanations:** “Your loan was denied mainly because of high credit utilisation (30%) and short credit history (25%).”  
- **Model debugging and feature engineering:** identifying irrelevant or noisy features.  
- **Scientific validation:** confirming that a model uses biologically meaningful features.  
- **Fairness audits:** checking if protected attributes have undue influence on predictions.

---

### Surrogate model methods

**Definition (as provided)**  
A surrogate model method approximates the complex model \(f\) with a simple interpretable model \(g \in \mathcal{G}\). For global surrogates,  

\[
g^* = \arg\min_{g \in \mathcal{G}} \; \mathbb{E}_{x \sim P_X}\bigl[ L(f(x), g(x)) \bigr].
\]  

For local surrogates, the expectation is restricted to a local neighbourhood.

**Explanation**  
A **white‑box model (the surrogate) is trained to mimic a black‑box model**. Instead of explaining the complex model directly, we learn an inherently interpretable copy that makes similar predictions. The surrogate (e.g., a small tree or a linear model) is then presented as the explanation. Local surrogates (like LIME) mimic the model only near a specific instance.

**Where they are used**  
- **Global model understanding:** a decision tree surrogates a deep neural network to give a rough overview of decision logic.  
- **When a black‑box model must be replaced by an interpretable one for deployment**, and the surrogate serves as a “validated” approximation.  
- **Local explanations for any model:** LIME trains a local linear surrogate per prediction.  
- **Debugging complex simulations:** a simple surrogate reveals the dominant driving factors.

---

### Example‑based methods

**Definition (as provided)**  
An example‑based explanation for a test instance \(x\) is a set of training instances \(\{z_1,\dots,z_k\}\) and their (possibly weighted) influence. Influence functions give:

\[
\mathcal{I}(z, x) = -\nabla_\theta L(x, \hat{\theta})^\top H_{\hat{\theta}}^{-1} \nabla_\theta L(z, \hat{\theta}),
\]  

where \(\hat{\theta}\) minimises the empirical loss and \(H_{\hat{\theta}}\) is the Hessian.

**Explanation**  
Instead of summarising with rules or feature weights, these methods explain by **pointing to actual training examples** that were most influential in the model’s decision. Prototypes show a representative example of a class; criticisms show poorly represented instances; influence functions quantify how removing a training point would change a prediction.

**Where they are used**  
- **Case‑based reasoning and legal analogies:** showing a judge similar past cases that led to the same outcome.  
- **Data debugging:** identifying mislabelled or influential training samples that caused an error.  
- **Interpretable machine learning in medicine:** showing a doctor similar patient records with known outcomes.  
- **Recommender systems:** “You might like this because it is similar to items X, Y, Z that you purchased.”

---

### Rule‑based methods

**Definition (as provided)**  
An explanation is a set of logical rules \(R = \{r_k\}_{k=1}^K\) where each rule is a conjunction of conditions. For a classification model \(f\),

\[
f(x) = y \;\Longleftrightarrow\; \bigvee_{r \in R_y} r(x) = 1 \quad \text{(with high probability)}.
\]  

Extracted rules are found by minimising \(\text{error}(f, R) + \lambda \cdot \text{complexity}(R)\).

**Explanation**  
The explanation is a **small set of if‑then rules** that approximate the model’s decisions. These rules are directly human‑readable and can be verified against domain knowledge. They can be extracted from a trained model or learned jointly. Each rule provides a simple condition that, if true, strongly indicates a particular class.

**Where they are used**  
- **Interpretable classification in risk assessment:** a set of rules that explain when a transaction is flagged as fraudulent.  
- **Medical triage systems:** rules like “if age > 65 and blood pressure > 140 then high risk.”  
- **Regulatory compliance:** rule lists can be directly submitted as model documentation.  
- **Building inherently interpretable systems** (e.g., CORELS, RuleFit) when accuracy must be paired with full transparency.

---

### Visualization‑based methods

**Definition (as provided)**  
Visual explanations are mappings into a human‑perceptible space, typically \(\mathbb{R}^2\) or a heatmap. Saliency map: \(S_{ij} = \|\nabla_{x_{ij}} f_c(x)\|\). Dimension‑reduction:  

\[
\min_{\phi} \sum_{i,j} \bigl( d_{\mathcal{X}}(x_i,x_j) - \|\phi(x_i)-\phi(x_j)\| \bigr)^2.
\]

**Explanation**  
These methods **create images or plots that highlight what the model is “looking at”** (saliency maps, Grad‑CAM) or how data points and representations are organised (t‑SNE, UMAP). The explanation is perceptual rather than propositional—a human must interpret the visualisation.

**Where they are used**  
- **Computer vision:** heatmaps showing which pixels drive a classification (e.g., in medical imaging to highlight tumours).  
- **Exploratory data analysis of learned representations:** projecting hidden layer activations to 2D to see if classes form clusters.  
- **Debugging neural networks:** noticing that a saliency map highlights background instead of the object.  
- **Human‑AI collaboration interfaces:** providing intuitive visual feedback to users.

---

### Counterfactual explanations

**Definition (as provided)**  
Given \(f: \mathcal{X} \to \mathcal{Y}\) and a desired output \(y^* \neq f(x_0)\), a counterfactual is a point \(x'\) solving:

\[
\begin{aligned}
& \min_{x'} \; d(x_0, x') \\
\text{s.t.} \quad & f(x') = y^*, \\
& x' \in \mathcal{A}(x_0) \quad \text{(actionable constraints)},
\end{aligned}
\]  

where \(d\) is a distance and \(\mathcal{A}(x_0)\) imposes feasibility.

**Explanation**  
Counterfactual explanations answer: **“What is the smallest change to my input that would flip the prediction to a desired outcome?”** They show a modified version of the input (e.g., “if your income were $5,000 higher, your loan would have been approved”). The focus is on actionable and realistic changes.

**Where they are used**  
- **Consumer recourse:** telling a rejected applicant exactly what they can change to get approved.  
- **Algorithmic fairness:** ensuring that actionable changes are equally available across demographic groups.  
- **What‑if analysis:** clinicians exploring how a patient’s risk would change if a certain biomarker were lowered.  
- **Model debugging:** finding small perturbations that cause large, unexpected changes in the output.

---

### Contrastive explanations

**Definition (as provided)**  
A contrastive explanation for a factual class \(y\) and a foil class \(y'\) identifies a minimal set of features \(S\) such that altering them changes the prediction:

\[
f(x_0) = y, \quad f\bigl( (x_0 \setminus x_S) \cup x'_S \bigr) = y',
\]  

with minimal \(|S|\) or minimal change.

**Explanation**  
Instead of answering “Why class A?”, contrastive explanations answer **“Why class A rather than class B?”** They isolate the features that differentiate the predicted class from an alternative, often referred to as “why‑this‑not‑that” explanations. The explanation highlights the crucial differences between the two outcomes.

**Where they are used**  
- **Differential diagnosis in medicine:** “Why does the model predict disease X and not disease Y?” showing the key distinguishing symptoms.  
- **Legal argumentation:** focusing on the few facts that would change the verdict.  
- **User interfaces for decision support:** presenting a side‑by‑side comparison of what feature values led to one classification over another.  
- **Fairness analysis:** checking if protected attributes are the distinguishing factor between two outcomes.

---

### Causal explanations

**Definition (as provided)**  
A causal explanation is based on a structural causal model \(\mathcal{M} = (U, V, F, P_U)\). For an intervention \(\text{do}(X_S = x_S)\),

\[
\mathbb{E}[Y \mid \text{do}(X_S = x_S)] \;-\; \mathbb{E}[Y].
\]  

Causal counterfactuals are obtained via abduction‑action‑prediction.

**Explanation**  
Causal explanations go beyond correlation and describe **what would happen if one intervened on a feature**. They use a causal graph to estimate the effect of setting a variable to a specific value, often answering “What would the prediction have been if feature \(X_i\) had taken a different value, while everything else remains the same in a causal sense?” This is strictly stronger than statistical counterfactuals because it respects causal mechanisms.

**Where they are used**  
- **Policy evaluation:** estimating the effect of a new treatment protocol on patient outcomes.  
- **Fairness and discrimination:** understanding whether a protected attribute has a direct causal effect on the decision.  
- **Robust recourse:** generating counterfactuals that remain valid under real‑world interventions, not just statistical correlation.  
- **Scientific inference:** testing hypotheses about cause‑and‑effect relationships within a model.

---

### Semantic explanations

**Definition (as provided)**  
A semantic explanation expresses predictions via human‑understandable concepts. Let a concept encoder map \(x\) to \(v(x) \in \mathbb{R}^k\) and the model be \(f(x) = g(v(x))\). A concept‑based explanation gives importance scores \(\beta\) such that \(f(x) \approx \beta^\top v(x)\). TCAV computes sensitivity via directional derivative.

**Explanation**  
Semantic explanations **explain predictions in terms of high‑level concepts that humans naturally understand**, like “stripes,” “red,” or “wheel,” rather than raw pixels or features. They map input features to a space of meaningful concepts and then show which concepts the model uses. For instance, rather than “pixel (123, 45) contributed 0.3”, it might say “the presence of ‘fur’ concept increases the ‘dog’ score by 0.8”.

**Where they are used**  
- **Image classification:** explaining a zebra prediction by the presence of the “stripes” concept.  
- **Medical imaging:** using concepts like “irregular margin” or “calcification” to explain tumour classifications.  
- **Bias detection:** finding that a model uses a concept like “gender” (even implicitly) to make decisions.  
- **Human‑friendly AI auditing:** allowing non‑technical stakeholders to review model behaviour via a concept‑based vocabulary.

---

### Simulatability

**Definition (as provided)**  
A model \(f\) is simulatable if a human can reproduce its computation step by step. Let \(\mathcal{A}_f\) be an algorithm for \(f\). Simulatability is:

\[
f \text{ is simulatable} \iff C(\mathcal{A}_f) \le K,
\]  

where \(K\) is a small cognitive threshold (e.g., depth ≤ 3 tree, ‖β‖₀ ≤ 5).

**Explanation**  
Simulatability means **a person can take the entire model—inputs, all parameters, and the computation rules—and manually step through it to make a prediction, without any tooling**. The model is so simple that its operation fits in a human’s working memory. This is the strongest local property of interpretability; if a model is simulatable, its reasoning is completely transparent to a human.

**Where they are used**  
- **Ultra‑transparent systems:** small rule lists used for triage in resource‑poor settings where automatic computation is unavailable.  
- **Education:** teaching students how a model works by having them replicate the calculations.  
- **Design target for high‑stakes decisions:** a model that can be verified by a human judge without software.  
- **Limiting the complexity of interpretable‑by‑design models** (e.g., restricting tree depth or number of non‑zero coefficients).

---

### Decomposability

**Definition (as provided)**  
A model is decomposable if its prediction can be expressed as a combination of individually interpretable components:

\[
f(x) = h\bigl( g_1(x), g_2(x), \dots, g_m(x) \bigr),
\]  

where each \(g_i\) is interpretable and \(h\) is a simple composition (e.g., sum). In a GAM, \(f(x) = \sum f_j(x_j)\).

**Explanation**  
Decomposability means **the model can be broken down into independent, understandable pieces, each depending on a small subset of features, and then combined in a transparent way** (typically by addition). Each piece can be inspected and interpreted in isolation. This is a component‑wise transparency: the whole model is not necessarily small enough to simulate at once, but one can examine each additive component.

**Where they are used**  
- **Generalized additive models (GAMs) in healthcare and finance:** each feature’s shape function is plotted, giving intuitive insight.  
- **Modular neural networks:** where separate sub‑networks are trained for distinct semantic parts and then combined.  
- **When features naturally segment (e.g., different medical tests)**, and an expert wants to see the contribution of each test independently.  
- **Building interpretable complex models** that retain the ability to audit individual pathways.

---

### Transparency‑based explanations

**Definition (as provided)**  
A model class \(\mathcal{F}\) is transparent if there exists a function \(\mathcal{T}: \mathcal{F} \to \mathcal{D}\) that maps each model to a fully faithful and human‑understandable description of its mechanism:

\[
\forall x \in \mathcal{X}, \quad f(x) = \mathcal{T}(f)(x),
\]  

and the complexity of \(\mathcal{T}(f)\) is bounded.

**Explanation**  
Transparency is the **umbrella property that combines simulatability and decomposability**. A fully transparent model is one where the entire inference algorithm can be inspected, understood, and faithfully described at all levels—parameter‑wise, component‑wise, and as a whole procedure. There is no black box; the model’s description is the model itself.

**Where they are used**  
- **Extreme regulatory environments:** where every aspect of the model must be open to scrutiny (e.g., some criminal justice risk assessments).  
- **White‑box modelling competitions:** where the winning model must be documented and justified line‑by‑line.  
- **Design philosophy for interpretable machine learning:** encouraging the development of models that are transparent by construction.  
- **Audit and certification processes:** if a model’s transparency can be formally proved, it may receive certification for safety‑critical applications.

---

These definitions, explanations, and usage contexts together provide a complete, rigorous picture of the landscape of interpretability and explainability in machine learning.

-->
</section>

<section id="interpreting linear regression ">



    <!--    interpreting linear regression-->
</section>


<section id="interpreting logistic regression">



    <!--    interpreting logistic regression-->
</section>

<section id="interpreting decision tree algorithm ">



    <!--    interpreting decision tree regression-->
</section>


<section id="interpreting support vector machines">



    <!--    interpreting support vector machines-->
</section>


<section id="parameter tuning and interpretability">



    <!--    different parater tuning methods and how interpretability is effected -->
</section>

<section id="shap lime cpp causal ice etc etc methods">



    <!--    interpreting support vector machine
        
    get all the math formulation how they are used what sort of tools you use pick a data set and study them for this do through data analysis and data mining     
    s-->
</section>


<section id="model agnostic methods and  interpretability for those  ">



    <!--  
    pdp partial dependency methods 
    accumated local effects 
    feature interaction 
    functional decomposition 
    permuatation of feature importance 
    lofo 
    surrogate 
    proto other methods 

    math formulation for each of these study them using an exaple provide jupyter note book links 


    
    
    -->
</section>


<section id="interpreting deep learning">



    <!--    local methods global methods
    learned features 
    gradient based methods // rate of chyange of slope based methods 
    perturbation methods math formulation etc 
    adverserial examples 

    transfer learning based interp 
    influential instances 

    
    
    
    -->
</section>

<section id="Evaluation of interpretability methods ">



    <!--    how good are they which one lacks what when to use what and when not to use what etc -->
</section>

<!--  use the ibm interpretability tools -->

<section id="circuoits for vision models ">



    <!--   taxonomy for each of different elemets of circuits 
       
    find a tool to create all the plots present in the chris olah works and recreate them 

    cover how they came up with idea generate an animation that would help user zoom and probe 
    
    apply it to a different model than what they gave in the blog 
    featuyres 

    circuits 

    universality 
    
    feature vis 

    examples 

    syntheic examples 

    join tuning 

    feature implementataion 

    feature use 

    hand written circuits 


    write math formulation for how each of the frequency detectors wrk how they are bleached 

    write basic introductory stuff about image procesing 

    pose invaraince 

    poly sematicity 

    give introductory stuff about higher dimensions etc 

    circuits \
    curve deectors 

    orinetation 

    super position 

    universality 



    picks a architecture write abpout gabour types of gabour colors 
    

    why they picmked these shapes 

    generate animations of the shapes find places where they occured and 

    color contrast, line, shifted linestextures, curves, brightness, gabor textures, hatch textures corners line divergence 



    write about how complexity and re construction of features forms across the different levels 

    causality generality purity family 

    human inutition \

    joint tuning curves 

    syntheic curves generate heat maps 

    angles do radial tracing 


    use a spline algorithm to map lines tracing the curve 

   equivalent features how does symttery occure rotational translational etc etc 


rotataional high low equivaraiance bw color circuits line curve divergence circuits 

how they all put togther in circuits 

write how complexity emerged which layer led to which forms of curve elements etc 

What’s the difference between visualizing activations, weights, and attributions?
In this article, we’re focusing on visualizing weights. But people often visualize activations, attributions, gradients, and much more. How should we think about the meaning of visualizing these different objects?

Activations: We generally think of these as being “what” the network saw. If understanding a neural network is like reverse compiling a computer program, the neurons are the variables, and the activations are the values of those variables.
Weights: We generally think of these as being “how” the neural network computes one layer from the previous one. In the reverse engineering analogy, these are compiled assembly instructions.
Attributions: Attributions try to tell us the extent to which one neuron influenced a later neuron.
[2, 3]
We often think of this as “why” the neuron fired. We need to be careful with attributions, because they’re a human-defined object on top of a neural network rather than a fundamental object. They aren’t always well defined, and people mean different things by them. (They are very well defined if you are only operating across adjacent layers!)




lack of contectualization 

indirect interaction dimensionality 
    
write about brancjhes 

weights banding 


branching interventions etc 



-->




</section>



<section id = "interpretability of transformer  model">


    <!--  


make this entire thing just one section alone 









    link to your work on trasnformers

    follo neel nandhas guide 


    reverse engineering transformers 

    start with zero layers 

    effects of  encoding tokenization zero layer 
    
    
    emergence of insuctrion circuits 

    residual stream 

    virtual weights 

    subspaces 
    attentrion heades additivity operations with them 


incontet learnoing and attention heads 

detailed breakdown of the argfuments 

Argument 1 (Macroscopic co-occurrence): Transformer language models undergo a “phase change” early in training, during which induction heads form and simultaneously in-context learning improves dramatically.
Argument 2 (Macroscopic co-perturbation): When we change the transformer architecture in a way that shifts whether induction heads can form (and when), the dramatic improvement in in-context learning shifts in a precisely matching way.
Argument 3 (Direct ablation):  When we directly “knock out” induction heads at test-time in small models, the amount of in-context learning greatly decreases.
Argument 4 (Specific examples of induction head generality): Although we define induction heads very narrowly in terms of copying literal sequences, we empirically observe that these same heads also appear to implement more sophisticated types of in-context learning, including highly abstract behaviors, making it plausible they explain a large fraction of in-context learning.
Argument 5 (Mechanistic plausibility of induction head generality): For small models, we can explain mechanistically how induction heads work, and can show they contribute to in-context learning. Furthermore, the actual mechanism of operation suggests natural ways in which it could be re-purposed to perform more general in-context learning.
Argument 6 (Continuity from small to large models): In the previous 5 arguments, the case for induction heads explaining in-context learning is stronger for small models than for large ones. However, many behaviors and data related to both induction heads and in-context learning are smoothly continuous from small to large models, suggesting the simplest explanation is that mechanisms are the same.

superposition 

mono semantic and poly semantic neurons 

features directions and super position 

word embeddings latent space 
interpretable neurons 

unoiversality 
poly semantic neurons 

features as arbitary neurons 

featueres as interpretable properties 

features of directions 

privileged and non privileged basis 

in residual stream 

the super position hypothesis 

decomposibility 

linearity 
super position 

basis aligned 

feature sparsity 

more features 6than neurons 

varying features in importance 

the geometry of superposition 

uniform super position 

feature dimensionality 

polytopes and low rank matrices 

non uniform super position 

perturbing a single feature 

correlated and anti correlated features 

local almost orthogonal bases 

collapsing of correlated features 

super position and learning dynamics 

discerete energy level jumps 

learning as a gemetric transformations 

adversarial robustness 

super position in a privileged basis 

computataion in super position 

experimental setup 

superposition and sparsity 


Distributed Representations: Composition & Superposition
the asymmetric super position motif 

safety,interpretability and solving super position 




    kqv analysis 


    skip trigrams 

    path expansions of logits \


    on interpretability 
    



    attention 


    Almost Orthogonal Vectors

    Compressed sensing

    mlp blocks 
    



    -->

</section>












            <p>
                When a neural network classifies an image, it doesn't <em>look</em> the way we do.
                It propagates activations through layers of learned transformations, compressing
                and expanding representations until a final linear combination of features produces
                a prediction. The challenge of interpretability is making that process legible.
            </p>
            <p>
                Over the last decade, a small set of core techniques has emerged: gradient-based
                attribution, representation geometry, and attention visualization. Each peels back
                a different layer of abstraction. None is complete on its own.
            </p>

            <!-- §1 Saliency -->
            <section id="saliency">
                <h2>Saliency maps: which pixels matter?</h2>
                <p>
                    The simplest interpretability question is attribution — given a prediction,
                    which input regions caused it? Saliency maps answer this via the gradient
                    of the output class score with respect to each input pixel:
                </p>
                <blockquote>
                    S(x) = |∂f_c / ∂x| — the magnitude of how much each pixel, if perturbed,
                    would change the class score.
                </blockquote>
                <p>
                    This is called <strong>vanilla gradient</strong> or simple backpropagation saliency.
                    It's fast — a single backward pass — and surprisingly informative, despite
                    its known instability to adversarial noise.
                </p>

                <figure>
                    <div class="demo-card" id="saliency-demo">
                        <div class="demo-card-header">
                            <span class="mono text-xs" style="color:var(--muted-foreground);">vanilla gradient saliency</span>
                            <div class="flex gap-1" id="saliency-class-btns">
                                <button class="pill-btn active" data-class="0">golden retriever</button>
                                <button class="pill-btn" data-class="1">tabby cat</button>
                                <button class="pill-btn" data-class="2">fire truck</button>
                            </div>
                        </div>
                        <div class="demo-card-body" id="saliency-body">
                            <div class="relative flex-shrink-0" id="saliency-grid-container" style="width:252px;height:252px;">
                                <!-- Filled by JS -->
                            </div>
                            <div class="flex flex-col gap-3 flex-1" style="min-width:180px;">
                                <div>
                                    <div class="mono text-xs mb-1" id="saliency-class-label" style="color:#f59e0b;">predicted class</div>
                                    <div class="display text-xl font-light" style="color:#dde3ed;" id="saliency-class-name">golden retriever</div>
                                </div>
                                <div>
                                    <div class="mono text-xs" style="color:var(--muted-foreground);margin-bottom:0.25rem;">confidence</div>
                                    <div style="display:flex;align-items:center;gap:0.75rem;">
                                        <div class="flex-1 h-1.5 rounded-full" style="background:rgba(255,255,255,0.06);">
                                            <div class="h-full rounded-full" id="saliency-confidence-bar" style="width:87%;background:#f59e0b;transition:width 0.8s ease;"></div>
                                        </div>
                                        <span class="mono text-xs" id="saliency-confidence-text" style="color:#f59e0b;">87.3%</span>
                                    </div>
                                </div>
                                <div style="margin-top:0.5rem;">
                                    <div class="mono text-xs" style="color:var(--muted-foreground);margin-bottom:0.5rem;">gradient magnitude</div>
                                    <div class="flex gap-2 items-center">
                                        <div class="w-2 h-2 rounded-full" id="saliency-legend-high" style="background:#f59e0b;"></div>
                                        <span class="mono text-xs" style="color:var(--muted-foreground);">high activation</span>
                                    </div>
                                    <div class="flex gap-2 items-center" style="margin-top:0.25rem;">
                                        <div class="w-2 h-2 rounded-full" style="background:rgba(13,18,32,0.6);border:1px solid #2a3550;"></div>
                                        <span class="mono text-xs" style="color:var(--muted-foreground);">no contribution</span>
                                    </div>
                                </div>
                                <button id="saliency-rerun-btn" class="mono text-xs px-4 py-2 rounded border transition-all self-start"
                                style="border:1px solid rgba(245,158,11,0.33);color:#f59e0b;background:rgba(245,158,11,0.067);margin-top:0.5rem;padding:0.5rem 1rem;border-radius:0.25rem;">
                                re-run backprop →
                            </button>
                        </div>
                    </div>
                </div>
                <figcaption>
                    Vanilla gradient saliency. Select a class above; the heatmap shows which
                    spatial regions carry the highest gradient magnitude. Re-run to watch the
                    backward pass animate.
                </figcaption>
            </figure>

            <h3>Beyond vanilla gradients</h3>
            <p>
                Vanilla saliency has a saturation problem: in regions where the model is
                highly confident, gradients become flat even though the features are critical.
                Several methods address this.
            </p>
            <p>
                <strong>Integrated Gradients</strong> accumulates gradients along a linear path
                from a baseline (often a black image) to the actual input, satisfying an axiom
                called <em>completeness</em> — the attributions sum to the total output difference.
                <strong> SmoothGrad</strong> adds Gaussian noise n times and averages, reducing
                high-frequency artifacts at the cost of n forward passes. <strong>GradCAM</strong>
                avoids per-pixel resolution by pooling gradients over spatial feature maps in
                the final convolutional layer, producing coarser but more stable localizations.
            </p>
            <p>
                None of these is universally superior. The choice depends on the downstream use:
                debugging a misclassification, explaining to a non-expert, or formally auditing
                a model's decision process each demands a different fidelity-stability tradeoff.
            </p>
        </section>

        <!-- §2 J-Space -->
        <section id="jspace">
            <h2>J-Space: the Jacobian as geometry</h2>
            <p>
                Gradient-based attribution tells us where a model looks. A different question
                is <em>how</em> the model has structured its internal representations — what
                geometry has it learned in activation space?
            </p>
            <p>
                The <strong>Jacobian matrix</strong> <code>J(x) = ∂f/∂x</code> evaluated at
                an input <code>x</code> is a local linearization of the network. Its rows
                point in the directions of steepest ascent for each output class; its singular
                values tell us how much each of those directions amplifies or attenuates.
            </p>
            <p>
                Projecting a dataset of inputs through their per-sample Jacobians — call it
                the <strong>J-space embedding</strong> — yields a representation that captures
                both the input's content and the model's local sensitivity structure. Unlike
                penultimate-layer activations, J-space preserves information about which
                input directions the model considers <em>discriminative</em> rather than merely
                which are <em>active</em>.
            </p>

            <figure>
                <div class="demo-card" id="jspace-demo">
                    <div class="demo-card-header">
                        <span class="mono text-xs" style="color:var(--muted-foreground);">Jacobian feature space — ResNet-50 layer 4</span>
                        <button id="jspace-play-btn" class="pill-btn" style="border:1px solid var(--border);">pause</button>
                    </div>
                    <div class="demo-card-body">
                        <svg id="jspace-svg" width="340" height="280" style="flex-shrink:0;"></svg>
                        <div class="flex flex-col gap-3" style="min-width:180px;">
                            <p class="text-xs" style="color:var(--muted-foreground);line-height:1.6;font-weight:300;font-size:0.8rem;">
                                Each point is an image projected through the network's Jacobian matrix — a linearization
                                of how the model responds to local perturbations around that input.
                            </p>
                            <p class="text-xs" style="color:var(--muted-foreground);line-height:1.6;font-weight:300;font-size:0.8rem;">
                                Semantically similar images cluster tightly, suggesting the Jacobian encodes
                                category structure even in mid-layer representations.
                            </p>
                            <div style="margin-top:0.5rem;" id="jspace-legend">
                                <!-- Filled by JS -->
                            </div>
                        </div>
                    </div>
                </div>
                <figcaption>
                    2D UMAP projection of the J-space embedding for 100 ImageNet images
                    (ResNet-50, layer 4 Jacobian, top-2 singular vectors). Hover a cluster
                    to highlight its class.
                </figcaption>
            </figure>

            <p>
                The structure visible here — tight, separated clusters — has a direct
                interpretation: images that activate similar Jacobian directions cluster
                together. This means the model has learned approximately <em>class-conditional</em>
                sensitivity structure. A golden retriever and a tabby cat activate different
                discriminative directions in weight space, even when their raw pixel distributions overlap.
            </p>
            <h3>Why J-space matters for interpretability</h3>
            <p>
                Standard activation-space analysis asks: <em>what did this layer output?</em>
                J-space analysis asks: <em>what would have changed the output?</em> The latter
                is closer to the counterfactual reasoning we care about in safety-critical
                applications. A model that gets the right answer for wrong reasons —
                relying on texture shortcuts, dataset artifacts, or spurious correlations —
                may produce similar activations to a well-calibrated model while having
                a very different J-space geometry.
            </p>
            <p>
                This makes J-space a useful probe for <strong>shortcut learning</strong>.
                If a model's J-space clusters cleanly by spurious feature (background color,
                photographer watermark) rather than semantic category, the Jacobian exposes it
                before it can cause a deployment failure.
            </p>
        </section>

        <!-- §3 Attention -->
        <section id="attention">
            <h2>Attention in Vision Transformers</h2>
            <p>
                Convolutional networks process images in fixed local neighborhoods. Vision
                Transformers (ViTs) divide an image into a grid of patches and process them
                as a sequence using self-attention — allowing every patch to attend to every
                other patch in a single layer.
            </p>
            <p>
                This makes attention weights a natural interpretability target: they tell us,
                for each query patch, which other patches the model weighted most heavily when
                computing its representation. In practice, attention is heads × patches × patches,
                so the question "what is this model attending to?" requires choosing how to
                aggregate across heads and layers.
            </p>

            <figure>
                <div class="demo-card" id="attention-demo">
                    <div class="demo-card-header">
                        <span class="mono text-xs" style="color:var(--muted-foreground);">ViT attention — click to set query patch</span>
                        <div class="flex gap-1 ml-auto" id="attn-head-btns">
                            <button class="pill-btn active" data-head="0">head 0</button>
                            <button class="pill-btn" data-head="1">head 3</button>
                            <button class="pill-btn" data-head="2">head 7</button>
                            <button class="pill-btn" data-head="3">head 11</button>
                        </div>
                    </div>
                    <div class="demo-card-body">
                        <div id="attn-grid" style="display:grid;grid-template-columns:repeat(7,36px);gap:2px;flex-shrink:0;">
                            <!-- Filled by JS -->
                        </div>
                        <div class="flex flex-col gap-3" style="min-width:180px;">
                            <p class="text-xs" style="color:var(--muted-foreground);line-height:1.6;font-weight:300;font-size:0.8rem;">
                                The orange patch is the <span class="mono" style="color:#e2a44b;">query</span> — the patch
                                asking "which other patches am I attending to?" Brighter blue indicates higher attention weight.
                            </p>
                            <p class="text-xs" style="color:var(--muted-foreground);line-height:1.6;font-weight:300;font-size:0.8rem;">
                                Different heads learn qualitatively different attention patterns.
                                Early heads tend toward local patterns; later heads show long-range semantic structure.
                            </p>
                            <div style="margin-top:0.5rem;display:flex;align-items:center;gap:0.75rem;">
                                <span class="mono text-xs" style="color:var(--muted-foreground);">low attention</span>
                                <div style="height:0.5rem;width:6rem;border-radius:0.125rem;background:linear-gradient(to right,rgba(13,18,32,1),rgba(139,159,255,1));"></div>
                                <span class="mono text-xs" style="color:var(--muted-foreground);">high</span>
                            </div>
                        </div>
                    </div>
                </div>
                <figcaption>
                    Self-attention weights from a ViT-B/16 (simulated). Click any patch to set
                    it as the query; brightness shows attention weight. Switch heads to see how
                    different heads specialize.
                </figcaption>
            </figure>

            <h3>The head specialization hypothesis</h3>
            <p>
                A persistent empirical finding is that different attention heads learn
                qualitatively different functions. Some heads attend locally, functioning
                like edge detectors. Others span the image, picking up long-range semantic
                dependencies — "this patch looks like an ear, which correlates with the
                dog-snout patch at the other side of the image."
            </p>
            <p>
                <strong>Attention Rollout</strong> propagates attention maps through all layers
                by multiplying adjacency matrices, accounting for skip connections via identity
                mixing. The result is a per-token "receptive field" in attention-space — analogous
                to the spatial receptive field in CNNs, but dynamically computed per input.
            </p>
            <p>
                The limitation is well-known: attention weight ≠ causal importance. A head
                can attend strongly to a patch while that patch contributes minimally to the
                final prediction (if subsequent MLP layers suppress the signal). Coupling
                attention maps with gradient information — <strong>Grad-CAM over attention</strong>
                — partially addresses this by weighting maps by their gradient w.r.t. the class score.
            </p>
        </section>

        <!-- §4 Activation Maximization -->
        <section id="maxact">
            <h2>Activation maximization: what does a neuron want?</h2>
            <p>
                Saliency and attention tell us which parts of a given input mattered.
                Activation maximization inverts the question: <em>what input would maximally
                excite a given neuron?</em> This is found by gradient ascent in image space,
                starting from noise and iterating:
            </p>
            <blockquote>
                x* = argmax_x f_i(x) − λ·R(x)
            </blockquote>
            <p>
                where <code>f_i</code> is the activation of unit <code>i</code> and
                <code>R(x)</code> is a regularizer discouraging unnatural images (total variation,
                Gaussian blur, frequency penalization, or a learned image prior).
            </p>

            <figure>
                <div class="demo-card">
                    <div class="demo-card-body" style="display:grid;grid-template-columns:repeat(2,1fr);gap:1rem;">
                        <div class="flex flex-col gap-2" id="maxact-cell-0">
                            <canvas width="96" height="96" style="border-radius:4px;"></canvas>
                            <div class="mono text-xs" style="color:var(--muted-foreground);">layer 1 · neuron 23</div>
                            <div class="mono text-xs" style="color:#8b9fff;font-size:0.68rem;">Gabor edge detector (45°)</div>
                        </div>
                        <div class="flex flex-col gap-2" id="maxact-cell-1">
                            <canvas width="96" height="96" style="border-radius:4px;"></canvas>
                            <div class="mono text-xs" style="color:var(--muted-foreground);">layer 2 · neuron 71</div>
                            <div class="mono text-xs" style="color:#8b9fff;font-size:0.68rem;">high-frequency texture</div>
                        </div>
                        <div class="flex flex-col gap-2" id="maxact-cell-2">
                            <canvas width="96" height="96" style="border-radius:4px;"></canvas>
                            <div class="mono text-xs" style="color:var(--muted-foreground);">layer 3 · neuron 142</div>
                            <div class="mono text-xs" style="color:#8b9fff;font-size:0.68rem;">curve / arc detector</div>
                        </div>
                        <div class="flex flex-col gap-2" id="maxact-cell-3">
                            <canvas width="96" height="96" style="border-radius:4px;"></canvas>
                            <div class="mono text-xs" style="color:var(--muted-foreground);">layer 4 · neuron 8</div>
                            <div class="mono text-xs" style="color:#8b9fff;font-size:0.68rem;">color blob (warm)</div>
                        </div>
                    </div>
                </div>
                <figcaption>
                    Synthetic activation maximization patterns for four neurons at different network depths.
                    Early layers show Gabor-like edge detectors; deeper layers produce complex textural structures.
                    (Animated — patterns evolve continuously via gradient ascent simulation.)
                </figcaption>
            </figure>

            <h3>From neurons to concepts</h3>
            <p>
                Early conv layers reliably produce Gabor filters — oriented edge detectors at
                various frequencies. This isn't surprising; it replicates the primary visual cortex.
                What's remarkable is that it emerges from random initialization and gradient descent,
                not from architectural inductive bias.
            </p>
            <p>
                Deeper layers are more interesting and harder to interpret. A single neuron in
                layer 4 might respond maximally to "a dog snout seen from slightly below, with
                golden fur, in warm light" — a combination so specific it resists any single English
                label. This is the <strong>polysemanticity problem</strong>: neurons at intermediate
                depth respond to multiple distinct, unrelated concepts, presumably because the
                network has learned to reuse representational capacity via superposition.
            </p>
            <p>
                Sparse dictionary learning — training a sparse autoencoder to reconstruct layer
                activations from an overcomplete basis — is the current best approach to decomposing
                polysemantic neurons into monosemantic features. Each basis vector corresponds to
                a single interpretable direction; their activation maximizations are far cleaner
                than those of raw neurons.
            </p>

            <h3>Closing thoughts</h3>
            <p>
                Each technique described here illuminates a different facet of a vision model's
                learned representation. No single method gives the full picture. Saliency maps
                identify attribution but not mechanism. J-space characterizes representation
                geometry but not causal structure. Attention weights are legible but not
                causally faithful. Activation maximization synthesizes preferred stimuli but
                conflates multiple functions.
            </p>
            <p>
                The deeper ambition — a complete mechanistic account of how a model transforms
                pixel values into semantic predictions — remains open. Progress is coming from
                combining these tools: using attention to identify candidate circuits, patching
                to verify causality, and sparse decomposition to isolate features. The field
                is young. The images are starting to come into focus.
            </p>
        </section>

        <!-- Footer refs -->
        <div style="margin-top:4rem;padding-top:2rem;border-top:1px solid var(--border);">
            <div class="mono text-xs tracking-widest uppercase mb-4" style="color:var(--muted-foreground);">Further Reading</div>
            <div class="space-y-3">
                <div style="display:flex;gap:0.75rem;">
                    <span class="mono text-xs flex-shrink-0" style="color:var(--muted-foreground);padding-top:0.125rem;">Simonyan et al., 2014</span>
                    <a href="#" class="mono text-xs no-underline transition-opacity leading-relaxed" style="color:var(--primary);">Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps</a>
                </div>
                <div style="display:flex;gap:0.75rem;">
                    <span class="mono text-xs flex-shrink-0" style="color:var(--muted-foreground);padding-top:0.125rem;">Sundararajan et al., 2017</span>
                    <a href="#" class="mono text-xs no-underline transition-opacity leading-relaxed" style="color:var(--primary);">Axiomatic Attribution for Deep Networks (Integrated Gradients)</a>
                </div>
                <div style="display:flex;gap:0.75rem;">
                    <span class="mono text-xs flex-shrink-0" style="color:var(--muted-foreground);padding-top:0.125rem;">Dosovitskiy et al., 2020</span>
                    <a href="#" class="mono text-xs no-underline transition-opacity leading-relaxed" style="color:var(--primary);">An Image is Worth 16×16 Words: Transformers for Image Recognition at Scale</a>
                </div>
                <div style="display:flex;gap:0.75rem;">
                    <span class="mono text-xs flex-shrink-0" style="color:var(--muted-foreground);padding-top:0.125rem;">Elhage et al., 2022</span>
                    <a href="#" class="mono text-xs no-underline transition-opacity leading-relaxed" style="color:var(--primary);">Toy Models of Superposition</a>
                </div>
                <div style="display:flex;gap:0.75rem;">
                    <span class="mono text-xs flex-shrink-0" style="color:var(--muted-foreground);padding-top:0.125rem;">Bricken et al., 2023</span>
                    <a href="#" class="mono text-xs no-underline transition-opacity leading-relaxed" style="color:var(--primary);">Towards Monosemanticity: Decomposing Language Models with Dictionary Learning</a>
                </div>
            </div>
        </div>
    </article>
</div>

<script>
    (function() {
        // ─── Seeded Random ────────────────────────────────────────
        function seededRandom(seed) {
            const x = Math.sin(seed + 1) * 43758.5453;
            return x - Math.floor(x);
        }

        // ═══════════════════════════════════════════════════════════
        // ─── 1. SALIENCY MAP DEMO ──────────────────────────────────
        // ═══════════════════════════════════════════════════════════
        const GRID = 14;
        const CLASSES = ["golden retriever", "tabby cat", "fire truck"];
        const CLASS_COLORS = ["#f59e0b", "#a78bfa", "#f87171"];
        const CLASS_RGB = [
            [245, 158, 11],
            [167, 139, 250],
            [248, 113, 113]
        ];
        const CLASS_BG_RGB = [
            "180,140,80",
            "120,100,160",
            "180,80,80"
        ];

        function buildSaliency(classIdx) {
            const result = [];
            for (let i = 0; i < GRID * GRID; i++) {
                const row = Math.floor(i / GRID);
                const col = i % GRID;
                const cx = [7, 4, 10][classIdx % 3];
                const cy = [7, 9, 5][classIdx % 3];
                const dist = Math.sqrt((col - cx) ** 2 + (row - cy) ** 2);
                const base = Math.max(0, 1 - dist / 6.5);
                const noise = seededRandom(i * 7 + classIdx * 131) * 0.22;
                result.push(Math.min(1, base * 1.2 + noise));
            }
            return result;
        }

        let saliencyClassIdx = 0;
        let saliencyProgress = 0;
        let saliencyRunning = false;
        let saliencyCurrent = Array(GRID * GRID).fill(0);
        let saliencyTarget = buildSaliency(0);
        let saliencyRafId = null;
        let saliencyStartTime = 0;

        const saliencyGridContainer = document.getElementById('saliency-grid-container');
        const saliencyClassLabel = document.getElementById('saliency-class-label');
        const saliencyClassName = document.getElementById('saliency-class-name');
        const saliencyConfidenceBar = document.getElementById('saliency-confidence-bar');
        const saliencyConfidenceText = document.getElementById('saliency-confidence-text');
        const saliencyLegendHigh = document.getElementById('saliency-legend-high');
        const saliencyRerunBtn = document.getElementById('saliency-rerun-btn');
        const saliencyClassBtns = document.getElementById('saliency-class-btns');

        // Build the saliency grid DOM once
        function buildSaliencyGridDOM() {
            saliencyGridContainer.innerHTML = '';
            // Background layer
            const bgLayer = document.createElement('div');
            bgLayer.className = 'absolute inset-0 rounded overflow-hidden';
            bgLayer.style.cssText =
                'background:linear-gradient(135deg,#1a1f35 0%,#111827 100%);border-radius:0.25rem;';
            bgLayer.id = 'saliency-bg-layer';
            saliencyGridContainer.appendChild(bgLayer);

            // Saliency overlay container
            const overlayContainer = document.createElement('div');
            overlayContainer.className = 'absolute inset-0';
            overlayContainer.id = 'saliency-overlay';
            saliencyGridContainer.appendChild(overlayContainer);

            // Progress bar container
            const progressContainer = document.createElement('div');
            progressContainer.className = 'absolute bottom-0 left-0 right-0';
            progressContainer.style.cssText = 'height:2px;background:rgba(255,255,255,0.08);';
            progressContainer.id = 'saliency-progress-container';
            const progressBar = document.createElement('div');
            progressBar.className = 'h-full transition-all';
            progressBar.id = 'saliency-progress-bar';
            progressBar.style.cssText = 'width:0%;background:' + CLASS_COLORS[0] + ';height:100%;';
            progressContainer.appendChild(progressBar);
            saliencyGridContainer.appendChild(progressContainer);
        }

        function updateSaliencyBackground() {
            const bgLayer = document.getElementById('saliency-bg-layer');
            if (!bgLayer) return;
            let html = '';
            const bgRgb = CLASS_BG_RGB[saliencyClassIdx];
            for (let i = 0; i < GRID * GRID; i++) {
                const row = Math.floor(i / GRID);
                const col = i % GRID;
                const base = seededRandom(i * 3 + 17) * 0.08;
                html +=
                    `<div style="position:absolute;left:${col*18}px;top:${row*18}px;width:18px;height:18px;background:rgba(${bgRgb},${base});"></div>`;
            }
            bgLayer.innerHTML = html;
        }

        function updateSaliencyOverlay() {
            const overlay = document.getElementById('saliency-overlay');
            if (!overlay) return;
            const [r, g, b] = CLASS_RGB[saliencyClassIdx];
            let html = '';
            for (let i = 0; i < GRID * GRID; i++) {
                const row = Math.floor(i / GRID);
                const col = i % GRID;
                const v = saliencyCurrent[i] || 0;
                const alpha = v * 0.88;
                html +=
                    `<div style="position:absolute;left:${col*18}px;top:${row*18}px;width:17px;height:17px;border-radius:2px;background:rgba(${r},${g},${b},${alpha});transition:background 0.06s;"></div>`;
            }
            overlay.innerHTML = html;
        }

        function updateSaliencyProgress() {
            const progressBar = document.getElementById('saliency-progress-bar');
            const progressContainer = document.getElementById('saliency-progress-container');
            if (progressBar) {
                progressBar.style.width = (saliencyProgress * 100) + '%';
                progressBar.style.background = CLASS_COLORS[saliencyClassIdx];
            }
            if (progressContainer) {
                progressContainer.style.display = saliencyRunning ? 'block' : 'none';
            }
        }

        function updateSaliencyUI() {
            const color = CLASS_COLORS[saliencyClassIdx];
            saliencyClassLabel.style.color = color;
            saliencyClassName.textContent = CLASSES[saliencyClassIdx];
            saliencyConfidenceBar.style.background = color;
            saliencyConfidenceText.style.color = color;
            saliencyLegendHigh.style.background = color;
            saliencyRerunBtn.style.borderColor = color + '55';
            saliencyRerunBtn.style.color = color;
            saliencyRerunBtn.style.background = color + '11';
            updateSaliencyBackground();
            updateSaliencyOverlay();
            updateSaliencyProgress();
        }

        function runSaliencyBackprop() {
            if (saliencyRafId) cancelAnimationFrame(saliencyRafId);
            saliencyRunning = true;
            saliencyProgress = 0;
            saliencyCurrent = Array(GRID * GRID).fill(0);
            saliencyTarget = buildSaliency(saliencyClassIdx);
            saliencyStartTime = performance.now();
            updateSaliencyUI();
            saliencyRerunBtn.textContent = 'propagating…';
            saliencyRerunBtn.disabled = true;
            saliencyRerunBtn.style.color = '#6e7d99';
            saliencyRerunBtn.style.borderColor = 'transparent';
            saliencyRerunBtn.style.background = 'rgba(255,255,255,0.03)';

            function animate(now) {
                const elapsed = now - saliencyStartTime;
                const t = Math.min(elapsed / 1400, 1);
                saliencyProgress = t;
                saliencyCurrent = saliencyTarget.map(v => v * t + seededRandom(v * 1000) * 0.05 * (1 - t));
                updateSaliencyOverlay();
                updateSaliencyProgress();
                if (t < 1) {
                    saliencyRafId = requestAnimationFrame(animate);
                } else {
                    saliencyCurrent = [...saliencyTarget];
                    saliencyRunning = false;
                    updateSaliencyOverlay();
                    updateSaliencyProgress();
                    saliencyRerunBtn.textContent = 're-run backprop →';
                    saliencyRerunBtn.disabled = false;
                    const color = CLASS_COLORS[saliencyClassIdx];
                    saliencyRerunBtn.style.color = color;
                    saliencyRerunBtn.style.borderColor = color + '55';
                    saliencyRerunBtn.style.background = color + '11';
                    saliencyRafId = null;
                }
            }
            saliencyRafId = requestAnimationFrame(animate);
        }

        saliencyClassBtns.addEventListener('click', function(e) {
            const btn = e.target.closest('button');
            if (!btn) return;
            const classIdx = parseInt(btn.getAttribute('data-class'));
            if (isNaN(classIdx) || classIdx === saliencyClassIdx) return;
            saliencyClassIdx = classIdx;
            // Update button styles
            const buttons = saliencyClassBtns.querySelectorAll('button');
            buttons.forEach(b => {
                const ci = parseInt(b.getAttribute('data-class'));
                const color = CLASS_COLORS[ci];
                if (ci === classIdx) {
                    b.classList.add('active');
                    b.style.background = color + '22';
                    b.style.color = color;
                    b.style.borderColor = color + '55';
                } else {
                    b.classList.remove('active');
                    b.style.background = 'transparent';
                    b.style.color = '#6e7d99';
                    b.style.borderColor = 'transparent';
                }
            });
            updateSaliencyUI();
            runSaliencyBackprop();
        });

        saliencyRerunBtn.addEventListener('click', function() {
            if (saliencyRunning) return;
            runSaliencyBackprop();
        });

        // Initialize saliency demo
        buildSaliencyGridDOM();
        updateSaliencyBackground();
        updateSaliencyUI();
        // Auto-run on load
        setTimeout(runSaliencyBackprop, 300);

        // ═══════════════════════════════════════════════════════════
        // ─── 2. J-SPACE VIZ ────────────────────────────────────────
        // ═══════════════════════════════════════════════════════════
        const JSPACE_CLASSES = [
            { name: "canines", color: "#f59e0b", center: [0.28, 0.35], spread: 0.12, n: 24 },
            { name: "felines", color: "#a78bfa", center: [0.52, 0.22], spread: 0.1, n: 20 },
            { name: "vehicles", color: "#f87171", center: [0.72, 0.65], spread: 0.11, n: 22 },
            { name: "structures", color: "#6ee7b7", center: [0.35, 0.72], spread: 0.1, n: 18 },
            { name: "text/symbols", color: "#60a5fa", center: [0.7, 0.38], spread: 0.09, n: 16 },
        ];

        function buildJSpacePoints() {
            const points = [];
            JSPACE_CLASSES.forEach((cls, ci) => {
                for (let i = 0; i < cls.n; i++) {
                    const angle = seededRandom(ci * 50 + i) * Math.PI * 2;
                    const r = seededRandom(ci * 100 + i * 3) * cls.spread;
                    points.push({
                        x: cls.center[0] + Math.cos(angle) * r,
                        y: cls.center[1] + Math.sin(angle) * r,
                        cls: ci,
                        color: cls.color,
                        name: cls.name,
                    });
                }
            });
            return points;
        }

        const JSPACE_POINTS = buildJSpacePoints();
        const JSPACE_W = 340;
        const JSPACE_H = 280;
        let jspaceAnimStep = 0;
        let jspacePlaying = true;
        let jspaceHoveredCls = null;
        let jspaceAnimId = null;

        const jspaceSvg = document.getElementById('jspace-svg');
        const jspacePlayBtn = document.getElementById('jspace-play-btn');
        const jspaceLegend = document.getElementById('jspace-legend');

        // Build SVG
        function buildJSpaceSVG() {
            jspaceSvg.innerHTML = '';

            // Defs
            const defs = document.createElementNS('http://www.w3.org/2000/svg', 'defs');
            const radGrad = document.createElementNS('http://www.w3.org/2000/svg', 'radialGradient');
            radGrad.setAttribute('id', 'jspace-bg-grad');
            radGrad.setAttribute('cx', '50%');
            radGrad.setAttribute('cy', '50%');
            radGrad.setAttribute('r', '60%');
            const stop1 = document.createElementNS('http://www.w3.org/2000/svg', 'stop');
            stop1.setAttribute('offset', '0%');
            stop1.setAttribute('stop-color', 'rgba(139,159,255,0.04)');
            const stop2 = document.createElementNS('http://www.w3.org/2000/svg', 'stop');
            stop2.setAttribute('offset', '100%');
            stop2.setAttribute('stop-color', 'transparent');
            radGrad.appendChild(stop1);
            radGrad.appendChild(stop2);
            defs.appendChild(radGrad);
            jspaceSvg.appendChild(defs);

            // Background
            const bgRect = document.createElementNS('http://www.w3.org/2000/svg', 'rect');
            bgRect.setAttribute('width', JSPACE_W);
            bgRect.setAttribute('height', JSPACE_H);
            bgRect.setAttribute('fill', 'url(#jspace-bg-grad)');
            jspaceSvg.appendChild(bgRect);

            // Grid lines
            [0.25, 0.5, 0.75].forEach(t => {
                const g = document.createElementNS('http://www.w3.org/2000/svg', 'g');
                g.setAttribute('stroke', 'rgba(255,255,255,0.04)');
                g.setAttribute('stroke-width', '1');
                const vLine = document.createElementNS('http://www.w3.org/2000/svg', 'line');
                vLine.setAttribute('x1', t * JSPACE_W);
                vLine.setAttribute('y1', 0);
                vLine.setAttribute('x2', t * JSPACE_W);
                vLine.setAttribute('y2', JSPACE_H);
                const hLine = document.createElementNS('http://www.w3.org/2000/svg', 'line');
                hLine.setAttribute('x1', 0);
                hLine.setAttribute('y1', t * JSPACE_H);
                hLine.setAttribute('x2', JSPACE_W);
                hLine.setAttribute('y2', t * JSPACE_H);
                g.appendChild(vLine);
                g.appendChild(hLine);
                jspaceSvg.appendChild(g);
            });

            // Hull group
            const hullGroup = document.createElementNS('http://www.w3.org/2000/svg', 'g');
            hullGroup.id = 'jspace-hulls';
            jspaceSvg.appendChild(hullGroup);

            // Points group
            const pointsGroup = document.createElementNS('http://www.w3.org/2000/svg', 'g');
            pointsGroup.id = 'jspace-points';
            jspaceSvg.appendChild(pointsGroup);

            // Labels group
            const labelsGroup = document.createElementNS('http://www.w3.org/2000/svg', 'g');
            labelsGroup.id = 'jspace-labels';
            jspaceSvg.appendChild(labelsGroup);
        }

        function updateJSpaceHulls() {
            const hullGroup = document.getElementById('jspace-hulls');
            if (!hullGroup) return;
            hullGroup.innerHTML = '';
            JSPACE_CLASSES.forEach((cls, ci) => {
                const pts = JSPACE_POINTS.filter(p => p.cls === ci);
                if (!pts.length) return;
                const hullPoints = pts.map(p => `${p.x*JSPACE_W},${p.y*JSPACE_H}`).join(' ');
                const polygon = document.createElementNS('http://www.w3.org/2000/svg', 'polygon');
                polygon.setAttribute('points', hullPoints);
                polygon.setAttribute('fill', cls.color);
                polygon.setAttribute('fill-opacity', jspaceHoveredCls === ci ? '0.07' : '0.03');
                polygon.setAttribute('stroke', cls.color);
                polygon.setAttribute('stroke-opacity', jspaceHoveredCls === ci ? '0.3' : '0.1');
                polygon.setAttribute('stroke-width', '1');
                polygon.style.transition = 'fill-opacity 0.2s';
                hullGroup.appendChild(polygon);
            });
        }

        function updateJSpacePoints() {
            const pointsGroup = document.getElementById('jspace-points');
            if (!pointsGroup) return;
            pointsGroup.innerHTML = '';
            JSPACE_POINTS.forEach((pt, i) => {
                const wobble = jspacePlaying ? Math.sin((jspaceAnimStep + i * 37) * 0.035) * 1.8 : 0;
                const wobble2 = jspacePlaying ? Math.cos((jspaceAnimStep + i * 53) * 0.028) * 1.4 : 0;
                const dim = jspaceHoveredCls !== null && jspaceHoveredCls !== pt.cls;
                const circle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
                circle.setAttribute('cx', pt.x * JSPACE_W + wobble);
                circle.setAttribute('cy', pt.y * JSPACE_H + wobble2);
                circle.setAttribute('r', jspaceHoveredCls === pt.cls ? '4.5' : '3');
                circle.setAttribute('fill', pt.color);
                circle.setAttribute('fill-opacity', dim ? '0.12' : '0.75');
                circle.style.transition = 'all 0.2s';
                circle.style.cursor = 'pointer';
                circle.setAttribute('data-cls', pt.cls);
                circle.addEventListener('mouseenter', function() {
                    jspaceHoveredCls = pt.cls;
                    updateJSpaceAll();
                });
                circle.addEventListener('mouseleave', function() {
                    jspaceHoveredCls = null;
                    updateJSpaceAll();
                });
                pointsGroup.appendChild(circle);
            });
        }

        function updateJSpaceLabels() {
            const labelsGroup = document.getElementById('jspace-labels');
            if (!labelsGroup) return;
            labelsGroup.innerHTML = '';
            JSPACE_CLASSES.forEach((cls, ci) => {
                const text = document.createElementNS('http://www.w3.org/2000/svg', 'text');
                text.setAttribute('x', cls.center[0] * JSPACE_W);
                text.setAttribute('y', cls.center[1] * JSPACE_H - 14);
                text.setAttribute('text-anchor', 'middle');
                text.setAttribute('font-size', '9');
                text.setAttribute('fill', cls.color);
                text.setAttribute('fill-opacity', jspaceHoveredCls === null || jspaceHoveredCls === ci ? '0.9' :
                    '0.3');
                text.setAttribute('font-family', 'DM Mono, monospace');
                text.style.transition = 'fill-opacity 0.2s';
                text.style.userSelect = 'none';
                text.textContent = cls.name;
                labelsGroup.appendChild(text);
            });
        }

        function updateJSpaceAll() {
            updateJSpaceHulls();
            updateJSpacePoints();
            updateJSpaceLabels();
            updateJSpaceLegend();
        }

        function updateJSpaceLegend() {
            jspaceLegend.innerHTML = '';
            JSPACE_CLASSES.forEach((cls, i) => {
                const div = document.createElement('div');
                div.className = 'jspace-legend-item';
                div.addEventListener('mouseenter', function() {
                    jspaceHoveredCls = i;
                    updateJSpaceAll();
                });
                div.addEventListener('mouseleave', function() {
                    jspaceHoveredCls = null;
                    updateJSpaceAll();
                });
                const dot = document.createElement('div');
                dot.className = 'jspace-legend-dot';
                dot.style.background = cls.color;
                const nameSpan = document.createElement('span');
                nameSpan.className = 'mono text-xs';
                nameSpan.style.color = jspaceHoveredCls === i ? cls.color : '#6e7d99';
                nameSpan.style.transition = 'color 0.15s';
                nameSpan.textContent = cls.name;
                const countSpan = document.createElement('span');
                countSpan.className = 'mono text-xs';
                countSpan.style.color = 'var(--muted-foreground)';
                countSpan.style.marginLeft = 'auto';
                countSpan.textContent = cls.n + ' samples';
                div.appendChild(dot);
                div.appendChild(nameSpan);
                div.appendChild(countSpan);
                jspaceLegend.appendChild(div);
            });
        }

        function jspaceAnimLoop() {
            if (jspacePlaying) {
                jspaceAnimStep = (jspaceAnimStep + 1) % 360;
                updateJSpacePoints();
            }
            jspaceAnimId = requestAnimationFrame(jspaceAnimLoop);
        }

        jspacePlayBtn.addEventListener('click', function() {
            jspacePlaying = !jspacePlaying;
            jspacePlayBtn.textContent = jspacePlaying ? 'pause' : 'play';
            updateJSpacePoints();
        });

        // Build legend
        updateJSpaceLegend();

        // Initialize J-Space
        buildJSpaceSVG();
        updateJSpaceAll();
        jspaceAnimId = requestAnimationFrame(jspaceAnimLoop);

        // ═══════════════════════════════════════════════════════════
        // ─── 3. ATTENTION VIZ ──────────────────────────────────────
        // ═══════════════════════════════════════════════════════════
        const PATCH_N = 7;
        const ATTN_HEADS = ["head 0", "head 3", "head 7", "head 11"];
        let attnHead = 0;
        let attnQuery = Math.floor(PATCH_N / 2) * PATCH_N + Math.floor(PATCH_N / 2);

        function buildAttn(head, query) {
            const result = [];
            const qrow = Math.floor(query / PATCH_N);
            const qcol = query % PATCH_N;
            for (let i = 0; i < PATCH_N * PATCH_N; i++) {
                const row = Math.floor(i / PATCH_N);
                const col = i % PATCH_N;
                const dist = Math.sqrt((col - qcol) ** 2 + (row - qrow) ** 2);
                const base = Math.exp(-dist * (0.5 + head * 0.15));
                const noise = seededRandom(i * 11 + head * 77 + query * 13) * 0.18;
                result.push(Math.min(1, base + noise));
            }
            return result;
        }

        const attnGrid = document.getElementById('attn-grid');
        const attnHeadBtns = document.getElementById('attn-head-btns');

        function renderAttnGrid() {
            const attn = buildAttn(attnHead, attnQuery);
            const maxV = Math.max(...attn);
            attnGrid.innerHTML = '';
            for (let i = 0; i < PATCH_N * PATCH_N; i++) {
                const v = attn[i] / maxV;
                const isQuery = i === attnQuery;
                const cell = document.createElement('div');
                cell.className = 'attention-grid-cell';
                cell.style.background = isQuery ? '#e2a44b' : `rgba(139,159,255,${v*0.85})`;
                cell.style.outline = isQuery ? '2px solid #e2a44b' : 'none';
                cell.style.outlineOffset = '1px';
                if (isQuery) {
                    cell.innerHTML = '<span style="font-size:10px;color:#070b14;font-family:DM Mono,monospace;">Q</span>';
                }
                cell.addEventListener('click', function() {
                    attnQuery = i;
                    renderAttnGrid();
                });
                attnGrid.appendChild(cell);
            }
        }

        attnHeadBtns.addEventListener('click', function(e) {
            const btn = e.target.closest('button');
            if (!btn) return;
            const headIdx = parseInt(btn.getAttribute('data-head'));
            if (isNaN(headIdx) || headIdx === attnHead) return;
            attnHead = headIdx;
            const buttons = attnHeadBtns.querySelectorAll('button');
            buttons.forEach(b => {
                const hi = parseInt(b.getAttribute('data-head'));
                if (hi === headIdx) {
                    b.classList.add('active');
                    b.style.background = 'rgba(139,159,255,0.15)';
                    b.style.color = '#8b9fff';
                    b.style.borderColor = 'rgba(139,159,255,0.4)';
                } else {
                    b.classList.remove('active');
                    b.style.background = 'transparent';
                    b.style.color = '#6e7d99';
                    b.style.borderColor = 'transparent';
                }
            });
            renderAttnGrid();
        });

        renderAttnGrid();

        // ═══════════════════════════════════════════════════════════
        // ─── 4. ACTIVATION MAXIMIZATION ────────────────────────────
        // ═══════════════════════════════════════════════════════════
        const NEURON_PATTERNS = [
            { label: "layer 1 · neuron 23", desc: "Gabor edge detector (45°)", freq: 4, angle: 45, type: 'gabor' },
            { label: "layer 2 · neuron 71", desc: "high-frequency texture", freq: 8, angle: 90, type: 'gabor' },
            { label: "layer 3 · neuron 142", desc: "curve / arc detector", freq: 2.5, angle: 30, type: 'arc' },
            { label: "layer 4 · neuron 8", desc: "color blob (warm)", freq: 1, angle: 0, type: 'blob' },
        ];

        const maxactCanvases = [];
        const maxactPhases = [0, 0, 0, 0];

        for (let i = 0; i < 4; i++) {
            const cell = document.getElementById('maxact-cell-' + i);
            const canvas = cell.querySelector('canvas');
            maxactCanvases.push({ canvas, pattern: NEURON_PATTERNS[i], phase: 0 });
        }

        function drawMaxActPattern(canvas, pattern, phase) {
            const ctx = canvas.getContext('2d');
            const N = canvas.width;
            const { freq, angle, label, type } = pattern;
            const rad = (angle * Math.PI) / 180;
            const imgData = ctx.createImageData(N, N);

            for (let y = 0; y < N; y++) {
                for (let x = 0; x < N; x++) {
                    const nx = (x / N - 0.5) * 2;
                    const ny = (y / N - 0.5) * 2;
                    let v;

                    if (type === 'blob') {
                        const dist = Math.sqrt(nx * nx + ny * ny);
                        v = Math.exp(-dist * 2) * (0.7 + 0.3 * Math.cos(phase));
                    } else if (type === 'arc') {
                        const r = Math.sqrt(nx * nx + ny * ny);
                        v = Math.cos(r * freq * Math.PI + phase) * Math.exp(-r * 1.2);
                        v = v * 0.5 + 0.5;
                    } else {
                        const proj = nx * Math.cos(rad) + ny * Math.sin(rad);
                        const gauss = Math.exp(-(nx * nx + ny * ny) * 1.8);
                        v = Math.cos(proj * freq * Math.PI + phase) * gauss;
                        v = v * 0.5 + 0.5;
                    }

                    const idx = (y * N + x) * 4;
                    if (type === 'blob') {
                        imgData.data[idx] = Math.round(v * 220 + 30);
                        imgData.data[idx + 1] = Math.round(v * 120 + 20);
                        imgData.data[idx + 2] = Math.round(v * 40 + 10);
                    } else {
                        const bright = Math.round(v * 200 + 30);
                        imgData.data[idx] = Math.round(bright * 0.55 + 30);
                        imgData.data[idx + 1] = Math.round(bright * 0.62 + 40);
                        imgData.data[idx + 2] = Math.round(bright * 0.95 + 60);
                    }
                    imgData.data[idx + 3] = 255;
                }
            }
            ctx.putImageData(imgData, 0, 0);
        }

        function maxactAnimLoop() {
            for (let i = 0; i < maxactCanvases.length; i++) {
                maxactCanvases[i].phase += 0.025;
                drawMaxActPattern(maxactCanvases[i].canvas, maxactCanvases[i].pattern, maxactCanvases[i].phase);
            }
            requestAnimationFrame(maxactAnimLoop);
        }
        requestAnimationFrame(maxactAnimLoop);

        // ═══════════════════════════════════════════════════════════
        // ─── 5. TOC SCROLL SPY ─────────────────────────────────────
        // ═══════════════════════════════════════════════════════════
        const sectionIds = ['saliency', 'jspace', 'attention', 'maxact'];
        const tocLinks = document.querySelectorAll('.toc-link');
        let activeSection = '';

        const observer = new IntersectionObserver(
            (entries) => {
                for (const entry of entries) {
                    if (entry.isIntersecting) {
                        activeSection = entry.target.id;
                        updateTOCActive();
                    }
                }
            }, { rootMargin: '-30% 0px -60% 0px' }
        );

        sectionIds.forEach(id => {
            const el = document.getElementById(id);
            if (el) observer.observe(el);
        });

        function updateTOCActive() {
            tocLinks.forEach(link => {
                const section = link.getAttribute('data-section');
                if (section === activeSection) {
                    link.classList.add('active');
                } else {
                    link.classList.remove('active');
                }
            });
        }

        // ═══════════════════════════════════════════════════════════
        // ─── CLEANUP NOTE ──────────────────────────────────────────
        // ═══════════════════════════════════════════════════════════
        // Animation frames run for the lifetime of the page.
        // In a full SPA you'd clean these up on unmount; here
        // they persist as long as the page is open, which is fine
        // for a static article page.

        console.log('✨ Interpretability article ready — all visualizations active.');
    })();
</script>
</body>
</html>