# AI Literacy Test v2.1

> 你的 AI 素养在哪个段位？— 一份检测 AI 理解深度与使用能力的交互式测评工具。

## 🎯 项目概述

这不是一份 AI 知识考卷，而是一次对用户**理解 AI 本质**与**驾驭 AI 方式**的综合诊断。通过 20 个精心设计的场景与判断题，评估用户在 6 大核心维度上的 AI 素养水平。

**在线体验**：[https://your-project.vercel.app](https://your-project.vercel.app)

---

## 📐 评估体系

### 6 大维度

| 维度 | 题数 | 考察内容 |
|------|------|---------|
| 🧠 模型认知 | 3 | 理解大模型的工作原理（next-token prediction、注意力机制、涌现能力） |
| ⚙️ 技术直觉 | 3 | 对模型能力边界的直觉判断（幻觉根因、长文本局限、精确计算弱项） |
| 🔥 前沿热点 | 3 | 对近期 AI 发展的理解（Reasoning Model、DeepSeek、Vibe Coding / Agent） |
| 🎯 使用能力 | 5 | 实际 AI 协作水平（纠错策略、Prompt 设计、多模型协作、上下文管理） |
| 🔍 批判思维 | 3 | 评估 AI 输出和行业话术的能力（基准测试解读、归因分析局限、信息溯源） |
| 🌐 战略视野 | 3 | 理解 AI 对行业和社会的深层影响（人才结构、竞争壁垒、发展方向） |

### 5 级段位

| 段位 | 名称 | 分数区间 | 画像 |
|------|------|---------|------|
| Lv.1 | AI 旁观者 The Observer | ≤35% | 存在多项核心误解，AI 是"黑箱" |
| Lv.2 | AI 使用者 The User | 36-50% | 能用工具但对原理理解浅层 |
| Lv.3 | AI 实践者 The Practitioner | 51-68% | 使用熟练、理解原理、能识别常见误区 |
| Lv.4 | AI 策略家 The Strategist | 69-85% | 深入理解技术本质，能做独立判断 |
| Lv.5 | AI 架构师 The Architect | 86-100% | 全维度高分，兼具技术洞察和战略视野 |

---

## 🧩 题目设计原则

### 反套路机制

传统测评往往最长的选项就是最优解、正确答案总在 C/D。本测评通过以下机制打破这些模式：

- **最优解长度不固定**：3 题最优解是最短选项，2 题是最长选项，其余居中
- **最优解位置分散**：A/B/C/D 均匀分布，无连续 3 题出现相同位置
- **选项展示顺序随机**：每题的 ABCD 排列使用确定性种子的 Fisher-Yates 洗牌
- **高级陷阱设计**：堆砌术语但本质错误的选项（如 Q11 的华丽角色扮演 prompt）
- **朴素正确设计**：看似简单但精准触及本质的选项（如 Q1 的 next-token prediction）

### 分数阶梯（每题 1-4 分）

- **1 分**：常见误解或表层认知
- **2 分**：方向正确但不够深入
- **3 分**：合理但非最优的判断
- **4 分**：精准触及本质的理解

---

## 🛠 技术栈

- **纯静态 HTML/CSS/JS**，无框架依赖，零构建步骤
- **响应式设计**，适配桌面和移动端
- **Canvas 雷达图**，6 维能力可视化
- **CSS 动画**，页面转场、进度条、结果展示动效
- **键盘快捷键**，桌面端支持 1-4 选择 + Enter 翻页
- **Google Fonts**：Noto Sans SC（正文）+ DM Mono（数据/标签）

---

## 🚀 部署

### Vercel（推荐）

```bash
# 1. 安装 Vercel CLI（如已安装跳过）
npm i -g vercel

# 2. 进入项目目录
cd ai-literacy-test

# 3. 部署
vercel

# 4. 部署到生产环境
vercel --prod
```

或者直接通过 Vercel Dashboard：

1. 前往 [vercel.com/new](https://vercel.com/new)
2. Import Git Repository 或拖拽上传项目文件夹
3. Framework Preset 选 **Other**
4. Output Directory 填 `public`
5. 点击 Deploy

### 其他平台

由于是纯静态项目，也可部署到 Netlify / GitHub Pages / Cloudflare Pages 等任何静态托管平台，只需将 `public/index.html` 作为入口即可。

---

## 📁 项目结构

```
ai-literacy-test/
├── public/
│   └── index.html      # 主页面（单文件，含所有逻辑和样式）
├── vercel.json          # Vercel 部署配置
├── package.json         # 项目元信息
└── README.md            # 本文档
```

---

## 📝 自定义与扩展

### 修改题目

所有题目数据在 `index.html` 的 `QS` 数组中。每题格式：

```javascript
{
  cat: 'Category Name',     // 显示在题目上方的分类标签
  dim: 'dimension_key',     // 对应 DIMS 中的维度 key
  text: '题目文本',
  opts: [
    { t: '选项文本', s: 1 },  // s = 分数 (1-4)
    { t: '选项文本', s: 4 },
    { t: '选项文本', s: 2 },
    { t: '选项文本', s: 3 },
  ]
}
```

### 修改维度

在 `DIMS` 数组中增减维度：

```javascript
{ k: 'key', n: '显示名称', c: '#颜色' }
```

### 修改段位

在 `PROFILES` 数组中调整段位描述和建议，在 `result()` 函数中调整分数阈值。

---

## License

MIT
