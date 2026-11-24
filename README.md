# Perplexity Explorer

An interactive, in-browser educational tool to explore and understand language model perplexity from real token probabilities step-by-step.

Built as a single-page application with HTML, CSS, and plain JavaScript—running a real quantized language model directly in the browser with **Transformers.js** (no backend, API keys, or frameworks required).

---

## Features

- **Real In-Browser Language Model**: Runs `Xenova/distilgpt2` (q8) locally via WebAssembly / WebGPU using Transformers.js.
- **Section 1 – Type a Sentence**: Quick presets or custom text with real-time download and inference status tracking.
- **Section 2 – Token Probabilities & Perplexity Walkthrough**:
  - Full breakdown of token IDs, tokens (with spaces shown as `␣`), probabilities $P$, and surprisals $1/P$.
  - 3-step geometric mean calculation:
    1. Multiply all $1/P$ values
    2. Count tokens $N$
    3. Calculate perplexity: $\text{Perplexity} = (\text{product})^{1/N} = \exp\left(\frac{1}{N}\sum -\ln P_i\right)$
- **Section 3 – Next Token Prediction**: Shows the top 8 candidate tokens predicted by DistilGPT-2 at the final position with visual probability bars.
- **Section 4 – Interactive Simulation**: Manually experiment with token probabilities or test presets (e.g. *“I love Python”*, *“All 1/8”*, *“One surprising word”*) to see how perplexity reacts in real time.

---

## How to Run

Simply open `index.html` in any modern web browser or serve it with a local static server:

```bash
# Using Python
python3 -m http.server 5500

# Using Node.js (npx)
npx serve .
```

Then visit `http://localhost:5500`.

---

## License

MIT
