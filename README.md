<p align="center">
  <img src="https://img.shields.io/badge/build-passing-brightgreen?style=flat-square" alt="Build Status" />
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License" />
  <img src="https://img.shields.io/badge/version-1.0.0-silver?style=flat-square" alt="Version" />
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square" alt="PRs Welcome" />
  <img src="https://img.shields.io/badge/zero-dependencies-black?style=flat-square" alt="Zero Dependencies" />
</p>

<h1 align="center">🔬 I'M MAD — Steganography Analyzer</h1>

<p align="center">
  <strong>Military-grade image forensics. Zero dependencies. One file.</strong><br/>
  <sub>Detect hidden data in images using Chi-Square analysis, RS Steganalysis, Shannon Entropy, Error Level Analysis, and more — all running client-side in the browser.</sub>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#%EF%B8%8F-live-demo">Demo</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-analysis-modules">Modules</a> •
  <a href="#-tech-stack">Stack</a> •
  <a href="#-how-it-works">How It Works</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-license">License</a>
</p>

---

## ✨ Features

| Feature | Description |
|:--------|:------------|
| **Chi-Square LSB Detection** | Statistical test that detects Least Significant Bit embedding with p-value scoring |
| **RS Steganalysis** | Regular-Singular group analysis to estimate hidden message capacity |
| **Shannon Entropy** | Per-channel entropy measurement to flag unnaturally high randomness |
| **Error Level Analysis (ELA)** | JPEG recompression differential to reveal tampered or embedded regions |
| **Noise Residual Analysis** | Isolates sensor noise patterns to detect anomalous injections |
| **Sobel Edge Detection** | Gradient-based edge map for visual stego artifact inspection |
| **FP-Killer Ensemble** | Multi-algorithm weighted verdict that eliminates false positives |
| **Metadata Extraction** | File structure, embedded signatures, and hex dump viewer |
| **String Extraction** | Scans raw bytes for hidden ASCII/Unicode text strings |
| **Batch Processing** | Drag-and-drop an entire folder — scans all images in one pass |
| **URL Scanning** | Paste any image URL to analyze remote images directly |
| **3D Particle Background** | Immersive Spline 3D scene with interactive particle system |

---

## 🖥️ Live Demo

> **[Click here to use the tool online](https://immad-khan.github.io/Advanced-Steganography-Detection-Image-Forensics/steneography-checker.html)**

Or simply open `steneography-checker.html` in any modern browser locally. No server, no install, no build step.

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/immad-khan/Advanced-Steganography-Detection-Image-Forensics.git

# Navigate into the directory
cd Advanced-Steganography-Detection-Image-Forensics


# Open in your default browser
start steneography-checker.html        # Windows
open steneography-checker.html         # macOS
xdg-open steneography-checker.html     # Linux
```

> **Requirements:** Any modern browser (Chrome, Firefox, Edge, Safari). Nothing else.

---

## 🔍 Analysis Modules

### Statistical Detection

```
┌──────────────────────────────────────────────────────────────┐
│                                                              │
│   Chi-Square Test          RS Steganalysis                   │
│   ┌─────────────┐         ┌─────────────────┐               │
│   │ p = 0.9834  │         │ R: 42.1%        │               │
│   │ ████████░░  │         │ S: 38.7%        │               │
│   │ LSB embed   │         │ Δ: 3.4% ← steg │               │
│   │ detected    │         │ capacity est.   │               │
│   └─────────────┘         └─────────────────┘               │
│                                                              │
│   Shannon Entropy          FP-Killer Ensemble                │
│   ┌─────────────┐         ┌─────────────────┐               │
│   │ R: 7.9142   │         │ Confidence: 87% │               │
│   │ G: 7.8934   │         │ Verdict:        │               │
│   │ B: 7.9201   │         │ STEGO DETECTED  │               │
│   │ High ⚠      │         │ (3/4 modules)   │               │
│   └─────────────┘         └─────────────────┘               │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### Visual Forensics

| Module | Output | Purpose |
|:-------|:-------|:--------|
| **ELA** | Heatmap overlay | Reveals JPEG recompression artifacts from embedding |
| **Noise Residuals** | Amplified noise map | Exposes unnatural noise patterns left by stego tools |
| **Sobel Edge** | Gradient magnitude | Highlights edge discontinuities from payload injection |

### Data Extraction

- **Metadata** — File signatures, structure validation, hex dump
- **Strings** — ASCII/Unicode text hidden in raw image bytes
- **Distribution** — Pixel intensity histograms per channel

---

## 🛠 Tech Stack

```
Frontend         Vanilla JavaScript (ES6+), HTML5 Canvas API
Typography       Orbitron 900 (Google Fonts)
3D Background    Spline Design (interactive particle system)
CSS Engine       Custom properties, backdrop-filter, keyframe animations
Architecture     Single-file, zero-dependency, fully client-side
```

---

## ⚙ How It Works

```
                    ┌─────────────┐
                    │  Image In   │
                    │ (file/URL)  │
                    └──────┬──────┘
                           │
                    ┌──────▼──────┐
                    │  Canvas API │
                    │  Decode     │
                    └──────┬──────┘
                           │
              ┌────────────┼────────────┐
              │            │            │
       ┌──────▼──┐  ┌─────▼─────┐  ┌──▼────────┐
       │ Pixel   │  │ Statistical│  │  Visual   │
       │ Extract │  │ Analysis   │  │ Forensics │
       └────┬────┘  └─────┬─────┘  └──┬────────┘
            │              │            │
            │      ┌───────┴───────┐    │
            │      │ • Chi-Square  │    │
            │      │ • RS Analysis │    │
            │      │ • Entropy     │    │
            │      └───────┬───────┘    │
            │              │            │
       ┌────▼────┐  ┌─────▼─────┐  ┌──▼────────┐
       │ Strings │  │ FP-Killer │  │ ELA +     │
       │ + Meta  │  │ Ensemble  │  │ Noise +   │
       │ + Hex   │  │ Verdict   │  │ Sobel     │
       └────┬────┘  └─────┬─────┘  └──┬────────┘
            │              │            │
            └──────────────┼────────────┘
                           │
                    ┌──────▼──────┐
                    │   Tabbed    │
                    │   Report    │
                    └─────────────┘
```

1. **Decode** — Image is loaded onto an HTML5 Canvas and pixel data is extracted via `getImageData()`
2. **Statistical Tests** — Chi-Square, RS, and Entropy algorithms run in parallel on raw RGBA buffers
3. **Visual Forensics** — ELA recompresses at quality 75, diffs against original; Noise and Sobel process luminance
4. **Ensemble Verdict** — FP-Killer weighs all module outputs and returns a confidence-scored verdict
5. **Report** — Results render into a tabbed interface with real-time progress indicators

---

## 📁 Project Structure

```
steg/
├── steneography-checker.html   # Entire application (single file)
├── README.md                   # You are here
└── .git/                       # Version control
```

> **Yes, it's one file.** ~1,950 lines of hand-written HTML, CSS, and JavaScript. No frameworks. No bundlers. No transpilers.

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **Fork** the repository
2. **Create** your feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Ideas for Contribution

- [ ] WebAssembly acceleration for large images
- [ ] EXIF/GPS metadata deep parser
- [ ] PDF and audio steganography support
- [ ] Export forensic reports as PDF
- [ ] Dark/light theme toggle
- [ ] Progressive Web App (PWA) support

---

## 📜 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

<p align="center">
  <sub>Built with obsessive attention to detail by <strong>Immad Ahmed</strong></sub><br/>
  <sub>If this tool helped you, consider giving it a ⭐</sub>
</p>
