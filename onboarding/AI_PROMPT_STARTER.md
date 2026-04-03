# AI Prompt Starter

这份文件给主要依赖 AI 的新成员使用。目标不是让 AI 替你乱做，而是让 AI 先帮你理解项目，再帮你执行。

## Prompt 1: 先理解项目

```text
请先阅读以下文档，并用新手能懂的话总结：
1. vaEvas-coordination/README.md
2. vaEvas-coordination/onboarding/NEW_MEMBER_START.md
3. vaEvas-coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md
4. vaEvas-coordination/docs/EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md

请回答我：
1. 这个项目到底在做什么
2. 我作为新同学最可能负责什么
3. 我今天不应该直接做什么
```

## Prompt 2: 检查本地 Git 是否正确

```text
请根据团队 fork + upstream 协作规则，帮我检查当前仓库的 Git remote 是否符合要求，并告诉我应该运行哪些命令修正它。
```

## Prompt 3: 开始第一个任务前先 interview

```text
请按 vaEvas 的 workflow，不要直接开始写代码。先采访我，确认这次任务属于哪个仓库、任务类型是什么、成功标准是什么、哪些内容不做、需要看哪些 KPI。然后帮我产出 brief 和 KPI 草稿。
```

## Prompt 4: 做一个最小任务

```text
请根据 vaEvas 的文档，帮我选择一个适合新手的最小任务，并按 brief -> kpi -> execute -> log -> review 的顺序带我完成。先解释每一步为什么要做，再给我具体命令或文件修改建议。
```

## Prompt 5: 让我理解一个仓库

```text
请先阅读以下仓库相关文档，然后告诉我这个仓库负责什么、我最可能在哪类文件里工作、改动后应该怎么验证：
[把仓库路径和文档路径写在这里]
```

## Prompt 6: 让我准备 PR

```text
请根据 vaEvas 的 GIT_WORKFLOW 和 worksche 模板，帮我检查这次任务是否已经具备提交 PR 的条件。请分别检查：
1. 分支是否合理
2. 验证命令是否齐全
3. log 和 review 是否齐全
4. 是否还缺 brief/kpi/plan
```

## 使用原则

1. 先让 AI 解释，再让 AI 执行
2. 先让 AI 读文档，再让 AI 产出方案
3. 不要只发一句“帮我写代码”
4. 不确定时，让 AI 先列出你当前缺失的信息
