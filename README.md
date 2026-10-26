# DGX Spark / GB10 实测资料索引

四台 DGX Spark（GB10，128GB 统一内存）本地推理集群的实测记录。按主题拆成独立仓库，方便单独引用和更新。

**交流群**：QQ 群 **1128010665**（加群备注：GitHub）

## 仓库列表

| 仓库 | 内容 | 关键数字 |
|---|---|---|
| [deepseek-v41-flash-4x-gb10](https://github.com/hdcdn/deepseek-v41-flash-4x-gb10) | 四机 TP4 跑 DeepSeek-V4.1-Flash MXFP4 | C1 106.7 / C8 317.0 / C16 439.9 tok/s，预填 ≈5,000 |
| [minimax-m31-flash-gb10](https://github.com/hdcdn/minimax-m31-flash-gb10) | MiniMax-M3.1-Flash 双方案（单机 EXL3 vs 四机 vLLM） | 单机 EXL3 19.7 tok/s 可用；四机 vLLM 崩在 SM121 |
| [rtx40-ada-unlock-notes](https://github.com/hdcdn/rtx40-ada-unlock-notes) | RTX 40 系 Ada 解锁资料整理（含 145s 视频） | 4090 165.6 → 331.6 TF/s，FP8 无收益 |
| [heterogeneous-pd-lab-data](https://github.com/hdcdn/heterogeneous-pd-lab-data) | 异构 PD 实验室 14 个实验、11 份 CSV | 3060 单卡预填 1589 > 395 整机 970 |
| [gpu-price-perf-ranking](https://github.com/hdcdn/gpu-price-perf-ranking) | 9 张显卡三维性价比测算 | 3080 20G 每千元 26.5 TFLOPS |

## 硬件与拓扑

- 4 × DGX Spark（GB10，sm_121，128GB 统一内存）
- 200GbE RoCE，**无交换机环形拓扑**
- TP4（每机一个 rank），DGX OS 580 / CUDA 13.0，NCCL 2.30.7（含 switchless ring 补丁）

## 记录原则

- 所有数字本地实测，测试口径写在各自仓库里（并发档位、提示词、是否剥离 TTFT、缓存是否清空）
- 引用社区数据必标注出处，并附原始 CSV
- 失败记录与成功记录同等重要——MiniMax 那篇有三分之一在讲崩在哪一行
- 仓库内 IP、密钥、内网地址已脱敏

## 许可

文档采用 CC BY-NC-SA 4.0，社区 CSV 遵循其原始许可。
