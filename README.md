# character-design-skills

基于 **CBVTM（人物言行思模式）** 的中文角色建模 agent skills，包含完整版与轻量版两个 skill。两者共用同一套参数体系、派生量计算与判定顺序，区别在深度模块、检查清单和输出预算。

> 集合原型，非指所有个体。不用于临床诊断、真实个体标签化或决定论预测。

## 两版对比

| | character-design-max | character-design-mini |
| --- | --- | --- |
| 定位 | 完整版：对齐提问 → 出卡 → 连续扮演 | 轻量版：一个原型 + 一个情境 → 快速卡 + 单次推演 |
| 适用 | 长篇小说主角色、核心 NPC、多轮冲突推演 | 一次性角色卡、单场景推演、上下文紧张、多角色并行 |
| 对齐访谈 | §6.0：轻问 3 问 / 标准 6 问 / 深问 9 问，出卡前给 brief | 无访谈，缺失项写「假设：……」 |
| 深度模块 | 思考逻辑、行为逻辑、四层视角、情景分析，可全开 | 同名模块可开，但默认不启用、只有最小产出 |
| 自检 | `references/checklist.md` 的 C 表 + A 表 | 内置 13 项自检表 |
| 输出预算 | 快速卡 ≤ 600 字；单模块 ≤ 1200 字；全开 ≤ 2000 字 | 同左 |
| 版本 | 1.0 | 1.0 |

两版共有的核心：

- 12 项情境参数 P、6 项风格变量 S
- 派生量 F / C / G / A 与 clamp、.5 进位的计算口径
- 「接受判定 → 规则 1—5」的判定顺序
- 补偿档 K
- 9 步拒绝链

## 目录结构

```text
character-design-skills/
├── character-design-max/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── checklist.md
│       ├── examples.md
│       └── runtime.md
├── character-design-mini/
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── examples.md
│       └── runtime.md
├── LICENSE
└── README.md
```

## 安装

把需要的 skill 目录整个复制到宿主的 skills 目录，重启会话后生效。

- ZCode：`~/.zcode/skills/`（Windows：`C:\Users\<用户名>\.zcode\skills\`）
- Claude Code：`~/.claude/skills/`

```bash
git clone https://github.com/123-qingluo/character-design-skills.git
cp -r character-design-skills/character-design-max ~/.zcode/skills/
cp -r character-design-skills/character-design-mini ~/.zcode/skills/
```

两个 skill 都设置了 `disable-model-invocation: true`，需要显式调用，不会被模型自动触发。

## 使用

- 建卡：`用 character-design-max 给一个高二男生建卡，先按标准档提问`
- 快速推演：`用 character-design-mini 推演他拒绝兄弟代练请求会怎么说`
- 连续扮演：先建卡，确认后要求「按 runtime 演」，对话层只输出角色言行

对话模式默认不输出卡面与参数；明确要卡时才出卡。

## 许可

[MIT](LICENSE)

## English

Two Chinese-language agent skills for character design based on **CBVTM**, a behavioral model of how a character thinks, speaks and acts. `character-design-max` is the full method: an alignment interview, a parameterized refusal model, checklists and a runtime role-play layer. `character-design-mini` is the lightweight version for quick character cards and single-scene simulations. Both share the same 12 situation parameters, 6 style variables, derived scores (F/C/G/A), decision order and 9-step refusal chain. Install by copying a skill folder into `~/.zcode/skills/` or `~/.claude/skills/`. MIT licensed.
