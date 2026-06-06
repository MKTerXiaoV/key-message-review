# Handoff — 关键信息体检（关键信息体检 skill）

只记**事实**：文件构成、各管什么、怎么验证。要读"为什么"看 `PRODUCT.md`。

最后更新：v0.1.0（首版骨架）

## 目录结构

```
key-message-review/
├── SKILL.md                  # 入口：4步工作流 + 三档 + 评级 + references索引 + 红线
├── PRODUCT.md                # 为什么：解决"看不出自己在说正确的废话"
├── HANDOFF.md                # 本文件
├── 能力圈.md                  # 做什么 / 不做什么 + NON-NEGOTIABLE
├── EXTEND.example.md         # 用户偏好模板（复制为 EXTEND.md 填真实数据/禁用词）
├── references/               # 方法内核，按需加载
│   ├── 大词虚词黑名单.md       #   扫空话三类 + 改写方向
│   ├── 有效信息三要素.md       #   具体病人 / 可记一句话 / 医生动作 + 主信息结构
│   ├── 策略可执行性检验.md     #   主谓宾还原法，判定定位虚不虚
│   ├── 合规红线.md            #   绝对化/裸数据/超适应症/禁用词 7 条
│   ├── 视觉信息权重倒挂.md     #   展架/海报/slide 专用：大字玻璃珠、脚注藏钻石
│   └── 评分卡.md             #   及格/良好/优秀 判定 + 固定输出格式
├── assets/
│   └── compare-card.html     # 对比卡模板：Guizang Swiss 数据驱动（accent 可切；改后支持 diamond/supports 两结构）
├── scripts/
│   └── render-card.mjs       # 把对比卡 HTML 渲染成 PNG（playwright）
├── examples/
│   ├── 络平宁-高血压-样张.md   # 全脱敏样张（虚构降压药，跑完 4 步）
│   └── 络平宁-card.json       # 对比卡数据，喂给 render-card.mjs
└── _private/                 # ⚠ 内部产物，.gitignore，不打包不发布
                              #   （如竞品分析对比卡——含真实竞品衍生内容，不可对外）
```

> **对外 / 内部分界**：`examples/` 只放虚构产品、可公开；真实竞品/客户衍生的产出一律进 `_private/`，由 `.gitignore` 挡住，不随产品分发。

## 脱敏铁律（改文件时必守）

1. **零私域来源信息**：无任何方法论来源人名、无招牌比喻、无可追溯案例。
2. **示例只用虚构产品**，且避开东家真实管线领域（当前用高血压）。
3. 方法表述均为原创，非复制私域文档。

## 怎么验证

- 内容自检：全仓不得出现任何方法论来源人名（人工抽查 + 内部维护一份私有禁词表，不写入仓库）。
- 对比卡：`cd examples && node ../scripts/render-card.mjs 络平宁-card.json out.png`，应生成 1080×1440 PNG（Swiss 风），文字清晰、改前灰色删除线、改后强调色，**页脚不被裁切**。
- 对比卡溢出自检：content scrollHeight 应 ≤ 1440（内容多时优先精简文案，勿超）。
- 依赖：render 需 playwright；无则自动回退系统 Chrome（脚本已内置）。

## 已完成（v0.1 → v0.2）

- [x] 对比卡固化为 Guizang **Swiss 数据驱动模板**（替换原朴素 HTML）；强调色可切；改后支持 diamond/supports 两结构。风格探索版(A 蓝 / B 橙)留在 `_private/guizang-card/`。
- [x] 修复默认值逐字段渗透 bug（传 CARD_DATA 时整体覆盖，不再渗透虚构默认）。
- [x] 加个人 IP 品牌签名（`brand`/`brandSeries`/`brandTag`，竖条+两行）；**公开卡署名，竞品卡不传 brand=自动不署名**。最终文案：线1「MKTer 小V Skill」线2「关键信息体检 · 一起进化」。
- [x] 视觉定稿：**改前灰块 / 改后淡蓝块（C 双色块区隔）+ 深蓝金句**（与"优秀"徽章同色，改后统一"蓝=答案"）。`footer` 合规小字改为可选（传才显示，公开卡不带）。`.support` 与改前 `.body` 同间距（gap-4/行高1.6）。修了 `.support` 漏 margin:0、brandSeries 空串顶默认两处 bug。

## 待办

- [ ] EXTEND.md schema 细化 + 首次配置交互文案
- [ ] 对比卡增加横版（公众号 21:9 / 1:1）尺寸
- [ ] examples 增加第二个领域（他汀/降糖）防止单一
- [ ] 可选：装饰封面用文生图（仅题图，不碰正文）
