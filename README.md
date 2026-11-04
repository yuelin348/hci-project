# A Better Way to Access In-game Activity Information

人机交互课程研究项目主页 · **Creative and Magic**（单人项目）

- 线上地址：<https://yuelin348.github.io/hci-project/>
- 源码仓库：<https://github.com/yuelin348/hci-project>
- 技术形态：纯静态 HTML / CSS，无 JavaScript、无构建步骤、无第三方资源。

## 这个页面是什么

一个用于展示 HCI 课程研究项目的单页主页，包含：

1. 团队介绍（单人研究者版式）
2. 项目提案：背景、工作假设、研究问题、预期产出
3. 数据收集计划：4 份半结构访谈 + 10 份匿名问卷
4. 四份访谈记录（Participant 01–04）
5. 十行匿名问卷数据表、示例摘要与 CSV 下载

页面用“游戏研究档案”的编辑设计语言，包含一个活动雷达概念界面、章节编号、示例数据标记和无障碍支持。页面不收集问卷、不包含后台、不发送任何网络请求。

## 当前状态：版式示例版

团队姓名、访谈问答、问卷题目和问卷数据目前均为**明确标注的示例内容**，不是真实研究结果：

- 团队姓名、课程教师、联系方式为占位符；
- 访谈 P01–P04 的问答为演示材料；
- 问卷 R01–R10 为合成示例数据；
- 访谈提纲与问卷题目为结构示例。

正式材料到位后，需要替换内容、重新计算问卷摘要，并移除“示例 / 待更新”标记。页面上的数量已经按最终计划固定为 **4 份访谈 / 10 份问卷**。

## 文件结构

```text
hci-project/
  index.html                 # 全部页面内容与语义结构
  assets/
    styles.css               # 设计系统、响应式与打印样式
    survey-sample.csv        # 示例问卷原始数据（10 行）
    favicon.svg              # 站点图标
  README.md
  .nojekyll                  # 让 GitHub Pages 直接发布静态文件
```

## 本地预览

直接双击 `index.html` 即可离线查看。若需要更接近线上环境：

```powershell
cd D:\DSagent\hci-project
python -m http.server 4173 --bind 127.0.0.1
```

然后打开 <http://127.0.0.1:4173/>。

## 内容替换清单

正式材料准备好后，按下表替换：

| 位置 | 当前内容 | 需要替换为 |
| --- | --- | --- |
| 团队卡 `.researcher-card` | “研究者姓名”占位 | 你确认公开的姓名 / 昵称 |
| 项目信息 `.project-facts` | 联系方式、状态 | 正式课程信息、状态 |
| 03 访谈提纲 | 结构示例 | 正式访谈提纲与追问 |
| 03 问卷题目 | 结构示例 | 正式问卷题目与选项 |
| 04 `P01`–`P04` | 示例问答、元信息 | 四份匿名访谈记录 |
| 05 统计卡与条形图 | 由示例 CSV 计算 | 按正式 CSV 重新计算 |
| 05 表格 `R01`–`R10` | 示例数据 | 十份匿名问卷回答 |
| `assets/survey-sample.csv` | 示例 CSV | 正式匿名数据（保持表头一致或同步调整表头） |
| `.sample-tag`、`.sample-notice`、`.preview-note`、`.materials-status` | 示例提示 | 删除或改成正式状态 |

注意：

- 公开页面和仓库会公开源码与所有数据。上传真实材料前必须匿名化，不要包含姓名、联系方式、录音、可识别细节。
- 访谈原始录音与匿名编号对应表只应保存在本地，不进入仓库。
- 如果正式问卷字段发生变化，需要同步修改 `index.html` 中的表头、字段说明和统计口径。
- 如果替换布局内容后页长变化，请重新检查手机端溢出与打印效果。

## 设计与可访问性说明

- 语义化 landmarks、正确的标题层级、跳转主内容链接；
- 原生 `<details>` 折叠，无需 JavaScript 即可键盘操作；
- 表格带 `<caption>`、列/行 `scope`，数据区可聚焦横向滚动；
- 所有文字与背景颜色按 4.5:1 对比度目标设计；
- 支持 `prefers-reduced-motion`；
- 提供打印样式，适合导出 PDF；
- 不使用外部字体、图片、脚本或追踪器。

## 发布

站点直接发布在 GitHub Pages：

- 仓库 `yuelin348/hci-project`
- 分支 `main`，目录 `/`
- 由根目录的 `.nojekyll` 跳过 Jekyll 构建。

修改后：

```powershell
cd D:\DSagent\hci-project
git add .
git commit -m "Update project materials"
git push
```

GitHub Pages 会自动重新构建。无需其他部署工具。

## 示例数据口径

- 样例样本：10 份匿名问卷；
- 汇总值与 `assets/survey-sample.csv` 保持一致（70% 近三个月错过活动、平均满意度 3.0/5、4/10 最想要统一时间线、社群/群聊 6/10 为最常见发现渠道）；
- 多选题比例按选择人数 / 10 计算，因此合计可超过 100%；
- 这些数字仅用于版式展示，不作为研究结论或总体推断。
