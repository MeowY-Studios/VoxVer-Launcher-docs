---
layout: home
title: "VoxVer Launcher - Minecraft Launcher"
hero:
  name: "VoxVer Launcher"
  text: "新一代 Minecraft 启动器"
  tagline: "基于 Electron + Vue 3 + TypeScript 构建的现代化启动器 —— 启动核心、Mod 生态、崩溃分析开箱即用，支持简体中文和英文"
  image:
    src: /Alogo.png
    alt: VoxVer Launcher
  actions:
    - theme: brand
      text: 立即下载
      link: /guide/download
    - theme: alt
      text: 查看文档
      link: /guide/
---

<div class="home-section">
  <div class="home-stats">
    <div class="home-stat">
      <span class="num">4</span>
      <span class="label">大 ModLoader 一键安装<br/>Fabric · Forge · NeoForge · Quilt</span>
    </div>
    <div class="home-stat">
      <span class="num">2</span>
      <span class="label">大 Mod 平台接入<br/>Modrinth（CurseForge 计划中）</span>
    </div>
    <div class="home-stat">
      <span class="num">10</span>
      <span class="label">类崩溃特征智能识别<br/>原因分析 + 修复建议</span>
    </div>
    <div class="home-stat">
      <span class="num">6</span>
      <span class="label">位分享码 P2P 传实例<br/>WebRTC 直连，无需服务器</span>
    </div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">CORE / 核心能力</p>
  <h2 class="home-h2">不只是启动游戏</h2>
  <p class="home-lead">从启动核心到崩溃分析，VoxVer Launcher 把折腾 Minecraft 的每个环节都做成了顺手的工具。</p>

  <div class="home-featured">
    <div class="feature-card feature-card-split">
      <div class="fc-text">
        <span class="icon">🎮</span>
        <h3>XMCL 启动核心</h3>
        <p>基于成熟稳定的 XMCL 核心驱动启动流程。Java 版本按 MC 版本自动匹配（8 / 11 / 17 / 21 / 25），LWJGL 2/3 自动区分运行时。文件完整性校验 + 多源下载（官方源 + BMCLAPI），启动进度实时推送。</p>
        <span class="feature-tag">XMCL 核心驱动</span>
      </div>
      <div class="fc-terminal" aria-hidden="true">
        <div class="term-bar"><i></i><i></i><i></i><span>launch.log</span></div>
        <div class="term-body">
          <p class="cmd">› voxver launch 1.20.1 --fabric</p>
          <p class="ok">✓ 匹配 Java 21.0.3</p>
          <p class="ok">✓ 文件校验通过 · LWJGL 3</p>
          <p class="run">› BMCLAPI 下载中 87%…<span class="cursor"></span></p>
        </div>
      </div>
    </div>
    <div class="feature-card">
      <span class="icon">📚</span>
      <h3>Mod 一站式管理</h3>
      <p>Modrinth 搜索下载、依赖自动安装、自动更新检测、兼容性检查与导出。CurseForge 接入计划中。</p>
      <span class="feature-tag">双源 · 依赖检测</span>
    </div>
    <div class="feature-card">
      <span class="icon">💥</span>
      <h3>崩溃分析</h3>
      <p>游戏异常退出自动捕获并解析崩溃报告，独立分析页面给出原因与修复建议。</p>
      <span class="feature-tag">10 类崩溃特征识别</span>
    </div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">FEATURES / 完整功能</p>
  <h2 class="home-h2">该有的都有</h2>
  <div class="home-list">
    <div class="mini-card"><span class="mc-icon">◈</span><div><h4>微软正版登录</h4><p>Device Code Flow 认证，token 自动刷新，多账户切换</p></div></div>
    <div class="mini-card"><span class="mc-icon">◌</span><div><h4>离线模式</h4><p>自定义用户名离线登录，单机游玩无门槛</p></div></div>
    <div class="mini-card"><span class="mc-icon">▤</span><div><h4>版本管理</h4><p>BMCLAPI 版本列表，正式版 / 快照 / 远古版一键安装</p></div></div>
    <div class="mini-card"><span class="mc-icon">▦</span><div><h4>实例系统</h4><p>独立管理 Mod 与配置，支持 HMCL / PCL2 一键导入</p></div></div>
    <div class="mini-card"><span class="mc-icon">⇄</span><div><h4>P2P 实例分享</h4><p>6 位分享码或 voxver:// 协议链接，WebRTC 直连</p></div></div>
    <div class="mini-card"><span class="mc-icon">↻</span><div><h4>自动更新</h4><p>独立版本更新页，可取消下载，GitHub Releases 一键安装</p></div></div>
    <div class="mini-card"><span class="mc-icon">◐</span><div><h4>主题自定义</h4><p>色盘编辑器 + 背景自定义，浅色 / 深色主题切换</p></div></div>
    <div class="mini-card"><span class="mc-icon">⌘</span><div><h4>全局快捷键</h4><p>自定义快捷键，随时快速启动游戏</p></div></div>
    <div class="mini-card"><span class="mc-icon">▣</span><div><h4>皮肤管理</h4><p>玩家皮肤下载与前端渲染</p></div></div>
    <div class="mini-card"><span class="mc-icon">▥</span><div><h4>数据备份</h4><p>实例数据备份与迁移，安全可靠</p></div></div>
    <div class="mini-card"><span class="mc-icon">⌂</span><div><h4>自定义游戏路径</h4><p>.minecraft 目录随意安放，多启动器共存</p></div></div>
    <div class="mini-card"><span class="mc-icon">◍</span><div><h4>国际化</h4><p>简体中文 / English 双语界面实时切换</p></div></div>
  </div>
</div>

<div class="home-section">
  <p class="home-eyebrow">QUICK START / 快速上手</p>
  <h2 class="home-h2">三步开始游戏</h2>
  <div class="home-steps">
    <div class="home-step">
      <h3>下载安装</h3>
      <p>前往 GitHub Releases 下载对应平台安装包，Windows 双击安装即用；macOS 版本仍在计划中，敬请期待。</p>
    </div>
    <div class="home-step">
      <h3>登录账户</h3>
      <p>使用微软正版账号一键登录（Device Code Flow），或者用离线模式自定义用户名直接开始。</p>
    </div>
    <div class="home-step">
      <h3>选择版本，开始游玩</h3>
      <p>挑选 Minecraft 版本一键安装，需要 ModLoader 就再点一下，Java 会被自动匹配，点击启动即可。</p>
    </div>
  </div>
</div>

<div class="home-section">
  <div class="home-panels">
    <div class="home-panel">
      <h3>支持平台</h3>
      <div class="plat-list">
        <div class="plat-row">
          <span class="plat-icon">⊞</span>
          <span class="plat-name">Windows 10+</span>
          <span class="status-badge ok">已支持</span>
          <span class="arch-chip">x64</span>
        </div>
        <div class="plat-row">
          <span class="plat-icon">◧</span>
          <span class="plat-name">macOS</span>
          <span class="status-badge planned">计划中</span>
          <span class="arch-chip">x64</span>
          <span class="arch-chip">arm64</span>
        </div>
        <div class="plat-row">
          <span class="plat-icon">◫</span>
          <span class="plat-name">Linux</span>
          <span class="status-badge planned">计划中</span>
          <span class="arch-chip">x64</span>
        </div>
      </div>
    </div>
    <div class="home-panel">
      <h3>技术栈</h3>
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
    <h2>鸣谢</h2>
    <ul>
      <li><a href="https://github.com/Ink-Marks/StarLight.Core" target="_blank" rel="noreferrer">StarLight.Core</a> —— 模块化架构参考</li>
      <li><a href="https://github.com/Hex-Dragon/PCL2" target="_blank" rel="noreferrer">PCL2</a> —— UI 排版参考</li>
      <li><a href="https://bmclapi2.bangbang93.com" target="_blank" rel="noreferrer">BMCLAPI</a> —— Minecraft 版本文件国内镜像</li>
      <li><a href="https://meta.fabricmc.net" target="_blank" rel="noreferrer">Fabric Meta API</a> / <a href="https://docs.curseforge.com" target="_blank" rel="noreferrer">CurseForge API</a> / <a href="https://docs.modrinth.com" target="_blank" rel="noreferrer">Modrinth API</a> —— 版本与 Mod 元数据</li>
    </ul>
    <p>本项目基于 <a href="https://github.com/MeowY-Studios/VoxVer-Launcher/blob/main/LICENSE" target="_blank" rel="noreferrer">MIT 协议</a> 开源。Minecraft 是 Microsoft Corporation 的商标，本项目与 Mojang Studios 或 Microsoft 无关。</p>
  </div>
</div>

<div class="home-section">
  <div class="home-cta">
    <h2>准备好开始了吗？</h2>
    <p>下载 VoxVer Launcher，把折腾留给启动器，把时间留给游戏。</p>
    <div class="actions">
      <a class="VPButton medium brand" href="/guide/download">立即下载</a>
      <a class="VPButton medium alt" href="/guide/">查看文档</a>
      <a class="VPButton medium alt" href="https://github.com/MeowY-Studios/VoxVer-Launcher" target="_blank" rel="noreferrer">GitHub</a>
    </div>
  </div>
</div>
