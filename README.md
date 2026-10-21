# mRNA_base: 转录组生信分析流程

[![R](https://img.shields.io/badge/R-%3E%3D%204.0-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

本仓库提供一套针对 **GEO 数据库** 的 mRNA 转录组生信分析流程，涵盖**数据整理、差异分析、富集分析、基因表达相关性分析及结果可视化**。脚本以 R 语言为主（部分富集模块结合 Python），适配 Linux 运行环境，支持命令行参数传入，便于批量处理与自动化分析。

---

## 📁 模块结构与功能概览

| 模块目录 | 核心功能 | 主要脚本/文件 |
| :--- | :--- | :--- |
| **`mRNA_DEG`** | 差异表达分析 | 基于 `limma` 计算差异基因，输出样本相关性热图、PCA 图、差异基因数量统计、火山图及差异基因热图 |
| **`Volcano`** | 火山图绘制 | 独立可视化差异分析结果，标注关键基因 |
| **`expression`** | 基因表达可视化 | 绘制小提琴图、箱线图，比较基因在分组间的表达差异 |
| **`enrichment`** | 功能富集分析 | 包含 `enrich_term`（GO/Reactome 富集）和 `GSEA`（基因集富集分析）两个子模块 |
| **`correlation_analysis`** | 基因表达相关性分析 | 包含 `Cor_curve`（相关性曲线）和 `Cor_point`（相关性散点图），支持 `linkET`/`WGCNA` 网络构建 |
| **`GEO`** | GEO 数据整理 | 针对 GEO 下载数据的预处理与整理脚本 |
| **`TCGA_mRNA`** | TCGA 数据处理 | 针对 TCGA 转录组数据的格式化与整合脚本 |

---

## 🖼️ 结果示例

> 以下图片/PDF 链接均来自原有 README，已原样保留。

### mRNA_DEG (差异分析)

- [Sample_corr_heatmap.pdf](https://github.com/user-attachments/files/33536339/Sample_corr_heatmap.pdf)
- [Sample_PCA_correlation.pdf](https://github.com/user-attachments/files/33536342/Sample_PCA_correlation.pdf)
- [numbers_of_diff_genes.pdf](https://github.com/user-attachments/files/33536375/numbers_of_diff_genes.pdf)
- [volcano_plot.pdf](https://github.com/user-attachments/files/33536379/volcano_plot.pdf)
- [heatmap_of_any_diff_genes.pdf](https://github.com/user-attachments/files/33536013/heatmap_of_any_diff_genes.pdf)
- [heatmap_of_top_diff_genes.pdf](https://github.com/user-attachments/files/33536386/heatmap_of_top_diff_genes.pdf)

### Volcano & Expression (基因表达可视化)

- [Normal_VS_Tumor.UBE2C.violin.pdf](https://github.com/user-attachments/files/33537874/Normal_VS_Tumor.UBE2C.violin.pdf)
- [Normal_VS_Tumor.TPX2_NEK2_UBE2C_HOXC9_KIF18B.box.pdf](https://github.com/user-attachments/files/33537880/Normal_VS_Tumor.TPX2_NEK2_UBE2C_HOXC9_KIF18B.box.pdf)

### enrich_term & GSEA (富集分析)

- [Gene_expr_diff.go.enrich.pdf](https://github.com/user-attachments/files/33537129/Gene_expr_diff.go.enrich.pdf)
- [acute_inflammatory_response.GO_0002526.gsea.pdf](https://github.com/user-attachments/files/33537133/acute_inflammatory_response.GO_0002526.gsea.pdf)

### Cor_curve & Cor_point (基因表达相关性)

- [Correlation_Ctsk_VS_Spp1_Gm3375.top_0.2.pdf](https://github.com/user-attachments/files/33537521/Correlation_Ctsk_VS_Spp1_Gm3375.top_0.2.pdf)
- [Con_VS_Treat.Ctsk_Spp1.correlation.pdf](https://github.com/user-attachments/files/33537529/Con_VS_Treat.Ctsk_Spp1.correlation.pdf)

---

## 💻 配置环境

大部分脚本为 R 编写，需要安装相应的 R 包。

### 基础依赖（所有脚本必需）

```r
install.packages("argparser")
```r

## 💻 使用方法

1. 所有脚本均需要在 Linux 系统下运行。
2. 给脚本可执行权限：

   ```bash
   chmod 755 mRNA_DEG
3. 查看脚本帮助文档，哪些是脚本必须参数，哪些是可选参数，补全必须参数即可分析。
   
   ```bash
   mRNA_DEG --help
<div align="center">
  <img src="https://github.com/user-attachments/assets/3949e740-d098-47fe-b9ce-8f38745fe015" width="600" alt="运行截图" />
</div>

