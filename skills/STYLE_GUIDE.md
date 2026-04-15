# 🎨 Slidev AI: Modern Presentation Design Guide

This guide provides strategies and templates for using AI (ChatGPT, Claude, etc.) to generate high-quality, modern presentations for **Slidev**. 

## 🚀 Overview

AI-generated Markdown often suffers from layout overflows or monotonous designs. This guide leverages **Bento Grids**, **Glassmorphism**, and **Modern Typography** patterns to ensure AI outputs "designed interfaces" rather than just plain documents.

---

## 1. Prompt Engineering: Define Spatial Constraints
AI models don't naturally understand the 1024x768 physical limit of a slide. You must explicitly define constraints:
- **Word Limits:** "Limit body text to a maximum of 5 bullet points, with no more than 15 words per point."
- **Component Placement:** "Reserve the right side of the slide for a chart. Use `col-span-6` to keep text on the left half."
- **Scale Instructions:** "If a component is likely to be large, apply `scale="0.8"` to the container."

---

## 2. Leverage Built-in Layouts & Grids
Explicitly instructing the AI to use Slidev's layout system is the most effective way to prevent overlapping.
- **Example Prompt:** "Always use the `two-cols` layout for slides containing both text and charts."

```markdown
---
layout: two-cols
---

# Left Side (Text)
- AI-generated concise points
- Stay within the grid

::right::

# Right Side (Chart/Image)
<div class="h-full flex items-center justify-center">
  </div>




3. AI Prompt Engineering Strategies

To ensure consistent rendering, include these constraints in your System Prompt:

1. **Spatial Awareness**: "The slide dimensions are fixed at 1024x768. Ensure the content occupies no more than 40-50% of the screen to maintain white space."
2. **Structural Layout**: "Avoid simple bullet points. Use UnoCSS Grid and Flexbox to organize information into 'Modular Cards'."
3. **Visual Hierarchy**: "Use gradient text (`bg-clip-text`) for primary keywords and low-contrast colors (`text-gray-400`) for secondary descriptions."

---

4. Key Design Patterns

### A. Bento Grid Layout
A modular approach used by top-tier tech companies like Apple and Stripe to organize information cleanly.

```markdown
---
layout: default
---

<div class="grid grid-cols-3 grid-rows-2 gap-4 h-full p-2">
  <div class="col-span-2 row-span-2 p-8 bg-gray-50/50 rounded-3xl border border-gray-200/50 shadow-sm flex flex-col justify-center">
    <h2 class="text-4xl font-extrabold mb-4 bg-gradient-to-r from-blue-600 to-indigo-500 bg-clip-text text-transparent">
      Main Value Proposition
    </h2>
    <p class="text-xl text-gray-600 leading-relaxed">
      Information shines brightest when structured. Dividing space into 
      modular sections drastically improves readability and aesthetics.
    </p>
  </div>

  <div class="p-6 bg-blue-50/50 rounded-3xl border border-blue-100 flex flex-col justify-center items-center text-center">
    <div class="i-lucide-rocket text-3xl mb-2 text-blue-600" />
    <div class="text-2xl font-bold text-blue-700 font-mono">99.9%</div>
    <div class="text-xs text-gray-400 uppercase tracking-widest mt-1">Uptime</div>
  </div>

  <div class="p-6 bg-indigo-50/50 rounded-3xl border border-indigo-100 flex flex-col justify-center items-center text-center">
    <div class="i-lucide-zap text-3xl mb-2 text-indigo-600" />
    <div class="text-2xl font-bold text-indigo-700 font-mono">< 20ms</div>
    <div class="text-xs text-gray-400 uppercase tracking-widest mt-1">Latency</div>
  </div>
</div>

B. Glassmorphism & Depth
Use semi-transparent backgrounds and blurs to create a sense of layering.

Markdown
<div class="absolute bottom-12 right-12 w-80 p-6 backdrop-blur-xl bg-white/60 rounded-2xl border border-white/30 shadow-2xl">
  <div class="flex items-center gap-2 mb-2">
    <span class="w-3 h-3 rounded-full bg-red-400"></span>
    <span class="font-bold text-gray-800 text-sm">Live Insight</span>
  </div>
  <p class="text-sm text-gray-600 leading-snug">
    Glassmorphism ensures text readability while maintaining a modern, airy feel over complex backgrounds.
  </p>
</div>

🎨 3. Global CSS Safety Net
Add this to your style.css to normalize AI-generated content across all slides.

CSS
/* style.css */
.slidev-layout h1 {
  @apply text-5xl font-black tracking-tight mb-6;
}

.slidev-layout p, .slidev-layout li {
  @apply text-lg leading-relaxed text-gray-700;
}

/* Auto-fit for Charts & Images */
canvas, svg, img {
  max-width: 100%;
  height: auto !important;
  @apply rounded-xl;
}