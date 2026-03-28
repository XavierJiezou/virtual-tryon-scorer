# 🎯 Virtual Try-On Scorer

**English** | [简体中文](./README.md)

An Agent Skill for evaluating the quality of AI-powered virtual try-on (VTON) results. It performs structured scoring across four dimensions: identity preservation, garment fidelity, body consistency, and background stability.

![Uploading image.png…]()


## ✨ Features

- 🧑 **Face Identity Preservation** — Ensures the person's face remains consistent before and after try-on
- 👕 **Garment Fidelity & Fit** — Checks color, pattern, structure, and natural fit of the target garment
- 🦵 **Non-Face Body Consistency** — Verifies body shape, skin tone, hands, and accessories remain unchanged
- 🏞️ **Background Stability** — Validates scene, lighting, and edge blending consistency
- 📊 **Weighted Total Score** — Aggregates dimension scores based on importance weights

## 📐 Scoring System

| Dimension | Weight | Key Checks |
|-----------|--------|------------|
| Face Identity Preservation | **40%** | Facial structure, features, skin tone, expression, hairstyle |
| Garment Fidelity & Fit | **30%** | Color, pattern, structure, fabric texture, natural fit |
| Non-Face Body Preservation | **20%** | Body proportions, skin tone, hands, tattoos, accessories |
| Background Preservation | **10%** | Scene consistency, lighting, artifacts, edge blending |

**Total = Face × 0.4 + Garment × 0.3 + Body × 0.2 + Background × 0.1**

Each dimension is scored **0–100** with a brief text explanation.

## 📥 Input Formats

Two input methods are supported:

### Option A: Three Separate Images
Upload individually:
1. **Source Person Image** — the original photo of the person before try-on
2. **Target Garment Image** — the reference clothing item
3. **Try-On Result Image** — the AI-generated virtual try-on output

### Option B: Single Concatenated Image
Upload one image containing all three photos stitched together (horizontal, vertical, or grid layout). The skill automatically identifies each panel's content.

## 📤 Output Example

```
## Virtual Try-On Scoring Report

### Input Recognition
- Format: Three separate images
- Source Person: Asian female, long hair, wearing white T-shirt
- Target Garment: Red floral dress, V-neck design
- Try-On Result: Same female wearing red floral dress

### Dimensional Scores

#### 1. Face Identity Preservation (Weight: 40%)
- **Score: 92/100**
- Note: Facial features are highly consistent; skin tone is natural;
  only the jawline appears slightly softened.

#### 2. Garment Fidelity & Fit (Weight: 30%)
- **Score: 85/100**
- Note: Red floral pattern is well reproduced; V-neck structure is accurate;
  minor pattern distortion on the left sleeve.

#### 3. Non-Face Body Preservation (Weight: 20%)
- **Score: 88/100**
- Note: Body proportions are consistent; hands look natural;
  wristwatch is fully preserved.

#### 4. Background Preservation (Weight: 10%)
- **Score: 95/100**
- Note: Indoor background is identical; lighting is natural;
  smooth transition at person edges.

### Total Score
- **Weighted Total: 89.9/100**
- Formula: (92 × 0.4) + (85 × 0.3) + (88 × 0.2) + (95 × 0.1)

### Overall Assessment
Excellent try-on quality with strong face identity preservation
and high garment fidelity. Main improvement area: floral pattern
detail on the left sleeve.
```

## 🔧 Installation

### Global Installation (Available in All Projects)

Copy the `virtual-tryon-scorer` folder to your global skills directory:

**Antigravity IDE:**
```bash
cp -r virtual-tryon-scorer ~/.gemini/antigravity/skills/
```

**Claude Code:**
```bash
cp -r virtual-tryon-scorer ~/.claude/skills/
```

**Generic Agent (.agent standard):**
```bash
cp -r virtual-tryon-scorer ~/.agent/skills/
```

### Project-Level Installation (Current Project Only)

```bash
mkdir -p .agents/skills
cp -r virtual-tryon-scorer .agents/skills/
```

## 🚀 Usage

Once installed, the skill triggers automatically when you mention try-on scoring in conversation:

- "Score this virtual try-on result"
- "Evaluate the quality of this VTON output"
- "Rate this clothing transfer result"
- Upload before/after images and say "compare the try-on effect"

## 🔗 Compatibility

This skill follows the [Agent Skills open standard](https://agentskills.io/) and is compatible with:

| Tool | Global Path | Project Path |
|------|-------------|--------------|
| Antigravity IDE | `~/.gemini/antigravity/skills/` | `.agents/skills/` |
| Claude Code | `~/.claude/skills/` | `.claude/skills/` |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` |
| GitHub Copilot | `~/.copilot/skills/` | `.github/skills/` |
| OpenCode | `~/.config/opencode/skills/` | `.opencode/skills/` |
| Windsurf | `~/.codeium/windsurf/skills/` | `.windsurf/skills/` |

## 📄 License

MIT License

## 🙏 Acknowledgments

- [Anthropic Skills](https://github.com/anthropics/skills) — Agent Skills standard and specification
- [Agent Skills Open Standard](https://agentskills.io/) — SKILL.md format definition
