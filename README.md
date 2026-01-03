# CryptoPlanet Community NFT (Generative)

一个由社区共创的「生成式 NFT」项目：traits 素材库 + 生成脚本 + metadata + 贡献者机制（badges / allowlist）。
第一批 NFT 主要发放给社区 OG 与贡献者（Proof-of-Contribution）。

---

## 1. 为什么做这个？

我们想做的不是“卖图”，而是把它做成一个可复用的社区生产线：

- 视觉素材库（透明 PNG 分层 traits）
- 生成器脚本（规则叠图 + 随机组合 + 稀有度控制）
- 标准化 metadata（属性、编号、稀有度）
- 公开透明的共创流程（认领任务、提交 PR、评审、积分/徽章）

目标：让更多人都能参与，并留下可验证的贡献记录。

---

## 2. 项目阶段（Roadmap）

Sprint 1 - 跑通生产线（MVP）
- [ ] 确定画布尺寸（默认：1024x1024）
- [ ] 确定分层顺序（layer order）与命名规范
- [ ] 生成器输出：images/ + metadata/
- [ ] 生成 200 张预览图用于社区评审

Sprint 2 - 社区化风格 & 规则
- [ ] 征集社区元素（梗/符号/身份标识）
- [ ] 投票选入 traits 库
- [ ] 稀有度权重表（rarity weights）
- [ ] 冲突/排除/依赖规则（rules）

Sprint 3 - 小规模发行
- [ ] 先小规模（建议 200–500）发给 OG & 贡献者
- [ ] 复盘：丑图剔除、受欢迎 traits、稀有度分布
- [ ] 再决定是否扩到更大规模

---

## 3. 如何参与（How to Join）

你不需要会画画或会写代码也能参与。我们把任务拆成四类：

A) 美术/设计
- 制作 traits（透明 PNG 分层）
- 统一风格、色板、命名规范
- 输出分层素材并按规范提交

B) 工程/脚本
- 叠图生成、稀有度、冲突规则、去重
- 导出 metadata（JSON）
- 提供预览/校验/统计工具

C) 质检/运营
- 发起投票、收集反馈
- 生成后的丑图筛选与标注原因
- 稀有度分布检查、命名校对

D) 文档/规范
- 贡献指南（CONTRIBUTING）
- 素材规范（traits spec）
- License/版权说明与反诈骗提示

参与流程（建议）：
- 到 Issues / Projects 认领任务
- Fork 本仓库
- 提交 PR（包含说明与截图/预览）
- Review 通过后合并

---

## 4. 仓库结构（Repo Structure）

.
├── assets/                 traits 素材库（分层 PNG）
│   ├── background/
│   ├── body/
│   ├── eyes/
│   ├── mouth/
│   ├── hair/
│   ├── accessory/
│   └── ...
├── config/
│   ├── layers.json         图层顺序定义
│   ├── rarity.json         稀有度权重表
│   └── rules.json          冲突/排除/依赖规则
├── scripts/
│   ├── generate.*          生成器入口（Node 或 Python）
│   ├── preview.*           预览/抽样工具
│   └── validate.*          校验工具（尺寸/命名/重复/规则）
├── output/
│   ├── images/             生成出的图片（不建议长期提交到 git）
│   └── metadata/           生成出的 metadata（不建议长期提交到 git）
├── CONTRIBUTING.md
├── LICENSE
└── README.md

---

## 5. 快速开始（Quick Start）

说明：生成器可以用 Node.js 或 Python。下面命令是占位示例，你可以按最终实现替换。

选项 A：Node.js（canvas）
1) 安装依赖
npm install

2) 生成（示例）
npm run generate -- --count 200 --seed 123

3) 校验与统计（示例）
npm run validate
npm run rarity-report

选项 B：Python（Pillow）
1) 创建环境
python -m venv .venv
source .venv/bin/activate
Windows: .venv\Scripts\activate

2) 安装依赖
pip install -r requirements.txt

3) 生成（示例）
python scripts/generate.py --count 200 --seed 123

4) 校验（示例）
python scripts/validate.py

---

## 6. 素材规范（Traits Spec）

请尽量统一，避免生成后出现“层级错位/风格破碎”。

- 格式：PNG（透明背景）
- 尺寸：1024x1024（或项目统一尺寸）
- 命名：英文小写 + 下划线，例如 laser_eyes.png
- 对齐：所有 traits 对齐同一锚点（不要漂移）
- 分层：一个文件只放该层内容，不要混层

---

## 7. 稀有度与规则（Rarity & Rules）

我们用配置文件保证可复现：

- config/rarity.json：每个 trait 的权重（weight）
- config/rules.json：冲突（conflict）、依赖（requires）、排除（excludes）

规则示例（伪代码）：
- hat_a 与 hair_b 冲突（不能同时出现）
- glasses 出现时，部分 eyes trait 禁用
- special_background 出现时，accessory 概率降低

---

## 8. 贡献与奖励（Proof-of-Contribution）

我们会记录贡献（PR / Issue / Review / 素材提交 / 质检）：

- 合并的 PR 会被计入贡献记录
- 贡献者可获得 Discord 角色/徽章（Badge）
- 第一批 NFT Allowlist 主要面向 OG 与贡献者

注意：本项目不承诺任何金融收益，不构成投资建议。

---

## 9. 安全提示（Anti-Scam）

- 我们不会私聊索要助记词/私钥/转账/下载不明软件
- 只在官方公告渠道发布链接与流程
- 任何主动私聊你的“官方人员”基本都是骗子

---

## 10. License / 版权说明

建议：
- 代码部分：MIT License
- 素材部分：CC BY-NC 4.0 或项目自定义许可（看是否允许商业使用）

提交素材即表示：你拥有版权或有权授权该素材在本项目中使用。

---

## 11. 讨论与协作

- Discord：以公告频道为准
- Issues：提需求、报 bug、认领任务
- PR：提交代码 / 素材 / 文档改进

---

## 12. 致谢

感谢所有参与共创的社区成员。
让我们把它做成一个“能跑、可复用、可验证”的社区作品。
