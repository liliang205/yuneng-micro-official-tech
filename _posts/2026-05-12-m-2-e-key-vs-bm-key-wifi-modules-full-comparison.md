---
layout: post
title: "M.2 E Key vs B+M Key WiFi Modules: Full Comparison"
date: 2026-05-12
categories: [Wireless-Modules]
tags: [M.2, E-Key, B+M-Key, Interface]
canonical_url: "https://www.zukaka.com/blog/m-2-e-key-vs-bm-key-wifi-modules-full-comparison"
excerpt: "M.2 E Key vs B+M Key WiFi Modules: Full Comparison"
---

<!-- GITHUB-PAGE-INTRO-AUTO -->

> 本文为 GitHub Pages 版本的独立导读：已为本站读者添加独特摘要与要点。

摘要代号：abed82bb — 若在发布前需要更改，请告知团队。

## Article Summary

M.2 E Key (Socket 1, notch pins 24–31, 60 active pins, 22×30 mm 2230 form factor) is the PCI-SIG-standardized interface for modern Wi-Fi/Bluetooth combo modules. It carries one PCI Express Gen 3 x1 lane (8 GT/s, 984 MB/s), a mandatory USB 2.0 differential pair on pins 3/5 for Bluetooth HCI transport, and optional Intel CNVi on pins 9–23/59–73 for CRF modules. M.2 B+M Key (Socket 2, dual notch at pins 12–19 and 58–65, 67 active pins, 2242/2280 form factor) is specified for SATA and PCIe x2 NVMe storage — not for Wi-Fi. The B+M Key electrical interface lacks mandated USB routing for Bluetooth, uses a host-interface detection mechanism via CONFIG[3:0] pins (pins 1/21/69/75) that identifies SATA, PCIe, or WWAN protocol configuration, and supports no CNVi. Physically, an E Key module cannot enter a B+M slot due to notch collision at pins 24–31; a B+M module cannot seat in an E Key slot due to continuous pin contact at the same region. Over 95% of M.2 Wi-Fi 6/6E/7 modules (Intel AX210/BE200/BE201, Qualcomm QCNCM865, MediaTek MT7925) ship as E Key 2230. B+M Key Wi-Fi modules are limited to legacy Wi-Fi 5 (Broadcom BCM94352Z, Intel 3165) and are end-of-life.

For an industrial perspective on MiniPCIe vs M.2 form factors — covering mechanical retention, vibration resistance, thermal performance, and lifecycle planning — see ourMiniPCIe vs M.2 WiFi Modules: Which is Better for Industrial?.

### Key Technical Takeaways

- CNV_WR_CLK_DP/CNV_WR_CLK_DN(pins 23/21) — differential receive clock from CRF to PCH, 1.8 V signaling.
- CNV_WR_LANE0_DP/CNV_WR_LANE0_DN(pins 17/15) — receive data lane 0.
- CNV_WR_LANE1_DP/CNV_WR_LANE1_DN(pins 11/9) — receive data lane 1.
- CNV_WT_CLK_DP/CNV_WT_CLK_DN(pins 73/71) — differential transmit clock from PCH to CRF.
- CNV_WT_LANE0_DP/CNV_WT_LANE0_DN(pins 67/65) — transmit data lane 0.

### Key Performance Data

| Signal Group | E Key (Socket 1) | B+M Key (Socket 2) |
| --- | --- | --- |
| Notch Position | Pins 24–31 (single, center-right) | Pins 12–19 + 58–65 (dual, left and right) |
| Active Pins | 60 (of 75 positions) | 67 (of 75 positions) |
| Standard Form Factor | 2230 (22 × 30 mm); 1216 (12 × 16 mm) | 2242, 2260, 2280 (22 mm × variable) |
| PCIe Lane Count | 1 (x1), Gen 3 at 8 GT/s | 2 (x2), Gen 3 at 8 GT/s per lane |
| PCIe Lane Mapping | PETp0/n0: 35/37, PERp0/n0: 41/43, REFCLK: 47/49, PERST#: 52, CLKREQ#: 53, PEWAKE#: 55 | L0: PETp0/n0: 49/47, PERp0/n0: 43/41. L1: PETp1/n1: 37/35, PERp1/n1: 31/29. REFCLK: 55/53, PERST#: 50, CLKREQ#: 52, PEWAKE#: 54 |
| USB 2.0 | Mandatory on pins 3 (D+), 5 (D-) | Optional on pins 7 (D+), 9 (D-); not required by spec |
| USB 3.0 | Not defined on E Key | Optional, shared with PCIe Lane 1 on pins 29/31 (Rx) and 35/37 (Tx) |
| Host Interface Detection | Not required; key type defines fixed interface | CONFIG[3:0] on pins 1/21/69/75; 4-bit strap encoding for SATA/PCIe/WWAN |
| CNVi (Intel) | Full support on pins 8–23, 32–38, 44–48, 59–73 | Not supported |
| Coexistence Interface | 3-wire COEX on pins 44/46/48 (1.8V); CNV_PA_BLANKING on pin 44; MFUART on pins 46/48 | CNV_PA_BLANKING optional on pin 60; no standard 3-wire COEX pins |
| Antenna Connector | IPEX MHF4 (I-PEX 20455), 2 ports, 9 GHz rated, 1.2 mm mating height | U.FL or MHF1, 2 ports, ≤6 GHz rated, 2.5 mm mating height |
| 3.3V Power | Pins 2, 4, 72, 74; max 1.5 A (VCC_E) | Pins 2, 4, 70, 72, 74; max 3 A (general M.2 limit) |
| RF Kill | W_DISABLE1# pin 56, W_DISABLE2# pin 54; active-low, 3.3 V | W_DISABLE1# pin 56, W_DISABLE2# pin 54; active-low, 3.3 V |
| Max Insertion Force | 20 N (Socket 1 limit) | 30 N (Socket 2 limit) |


---

## Read the Full Article

This excerpt covers the key technical highlights. For the complete article with detailed analysis, additional data tables, engineering guidance, and expert insights, visit the original post on Zukaka.

**[Read the full article on Zukaka →](https://www.zukaka.com/blog/m-2-e-key-vs-bm-key-wifi-modules-full-comparison?utm_source=github&utm_medium=blog&utm_campaign=mirror)**

The full article includes:
- Detailed technical analysis and engineering data
- Complete comparison tables and performance benchmarks
- Practical design guidance and deployment considerations
- Expert insights from real-world field experience

### Related Articles on Zukaka

- [WiFi module complete guide](https://zukaka.com/blog/wifi-module-complete-guide-wifi-5-to-wifi-7-form-factors-chipsets-selection/?utm_source=github&utm_medium=blog&utm_campaign=mirror)
- [MiniPCIe vs M.2 WiFi Modules: Which is Better for Industrial?](https://zukaka.com/blog/minipcie-vs-m-2-wifi-modules-which-is-better-for-industrial/?utm_source=github&utm_medium=blog&utm_campaign=mirror)

<!--
  Generated from: m-2-e-key-vs-bm-key-wifi-modules-full-comparison.5537.html
  Slug: m-2-e-key-vs-bm-key-wifi-modules-full-comparison
  Tags: M.2, E-Key, B+M-Key, Interface
-->

<script type="application/ld+json">{"@context": "https://schema.org", "@type": "Article", "headline": "M.2 E Key vs B+M Key WiFi Modules: Full Comparison", "datePublished": "2026-05-12", "url": "https://www.zukaka.com/blog/m-2-e-key-vs-bm-key-wifi-modules-full-comparison"}</script>
