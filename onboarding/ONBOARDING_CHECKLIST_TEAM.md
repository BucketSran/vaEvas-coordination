# 新成员接入清单（可单独随 coordination 上传）

## 1. 目标

本清单用于在只提供 `vaEvas-coordination` 的情况下，仍能让新成员完整开始工作。

第一天至少完成：

1. 理解项目目标与协作规则
2. 完成 Git remote 检查
3. 跑通一条最小双验证流程（EVAS 预检 + Spectre 对照）

---

## 2. 必读文档（都在本仓库内）

1. `README.md`
2. `onboarding/QUICK_START.md`
3. `onboarding/NEW_MEMBER_START.md`
4. `onboarding/VIRTUOSO_EVAS_TEAM_GUIDE.md`
5. `docs/EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md`
6. `docs/PROJECT_OVERVIEW.md`
7. `docs/REPOSITORIES.md`

---

## 3. Git 初始化检查

对你要参与的代码仓库（EVAS / eval / skills）逐一检查：

1. 是否已经 fork 到个人账号
2. `origin` 是否指向个人 fork
3. `upstream` 是否指向团队主仓

命令：

```bash
git remote -v
```

建议同步：

```bash
git checkout main
git fetch upstream
git merge --ff-only upstream/main
git push origin main
```

---

## 4. Virtuoso bridge 最小连通检查

进入 bridge 目录（路径按你机器实际情况）：

```bash
cd <repo>/sshConnect/virtuoso-bridge-lite
zsh ./start_thu_bridge.sh
zsh ./status_thu_bridge.sh
```

最小 SKILL 烟测：

```python
from virtuoso_bridge import BridgeClient
c = BridgeClient()
print(c.execute_skill("1+2"))
```

---

## 5. EVAS-first 闭环最小执行

在 CPPLL 示例目录执行：

```bash
cd <repo>/vaEvas/testspace/cppll
python3 run_dual_verify.py --tb tb_cppll_lock_iter2.scs --va cppll_va.va --label first_run --evas-only
python3 run_dual_verify.py --tb tb_cppll_lock_iter2.scs --va cppll_va.va --label first_run
python3 ab_gate_decision.py --baseline output/baseline_no_idt_ppm/consistency_report.json --candidate output/first_run/consistency_report.json --primary ppm_cross_delta --max-abs 1000 --evas-fix-attempt 1 --max-evas-fix-attempts 3
```

---

## 6. 首周最低交付标准

每位新成员至少提交：

1. 一次完整命令记录
2. `consistency_report.json` 路径
3. gate 结果（含 `next_action`）
4. 文字结论：本轮是否通过、下一步做什么

---

## 7. 失败时统一动作

1. 不一致时先修 EVAS 语义层
2. 不改矩阵求解底层原理
3. 连续多轮无效后再回看模型代码
4. 每轮必须保留可复现实验标签和结果文件
