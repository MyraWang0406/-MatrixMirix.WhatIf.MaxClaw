# MatrixMirix.WhatIf × MaxClaw

> EverMemOS Hackathon 版本 — 接入 EverMemOS Cloud 长期记忆 + ECharts K线美化

## 改动说明

### 1. K线图美化 (KLineChart.tsx)
- 从 SVG 折线图升级为 **ECharts 真实蜡烛图 (candlestick)**
- 视觉风格参考 [lifekline.ai](https://www.lifekline.ai)
- 红色=运势上行，绿色=运势下行（中国股票色系）
- 带悬停 tooltip、底部趋势区域、响应式自适应

### 2. EverMemOS Cloud 接入 (evermemos.ts)
- **无需自建服务器！** 直接接 EverMemOS Cloud 托管 API
- Base URL: `https://api.evermind.ai`
- 支持：存档案、存悔棋记录、存WhatIf推演、检索相似场景

## 快速开始

### 1. 获取 EverMemOS API Key
1. 访问 https://console.evermind.ai 注册
2. 创建 Memory Space（选择 Scenario Mode）
3. 点击 "Create API Key"，复制 Key

### 2. 配置环境变量
```bash
cp .env.example .env
# 编辑 .env，填入你的 API Key：
# VITE_EVERMEMOS_CLOUD_KEY=your_api_key_here
```

### 3. 安装并启动
```bash
npm install
npm run dev
```

## 部署到 Cloudflare Pages

1. Fork 这个仓库到你的 GitHub
2. 打开 Cloudflare Pages → Create a project → Connect to Git
3. 选择这个仓库，配置：
   - Build command: `npm run build`
   - Build output directory: `dist`
4. 在 **Settings → Environment Variables** 添加：
   - `VITE_EVERMEMOS_CLOUD_KEY` = 你的 API Key
5. 点击 Save and Deploy ✅

## EverMemOS Cloud API 说明

| 功能 | 端点 |
|------|------|
| 存记忆 | POST /api/v0/memories |
| 查记忆 | GET /api/v0/memories |
| 搜记忆 | GET /api/v0/memories/search |

认证：`Authorization: Bearer <api-key>`

文档：https://docs.evermind.ai
