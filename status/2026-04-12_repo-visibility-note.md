# Repo Visibility Note — 2026-04-12

## 背景

出现了一个新人 onboarding 中容易复现的混淆：

1. `coordination` 的分工文档会直接列出当前阶段应做的 benchmark case
2. 但新同学本地如果只看 `Arcadia-1/behavioral-veriloga-eval` 的 `upstream/main`
3. 可能只能看到公开基线中的少量任务
4. 从而误以为自己拉错仓库，或者误以为 `coordination` 文档引用了不存在的任务

## 已确认事实

`Arcadia-1/behavioral-veriloga-eval` 当前 `upstream/main` 只包含公开基线任务，例如：

1. `clk_div_smoke`
2. `comparator_smoke`
3. `d2b_4bit_smoke`
4. `ramp_gen_smoke`
5. `adpll_lock_smoke`

而 `coordination` 中分配给 `liangyuxuan` 的一些任务，例如：

1. `adc_dac_ideal_4b_smoke`
2. `dac_binary_clk_4b_smoke`
3. `dwa_ptr_gen_smoke`
4. `noise_gen_smoke`
5. `dac_therm_16b_smoke`
6. `sample_hold_smoke`
7. `flash_adc_3b_smoke`
8. `serializer_8b_smoke`

不在当前 `upstream/main`，而是在团队后续扩展 benchmark 的分支中。

本地已确认其中一部分来源于：

1. 分支 `feat/new-benchmark-seeds-2026-04-05`

注意：

1. 不同人的机器上，这个分支前面的 remote 名可能不同
2. 例如有人会看到 `origin/feat/new-benchmark-seeds-2026-04-05`
3. 也有人可能看到 `team/feat/new-benchmark-seeds-2026-04-05`
4. 所以判断时应先看“分支名”，再看“它挂在哪个 remote 下”

## 这意味着什么

1. 新同学如果“只能看到 coordination 仓库”，需要在 coordination 里就能读到这个说明
2. 不能默认大家都会自己推断出“文档引用的是 fork / feature branch 上的任务”
3. 所以 repo 来源和 branch 可见性必须作为 onboarding 信息公开写在 coordination 中

## 给新同学的最短判断规则

如果你遇到：

1. `coordination` 里写了某个任务
2. 但你本地 `behavioral-veriloga-eval` 的 `upstream/main` 看不到它

先按下面顺序排查：

1. `git remote -v`
2. `git branch -a`
3. 看团队 fork / feature branch 是否包含该任务
4. 再联系负责人确认当前建议使用的 remote + branch

最短命令版：

```bash
git remote -v
git branch -a
find tasks/end-to-end/voltage -maxdepth 1 -mindepth 1 -type d | sed 's#.*/##' | sort
```

如果你怀疑任务在某个远端分支但本地没切到：

```bash
git fetch --all --prune
git branch -a
```

不要直接假设：

1. 自己拉错仓库
2. 文档完全失效
3. 任务一定来自私有不可见源

## 协作建议

以后如果 `coordination` 新增了分工任务，而这些任务尚未进入 `upstream/main`，请同步补三样东西：

1. 对应仓库名
2. 对应 remote 来源
3. 对应 branch 名

这样新成员只看 `coordination` 也能自助完成仓库定位。
