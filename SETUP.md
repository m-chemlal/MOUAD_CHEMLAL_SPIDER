# SPIDER animated GitHub profile — setup

This release has **no PNG, JPG, or GIF files**. The three self-hosted assets are **real animated SVGs** with vector gradients, continuously morphing paths, rotations, pulsing dots, and a blinking cursor. The contribution snake is generated as SVG by GitHub Actions, while Activity Pulse is generated daily using actual account data.

## 1. Publish to the special profile repository

GitHub displays a profile README only when the repository is **public**, its name is **exactly your username** (`m-chemlal/m-chemlal`), and the file is `README.md` in its root. If you currently have a private `m-chemlal` repository, **review all existing files, commit history, tokens and private information before changing its visibility**; otherwise create or use a safe profile repository. This ZIP doesn't change any repository remotely.

Upload `README.md`, the `assets/` directory and `.github/workflows/` as provided. **Do not flatten directories.**

## 2. Run the contribution snake (no personal access token needed)

In the profile repository, go to **Actions → Animated Contribution Snake → Run workflow**. The workflow creates an `output` branch containing `snake.svg` and `snake-dark.svg`, then GitHub will show them in the README. Ensure GitHub Actions has permission to write repository contents; some repositories require **Settings → Actions → General → Workflow permissions → Read and write permissions**.

## 3. Configure Activity Pulse (optional; actual stats)

The reference `lowlighter/metrics` workflow uses a GitHub personal access token for enhanced access. Add a limited-scope token to your repository's **Settings → Secrets and variables → Actions → New repository secret**, named **`METRICS_TOKEN`**. For a classic PAT, use only the scopes actually required for your metrics (the source template mentions `read:user`, optionally `repo` for private repositories; use least privilege and avoid unnecessary repository write access). Don't put the token in a README, a workflow YAML, or a ZIP. Run **Actions → Activity Pulse → Run workflow**. After a successful run, the file `metrics.activity.svg` appears and the README displays it.

## 4. Check animation

Open the SVG files through the **GitHub profile README** or a browser page that displays SVG animations. Some viewers (static image previews, screenshots, some Markdown clients, or reduced-motion settings) show only one frame. GitHub README doesn't execute custom JavaScript, CSS from HTML, or embedded iframe pages; this package intentionally uses SVG SMIL animation and Actions.

## 5. Visual reference

Inspired by templates in https://github.com/beydemirfurkan/awesome-github-profile : `neon-pulse-banner`, `typewriter-intro`, `tech-sphere`, `activity-pulse`, `snake-eat-graph`. Original custom banner, terminal, and pipeline SVGs were built for SPIDER, with the earlier customized SPIDER sphere reused. External projects: https://github.com/lowlighter/metrics and https://github.com/Platane/snk .
