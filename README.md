# SDR

## Hardware Sweet Spot
(Apr 2025)
```
                /--> 5 Gbit interface (or more) ---> USB 3.0 CYUSB3014-BZX
                |                                                                 \
                |--> 70 MHz - 6 GHz Transceiver  --> AD9361/AD9364                 \      
[ Desired ]-----|                                                                   ===>>> Ettus USRP device (or clone) = Expensive due cost of a Spartan-6 FPGA
                |--> Sample Rate 61.44 MSPS                                        /
                |                                                                 /
                \--> FPGA compatible with UHD  ----> Xilinx Spartan-6
                     (USRP Hardware Driver™)            XC6SLX75
                                                        XC6SLX150
```

## Devices

### Main architectures
| Name                             | Interface  | Interface Speed | Interface Controller | FPGA                        | Transceiver     | Sample rate (sustained) | Sample rate (burst) | RF Coverage       | RF Bandwidth    | x2 | Project page | Block diagram |
| -                                | -          | -               | -                    | -                           | -               | -                       | -                   | -                 | -               |:-: | :-:          | :-:           |
| Analog Devices ADALM-Pluto       | USB 2.0    | 480 Mbits       | SoC                  | Xilinx Zynq XC7Z010         | AD9363          | ?                       |                     | 325 MHz - 3.8 GHz | 20 MHz ? (2)    |    | [Project page](https://www.analog.com/en/resources/evaluation-hardware-and-software/evaluation-boards-kits/adalm-pluto.html) | [Block diagram](https://www.analog.com/en/_/media/analog/en/evaluation-board-images/images/adalm-pluto_medium_block_diagram.png?rev=d3869332df90484e97edb8b307e2e92f&sc_lang=en&h=500&hash=B4D7CB83CF8B80189F0CBFC83F35CE43) |
| Lime Microsystems LimeSDR        | USB 3.0    | 5 Gbits         | CYUSB3014-BZXC       | Altera Cyclone IV EP4CE40F23| LMS7002M        | 61.44MSPS ?  12bit      |                     | 100 kHz – 3.8 GHz | 61.44 MHz       |    |  | [Block diagram](https://www.crowdsupply.com/img/583e/02fad771-15e1-4500-8548-1101ffa1583e/limesdr-block-diagram_png_gallery-lg.jpg) |
| Lime Microsystems LimeSDR Mini 2 | USB 3.0    | 5 Gbits         | FTDI FT601Q          | Lattice ECP5 LFE5U-45F      | LMS7002M        | 30.72 MSPS ?            |                     | 100 kHz – 3.8 GHz | 30.72 MHz       |    |  | [Block diagram](https://www.crowdsupply.com/img/051a/c34f2ba2-f244-419a-bde6-398adc46051a/limesdr-mini-2-block-diagram-1.svg) |
| Lime Microsystems LimeSDR XTRX   | PCIe Gen2 x1 x2 ? | 10 Gbits ?  | SoC               | AMD Artix 7 XC7A50T-2CPG236I| LMS7002M        | 120 MSPS     12bit      |                     |  30 MHz – 3.8 GHz | 120 MHz ?       |    | [Project page](https://www.crowdsupply.com/lime-micro/limesdr-xtrx) | [Block diagram](https://www.crowdsupply.com/img/b667/3d170226-220a-4e15-8564-679673d1b667/limesdr-xtrx-block-diagram-1.svg) |
| Wavelet Lab uSDR                 | PCIe Gen2 x2 lanes M.2  | 10 Gbits    | SoC         | AMD Artix 7 XC7A35T         | LMS6002D        | 30.72 MSPS              |                     | 230 MHz - 3.7 GHz | 28 MHz          |    | [Project page](https://www.crowdsupply.com/wavelet-lab/usdr) | [Block diagram](https://www.crowdsupply.com/img/f161/5020cb82-a0b4-4bb4-89ec-6d856feaf161/usdr-block-diagram-crop.svg) |
| bladeRF 2.0 micro xA4            | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Intel Cyclone V ?           | AD9361          | 61.44 MSPS ?            |                     |                   | 56 MHz          |    |  | [Block diagram](https://www.nuand.com/wp-content/uploads/2018/08/bladeRF-2.0-micro-Block-Diagram-4.png) |
| bladeRF 2.0 micro xA9            | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Intel Cyclone V 301KL       | AD9361          | 61.44 MSPS (1)          | (1)                 |                   | 56 MHz (1)      |    |  | [Block diagram](https://www.nuand.com/product/bladerf-xa9/) |
| Ettus USRP B200                  | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Xilinx Spartan-6 XC6SLX75   | AD9364          | 61.44 MSPS ?            |                     | 70 MHz - 6 GHz    | 56 MHz          |    |  | [Block diagram](https://www.amazon.co.uk/Ettus-USRP-B200-70MHz-6GHz-Cognitive/dp/B09B7G8JD4?ref_=ast_sto_dp) |
| Ettus USRP B205mini-i            | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Xilinx Spartan-6 XC6SLX150  | AD9364          | ?                       |                     | 70 MHz - 6 GHz    | 56 MHz          |    |  | [Block diagram](https://www.ettus.com/wp-content/uploads/2019/01/USRP_B200mini_BD_925x422-1.png) |
| Ettus USRP B210                  | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Xilinx Spartan-6 XC6SLX150  | AD9361          | 61.44 MSPS ?            |                     | 70 MHz - 6 GHz    | 61.44 MHz ?     | Y  |  | [Block diagram](https://www.amazon.co.uk/Ettus-USRP-B210-MHz-6-cognitive/dp/B09B7DFQ89?ref_=ast_sto_dp) |
| Ettus USRP N320                  | Ethernet 10 GbE SFP+ x2 | 10 Gbits x2 | SoC         | Xilinx Zynq 7100 SoC        | ?               | ??? 14bit ADC 16bit DAC |                     | 3 MHz - 6 GHz     | 200 MHz         |    | [Project page](https://www.ettus.com/all-products/usrp-n320/) | [Block diagram](https://www.ettus.com/wp-content/uploads/2019/03/N320BlockDiagram.png) |

### Pluto like
| Name                             | Interface  | Interface Speed | Interface Controller | FPGA                        | Transceiver     | Sample rate (sustained) | Sample rate (burst) | RF Coverage       | RF Bandwidth    | x2 | Project page | Block diagram |
| -                                | -          | -               | -                    | -                           | -               | -                       | -                   | -                 | -               |:-: | :-:          | :-:           |
| AntSDR E200 AD9361 (Crowdsupply) | Ethernet   | 1 Gbit          | RTL8211F             | Xilinx Zynq XA7Z020         | AD9361          | 61.44 MSPS ? 12bit      | ?                   | 70 MHz - 6 GHz    | 56 MHz          |    | [Project page](https://www.crowdsupply.com/microphase-technology/antsdr-e200) | [Block diagram](https://www.crowdsupply.com/img/6a63/6af378d0-07ec-44fe-9df1-29761bf26a63/ant-e200-block-diagram_png_gallery-lg.jpg) |
| AntSDR E200 AD9363 (Crowdsupply) | Ethernet   | 1 Gbit          | RTL8211F             | Xilinx Zynq XA7Z020         | AD9363          | 61.44 MSPS ? 12bit      | ?                   | 325 MHz - 3.8 GHz | 20 MHz          |    | [Project page](https://www.crowdsupply.com/microphase-technology/antsdr-e200) | [Block diagram](https://www.crowdsupply.com/img/6a63/6af378d0-07ec-44fe-9df1-29761bf26a63/ant-e200-block-diagram_png_gallery-lg.jpg) |
| AntSDR E316 (microphase.cn)      | Ethernet   | 1 Gbit          | RTL8211F             | Xilinx Zynq XC7Z020         | AD9361 / AD9363 | UHD:20MSPS / IIO:10MSPS | 56 MSPS             | 70MHz-6GHz / 325MHz-3.8GHz | 56 MHz / 20 MHz | Y  | [Project page](https://www.microphase.cn/productinfo/2299498.html) | |
| AntSDR U220 (microphase.cn)      | USB 3.0 C  | 5 Gbits         | CYUSB3014-BZX        | Xilinx Zynq XC7A200T/100T   | AD9361 / AD9363 | UHD:56 MSPS             | 56 MSPS             | 70MHz-6GHz / 325MHz-3.8GHz | 56 MHz / 20 MHz | Y  | [Project page](https://www.microphase.cn/productinfo/2299514.html) | |
| LibreSDR (better FPGA + Eth) $300| USB 2.0 + Ethernet 1Gbit | 480 Mbits + 1 Gbit | FT2232HQ + USB3320C-EZK-TR ? + RTL8211E-VB | Xilinx Zynq XC7Z020-1CLG400I | AD9363 | ?    | ?       | 325 MHz - 3.8 GHz | ?               | Y  | [Shop page](https://www.aliexpress.com/item/1005004916987318.html) | [Block diagram](https://github.com/day0wl/libresdr-fw/tree/main) |
| Neptune SDR K210 (better FPGA + Eth) $350 | Ethernet | 1 Gbit   | FT2232               | Xilinx Zynq XC7Z020 1GByte  | AD9361          | 25 MPS                  |                     | 70 MHz - 6 GHz    | ?               | Y  | [Shop page](https://www.aliexpress.com/item/1005007995977956.html) | |
| Signalens SignalSDR Pro          | USB 3.0 (3)| 5 Gbits         | SoC                  | Xilinx Zynq XC7Z020 2CLG400 SoC| AD9361       | 61.44 MSPS 12bit        |                     | 70 MHz - 6 GHz    | 56 MHz          | Y  | [Project page](https://www.crowdsupply.com/signalens/signalsdr-pro) | [Block diagram](https://www.crowdsupply.com/img/1039/50daf1c1-9191-46b1-9b91-c68587751039/signalsdr-pro-block-diagram.svg) |

### Ettus like
| Name                             | Interface  | Interface Speed | Interface Controller | FPGA                        | Transceiver     | Sample rate (sustained) | Sample rate (burst) | RF Coverage       | RF Bandwidth    | x2 | Project page | Block diagram |
| -                                | -          | -               | -                    | -                           | -               | -                       | -                   | -                 | -               |:-: | :-:          | :-:           |
| LibreSDR (B210)        $300 (4)! | USB 3.0    | 5 Gbits         | CYUSB3014 ?          | Xilinx Artix 7 XC7A100T     | AD9363          | 61.44 MSPS 12bit ?      |                     | 325 MHz - 3.8 GHz | 56 MHz          | Y  | [Shop page](https://www.aliexpress.com/item/1005008177145326.html) | |
| LibreSDR (B210)        $350 (4)! | USB 3.0    | 5 Gbits         | CYUSB3014 ?          | Xilinx Artix 7 XC7A200T     | AD9361          | 61.44 MSPS 12bit        |                     | 70 MHz - 6 GHz    | 56 MHz          | Y  | [Shop page](https://www.aliexpress.com/item/1005008177145326.html) | [Board picture](https://ae01.alicdn.com/kf/S591686fe3fd24b76b0874fe486e3a498b.jpg) |
| SC-B210 (B210 clone)      $1,000 | USB 3.0    | 5 Gbits         | ?                    | Xilinx Spartan-6 ?          | ?               | ?                       |                     | 70 MHz - 6 GHz    | ?               | Y  | [Shop page](https://www.aliexpress.com/item/1005008525068995.html) | |
| CBTS U210-mini (B205mini) $1,000 | USB 3.0    | 5 Gbits         | ?                    | Xilinx Spartan-6 XC6SLX150  | AD9361 ?        | 61.44 MSPS 12bit ?      |                     | 70 MHz - 6 GHz    |                 |    | [Shop page](https://www.aliexpress.com/item/4000170698563.html)    | [Board picture](https://ae01.alicdn.com/kf/H1dd59e5b850e4393b9bc6d2734d684f5V.jpg) |
| CBTS B210-micro (B210)    $1,100 | USB 3.0    | 5 Gbits         | CYUSB3014-BZX        | Xilinx Spartan-6 XC6SLX150  | AD9361          | 61.44 MSPS 12bit        |                     | 70 MHz - 6 GHz    |                 | Y  | [Shop page](https://www.aliexpress.com/item/1005008479361830.html) | [Board picture](https://ae01.alicdn.com/kf/Hed501b7a6f02452d886f772290d5b413Y.jpg) |

- (4) Claim that Artix 7 does not work with UHD https://wucke13.de/posts/blacksdr-b210mini-sdr/

### Work in progress / Miscellaneous
| Name                             | Interface  | Interface Speed | Interface Controller | FPGA                        | Transceiver     | Sample rate (sustained) | Sample rate (burst) | RF Coverage       | RF Bandwidth    | Project page | Block diagram |
| -                                | -          | -               | -                    | -                           | -               | -                       | -                   | -                 | -               | :-:          | :-:           |
| Red Pitaya                       | Ethernet   | 1 Gbit          | SoC                  | Xilinx Zynq XC7Z010-1CLG400C| ADC LTC2145-14 / DAC AD9767 | 125 MSPS 14bit |                  | DC - 60 MHz       | ?               |  | [Block diagram](https://redpitaya.readthedocs.io/en/latest/developerGuide/hardware/125-14/top.html) |
| Wavelet Lab sSDR                 | PCIe Gen2 x2 lanes M.2 | 10 Gbits | SoC             | AMD Artix 7 XC7A35T         | LMS7002M + LMS8001A | 100 MSps ?          | ?                   | 30 MHz - 8.5 GHz RX/TX | 90 MHz     |  | [Block diagram](https://www.crowdsupply.com/img/9bfc/e0724489-2123-4f79-be66-b8161e8f9bfc/susdr-sch-lg_jpg_gallery-lg.jpg) |
| Vesperix Corp. VXSDR-20-160      | Ethernet 10 GbE SFP+   | 10 Gbits | SoC             | Altera Cyclone 10 GX105     | ADC32J45 + DAC37J82 | 160 MSPS ADC 14bit / 160 MSPS DAC 16bit | | 5 - 20 GHz        |                 | [Project page](https://www.crowdsupply.com/vesperix-corporation/vxsdr-20-160) | [Block diagram](https://www.crowdsupply.com/img/8bb1/82c06c38-a9f8-45fa-b36f-3925ea5a8bb1/vxsdr-20-160-block-diagram.svg) |

- (1) Overclock 122.88MSPS https://www.nuand.com/2023-02-release-122-88mhz-bandwidth/
- (2) GNUradio "20 MHz limited by USB 2.0 and software to ~4Mhz" https://wiki.gnuradio.org/index.php/Hardware
- (3) Ethernet also available

## References

### Ettus matrix

| USRP Bus Series  | Xilinx Spartan-6 XC6SLX75 | Xilinx Spartan-6 XC6SLX150 | AD9361 | AD9364 | USB 3.0 | x2 |                  |
| -                | :-:                       | :-:                        | :-:    | :-:    | :-:     | :-:| :-:              | 
| B200mini         | ✅                        |                            |        | ✅     | ✅      |    | [Product Page](https://www.ettus.com/all-products/usrp-b200mini/) |
| B200mini-i       | ✅                        |                            |        | ✅     | ✅      |    | [Product Page](https://www.ettus.com/all-products/usrp-b200mini-i-2/) |
| B205mini-i       |                           | ✅                         |        | ✅     | ✅      |    | [Product Page](https://www.ettus.com/all-products/usrp-b205mini-i/) |
| B200             | ✅                        |                            |        | ✅     | ✅      |    | [Product Page](https://www.ettus.com/all-products/ub200-kit/) |
| B210             |                           | ✅                         | ✅     |        | ✅      | ✅ | [Product Page](https://www.ettus.com/all-products/ub210-kit/) |

### Transceivers
| Name     | Frequency Range   | Datasheet |
| -        | -                 | :-:       |
| LMS6002D | 300 MHz - 3.8 GHz | [PDF](https://cdn.sanity.io/files/yv2p7ubm/production/47449c61cd388c058561bfd3121b8a10b3d2c987.pdf 'LMS6002D Datasheet') |
| LMS7002M | 100 kHz - 3.5 GHz | [PDF](https://cdn.sanity.io/files/yv2p7ubm/production/dc7fec4c445b008b9a1d35ea5a16a2850e923fe2.pdf 'LMS7002M Datasheet') |
| LMS8001A Up/Down converter | 0.8 - 10 GHz | [PDF](https://github.com/myriadrf/LMS8001-docs/blob/master/LMS8001A-Datasheet%204.0r5.pdf 'LMS8001A Datasheet') |
| AD9361   |  70 MHz - 6 GHz   | [https://www.analog.com/en/products/ad9361.html](https://www.analog.com/en/products/ad9361.html 'AD9361 Datasheet') |
| AD9363   | 325 MHz - 3.8 GHz | [https://www.analog.com/en/products/ad9363.html](https://www.analog.com/en/products/ad9363.html 'AD9363 Datasheet') |
| AD9364   |  70 MHz - 6 GHz   | [https://www.analog.com/en/products/ad9364.html](https://www.analog.com/en/products/ad9364.html 'AD9364 Datasheet') |
