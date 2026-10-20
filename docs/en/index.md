---
layout: home
title: "VoxVer Launcher - Minecraft Launcher"
hero:
  name: "VoxVer Launcher"
  text: "A Next-Gen Minecraft Launcher"
  tagline: "A modern launcher built with Electron + Vue 3 + TypeScript — launch core, mod ecosystem and crash analysis out of the box. Available in Chinese and English"
  image:
    src: /Alogo.png
    alt: VoxVer Launcher
  actions:
    - theme: brand
      text: Download
      link: /en/guide/download
    - theme: alt
      text: Read the Docs
      link: /en/guide/
---

<div class="home-section">
  <div class="home-stats">
    <div class="home-stat">
      <span class="num">4</span>
      <span class="label">ModLoaders, one-click install<br/>Fabric · Forge · NeoForge · Quilt</span>
    </div>
    <div class="home-stat">
      <span class="num">2</span>
      <span class="label">mod platform integrated<br/>Modrinth (CurseForge planned)</span>
    </div>
    <div class="home-stat">
      <span class="num">10</span>
      <span class="label">crash signatures recognized<br/>causes + fix suggestions</span>
    </div>
    <div class="home-stat">
      <span class="num">6</span>
      <span class="label">-digit codes to share instances<br/>WebRTC P2P, no server needed</span>
    </div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">CORE / Core Capabilities</p>
  <h2 class="home-h2">More than just launching the game</h2>
  <p class="home-lead">From the launch core to crash analysis, VoxVer Launcher turns every part of wrangling Minecraft into a tool that just works.</p>

  <div class="home-featured">
    <div class="feature-card feature-card-split">
      <div class="fc-text">
        <span class="icon">🎮</span>
        <h3>XMCL Launch Core</h3>
        <p>Powered by the proven, stable XMCL launch core. Java versions are auto-matched to your MC version (8 / 11 / 17 / 21 / 25), with LWJGL 2/3 runtimes selected automatically. File integrity checks + multi-source downloads (official + BMCLAPI) with real-time launch progress.</p>
        <span class="feature-tag">Powered by XMCL core</span>
      </div>
      <div class="fc-terminal" aria-hidden="true">
        <div class="term-bar"><i></i><i></i><i></i><span>launch.log</span></div>
        <div class="term-body">
          <p class="cmd">› voxver launch 1.20.1 --fabric</p>
          <p class="ok">✓ Java 21.0.3 matched</p>
          <p class="ok">✓ Files verified · LWJGL 3</p>
          <p class="run">› Downloading via BMCLAPI 87%…<span class="cursor"></span></p>
        </div>
      </div>
    </div>
    <div class="feature-card">
      <span class="icon">📚</span>
      <h3>One-Stop Mod Management</h3>
      <p>Search and download from Modrinth, with dependency auto-install, update detection, compatibility checks and zip export. CurseForge integration is planned.</p>
      <span class="feature-tag">Dual-source · dependency detection</span>
    </div>
    <div class="feature-card">
      <span class="icon">💥</span>
      <h3>Crash Analysis</h3>
      <p>Crash reports are captured and parsed automatically on abnormal exit, with a dedicated analysis page offering causes and fix suggestions.</p>
      <span class="feature-tag">10 crash signature categories</span>
    </div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">FEATURES / Full Feature Set</p>
  <h2 class="home-h2">Everything you need</h2>
  <div class="home-list">
    <div class="mini-card"><span class="mc-icon">◈</span><div><h4>Microsoft authentication</h4><p>Device Code Flow login, automatic token refresh, multi-account switching</p></div></div>
    <div class="mini-card"><span class="mc-icon">◌</span><div><h4>Offline mode</h4><p>Custom username offline login for single-player</p></div></div>
    <div class="mini-card"><span class="mc-icon">▤</span><div><h4>Version management</h4><p>BMCLAPI version list, one-click install for release / snapshot / legacy</p></div></div>
    <div class="mini-card"><span class="mc-icon">▦</span><div><h4>Instance system</h4><p>Isolated mods and configs, one-click import from HMCL / PCL2</p></div></div>
    <div class="mini-card"><span class="mc-icon">⇄</span><div><h4>P2P instance sharing</h4><p>6-digit codes or voxver:// links over WebRTC direct connection</p></div></div>
    <div class="mini-card"><span class="mc-icon">↻</span><div><h4>Auto update</h4><p>Standalone update page, cancellable downloads, one-click install from GitHub Releases</p></div></div>
    <div class="mini-card"><span class="mc-icon">◐</span><div><h4>Theme customization</h4><p>Color palette editor, custom backgrounds, light / dark themes</p></div></div>
    <div class="mini-card"><span class="mc-icon">⌘</span><div><h4>Global hotkeys</h4><p>Custom shortcuts to launch the game instantly</p></div></div>
    <div class="mini-card"><span class="mc-icon">▣</span><div><h4>Skin management</h4><p>Player skin download and in-app rendering</p></div></div>
    <div class="mini-card"><span class="mc-icon">▥</span><div><h4>Data backup</h4><p>Instance backup and migration, safe and reliable</p></div></div>
    <div class="mini-card"><span class="mc-icon">⌂</span><div><h4>Custom game path</h4><p>Put .minecraft anywhere, coexist with other launchers</p></div></div>
    <div class="mini-card"><span class="mc-icon">◍</span><div><h4>Internationalization</h4><p>Simplified Chinese / English with live switching</p></div></div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">QUICK START / Get Going</p>
  <h2 class="home-h2">Playing in three steps</h2>
  <div class="home-steps">
    <div class="home-step">
      <h3>Download & Install</h3>
      <p>Grab the installer for your platform from GitHub Releases. Double-click to install on Windows; macOS builds are still in planning — stay tuned.</p>
    </div>
    <div class="home-step">
      <h3>Sign In</h3>
      <p>Log in with your Microsoft account (Device Code Flow), or jump straight in with offline mode and a custom username.</p>
    </div>
    <div class="home-step">
      <h3>Pick a Version & Play</h3>
      <p>Choose a Minecraft version and install it in one click. Need a ModLoader? One more click. Java is matched automatically — then hit launch.</p>
    </div>
  </div>
</div>

<div class="home-section">
  <div class="home-panels">
    <div class="home-panel">
      <h3>Supported Platforms</h3>
      <div class="plat-list">
        <div class="plat-row">
          <span class="plat-icon">⊞</span>
          <span class="plat-name">Windows 10+</span>
          <span class="status-badge ok">Supported</span>
          <span class="arch-chip">x64</span>
        </div>
        <div class="plat-row">
          <span class="plat-icon">◧</span>
          <span class="plat-name">macOS</span>
          <span class="status-badge planned">Planned</span>
          <span class="arch-chip">x64</span>
          <span class="arch-chip">arm64</span>
        </div>
        <div class="plat-row">
          <span class="plat-icon">◫</span>
          <span class="plat-name">Linux</span>
          <span class="status-badge planned">Planned</span>
          <span class="arch-chip">x64</span>
        </div>
      </div>
    </div>
    <div class="home-panel">
      <h3>Tech Stack</h3>
      <div class="pill-cloud">
        <span class="pill">Electron <b>42.6</b></span>
        <span class="pill">Vue <b>3.5</b></span>
        <span class="pill">electron-vite <b>5.0</b></span>
        <span class="pill">TypeScript <b>5.5</b></span>
        <span class="pill">better-sqlite3 <b>12.0</b></span>
      </div>
    </div>
  </div>

  <div class="home-footnote">
    <h2>Acknowledgements</h2>
    <ul>
      <li><a href="https://github.com/Ink-Marks/StarLight.Core" target="_blank" rel="noreferrer">StarLight.Core</a> — modular architecture reference</li>
      <li><a href="https://github.com/Hex-Dragon/PCL2" target="_blank" rel="noreferrer">PCL2</a> — UI layout reference</li>
      <li><a href="https://bmclapi2.bangbang93.com" target="_blank" rel="noreferrer">BMCLAPI</a> — Minecraft version file mirror</li>
      <li><a href="https://meta.fabricmc.net" target="_blank" rel="noreferrer">Fabric Meta API</a> / <a href="https://docs.curseforge.com" target="_blank" rel="noreferrer">CurseForge API</a> / <a href="https://docs.modrinth.com" target="_blank" rel="noreferrer">Modrinth API</a> — version & mod metadata</li>
    </ul>
    <p>This project is open source under the <a href="https://github.com/MeowY-Studios/VoxVer-Launcher/blob/main/LICENSE" target="_blank" rel="noreferrer">MIT License</a>. Minecraft is a trademark of Microsoft Corporation. This project is not affiliated with Mojang Studios or Microsoft.</p>
  </div>
</div>

<div class="home-section">
  <div class="home-cta">
    <h2>Ready to start?</h2>
    <p>Download VoxVer Launcher and leave the wrangling to the launcher — the game time is yours.</p>
    <div class="actions">
      <a class="VPButton medium brand" href="/en/guide/download">Download</a>
      <a class="VPButton medium alt" href="/en/guide/">Read the Docs</a>
      <a class="VPButton medium alt" href="https://github.com/MeowY-Studios/VoxVer-Launcher" target="_blank" rel="noreferrer">GitHub</a>
    </div>
  </div>
</div>
