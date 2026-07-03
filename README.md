# TTR Calculator · TTR 计算器

在线计算华法林抗凝治疗达标时间（Time in Therapeutic Range, TTR），采用 Rosendaal 线性插值法。

A browser-based Warfarin Time-in-Therapeutic-Range (TTR) calculator using the Rosendaal linear interpolation method.

**在线使用 / Live demo:** https://xuxiaobogit.github.io/ttr-calculator/

## 功能 / Features

- 📄 拖拽上传 CSV / TXT，或直接从 Excel 复制粘贴；自动识别 UTF-8 / GBK 编码与逗号、制表符、分号分隔符
- 👥 支持多患者、多分组批量计算；也支持单患者两列数据
- 📊 每位患者的 TTR、低于窗时间、高于窗时间、评估天数；分组汇总（均值 ± SD、中位数、范围）
- 📈 交互式 INR 轨迹图，治疗窗色带标注，数据点按窗内 / 窗下 / 窗上着色
- ⚙️ 治疗窗预设（2.0–3.0 / 2.5–3.5）与自定义；可选排除超长检测间隔（默认阈值 56 天）
- 💾 一键导出结果 CSV（Excel 可直接打开）
- 🌐 中英文界面、深浅色主题
- 🔒 纯前端零依赖单文件，所有数据仅在浏览器本地处理，不上传任何服务器

## 数据格式 / Data format

每行一条 INR 记录，按列数自动识别 / One record per line, layout auto-detected by column count:

| 列数 Columns | 含义 Layout |
| --- | --- |
| 4 | PatientID, Group, DateTime, INR |
| 3 | PatientID, DateTime, INR |
| 2 | DateTime, INR（单患者 single patient）|

日期支持 `2023-08-19 14:30`、`2023/8/19`、`8/19/2023 0:05` 等格式（`x/y/年` 按 月/日/年 解释）。

示例 / Example:

```csv
PatientID,Group,DateTime,INR
P01,A,2025-01-06 09:00,1.85
P01,A,2025-01-20 09:30,2.40
P02,B,2025-01-08 08:15,3.10
```

## 方法 / Method

Rosendaal FR, Cannegieter SC, van der Meer FJ, Briët E. **A method to determine the optimal intensity of oral anticoagulant therapy.** *Thromb Haemost.* 1993;69(3):236-239.

相邻两次 INR 检测之间按线性插值分配时间；可选排除超过阈值天数的检测间隔（该区间不计入分子与分母）。

## 免责声明 / Disclaimer

本工具仅供科研与教学使用，不构成临床决策依据。
For research and educational use only; not for clinical decision-making.

## License

MIT
