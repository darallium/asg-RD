---
title: 'Rockchip上で何が変わっていたら何を観測すべきかメモ'
pubDate: 2025-10-14T14:55:50+09:00
author: 'darallium'
tags: ["Rock5", "検討"]
---

> まず何が書き換わっている可能性があって、何と何を比較すれば書き換わっている箇所が確認できるのか、を図なり箇条書きなりにして整理してください。例えばキャッシュと DRAM 以外にも ALU の中の何かがやられていてたまたま読み出し命令の結果がかわった可能性もありますよね。
いきなり突っ走ってもあとでやっぱりこの作業は無意味でした、とかになりがちです。目的を実現するための技術的要素としてこういう命令があるとか、こういう機能（DMA など）があるとかを調べるのはよいですが、その前段階もちゃんとやりましょう。

# 検討対象
## 要求
- 何が書き換わっている可能性があるか
- 何が書き換わったときに何を比較すれば検証できるか

# 記憶領域の一覧

![fig:block map](fig/RK3558S-block-diagram.png)

Internal on-chip memory
 - BootRom
   * Support system boot from the following device:
     - SPI interface
     - eMMC interface
     - SD/MMC interface
   * Support system code download by the following interface:
     - USB OTG interface
 - Share Memory in the voltage domain of VD_LOGIC
 - PMU SRAM in VD_PMU for low power application
External off-chip memory
 - Dynamic Memory Interface
   * Compatible with JEDEC standards LPDDR4/LPDDR4X/LPDDR5
   * Support four channels, each channel 16bits data widths
   * Support up to 2 ranks (chip selects) for each channel
   * Totally up to 32GB address space
   * Low power modes, such as power-down and self-refresh for SDRAM
 - eMMC Interface
   * Fully compliant with JEDEC eMMC 5.1 and eMMC 5.0 specification
   * Backward compliant with eMMC 4.51 and earlier versions specification.
   * Support HS400, HS200, DDR50 and legacy operating modes
   * Support three data bus width: 1bit, 4bits or 8bits
 - SD/MMC Interface
   * Compatible with SD3.0, MMC ver4.51
   * Data bus width is 4bits
 - Flexible Serial Flash Interface(FSPI)
   * Support transfer data from/to serial flash device
   * Support 1bit, 2bits or 4bits data bus width
   * Support 2 chips select

# 書き換わる可能性のある場所

Internal on-chip memory
 - [ ]  BootRom
   * [ ]  Support system boot from the following device:
     - [ ]  SPI interface
     - [ ]  eMMC interface
     - [ ]  SD/MMC interface
   * [ ]  Support system code download by the following interface:
     - [ ]  USB OTG interface
 - [ ]  Share Memory in the voltage domain of VD_LOGIC
 - [ ]  PMU SRAM in VD_PMU for low power application
External off-chip memory
 - [ ]  Dynamic Memory Interface
   * [ ]  Compatible with JEDEC standards LPDDR4/LPDDR4X/LPDDR5
   * [ ]  Support four channels, each channel 16bits data widths
   * [ ]  Support up to 2 ranks (chip selects) for each channel
   * [ ]  Totally up to 32GB address space
   * [ ]  Low power modes, such as power-down and self-refresh for SDRAM
 - [ ]  eMMC Interface
   * [ ]  Fully compliant with JEDEC eMMC 5.1 and eMMC 5.0 specification
   * [ ]  Backward compliant with eMMC 4.51 and earlier versions specification.
   * [ ]  Support HS400, HS200, DDR50 and legacy operating modes
   * [ ]  Support three data bus width: 1bit, 4bits or 8bits
 - [ ]  SD/MMC Interface
   * [ ]  Compatible with SD3.0, MMC ver4.51
   * [ ]  Data bus width is 4bits
 - [ ]  Flexible Serial Flash Interface(FSPI)
   * [ ]  Support transfer data from/to serial flash device
   * [ ]  Support 1bit, 2bits or 4bits data bus width
   * [ ]  Support 2 chips select


# 調査方法
## チップ内部レジスタ
##  FPU内部レジスタ
##  NPU内部レジスタ
##  VPU内部レジスタ
##  L1
##  L2
##  L3
##  DMAコントローラ
##  ALU内部の何か













