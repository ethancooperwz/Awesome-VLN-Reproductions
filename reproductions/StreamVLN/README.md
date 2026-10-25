# StreamVLN 复现笔记

本仓库整理 [StreamVLN](https://github.com/InternRobotics/StreamVLN) 的中文复现流程，重点覆盖公开 checkpoint 在 R2R-CE `val_unseen` 上的环境搭建、数据准备、推理评测与结果分析。

> 文档基于 StreamVLN 官方当前代码和 R2R_VLNCE v1-3 checkpoint。MP3D/HM3D 数据需要按各自许可从官方渠道申请，本仓库不包含模型权重和数据集。

## 文档目录

1. [论文介绍](docs/01%20-%20论文介绍.md)：任务、方法、动作空间和指标
2. [环境配置](docs/02%20-%20环境配置.md)：Conda、Habitat、依赖和 checkpoint
3. [数据集准备](docs/03%20-%20数据集准备.md)：MP3D、VLN-CE episodes 与训练数据
4. [模型推理与测评](docs/04%20-%20模型推理与测评.md)：单卡/多卡命令、日志、结果和视频
5. [常见报错与解决](docs/05%20-%20常见报错与解决.md)：依赖、显存、数据路径和分布式问题
6. [实验结果与分析](docs/06%20-%20实验结果与分析.md)：官方基准、消融与本地记录模板

## 最短复现路线

```text
Python 3.9 + Habitat 0.2.4
        ↓
安装 StreamVLN requirements 与 FlashAttention
        ↓
下载 v1-3 checkpoint
        ↓
准备 MP3D 场景和 R2R_VLNCE v1-3 episodes
        ↓
运行 streamvln/streamvln_eval.py
        ↓
核对 NE / OS / SR / SPL
```

官方 R2R-CE `val_unseen` 参考结果为：**NE 4.90、OS 63.6、SR 56.4、SPL 50.2**。完整复现前请先阅读每篇文档中的版本和目录说明。

## 仓库结构

```text
.
├── README.md
├── docs/
│   ├── 01 - 论文介绍.md
│   ├── 02 - 环境配置.md
│   ├── 03 - 数据集准备.md
│   ├── 04 - 模型推理与测评.md
│   ├── 05 - 常见报错与解决.md
│   └── 06 - 实验结果与分析.md
└── images/                 # 截图和实验结果（可选）
```

## 参考资料

- [论文（arXiv 2507.05240）](https://arxiv.org/abs/2507.05240)
- [官方代码](https://github.com/InternRobotics/StreamVLN)
- [项目主页](https://streamvln.github.io/)
- [StreamVLN trajectory data](https://huggingface.co/datasets/cywan/StreamVLN-Trajectory-Data)
