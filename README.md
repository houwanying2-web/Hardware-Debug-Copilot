# Hardware Debug Copilot

> A circuit-aware waveform diagnostic tool for hardware debugging.

一个结合电路参数和实测波形，帮助硬件学习者与工程师判断“哪里可能有问题、应该先调什么、下一步如何验证”的本地硬件调试助手。

## Download / 下载

**当前版本：v0.1.0 Beta · Windows x64 · 闭源免费 Beta**

1. 打开 [GitHub Releases](../../releases)。
2. 下载 `Hardware-Debug-Copilot-v0.1-gui-win64.zip`。
3. 完整解压 ZIP，不要只取出或单独移动 `hardware-debug.exe`。
4. 双击 `hardware-debug.exe`。

用户不需要安装 Python、pip 或开发环境。

当前构建 SHA-256：

```text
2991EE129C7D06FA6BA294D4CD02FDF961A3ECDA9309636514672ED76FC92EC6
```

## 它与普通波形分析器有什么不同？

Hardware Debug Copilot 不是简单的 FFT 工具，也不是 AI 聊天工具。理论计算和波形测量只是诊断依据，产品重点是指导下一步调试：

```text
波形 + 电路上下文
→ 理论预期
→ 实际测量
→ 异常证据
→ 可能原因
→ 调整方向
→ 验证方法
```

| 普通波形分析器 | Hardware Debug Copilot |
|---|---|
| Gain = 8.7 | 检测：实际增益低于理论值 |
| THD = -18 dB | 证据：理论增益 10，实测增益 8.7 |
| 给出测量数字 | 第一步建议：降低输入频率复测 |
| — | 观察：增益是否恢复，相位滞后是否减小 |

## 三个核心诊断模块

### 1. 运放诊断

- 同相放大器、反相放大器、电压跟随器
- 理论增益与实际增益、相位、DC 工作点
- 输出压缩迹象与带宽风险
- 结合 Vbias 分析单电源工作中心

### 2. MOSFET 栅极驱动诊断

- Rise/Fall Time、Overshoot、Undershoot、Ringing
- Gate level、上下沿不对称、Measurement artifact
- 带代价说明的 Rg 调整方向

软件不会看到振铃就直接断言 PCB 有问题。它会同时提示 PCB 寄生、探头地线、探头类型、测量点和测量回路等可能影响。

### 3. ADC / 采样链诊断

- SNR、THD、SINAD、SFDR、ENOB
- LSB、dBFS、Nyquist margin
- 50/60 Hz 工频干扰、Clipping、Dynamic performance

动态 ENOB 基于当前波形的 SINAD 估算。ENOB 偏低不等于 ADC 已损坏；输入电平、削顶、混叠、噪声、失真和测试条件都会影响结果。

## 产品特性

- Windows Desktop GUI
- 中文 / English 即时切换
- 完全本地分析，波形不会自动上传
- 单通道 / 双通道波形预览
- 中英文 PDF 用户手册
- 自包含 HTML 工程诊断报告及可选 Markdown 报告
- 无账户、无云端分析、无 Python 环境要求
- 闭源免费 Beta

## Beta 说明

这是 **v0.1.0 Beta**。当前诊断属于工程辅助建议，部分诊断阈值仍需要更多真实硬件数据验证。软件不会承诺对所有电路或所有测量条件给出准确结论。

诊断结果不能替代：

- 器件 Datasheet
- 示波器或其他仪器复测
- 电气安全评估
- 工程师的最终判断

对功率、高压、高温或可能损坏设备的操作，请先遵循相应安全规范。

## 隐私

- 波形在用户电脑本地处理。
- 软件不会自动上传波形、配置或报告。
- 不需要账户。
- 当前没有云端分析。

## Feedback / 反馈

欢迎通过 [GitHub Issues](../../issues) 提交：

- Bug
- 疑似错误诊断
- 尚未覆盖的硬件场景
- 功能建议

为了帮助复现真实硬件问题，建议说明：

1. 硬件类型
2. 使用场景
3. 波形现象
4. 软件诊断结果
5. 实际最终故障原因
6. 最终解决方法

上传日志、截图、配置或波形前，请删除公司名称、项目名称、序列号、路径、账号、密钥以及其他敏感或私有信息。

---

## English

Hardware Debug Copilot combines measured waveforms with circuit parameters to explain what may be abnormal, what to adjust first, and how to verify the hypothesis. It is not merely an FFT calculator and it is not an AI chat tool.

### Download

This release is **v0.1.0 Beta for Windows x64**.

1. Open [GitHub Releases](../../releases).
2. Download `Hardware-Debug-Copilot-v0.1-gui-win64.zip`.
3. Extract the complete archive. Do not move `hardware-debug.exe` away from its accompanying folders.
4. Double-click `hardware-debug.exe`.

Python, pip, and a development environment are not required.

### Core modules

- **Op-amp diagnosis:** non-inverting, inverting, and follower circuits; theoretical/measured gain, phase, DC working point, compression evidence, and bandwidth risk.
- **MOSFET gate-drive diagnosis:** rise/fall time, overshoot, undershoot, ringing, gate level, measurement artifacts, and trade-off-aware Rg guidance. Ringing is not treated as automatic proof of a PCB defect.
- **ADC and sampling-chain diagnosis:** SNR, THD, SINAD, SFDR, ENOB, LSB, dBFS, Nyquist margin, 50/60 Hz interference, clipping, and dynamic performance. Low ENOB alone is not proof of a damaged ADC.

### Beta notice

The results are engineering-assistance suggestions. They do not replace datasheets, instrument verification, safety assessment, or final engineering judgment. Some thresholds still require validation with more real hardware captures; no accuracy percentage is claimed.

### Privacy and feedback

Waveforms and reports are processed locally. Files are not uploaded automatically, no account is required, and v0.1.0 has no cloud analysis.

Please use [GitHub Issues](../../issues) for bugs, questionable diagnoses, unsupported hardware cases, and feature ideas. When possible, describe the hardware, use case, waveform symptom, software finding, confirmed root cause, and final fix. Remove sensitive or proprietary information before attaching any file.

## Licensing

Hardware Debug Copilot is proprietary, closed-source software. Public repository documents do not grant a license to the application source code, internal rules, or diagnostic algorithms. See `THIRD_PARTY_NOTICES.md` for the third-party component review status.
