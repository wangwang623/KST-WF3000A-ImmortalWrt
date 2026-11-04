# KST WF3000A · ImmortalWrt 24.10 / Linux 6.6

## 👉 源码、固件与文档都在新仓库

### https://github.com/wangwang623/immortalwrt-mt798x-6.6

本仓库只作型号索引与引导，**不含源码、不再发布固件**。
云编译、下载 Release、刷机说明、问题反馈请全部到新仓库。

---

## 适用硬件

| 项目 | 值 |
|---|---|
| 机型 | **KST WF3000A** |
| SoC | MediaTek MT7981B（双核 A53 @ 1.3GHz） |
| 内存 | 256 MB |
| Flash | 128 MB SPI-NAND |
| 无线 | MT7976，2.4G + 5G 双频 AX3000 |

## 分区布局

只支持 **expand(114m)** 大分区布局：

```text
nmbm0:1024k(bl2),512k(u-boot-env),2048k(factory),2048k(fip),116736k(ubi)
```

| 分区 | 起始 | 大小 |
|---|---:|---:|
| bl2 | `0x0000000` | `0x0100000` |
| u-boot-env | `0x0100000` | `0x0080000` |
| factory | `0x0180000` | `0x0200000` |
| fip | `0x0380000` | `0x0200000` |
| ubi | `0x0580000` | `0x07200000`（116736 KiB） |

> 刷机时 U-Boot Web 的布局下拉框也必须选 **114m**，两者必须对应。
> 该布局需先刷入支持多分区的 U-Boot，步骤见新仓库 README「刷机前提」。

---

## 新仓库有什么

- **完整 fork 源码** —— 设备树、机型定义、MAC 推导、无线驱动配置等移植改动已直接写进源码
- **GitHub Actions 一键云编译** —— 产出 `initramfs-kernel.bin` / `squashfs-factory.bin` / `squashfs-sysupgrade.bin` 三个镜像
- **纯净固件** —— 官方默认包 + LuCI 中文 + HNAT 硬件加速 + MTK 无线驱动，不含第三方插件，需要什么刷完自己 `opkg install`
- **内置 NMBM oobsize 对齐修复** —— 解决「同一份固件，有的机器正常、有的机器刷完反复重启或一直停在 U-Boot Web」的问题
- **完整文档** —— 刷机步骤、验证命令、MAC 规律、无线驱动说明、NMBM 原理与排查
- 同时支持 **Redmi AX6000（MT7986）**

---

编译、下载、刷机、提 Issue / PR，请直接前往
**https://github.com/wangwang623/immortalwrt-mt798x-6.6**
