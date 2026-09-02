# Web to EXE — Website

Official landing page for **Web to EXE**, a Windows desktop utility designed to turn supported web-project ZIP files into Windows `.exe` applications without requiring users to manually configure Electron, Node.js, or the packaging workflow.

> **Current status:** Web to EXE V1 is focused on simple, local Windows packaging for basic web projects.

---

## What is Web to EXE?

Web to EXE simplifies the process of packaging a basic web project as a Windows desktop application.

Instead of manually setting up Electron, configuring packaging files, installing build tools, and running terminal commands, the user provides a ZIP containing a supported project and Web to EXE handles the packaging workflow locally.

### Simple idea

```text
Web project ZIP
      ↓
Inspect & validate
      ↓
Prepare desktop wrapper
      ↓
Build with Electron
      ↓
Windows EXE
```

The current V1 is intentionally focused on keeping this workflow simple and understandable.

---

## Website Purpose

This repository contains the **official product/download website** for Web to EXE.

The website is designed to:

- Explain what Web to EXE does.
- Show how the local ZIP-to-EXE workflow works.
- Clearly state which project types are currently supported.
- Explain the Windows SmartScreen warning that may appear for an unsigned build.
- Provide a clear **Download for Windows** call to action.
- Give visitors background information about the project.
- Link back to the creator's GitHub profile.

The website is a single-page experience with smooth scrolling and lightweight visual effects.

---

## Website Sections

The landing page contains:

1. **Hero**
   - Product introduction.
   - Main Windows download CTA.
   - Quick overview of the ZIP → EXE workflow.

2. **What is Web to EXE?**
   - Explains the purpose of the application.

3. **How It Works**
   - Upload ZIP.
   - Inspect the project.
   - Prepare the Electron desktop wrapper.
   - Build the Windows executable.
   - Download the result.

4. **Supported Projects**
   - Explains the current V1 compatibility.

5. **Windows SmartScreen Notice**
   - Explains why Windows may display an unrecognized-app warning.
   - Shows the user where to select **More info**.
   - Shows the user where **Run anyway** appears.

6. **Download for Windows**
   - Main download area for the portable Web to EXE application.

7. **About**
   - Short background on the goal of the project.

8. **Footer**
   - Creator attribution and GitHub link.

---

## Supported Projects — V1

Web to EXE V1 is deliberately limited instead of pretending to support every web stack.

### Supported

- HTML
- CSS
- Vanilla JavaScript
- Basic static web projects
- Basic vanilla Vite projects supported by the current build engine

### Not the current focus

Broader framework support is planned for later versions rather than being forced into V1.

Future versions may expand compatibility and packaging options based on testing and actual usage.

---

## How Web to EXE Works

Web to EXE runs the packaging process **locally on the user's Windows PC**.

The general workflow is:

### 1. Upload
The user selects a `.zip` containing the web project.

### 2. Extract
Web to EXE extracts the project into a temporary build workspace.

### 3. Inspect
The application looks for the expected project structure and entry files.

### 4. Validate
Basic checks are performed before packaging so obvious project problems can be reported earlier.

### 5. Prepare
Web to EXE creates the Electron desktop wrapper required for the project.

### 6. Build
Electron and `electron-builder` are used to package the project as a Windows application.

### 7. Download
After a successful build, the generated Windows `.exe` is made available to the user.

---

## Local-First Design

Web to EXE V1 is designed around **local builds**.

That means the core packaging process runs on the user's own Windows computer rather than sending the uploaded project to a remote build server.

This approach keeps the first version focused and avoids introducing unnecessary cloud infrastructure into the core packaging workflow.

---

## Windows SmartScreen Warning

The current Web to EXE build may trigger a Microsoft Defender SmartScreen message such as:

> **Windows protected your PC**

This can happen because a new or unsigned executable may not yet have established publisher/reputation information with Windows.

The warning **does not by itself mean that Windows detected malware**.

The website includes a visual guide showing the SmartScreen flow:

```text
Windows protected your PC
        ↓
More info
        ↓
Run anyway
```

Users should still only run software they intentionally downloaded from a source they trust.

A future signed release can improve the installation/download experience.

---

## Tech Used for the Website

The landing page intentionally stays lightweight.

- **HTML** — structure and content
- **CSS** — responsive design, layout, visual system, and effects
- **JavaScript** — small interaction and scroll-related enhancements

No heavy frontend framework is required for the website.

---

## Project Structure

A typical copy of the website repository looks like:

```text
Web-to-EXE-website/
│
├── index.html
├── styles.css
├── script.js
├── README.md
│
└── assets/
    ├── smartscreen-step1.png
    ├── smartscreen-step2.png
    └── Web-to-EXE-0.1.8-Portable.exe
```

> For public deployment, hosting the large portable executable through **GitHub Releases** and linking the website's download button to the release asset is cleaner than keeping large binaries in normal Git history.

---

## Run the Website Locally

The website has no complicated setup.

### Option 1 — Open directly

Clone/download the repository and open:

```text
index.html
```

in a modern browser.

### Option 2 — Use a local development server

If you use VS Code, you can serve the folder with a static development server such as Live Server.

No application backend is required for the landing page itself.

---

## Deployment

Because the website is static, it can be deployed on platforms such as:

- Netlify
- Vercel
- GitHub Pages
- Any ordinary static web host

For this project, a straightforward production setup is:

```text
Website
   ↓
Netlify / static hosting

Application binary
   ↓
GitHub Releases

Download button
   ↓
Direct release asset
```

This keeps website deployment lightweight while keeping compiled application releases separate from the website source.

---

## Download Button

The website's Windows download CTA can either:

1. Reference a local file in `assets/`, or
2. Point to the latest executable hosted through **GitHub Releases**.

For a public deployment, the second approach is recommended.

Example:

```html
<a href="YOUR_GITHUB_RELEASE_ASSET_URL">
  Download for Windows
</a>
```

Replace the placeholder with the release asset URL when publishing.

---

## Design Direction

The website is intentionally different from the Web to EXE desktop application's interface.

The landing page uses:

- Stronger visual hierarchy.
- Multiple accent colors.
- More expressive typography.
- Product-focused storytelling.
- Less repetitive card-based UI.
- Responsive desktop/mobile layouts.
- Lightweight motion instead of unnecessary animation.

The goal is for the website to feel like a real product landing page rather than a generic generated template.

---

## Roadmap

Web to EXE is being developed incrementally.

### V1
- Local Windows packaging.
- HTML / CSS / JavaScript projects.
- Basic vanilla Vite support.
- ZIP input.
- Basic project validation.
- Automatic Electron wrapper.
- Windows `.exe` output.
- Clear build status and error handling.

### Future versions

Potential future directions include:

- Broader framework compatibility.
- Improved project analysis.
- Better packaging controls.
- Improved diagnostics.
- Code-signed Windows releases.
- Additional platform/build options where practical.

Features are not considered complete until they have been implemented and tested.

---

## Repository Scope

This repository is for the **Web to EXE website**.

The website and the Web to EXE packaging application are separate parts of the project:

```text
Web to EXE Website
→ Product information + download experience

Web to EXE Application
→ Actual local ZIP-to-EXE packaging engine
```

Keeping them separate makes the website easier to deploy and the application easier to develop independently.

---

## Creator

Built by **Mohammed Zaid**.

GitHub: [mohammedzaid00100](https://github.com/mohammedzaid00100)

---

## Project Note

Web to EXE is still evolving. Compatibility, UI, packaging behavior, and distribution may change as the application is tested on more Windows systems.

If you are testing a release, use a backup copy of your web project and verify the generated application before distributing it.
