---
title: rk3328-roc-cc
layout: page
parent: Rebuilding
---
## rk3328-roc-cc

Source of Sovol's rk3328-roc-cc.dtb from 5.16.20 kernel [download](files/rk3328-roc-cc.dts)

(This does not yet include the [wifi-patch](#wifi-patch))

To apply the patch by your own:
  * Decompile dtb to dts: `dtc -I dtb -O dts /boot/dtb/rockchip/rk3328-roc-cc.dtb -o rk3328-roc-cc.dts`
  * Modify rk3328-roc-cc.dts: Change line 863 from "rockchip,spi_test_bus1_cs2" to "armbian,spi-dev"
  * Compile dts back to dtb: `dtc -I dts -O dtb rk3328-roc-cc.dts -o /boot/dtb/rockchip/rk3328-roc-cc.dtb`


```
/dts-v1/;

/ {
	compatible = "firefly,roc-rk3328-cc\0rockchip,rk3328";
	interrupt-parent = <0x01>;
	#address-cells = <0x02>;
	#size-cells = <0x02>;
	model = "Firefly roc-rk3328-cc";

	ddr_timing {
		compatible = "rockchip,ddr-timing";
		ddr3_speed_bin = <0x15>;
		ddr4_speed_bin = <0x0c>;
		pd_idle = <0x00>;
		sr_idle = <0x00>;
		sr_mc_gate_idle = <0x00>;
		srpd_lite_idle = <0x00>;
		standby_idle = <0x00>;
		auto_pd_dis_freq = <0x42a>;
		auto_sr_dis_freq = <0x320>;
		ddr3_dll_dis_freq = <0x12c>;
		ddr4_dll_dis_freq = <0x271>;
		phy_dll_dis_freq = <0x190>;
		ddr3_odt_dis_freq = <0x64>;
		phy_ddr3_odt_dis_freq = <0x64>;
		ddr3_drv = <0x28>;
		ddr3_odt = <0x78>;
		phy_ddr3_ca_drv = <0x15>;
		phy_ddr3_ck_drv = <0x12>;
		phy_ddr3_dq_drv = <0x15>;
		phy_ddr3_odt = <0x02>;
		lpddr3_odt_dis_freq = <0x29a>;
		phy_lpddr3_odt_dis_freq = <0x29a>;
		lpddr3_drv = <0x28>;
		lpddr3_odt = <0xf0>;
		phy_lpddr3_ca_drv = <0x16>;
		phy_lpddr3_ck_drv = <0x13>;
		phy_lpddr3_dq_drv = <0x16>;
		phy_lpddr3_odt = <0x02>;
		lpddr4_odt_dis_freq = <0x320>;
		phy_lpddr4_odt_dis_freq = <0x320>;
		lpddr4_drv = <0x3c>;
		lpddr4_dq_odt = <0x28>;
		lpddr4_ca_odt = <0x28>;
		phy_lpddr4_ca_drv = <0x14>;
		phy_lpddr4_ck_cs_drv = <0x06>;
		phy_lpddr4_dq_drv = <0x06>;
		phy_lpddr4_odt = <0x10>;
		ddr4_odt_dis_freq = <0x29a>;
		phy_ddr4_odt_dis_freq = <0x29a>;
		ddr4_drv = <0x22>;
		ddr4_odt = <0xf0>;
		phy_ddr4_ca_drv = <0x16>;
		phy_ddr4_ck_drv = <0x13>;
		phy_ddr4_dq_drv = <0x16>;
		phy_ddr4_odt = <0x02>;
		ddr3a1_ddr4a9_de-skew = <0x00>;
		ddr3a0_ddr4a10_de-skew = <0x00>;
		ddr3a3_ddr4a6_de-skew = <0x01>;
		ddr3a2_ddr4a4_de-skew = <0x01>;
		ddr3a5_ddr4a8_de-skew = <0x00>;
		ddr3a4_ddr4a5_de-skew = <0x02>;
		ddr3a7_ddr4a11_de-skew = <0x00>;
		ddr3a6_ddr4a7_de-skew = <0x02>;
		ddr3a9_ddr4a0_de-skew = <0x01>;
		ddr3a8_ddr4a13_de-skew = <0x00>;
		ddr3a11_ddr4a3_de-skew = <0x02>;
		ddr3a10_ddr4cs0_de-skew = <0x00>;
		ddr3a13_ddr4a2_de-skew = <0x01>;
		ddr3a12_ddr4ba1_de-skew = <0x00>;
		ddr3a15_ddr4odt0_de-skew = <0x00>;
		ddr3a14_ddr4a1_de-skew = <0x01>;
		ddr3ba1_ddr4a15_de-skew = <0x00>;
		ddr3ba0_ddr4bg0_de-skew = <0x00>;
		ddr3ras_ddr4cke_de-skew = <0x00>;
		ddr3ba2_ddr4ba0_de-skew = <0x01>;
		ddr3we_ddr4bg1_de-skew = <0x01>;
		ddr3cas_ddr4a12_de-skew = <0x00>;
		ddr3ckn_ddr4ckn_de-skew = <0x05>;
		ddr3ckp_ddr4ckp_de-skew = <0x05>;
		ddr3cke_ddr4a16_de-skew = <0x01>;
		ddr3odt0_ddr4a14_de-skew = <0x00>;
		ddr3cs0_ddr4act_de-skew = <0x01>;
		ddr3reset_ddr4reset_de-skew = <0x00>;
		ddr3cs1_ddr4cs1_de-skew = <0x00>;
		ddr3odt1_ddr4odt1_de-skew = <0x00>;
		cs0_dm0_rx_de-skew = <0x07>;
		cs0_dm0_tx_de-skew = <0x08>;
		cs0_dq0_rx_de-skew = <0x07>;
		cs0_dq0_tx_de-skew = <0x08>;
		cs0_dq1_rx_de-skew = <0x07>;
		cs0_dq1_tx_de-skew = <0x08>;
		cs0_dq2_rx_de-skew = <0x07>;
		cs0_dq2_tx_de-skew = <0x08>;
		cs0_dq3_rx_de-skew = <0x07>;
		cs0_dq3_tx_de-skew = <0x08>;
		cs0_dq4_rx_de-skew = <0x07>;
		cs0_dq4_tx_de-skew = <0x08>;
		cs0_dq5_rx_de-skew = <0x07>;
		cs0_dq5_tx_de-skew = <0x08>;
		cs0_dq6_rx_de-skew = <0x07>;
		cs0_dq6_tx_de-skew = <0x08>;
		cs0_dq7_rx_de-skew = <0x07>;
		cs0_dq7_tx_de-skew = <0x08>;
		cs0_dqs0_rx_de-skew = <0x06>;
		cs0_dqs0p_tx_de-skew = <0x09>;
		cs0_dqs0n_tx_de-skew = <0x09>;
		cs0_dm1_rx_de-skew = <0x07>;
		cs0_dm1_tx_de-skew = <0x07>;
		cs0_dq8_rx_de-skew = <0x07>;
		cs0_dq8_tx_de-skew = <0x08>;
		cs0_dq9_rx_de-skew = <0x07>;
		cs0_dq9_tx_de-skew = <0x07>;
		cs0_dq10_rx_de-skew = <0x07>;
		cs0_dq10_tx_de-skew = <0x08>;
		cs0_dq11_rx_de-skew = <0x07>;
		cs0_dq11_tx_de-skew = <0x07>;
		cs0_dq12_rx_de-skew = <0x07>;
		cs0_dq12_tx_de-skew = <0x08>;
		cs0_dq13_rx_de-skew = <0x07>;
		cs0_dq13_tx_de-skew = <0x07>;
		cs0_dq14_rx_de-skew = <0x07>;
		cs0_dq14_tx_de-skew = <0x08>;
		cs0_dq15_rx_de-skew = <0x07>;
		cs0_dq15_tx_de-skew = <0x07>;
		cs0_dqs1_rx_de-skew = <0x07>;
		cs0_dqs1p_tx_de-skew = <0x09>;
		cs0_dqs1n_tx_de-skew = <0x09>;
		cs0_dm2_rx_de-skew = <0x07>;
		cs0_dm2_tx_de-skew = <0x08>;
		cs0_dq16_rx_de-skew = <0x07>;
		cs0_dq16_tx_de-skew = <0x08>;
		cs0_dq17_rx_de-skew = <0x07>;
		cs0_dq17_tx_de-skew = <0x08>;
		cs0_dq18_rx_de-skew = <0x07>;
		cs0_dq18_tx_de-skew = <0x08>;
		cs0_dq19_rx_de-skew = <0x07>;
		cs0_dq19_tx_de-skew = <0x08>;
		cs0_dq20_rx_de-skew = <0x07>;
		cs0_dq20_tx_de-skew = <0x08>;
		cs0_dq21_rx_de-skew = <0x07>;
		cs0_dq21_tx_de-skew = <0x08>;
		cs0_dq22_rx_de-skew = <0x07>;
		cs0_dq22_tx_de-skew = <0x08>;
		cs0_dq23_rx_de-skew = <0x07>;
		cs0_dq23_tx_de-skew = <0x08>;
		cs0_dqs2_rx_de-skew = <0x06>;
		cs0_dqs2p_tx_de-skew = <0x09>;
		cs0_dqs2n_tx_de-skew = <0x09>;
		cs0_dm3_rx_de-skew = <0x07>;
		cs0_dm3_tx_de-skew = <0x07>;
		cs0_dq24_rx_de-skew = <0x07>;
		cs0_dq24_tx_de-skew = <0x08>;
		cs0_dq25_rx_de-skew = <0x07>;
		cs0_dq25_tx_de-skew = <0x07>;
		cs0_dq26_rx_de-skew = <0x07>;
		cs0_dq26_tx_de-skew = <0x07>;
		cs0_dq27_rx_de-skew = <0x07>;
		cs0_dq27_tx_de-skew = <0x07>;
		cs0_dq28_rx_de-skew = <0x07>;
		cs0_dq28_tx_de-skew = <0x07>;
		cs0_dq29_rx_de-skew = <0x07>;
		cs0_dq29_tx_de-skew = <0x07>;
		cs0_dq30_rx_de-skew = <0x07>;
		cs0_dq30_tx_de-skew = <0x07>;
		cs0_dq31_rx_de-skew = <0x07>;
		cs0_dq31_tx_de-skew = <0x07>;
		cs0_dqs3_rx_de-skew = <0x07>;
		cs0_dqs3p_tx_de-skew = <0x09>;
		cs0_dqs3n_tx_de-skew = <0x09>;
		cs1_dm0_rx_de-skew = <0x07>;
		cs1_dm0_tx_de-skew = <0x08>;
		cs1_dq0_rx_de-skew = <0x07>;
		cs1_dq0_tx_de-skew = <0x08>;
		cs1_dq1_rx_de-skew = <0x07>;
		cs1_dq1_tx_de-skew = <0x08>;
		cs1_dq2_rx_de-skew = <0x07>;
		cs1_dq2_tx_de-skew = <0x08>;
		cs1_dq3_rx_de-skew = <0x07>;
		cs1_dq3_tx_de-skew = <0x08>;
		cs1_dq4_rx_de-skew = <0x07>;
		cs1_dq4_tx_de-skew = <0x08>;
		cs1_dq5_rx_de-skew = <0x07>;
		cs1_dq5_tx_de-skew = <0x08>;
		cs1_dq6_rx_de-skew = <0x07>;
		cs1_dq6_tx_de-skew = <0x08>;
		cs1_dq7_rx_de-skew = <0x07>;
		cs1_dq7_tx_de-skew = <0x08>;
		cs1_dqs0_rx_de-skew = <0x06>;
		cs1_dqs0p_tx_de-skew = <0x09>;
		cs1_dqs0n_tx_de-skew = <0x09>;
		cs1_dm1_rx_de-skew = <0x07>;
		cs1_dm1_tx_de-skew = <0x07>;
		cs1_dq8_rx_de-skew = <0x07>;
		cs1_dq8_tx_de-skew = <0x08>;
		cs1_dq9_rx_de-skew = <0x07>;
		cs1_dq9_tx_de-skew = <0x07>;
		cs1_dq10_rx_de-skew = <0x07>;
		cs1_dq10_tx_de-skew = <0x08>;
		cs1_dq11_rx_de-skew = <0x07>;
		cs1_dq11_tx_de-skew = <0x07>;
		cs1_dq12_rx_de-skew = <0x07>;
		cs1_dq12_tx_de-skew = <0x08>;
		cs1_dq13_rx_de-skew = <0x07>;
		cs1_dq13_tx_de-skew = <0x07>;
		cs1_dq14_rx_de-skew = <0x07>;
		cs1_dq14_tx_de-skew = <0x08>;
		cs1_dq15_rx_de-skew = <0x07>;
		cs1_dq15_tx_de-skew = <0x07>;
		cs1_dqs1_rx_de-skew = <0x07>;
		cs1_dqs1p_tx_de-skew = <0x09>;
		cs1_dqs1n_tx_de-skew = <0x09>;
		cs1_dm2_rx_de-skew = <0x07>;
		cs1_dm2_tx_de-skew = <0x08>;
		cs1_dq16_rx_de-skew = <0x07>;
		cs1_dq16_tx_de-skew = <0x08>;
		cs1_dq17_rx_de-skew = <0x07>;
		cs1_dq17_tx_de-skew = <0x08>;
		cs1_dq18_rx_de-skew = <0x07>;
		cs1_dq18_tx_de-skew = <0x08>;
		cs1_dq19_rx_de-skew = <0x07>;
		cs1_dq19_tx_de-skew = <0x08>;
		cs1_dq20_rx_de-skew = <0x07>;
		cs1_dq20_tx_de-skew = <0x08>;
		cs1_dq21_rx_de-skew = <0x07>;
		cs1_dq21_tx_de-skew = <0x08>;
		cs1_dq22_rx_de-skew = <0x07>;
		cs1_dq22_tx_de-skew = <0x08>;
		cs1_dq23_rx_de-skew = <0x07>;
		cs1_dq23_tx_de-skew = <0x08>;
		cs1_dqs2_rx_de-skew = <0x06>;
		cs1_dqs2p_tx_de-skew = <0x09>;
		cs1_dqs2n_tx_de-skew = <0x09>;
		cs1_dm3_rx_de-skew = <0x07>;
		cs1_dm3_tx_de-skew = <0x07>;
		cs1_dq24_rx_de-skew = <0x07>;
		cs1_dq24_tx_de-skew = <0x08>;
		cs1_dq25_rx_de-skew = <0x07>;
		cs1_dq25_tx_de-skew = <0x07>;
		cs1_dq26_rx_de-skew = <0x07>;
		cs1_dq26_tx_de-skew = <0x07>;
		cs1_dq27_rx_de-skew = <0x07>;
		cs1_dq27_tx_de-skew = <0x07>;
		cs1_dq28_rx_de-skew = <0x07>;
		cs1_dq28_tx_de-skew = <0x07>;
		cs1_dq29_rx_de-skew = <0x07>;
		cs1_dq29_tx_de-skew = <0x07>;
		cs1_dq30_rx_de-skew = <0x07>;
		cs1_dq30_tx_de-skew = <0x07>;
		cs1_dq31_rx_de-skew = <0x07>;
		cs1_dq31_tx_de-skew = <0x07>;
		cs1_dqs3_rx_de-skew = <0x07>;
		cs1_dqs3p_tx_de-skew = <0x09>;
		cs1_dqs3n_tx_de-skew = <0x09>;
		phandle = <0x43>;
	};

	aliases {
		serial0 = "/serial@ff110000";
		serial1 = "/serial@ff120000";
		serial2 = "/serial@ff130000";
		i2c0 = "/i2c@ff150000";
		i2c1 = "/i2c@ff160000";
		i2c2 = "/i2c@ff170000";
		i2c3 = "/i2c@ff180000";
		ethernet0 = "/ethernet@ff540000";
		ethernet1 = "/ethernet@ff550000";
		mmc0 = "/mmc@ff500000";
		mmc1 = "/mmc@ff520000";
	};

	cpus {
		#address-cells = <0x02>;
		#size-cells = <0x00>;

		cpu@0 {
			device_type = "cpu";
			compatible = "arm,cortex-a53";
			reg = <0x00 0x00>;
			clocks = <0x02 0x06>;
			#cooling-cells = <0x02>;
			cpu-idle-states = <0x03>;
			dynamic-power-coefficient = <0x78>;
			enable-method = "psci";
			next-level-cache = <0x04>;
			operating-points-v2 = <0x05>;
			cpu-supply = <0x06>;
			phandle = <0x09>;
		};

		cpu@1 {
			device_type = "cpu";
			compatible = "arm,cortex-a53";
			reg = <0x00 0x01>;
			clocks = <0x02 0x06>;
			#cooling-cells = <0x02>;
			cpu-idle-states = <0x03>;
			dynamic-power-coefficient = <0x78>;
			enable-method = "psci";
			next-level-cache = <0x04>;
			operating-points-v2 = <0x05>;
			cpu-supply = <0x06>;
			phandle = <0x0a>;
		};

		cpu@2 {
			device_type = "cpu";
			compatible = "arm,cortex-a53";
			reg = <0x00 0x02>;
			clocks = <0x02 0x06>;
			#cooling-cells = <0x02>;
			cpu-idle-states = <0x03>;
			dynamic-power-coefficient = <0x78>;
			enable-method = "psci";
			next-level-cache = <0x04>;
			operating-points-v2 = <0x05>;
			cpu-supply = <0x06>;
			phandle = <0x0b>;
		};

		cpu@3 {
			device_type = "cpu";
			compatible = "arm,cortex-a53";
			reg = <0x00 0x03>;
			clocks = <0x02 0x06>;
			#cooling-cells = <0x02>;
			cpu-idle-states = <0x03>;
			dynamic-power-coefficient = <0x78>;
			enable-method = "psci";
			next-level-cache = <0x04>;
			operating-points-v2 = <0x05>;
			cpu-supply = <0x06>;
			phandle = <0x0c>;
		};

		idle-states {
			entry-method = "psci";

			cpu-sleep {
				compatible = "arm,idle-state";
				local-timer-stop;
				arm,psci-suspend-param = <0x10000>;
				entry-latency-us = <0x78>;
				exit-latency-us = <0xfa>;
				min-residency-us = <0x384>;
				phandle = <0x03>;
			};
		};

		l2-cache0 {
			compatible = "cache";
			phandle = <0x04>;
		};
	};

	opp-table-0 {
		compatible = "operating-points-v2";
		opp-shared;
		phandle = <0x05>;

		opp-408000000 {
			opp-hz = <0x00 0x18519600>;
			opp-microvolt = <0xe7ef0>;
			clock-latency-ns = <0x9c40>;
			opp-suspend;
		};

		opp-600000000 {
			opp-hz = <0x00 0x23c34600>;
			opp-microvolt = <0xe7ef0>;
			clock-latency-ns = <0x9c40>;
		};

		opp-816000000 {
			opp-hz = <0x00 0x30a32c00>;
			opp-microvolt = <0xf4240>;
			clock-latency-ns = <0x9c40>;
		};

		opp-1008000000 {
			opp-hz = <0x00 0x3c14dc00>;
			opp-microvolt = <0x10c8e0>;
			clock-latency-ns = <0x9c40>;
		};

		opp-1200000000 {
			opp-hz = <0x00 0x47868c00>;
			opp-microvolt = <0x12b128>;
			clock-latency-ns = <0x9c40>;
		};

		opp-1296000000 {
			opp-hz = <0x00 0x4d3f6400>;
			opp-microvolt = <0x13d620>;
			clock-latency-ns = <0x9c40>;
		};
	};

	analog-sound {
		compatible = "simple-audio-card";
		simple-audio-card,format = "i2s";
		simple-audio-card,mclk-fs = <0x100>;
		simple-audio-card,name = "TRS Jack";
		status = "okay";
		phandle = <0x75>;

		simple-audio-card,cpu {
			sound-dai = <0x07>;
		};

		simple-audio-card,codec {
			sound-dai = <0x08>;
		};
	};

	arm-pmu {
		compatible = "arm,cortex-a53-pmu";
		interrupts = <0x00 0x64 0x04 0x00 0x65 0x04 0x00 0x66 0x04 0x00 0x67 0x04>;
		interrupt-affinity = <0x09 0x0a 0x0b 0x0c>;
	};

	display-subsystem {
		compatible = "rockchip,display-subsystem";
		ports = <0x0d>;
		phandle = <0x76>;
	};

	hdmi-sound {
		compatible = "simple-audio-card";
		simple-audio-card,format = "i2s";
		simple-audio-card,mclk-fs = <0x80>;
		simple-audio-card,name = "HDMI";
		status = "disabled";
		phandle = <0x77>;

		simple-audio-card,cpu {
			sound-dai = <0x0e>;
		};

		simple-audio-card,codec {
			sound-dai = <0x0f>;
		};
	};

	psci {
		compatible = "arm,psci-1.0\0arm,psci-0.2";
		method = "smc";
	};

	spdif-out {
		compatible = "linux,spdif-dit";
		#sound-dai-cells = <0x00>;
		status = "disabled";
		phandle = <0x11>;
	};

	spdif-sound {
		compatible = "simple-audio-card";
		simple-audio-card,name = "SPDIF";
		status = "disabled";
		phandle = <0x78>;

		simple-audio-card,cpu {
			sound-dai = <0x10>;
		};

		simple-audio-card,codec {
			sound-dai = <0x11>;
		};
	};

	timer {
		compatible = "arm,armv8-timer";
		interrupts = <0x01 0x0d 0xf08 0x01 0x0e 0xf08 0x01 0x0b 0xf08 0x01 0x0a 0xf08>;
	};

	xin24m {
		compatible = "fixed-clock";
		#clock-cells = <0x00>;
		clock-frequency = <0x16e3600>;
		clock-output-names = "xin24m";
		phandle = <0x50>;
	};

	i2s@ff000000 {
		compatible = "rockchip,rk3328-i2s\0rockchip,rk3066-i2s";
		reg = <0x00 0xff000000 0x00 0x1000>;
		interrupts = <0x00 0x1a 0x04>;
		clocks = <0x02 0x29 0x02 0x137>;
		clock-names = "i2s_clk\0i2s_hclk";
		dmas = <0x12 0x0b 0x12 0x0c>;
		dma-names = "tx\0rx";
		#sound-dai-cells = <0x00>;
		status = "disabled";
		phandle = <0x0e>;
	};

	i2s@ff010000 {
		compatible = "rockchip,rk3328-i2s\0rockchip,rk3066-i2s";
		reg = <0x00 0xff010000 0x00 0x1000>;
		interrupts = <0x00 0x1b 0x04>;
		clocks = <0x02 0x2a 0x02 0x138>;
		clock-names = "i2s_clk\0i2s_hclk";
		dmas = <0x12 0x0e 0x12 0x0f>;
		dma-names = "tx\0rx";
		#sound-dai-cells = <0x00>;
		status = "okay";
		phandle = <0x07>;
	};

	i2s@ff020000 {
		compatible = "rockchip,rk3328-i2s\0rockchip,rk3066-i2s";
		reg = <0x00 0xff020000 0x00 0x1000>;
		interrupts = <0x00 0x1c 0x04>;
		clocks = <0x02 0x2b 0x02 0x139>;
		clock-names = "i2s_clk\0i2s_hclk";
		dmas = <0x12 0x00 0x12 0x01>;
		dma-names = "tx\0rx";
		#sound-dai-cells = <0x00>;
		status = "disabled";
		phandle = <0x79>;
	};

	spdif@ff030000 {
		compatible = "rockchip,rk3328-spdif";
		reg = <0x00 0xff030000 0x00 0x1000>;
		interrupts = <0x00 0x1d 0x04>;
		clocks = <0x02 0x2e 0x02 0x13a>;
		clock-names = "mclk\0hclk";
		dmas = <0x12 0x0a>;
		dma-names = "tx";
		pinctrl-names = "default";
		pinctrl-0 = <0x13>;
		#sound-dai-cells = <0x00>;
		status = "disabled";
		phandle = <0x10>;
	};

	pdm@ff040000 {
		compatible = "rockchip,pdm";
		reg = <0x00 0xff040000 0x00 0x1000>;
		clocks = <0x02 0x3d 0x02 0x152>;
		clock-names = "pdm_clk\0pdm_hclk";
		dmas = <0x12 0x10>;
		dma-names = "rx";
		pinctrl-names = "default\0sleep";
		pinctrl-0 = <0x14 0x15 0x16 0x17 0x18>;
		pinctrl-1 = <0x19 0x1a 0x1b 0x1c 0x1d>;
		status = "disabled";
		phandle = <0x7a>;
	};

	syscon@ff100000 {
		compatible = "rockchip,rk3328-grf\0syscon\0simple-mfd";
		reg = <0x00 0xff100000 0x00 0x1000>;
		phandle = <0x3f>;

		io-domains {
			compatible = "rockchip,rk3328-io-voltage-domain";
			status = "okay";
			vccio1-supply = <0x1e>;
			vccio2-supply = <0x1f>;
			vccio3-supply = <0x20>;
			vccio4-supply = <0x1e>;
			vccio5-supply = <0x1e>;
			vccio6-supply = <0x1e>;
			pmuio-supply = <0x1e>;
			phandle = <0x7b>;
		};

		gpio {
			compatible = "rockchip,rk3328-grf-gpio";
			gpio-controller;
			#gpio-cells = <0x02>;
			phandle = <0x7c>;
		};

		power-controller {
			compatible = "rockchip,rk3328-power-controller";
			#power-domain-cells = <0x01>;
			#address-cells = <0x01>;
			#size-cells = <0x00>;
			phandle = <0x44>;

			power-domain@1 {
				reg = <0x01>;
				clocks = <0x02 0x87>;
			};

			power-domain@6 {
				reg = <0x06>;
				#power-domain-cells = <0x00>;
			};

			power-domain@5 {
				reg = <0x05>;
				clocks = <0x02 0x8b 0x02 0x142 0x02 0x41 0x02 0x42>;
				#power-domain-cells = <0x00>;
			};

			power-domain@8 {
				reg = <0x08>;
				clocks = <0x02 0x8f 0x02 0x146>;
				#power-domain-cells = <0x00>;
			};
		};

		reboot-mode {
			compatible = "syscon-reboot-mode";
			offset = <0x5c8>;
			mode-normal = <0x5242c300>;
			mode-recovery = <0x5242c303>;
			mode-bootloader = <0x5242c309>;
			mode-loader = <0x5242c301>;
		};
	};

	serial@ff110000 {
		compatible = "rockchip,rk3328-uart\0snps,dw-apb-uart";
		reg = <0x00 0xff110000 0x00 0x100>;
		interrupts = <0x00 0x37 0x04>;
		clocks = <0x02 0x26 0x02 0xd2>;
		clock-names = "baudclk\0apb_pclk";
		dmas = <0x12 0x02 0x12 0x03>;
		dma-names = "tx\0rx";
		pinctrl-names = "default";
		pinctrl-0 = <0x21 0x22>;
		reg-io-width = <0x04>;
		reg-shift = <0x02>;
		status = "okay";
		phandle = <0x7d>;
	};

	serial@ff120000 {
		compatible = "rockchip,rk3328-uart\0snps,dw-apb-uart";
		reg = <0x00 0xff120000 0x00 0x100>;
		interrupts = <0x00 0x38 0x04>;
		clocks = <0x02 0x27 0x02 0xd3>;
		clock-names = "baudclk\0apb_pclk";
		dmas = <0x12 0x04 0x12 0x05>;
		dma-names = "tx\0rx";
		pinctrl-names = "default";
		pinctrl-0 = <0x23 0x24 0x25>;
		reg-io-width = <0x04>;
		reg-shift = <0x02>;
		status = "disabled";
		phandle = <0x7e>;
	};

	serial@ff130000 {
		compatible = "rockchip,rk3328-uart\0snps,dw-apb-uart";
		reg = <0x00 0xff130000 0x00 0x100>;
		interrupts = <0x00 0x39 0x04>;
		clocks = <0x02 0x28 0x02 0xd4>;
		clock-names = "baudclk\0apb_pclk";
		dmas = <0x12 0x06 0x12 0x07>;
		dma-names = "tx\0rx";
		pinctrl-names = "default";
		pinctrl-0 = <0x26>;
		reg-io-width = <0x04>;
		reg-shift = <0x02>;
		status = "okay";
		phandle = <0x7f>;
	};

	i2c@ff150000 {
		compatible = "rockchip,rk3328-i2c\0rockchip,rk3399-i2c";
		reg = <0x00 0xff150000 0x00 0x1000>;
		interrupts = <0x00 0x24 0x04>;
		#address-cells = <0x01>;
		#size-cells = <0x00>;
		clocks = <0x02 0x37 0x02 0xcd>;
		clock-names = "i2c\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x27>;
		status = "disabled";
		phandle = <0x80>;
	};

	i2c@ff160000 {
		compatible = "rockchip,rk3328-i2c\0rockchip,rk3399-i2c";
		reg = <0x00 0xff160000 0x00 0x1000>;
		interrupts = <0x00 0x25 0x04>;
		#address-cells = <0x01>;
		#size-cells = <0x00>;
		clocks = <0x02 0x38 0x02 0xce>;
		clock-names = "i2c\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x28>;
		status = "okay";
		phandle = <0x81>;

		pmic@18 {
			compatible = "rockchip,rk805";
			reg = <0x18>;
			interrupt-parent = <0x29>;
			interrupts = <0x18 0x08>;
			#clock-cells = <0x01>;
			clock-output-names = "xin32k\0rk805-clkout2";
			gpio-controller;
			#gpio-cells = <0x02>;
			pinctrl-names = "default";
			pinctrl-0 = <0x2a>;
			rockchip,system-power-controller;
			wakeup-source;
			vcc1-supply = <0x2b>;
			vcc2-supply = <0x2b>;
			vcc3-supply = <0x2b>;
			vcc4-supply = <0x2b>;
			vcc5-supply = <0x1e>;
			vcc6-supply = <0x1e>;
			phandle = <0x74>;

			regulators {

				DCDC_REG1 {
					regulator-name = "vdd_logic";
					regulator-min-microvolt = <0xdbba0>;
					regulator-max-microvolt = <0x11edd8>;
					regulator-ramp-delay = <0x30d4>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x42>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0xf4240>;
					};
				};

				DCDC_REG2 {
					regulator-name = "vdd_arm";
					regulator-min-microvolt = <0xe7ef0>;
					regulator-max-microvolt = <0x162010>;
					regulator-ramp-delay = <0x30d4>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x06>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0xe7ef0>;
					};
				};

				DCDC_REG3 {
					regulator-name = "vcc_ddr";
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x82>;

					regulator-state-mem {
						regulator-on-in-suspend;
					};
				};

				DCDC_REG4 {
					regulator-name = "vcc_io";
					regulator-min-microvolt = <0x325aa0>;
					regulator-max-microvolt = <0x325aa0>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x1e>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0x325aa0>;
					};
				};

				LDO_REG1 {
					regulator-name = "vcc_18";
					regulator-min-microvolt = <0x1b7740>;
					regulator-max-microvolt = <0x1b7740>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x83>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0x1b7740>;
					};
				};

				LDO_REG2 {
					regulator-name = "vcc18_emmc";
					regulator-min-microvolt = <0x1b7740>;
					regulator-max-microvolt = <0x1b7740>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x1f>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0x1b7740>;
					};
				};

				LDO_REG3 {
					regulator-name = "vdd_10";
					regulator-min-microvolt = <0xf4240>;
					regulator-max-microvolt = <0xf4240>;
					regulator-always-on;
					regulator-boot-on;
					phandle = <0x84>;

					regulator-state-mem {
						regulator-on-in-suspend;
						regulator-suspend-microvolt = <0xf4240>;
					};
				};
			};
		};
	};

	i2c@ff170000 {
		compatible = "rockchip,rk3328-i2c\0rockchip,rk3399-i2c";
		reg = <0x00 0xff170000 0x00 0x1000>;
		interrupts = <0x00 0x26 0x04>;
		#address-cells = <0x01>;
		#size-cells = <0x00>;
		clocks = <0x02 0x39 0x02 0xcf>;
		clock-names = "i2c\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x2c>;
		status = "disabled";
		phandle = <0x85>;
	};

	i2c@ff180000 {
		compatible = "rockchip,rk3328-i2c\0rockchip,rk3399-i2c";
		reg = <0x00 0xff180000 0x00 0x1000>;
		interrupts = <0x00 0x27 0x04>;
		#address-cells = <0x01>;
		#size-cells = <0x00>;
		clocks = <0x02 0x3a 0x02 0xd0>;
		clock-names = "i2c\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x2d>;
		status = "disabled";
		phandle = <0x86>;
	};

	spi@ff190000 {
		compatible = "rockchip,rk3328-spi\0rockchip,rk3066-spi";
		reg = <0x00 0xff190000 0x00 0x1000>;
		interrupts = <0x00 0x31 0x04>;
		#address-cells = <0x01>;
		#size-cells = <0x00>;
		clocks = <0x02 0x20 0x02 0xd1>;
		clock-names = "spiclk\0apb_pclk";
		dmas = <0x12 0x08 0x12 0x09>;
		dma-names = "tx\0rx";
		pinctrl-names = "default";
		pinctrl-0 = <0x2e 0x2f 0x30>;
		status = "okay";
		max-freq = <0x2dc6c00>;
		cs-gpios = <0x31 0x07 0x01>;
		phandle = <0x87>;

		spi_for_cs2@0 {
			reg = <0x00>;
			compatible = "rockchip,spi_test_bus1_cs2";
			pinctrl-names = "default";
			pinctrl-0 = <0x35>;
			spi-max-frequency = <0x4c4b40>;
			status = "okay";
		};
	};

	watchdog@ff1a0000 {
		compatible = "rockchip,rk3328-wdt\0snps,dw-wdt";
		reg = <0x00 0xff1a0000 0x00 0x100>;
		interrupts = <0x00 0x28 0x04>;
		clocks = <0x02 0xec>;
		phandle = <0x88>;
	};

	pwm@ff1b0000 {
		compatible = "rockchip,rk3328-pwm";
		reg = <0x00 0xff1b0000 0x00 0x10>;
		clocks = <0x02 0x3c 0x02 0xd6>;
		clock-names = "pwm\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x36>;
		#pwm-cells = <0x03>;
		status = "disabled";
		phandle = <0x89>;
	};

	pwm@ff1b0010 {
		compatible = "rockchip,rk3328-pwm";
		reg = <0x00 0xff1b0010 0x00 0x10>;
		clocks = <0x02 0x3c 0x02 0xd6>;
		clock-names = "pwm\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x37>;
		#pwm-cells = <0x03>;
		status = "disabled";
		phandle = <0x8a>;
	};

	pwm@ff1b0020 {
		compatible = "rockchip,rk3328-pwm";
		reg = <0x00 0xff1b0020 0x00 0x10>;
		clocks = <0x02 0x3c 0x02 0xd6>;
		clock-names = "pwm\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x38>;
		#pwm-cells = <0x03>;
		status = "disabled";
		phandle = <0x8b>;
	};

	pwm@ff1b0030 {
		compatible = "rockchip,rk3328-pwm";
		reg = <0x00 0xff1b0030 0x00 0x10>;
		interrupts = <0x00 0x32 0x04>;
		clocks = <0x02 0x3c 0x02 0xd6>;
		clock-names = "pwm\0pclk";
		pinctrl-names = "default";
		pinctrl-0 = <0x39>;
		#pwm-cells = <0x03>;
		status = "disabled";
		phandle = <0x8c>;
	};

	dma-controller@ff1f0000 {
		compatible = "arm,pl330\0arm,primecell";
		reg = <0x00 0xff1f0000 0x00 0x4000>;
		interrupts = <0x00 0x00 0x04 0x00 0x01 0x04>;
		arm,pl330-periph-burst;
		clocks = <0x02 0x86>;
		clock-names = "apb_pclk";
		#dma-cells = <0x01>;
		phandle = <0x12>;
	};

	thermal-zones {

		soc-thermal {
			polling-delay-passive = <0x14>;
			polling-delay = <0x3e8>;
			sustainable-power = <0x3e8>;
			thermal-sensors = <0x3a 0x00>;
			phandle = <0x8d>;

			trips {

				trip-point0 {
					temperature = <0x11170>;
					hysteresis = <0x7d0>;
					type = "passive";
					phandle = <0x8e>;
				};

				trip-point1 {
					temperature = <0x14c08>;
					hysteresis = <0x7d0>;
					type = "passive";
					phandle = <0x3b>;
				};

				soc-crit {
					temperature = <0x17318>;
					hysteresis = <0x7d0>;
					type = "critical";
					phandle = <0x8f>;
				};
			};

			cooling-maps {

				map0 {
					trip = <0x3b>;
					cooling-device = <0x09 0xffffffff 0xffffffff 0x0a 0xffffffff 0xffffffff 0x0b 0xffffffff 0xffffffff 0x0c 0xffffffff 0xffffffff>;
					contribution = <0x1000>;
				};

				map1 {
					trip = <0x3b>;
					cooling-device = <0x3c 0xffffffff 0xffffffff>;
					contribution = <0x1000>;
				};
			};
		};
	};

	tsadc@ff250000 {
		compatible = "rockchip,rk3328-tsadc";
		reg = <0x00 0xff250000 0x00 0x100>;
		interrupts = <0x00 0x3a 0x04>;
		assigned-clocks = <0x02 0x24>;
		assigned-clock-rates = <0xc350>;
		clocks = <0x02 0x24 0x02 0xd5>;
		clock-names = "tsadc\0apb_pclk";
		pinctrl-names = "init\0default\0sleep";
		pinctrl-0 = <0x3d>;
		pinctrl-1 = <0x3e>;
		pinctrl-2 = <0x3d>;
		resets = <0x02 0x42>;
		reset-names = "tsadc-apb";
		rockchip,grf = <0x3f>;
		rockchip,hw-tshut-temp = <0x186a0>;
		#thermal-sensor-cells = <0x01>;
		status = "okay";
		rockchip,hw-tshut-mode = <0x00>;
		rockchip,hw-tshut-polarity = <0x00>;
		phandle = <0x3a>;
	};

	dfi@ff790000 {
		reg = <0x00 0xff790000 0x00 0x400>;
		compatible = "rockchip,rk3328-dfi";
		rockchip,grf = <0x3f>;
		status = "okay";
		phandle = <0x40>;
	};

	dmc@ff780000 {
		reg = <0x00 0xff780000 0x00 0x400>;
		compatible = "rockchip,rk3328-dmc";
		devfreq-events = <0x40>;
		clocks = <0x02 0x40>;
		clock-names = "dmc_clk";
		operating-points-v2 = <0x41>;
		#cooling-cells = <0x02>;
		status = "okay";
		center-supply = <0x42>;
		ddr_timing = <0x43>;
		phandle = <0x90>;
	};

	dmc-opp-table {
		compatible = "operating-points-v2";
		phandle = <0x41>;

		opp-786000000 {
			opp-hz = <0x00 0x2ed96880>;
			opp-microvolt = <0x106738 0x106738 0xb71b00>;
			status = "disabled";
		};

		opp-798000000 {
			opp-hz = <0x00 0x2f908380>;
			opp-microvolt = <0x106738 0x106738 0xb71b00>;
			status = "disabled";
		};

		opp-840000000 {
			opp-hz = <0x00 0x32116200>;
			opp-microvolt = <0x106738 0x106738 0xb71b00>;
		};

		opp-924000000 {
			opp-hz = <0x00 0x37131f00>;
			opp-microvolt = <0x10c8e0 0x10c8e0 0xb71b00>;
		};

		opp-1068000000 {
			opp-hz = <0x00 0x3fa86300>;
			opp-microvolt = <0x11edd8 0x11edd8 0xb71b00>;
		};
	};

	efuse@ff260000 {
		compatible = "rockchip,rk3328-efuse";
		reg = <0x00 0xff260000 0x00 0x50>;
		#address-cells = <0x01>;
		#size-cells = <0x01>;
		clocks = <0x02 0x3e>;
		clock-names = "pclk_efuse";
		rockchip,efuse-size = <0x20>;
		phandle = <0x91>;

		id@7 {
			reg = <0x07 0x10>;
			phandle = <0x92>;
		};

		cpu-leakage@17 {
			reg = <0x17 0x01>;
			phandle = <0x93>;
		};

		logic-leakage@19 {
			reg = <0x19 0x01>;
			phandle = <0x94>;
		};

		cpu-version@1a {
			reg = <0x1a 0x01>;
			bits = <0x03 0x03>;
			phandle = <0x51>;
		};
	};

	adc@ff280000 {
		compatible = "rockchip,rk3328-saradc\0rockchip,rk3399-saradc";
		reg = <0x00 0xff280000 0x00 0x100>;
		interrupts = <0x00 0x50 0x04>;
		#io-channel-cells = <0x01>;
		clocks = <0x02 0x25 0x02 0xea>;
		clock-names = "saradc\0apb_pclk";
		resets = <0x02 0x56>;
		reset-names = "saradc-apb";
		status = "disabled";
		phandle = <0x95>;
	};

	gpu@ff300000 {
		compatible = "rockchip,rk3328-mali\0arm,mali-450";
		reg = <0x00 0xff300000 0x00 0x30000>;
		interrupts = <0x00 0x5a 0x04 0x00 0x57 0x04 0x00 0x5d 0x04 0x00 0x58 0x04 0x00 0x59 0x04 0x00 0x5b 0x04 0x00 0x5c 0x04>;
		interrupt-names = "gp\0gpmmu\0pp\0pp0\0ppmmu0\0pp1\0ppmmu1";
		clocks = <0x02 0x87 0x02 0x87>;
		clock-names = "bus\0core";
		power-domains = <0x44 0x01>;
		resets = <0x02 0x66>;
		operating-points-v2 = <0x45>;
		#cooling-cells = <0x02>;
		mali-supply = <0x42>;
		phandle = <0x3c>;
	};

	gpu-opp-table {
		compatible = "operating-points-v2";
		phandle = <0x45>;

		opp-200000000 {
			opp-hz = <0x00 0xbebc200>;
			opp-microvolt = <0x100590 0xe7ef0 0x124f80>;
		};

		opp-300000000 {
			opp-hz = <0x00 0x11e1a300>;
			opp-microvolt = <0x100590 0xe7ef0 0x124f80>;
		};

		opp-400000000 {
			opp-hz = <0x00 0x17d78400>;
			opp-microvolt = <0x100590 0xe7ef0 0x124f80>;
		};

		opp-500000000 {
			opp-hz = <0x00 0x1dcd6500>;
			opp-microvolt = <0x118c30 0xe7ef0 0x124f80>;
		};
	};

	iommu@ff330200 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff330200 0x00 0x100>;
		interrupts = <0x00 0x60 0x04>;
		clocks = <0x02 0x93 0x02 0xdd>;
		clock-names = "aclk\0iface";
		#iommu-cells = <0x00>;
		status = "disabled";
		phandle = <0x96>;
	};

	iommu@ff340800 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff340800 0x00 0x40>;
		interrupts = <0x00 0x62 0x04>;
		clocks = <0x02 0x8f 0x02 0x146>;
		clock-names = "aclk\0iface";
		#iommu-cells = <0x00>;
		status = "disabled";
		phandle = <0x97>;
	};

	video-codec@ff350000 {
		compatible = "rockchip,rk3328-vpu";
		reg = <0x00 0xff350000 0x00 0x800>;
		interrupts = <0x00 0x09 0x04>;
		interrupt-names = "vdpu";
		clocks = <0x02 0x8f 0x02 0x146>;
		clock-names = "aclk\0hclk";
		iommus = <0x46>;
		power-domains = <0x44 0x08>;
		phandle = <0x98>;
	};

	iommu@ff350800 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff350800 0x00 0x40>;
		interrupts = <0x00 0x0b 0x04>;
		clocks = <0x02 0x8f 0x02 0x146>;
		clock-names = "aclk\0iface";
		#iommu-cells = <0x00>;
		power-domains = <0x44 0x08>;
		phandle = <0x46>;
	};

	video-codec@ff360000 {
		compatible = "rockchip,rk3328-vdec\0rockchip,rk3399-vdec";
		reg = <0x00 0xff360000 0x00 0x480>;
		interrupts = <0x00 0x07 0x04>;
		assigned-clocks = <0x02 0x8b 0x02 0x41 0x02 0x42>;
		assigned-clock-rates = <0x17d78400 0x17d78400 0x11e1a300>;
		clocks = <0x02 0x8b 0x02 0x142 0x02 0x41 0x02 0x42>;
		clock-names = "axi\0ahb\0cabac\0core";
		iommus = <0x47>;
		power-domains = <0x44 0x05>;
		resets = <0x02 0xa6 0x02 0xa4 0x02 0xa8 0x02 0xa9 0x02 0xa5 0x02 0xa7>;
		reset-names = "video_h\0video_a\0video_core\0video_cabac\0niu_a\0niu_h";
		phandle = <0x99>;
	};

	iommu@ff360480 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff360480 0x00 0x40 0x00 0xff3604c0 0x00 0x40>;
		interrupts = <0x00 0x4a 0x04>;
		clocks = <0x02 0x8b 0x02 0x142>;
		clock-names = "aclk\0iface";
		#iommu-cells = <0x00>;
		power-domains = <0x44 0x05>;
		phandle = <0x47>;
	};

	vop@ff370000 {
		compatible = "rockchip,rk3328-vop";
		reg = <0x00 0xff370000 0x00 0x3efc>;
		interrupts = <0x00 0x20 0x04>;
		clocks = <0x02 0x91 0x02 0x78 0x02 0x13b>;
		clock-names = "aclk_vop\0dclk_vop\0hclk_vop";
		resets = <0x02 0x85 0x02 0x86 0x02 0x87>;
		reset-names = "axi\0ahb\0dclk";
		iommus = <0x48>;
		assigned-clocks = <0x02 0x78>;
		assigned-clock-parents = <0x02 0x7a>;
		status = "okay";
		phandle = <0x9a>;

		port {
			#address-cells = <0x01>;
			#size-cells = <0x00>;
			phandle = <0x0d>;

			endpoint@0 {
				reg = <0x00>;
				remote-endpoint = <0x49>;
				phandle = <0x4f>;
			};
		};
	};

	iommu@ff373f00 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff373f00 0x00 0x100>;
		interrupts = <0x00 0x20 0x04>;
		clocks = <0x02 0x91 0x02 0x13b>;
		clock-names = "aclk\0iface";
		#iommu-cells = <0x00>;
		status = "okay";
		phandle = <0x48>;
	};

	rga@ff390000 {
		compatible = "rockchip,rk3328-rga\0rockchip,rk3399-rga";
		reg = <0x00 0xff390000 0x00 0x1000>;
		interrupts = <0x00 0x21 0x04>;
		clocks = <0x02 0x9a 0x02 0x154 0x02 0x45>;
		clock-names = "aclk\0hclk\0sclk";
		resets = <0x02 0x88 0x02 0x8a 0x02 0x8b>;
		reset-names = "core\0axi\0ahb";
		phandle = <0x9b>;
	};

	iep@ff3a0000 {
		compatible = "rockchip,rk3328-iep\0rockchip,rk3228-iep";
		reg = <0x00 0xff3a0000 0x00 0x800>;
		interrupts = <0x00 0x1f 0x04>;
		interrupt-names = "iep";
		clocks = <0x02 0x9b 0x02 0x153>;
		clock-names = "axi\0ahb";
		power-domains = <0x44 0x05>;
		iommus = <0x4a>;
		phandle = <0x9c>;
	};

	iommu@ff3a0800 {
		compatible = "rockchip,iommu";
		reg = <0x00 0xff3a0800 0x00 0x40>;
		interrupts = <0x00 0x1f 0x04>;
		interrupt-names = "iep_mmu";
		clocks = <0x02 0x9b 0x02 0x153>;
		clock-names = "aclk\0iface";
		power-domains = <0x44 0x05>;
		#iommu-cells = <0x00>;
		phandle = <0x4a>;
	};

	hdmi@ff3c0000 {
		compatible = "rockchip,rk3328-dw-hdmi";
		reg = <0x00 0xff3c0000 0x00 0x20000>;
		reg-io-width = <0x04>;
		interrupts = <0x00 0x23 0x04 0x00 0x47 0x04>;
		clocks = <0x02 0xe7 0x02 0x46 0x4b 0x02 0x1e>;
		clock-names = "iahb\0isfr\0vpll\0cec";
		phys = <0x4b>;
		phy-names = "hdmi";
		pinctrl-names = "default";
		pinctrl-0 = <0x4c 0x4d 0x4e 0x205>;
		rockchip,grf = <0x3f>;
		#sound-dai-cells = <0x00>;
		status = "okay";
		phandle = <0x0f>;

		ports {

			port {
				phandle = <0x9d>;

				endpoint {
					remote-endpoint = <0x4f>;
					phandle = <0x49>;
				};
			};
		};
	};

	codec@ff410000 {
		compatible = "rockchip,rk3328-codec";
		reg = <0x00 0xff410000 0x00 0x1000>;
		clocks = <0x02 0xeb 0x02 0x2a>;
		clock-names = "pclk\0mclk";
		rockchip,grf = <0x3f>;
		mute-gpios = <0x7c 0x00 0x01>;
		#sound-dai-cells = <0x00>;
		status = "okay";
		phandle = <0x08>;
	};

	phy@ff430000 {
		compatible = "rockchip,rk3328-hdmi-phy";
		reg = <0x00 0xff430000 0x00 0x10000>;
		interrupts = <0x00 0x53 0x04>;
		clocks = <0x02 0xe4 0x50 0x02 0x79>;
		clock-names = "sysclk\0refoclk\0refpclk";
		clock-output-names = "hdmi_phy";
		#clock-cells = <0x00>;
		nvmem-cells = <0x51>;
		nvmem-cell-names = "cpu-version";
		#phy-cells = <0x00>;
		status = "okay";
		phandle = <0x4b>;
	};

	clock-controller@ff440000 {
		compatible = "rockchip,rk3328-cru\0rockchip,cru\0syscon";
		reg = <0x00 0xff440000 0x00 0x1000>;
		rockchip,grf = <0x3f>;
		#clock-cells = <0x01>;
		#reset-cells = <0x01>;
		assigned-clocks = <0x02 0x78 0x02 0x3d 0x02 0x1e 0x02 0x26 0x02 0x27 0x02 0x28 0x02 0x88 0x02 0x89 0x02 0x8e 0x02 0x85 0x02 0x83 0x02 0x8a 0x02 0x8c 0x02 0x8d 0x02 0x41 0x02 0x42 0x02 0x44 0x02 0x43 0x02 0x22 0x02 0x5c 0x02 0x35 0x02 0x06 0x02 0x04 0x02 0x03 0x02 0x88 0x02 0x148 0x02 0xd8 0x02 0x89 0x02 0x134 0x02 0xe6 0x02 0x87 0x02 0x1e>;
		assigned-clock-parents = <0x02 0x7a 0x02 0x01 0x02 0x04 0x50 0x50 0x50>;
		assigned-clock-rates = <0x00 0x3a98000 0x00 0x16e3600 0x16e3600 0x16e3600 0xe4e1c0 0xe4e1c0 0x11e1a300 0x5f5e100 0x17d78400 0x5f5e100 0x2faf080 0x5f5e100 0x5f5e100 0x5f5e100 0x2faf080 0x2faf080 0x2faf080 0x2faf080 0x16e3600 0x23c34600 0x1d4c0000 0x47868c00 0x8f0d180 0x47868c0 0x47868c0 0x8f0d180 0x47868c0 0x47868c0 0x1dcd6500 0x8000>;
		phandle = <0x02>;
	};

	syscon@ff450000 {
		compatible = "rockchip,rk3328-usb2phy-grf\0syscon\0simple-mfd";
		reg = <0x00 0xff450000 0x00 0x10000>;
		#address-cells = <0x01>;
		#size-cells = <0x01>;
		phandle = <0x9e>;

		usb2phy@100 {
			compatible = "rockchip,rk3328-usb2phy";
			reg = <0x100 0x10>;
			clocks = <0x50>;
			clock-names = "phyclk";
			clock-output-names = "usb480m_phy";
			#clock-cells = <0x00>;
			assigned-clocks = <0x02 0x7b>;
			assigned-clock-parents = <0x52>;
			status = "okay";
			phandle = <0x52>;

			otg-port {
				#phy-cells = <0x00>;
				interrupts = <0x00 0x3b 0x04 0x00 0x3c 0x04 0x00 0x3d 0x04>;
				interrupt-names = "otg-bvalid\0otg-id\0linestate";
				status = "okay";
				phandle = <0x62>;
			};

			host-port {
				#phy-cells = <0x00>;
				interrupts = <0x00 0x3e 0x04>;
				interrupt-names = "linestate";
				status = "okay";
				phandle = <0x63>;
			};
		};
	};

	syscon@ff460000 {
		compatible = "rockchip,usb3phy-grf\0syscon";
		reg = <0x00 0xff460000 0x00 0x1000>;
		phandle = <0x53>;
	};

	usb3-phy@ff470000 {
		compatible = "rockchip,rk3328-u3phy";
		reg = <0x00 0xff470000 0x00 0x00>;
		rockchip,u3phygrf = <0x53>;
		rockchip,grf = <0x3f>;
		interrupts = <0x00 0x4d 0x04>;
		interrupt-names = "linestate";
		clocks = <0x02 0xe0 0x02 0xe1>;
		clock-names = "u3phy-otg\0u3phy-pipe";
		resets = <0x02 0x7d 0x02 0x7e 0x02 0x7f 0x02 0x7c 0x02 0x9e 0x02 0x9f>;
		reset-names = "u3phy-u2-por\0u3phy-u3-por\0u3phy-pipe-mac\0u3phy-utmi-mac\0u3phy-utmi-apb\0u3phy-pipe-apb";
		#address-cells = <0x02>;
		#size-cells = <0x02>;
		ranges;
		status = "okay";
		phandle = <0x9f>;

		utmi@ff470000 {
			reg = <0x00 0xff470000 0x00 0x8000>;
			#phy-cells = <0x00>;
			status = "okay";
			phandle = <0xa0>;
		};

		pipe@ff478000 {
			reg = <0x00 0xff478000 0x00 0x8000>;
			#phy-cells = <0x00>;
			status = "okay";
			phandle = <0xa1>;
		};
	};

	mmc@ff500000 {
		compatible = "rockchip,rk3328-dw-mshc\0rockchip,rk3288-dw-mshc";
		reg = <0x00 0xff500000 0x00 0x4000>;
		interrupts = <0x00 0x0c 0x04>;
		clocks = <0x02 0x13d 0x02 0x21 0x02 0x4a 0x02 0x4e>;
		clock-names = "biu\0ciu\0ciu-drive\0ciu-sample";
		resets = <0x02 0x6d>;
		reset-names = "reset";
		fifo-depth = <0x100>;
		max-frequency = <0x8f0d180>;
		status = "okay";
		bus-width = <0x04>;
		cap-mmc-highspeed;
		cap-sd-highspeed;
		disable-wp;
		pinctrl-names = "default";
		pinctrl-0 = <0x54 0x55 0x56 0x57>;
		sd-uhs-sdr12;
		sd-uhs-sdr25;
		sd-uhs-sdr50;
		sd-uhs-sdr104;
		vmmc-supply = <0x58>;
		vqmmc-supply = <0x20>;
		phandle = <0xa2>;
	};

	mmc@ff510000 {
		compatible = "rockchip,rk3328-dw-mshc\0rockchip,rk3288-dw-mshc";
		reg = <0x00 0xff510000 0x00 0x4000>;
		pinctrl-names = "default";
		pinctrl-0 = <0xf1 0xec 0xeb>;
		interrupts = <0x00 0x0d 0x04>;
		clocks = <0x02 0x13e 0x02 0x22 0x02 0x4b 0x02 0x4f>;
		clock-names = "biu\0ciu\0ciu-drive\0ciu-sample";
		resets = <0x02 0x6e>;
		reset-names = "reset";
		fifo-depth = <0x100>;
		max-frequency = <0x8f0d180>;
		status = "okay";
		phandle = <0xa3>;
		cap-sd-highspeed;
		cap-sdio-irq;
		non-removable;
		bus-width = <0x04>;
		mmc-pwrseq = <0x200>;
	};

	mmc@ff520000 {
		compatible = "rockchip,rk3328-dw-mshc\0rockchip,rk3288-dw-mshc";
		reg = <0x00 0xff520000 0x00 0x4000>;
		interrupts = <0x00 0x0e 0x04>;
		clocks = <0x02 0x13f 0x02 0x23 0x02 0x4c 0x02 0x50>;
		clock-names = "biu\0ciu\0ciu-drive\0ciu-sample";
		resets = <0x02 0x6f>;
		reset-names = "reset";
		fifo-depth = <0x100>;
		max-frequency = <0x8f0d180>;
		status = "okay";
		bus-width = <0x08>;
		cap-mmc-highspeed;
		mmc-ddr-1_8v;
		mmc-hs200-1_8v;
		non-removable;
		pinctrl-names = "default";
		pinctrl-0 = <0x59 0x5a 0x5b>;
		vmmc-supply = <0x1e>;
		vqmmc-supply = <0x1f>;
		phandle = <0xa4>;
	};

	dwmmc@ff5f0000 {
		compatible = "rockchip,rk3328-dw-mshc\0rockchip,rk3288-dw-mshc";
		reg = <0x00 0xff5f0000 0x00 0x4000>;
		interrupts = <0x00 0x04 0x04>;
		clocks = <0x02 0x140 0x02 0x1f 0x02 0x4d 0x02 0x51>;
		clock-names = "biu\0ciu\0ciu-drive\0ciu-sample";
		fifo-depth = <0x100>;
		max-frequency = <0x8f0d180>;
		resets = <0x02 0x68>;
		reset-names = "reset";
		status = "disabled";
		phandle = <0xa5>;
	};

	ethernet@ff540000 {
		compatible = "rockchip,rk3328-gmac";
		reg = <0x00 0xff540000 0x00 0x10000>;
		interrupts = <0x00 0x18 0x04>;
		interrupt-names = "macirq";
		clocks = <0x02 0x64 0x02 0x57 0x02 0x58 0x02 0x5a 0x02 0x59 0x02 0x96 0x02 0xdf>;
		clock-names = "stmmaceth\0mac_clk_rx\0mac_clk_tx\0clk_mac_ref\0clk_mac_refout\0aclk_mac\0pclk_mac";
		resets = <0x02 0x63>;
		reset-names = "stmmaceth";
		rockchip,grf = <0x3f>;
		snps,txpbl = <0x04>;
		status = "disable";
		assigned-clocks = <0x02 0x64 0x02 0x66>;
		assigned-clock-parents = <0x5c 0x5c>;
		clock_in_out = "input";
		phy-supply = <0x5d>;
		phy-mode = "rgmii";
		pinctrl-names = "default";
		pinctrl-0 = <0x5e>;
		snps,aal;
		snps,reset-gpio = <0x29 0x12 0x01>;
		snps,reset-active-low;
		snps,reset-delays-us = <0x00 0x2710 0xc350>;
		snps,rxpbl = <0x04>;
		tx_delay = <0x24>;
		rx_delay = <0x18>;
		phandle = <0xa6>;
	};

	ethernet@ff550000 {
		compatible = "rockchip,rk3328-gmac";
		reg = <0x00 0xff550000 0x00 0x10000>;
		rockchip,grf = <0x3f>;
		interrupts = <0x00 0x15 0x04>;
		interrupt-names = "macirq";
		clocks = <0x02 0x54 0x02 0x53 0x02 0x53 0x02 0x55 0x02 0x95 0x02 0xde 0x02 0x56>;
		clock-names = "stmmaceth\0mac_clk_rx\0mac_clk_tx\0clk_mac_ref\0aclk_mac\0pclk_mac\0clk_macphy";
		resets = <0x02 0x62>;
		reset-names = "stmmaceth";
		phy-mode = "rmii";
		phy-handle = <0x5f>;
		snps,txpbl = <0x04>;
		clock_in_out = "output";
		status = "okay";
		phy-supply = <0x5d>;
		assigned-clocks = <0x02 0x65>;
		assigned-clock-rate = <0x2faf080>;
		assigned-clock-parents = <0x02 0x54>;
		phandle = <0xa7>;

		mdio {
			compatible = "snps,dwmac-mdio";
			#address-cells = <0x01>;
			#size-cells = <0x00>;

			ethernet-phy@0 {
				compatible = "ethernet-phy-id1234.d400\0ethernet-phy-ieee802.3-c22";
				reg = <0x00>;
				clocks = <0x02 0x56>;
				resets = <0x02 0x64>;
				pinctrl-names = "default";
				pinctrl-0 = <0x60 0x61>;
				phy-is-integrated;
				phandle = <0x5f>;
			};
		};
	};

	usb@ff580000 {
		compatible = "rockchip,rk3328-usb\0rockchip,rk3066-usb\0snps,dwc2";
		reg = <0x00 0xff580000 0x00 0x40000>;
		interrupts = <0x00 0x17 0x04>;
		clocks = <0x02 0x14d>;
		clock-names = "otg";
		dr_mode = "host";
		g-np-tx-fifo-size = <0x10>;
		g-rx-fifo-size = <0x118>;
		g-tx-fifo-size = <0x100 0x80 0x80 0x40 0x20 0x10>;
		phys = <0x62>;
		phy-names = "usb2-phy";
		status = "okay";
		phandle = <0xa8>;
	};

	usb@ff5c0000 {
		compatible = "generic-ehci";
		reg = <0x00 0xff5c0000 0x00 0x10000>;
		interrupts = <0x00 0x10 0x04>;
		clocks = <0x02 0x14e 0x52>;
		phys = <0x63>;
		phy-names = "usb";
		status = "okay";
		phandle = <0xa9>;
	};

	usb@ff5d0000 {
		compatible = "generic-ohci";
		reg = <0x00 0xff5d0000 0x00 0x10000>;
		interrupts = <0x00 0x11 0x04>;
		clocks = <0x02 0x14e 0x52>;
		phys = <0x63>;
		phy-names = "usb";
		status = "okay";
		phandle = <0xaa>;
	};

	usb@ff600000 {
		compatible = "rockchip,rk3328-dwc3\0snps,dwc3";
		reg = <0x00 0xff600000 0x00 0x100000>;
		interrupts = <0x00 0x43 0x04>;
		clocks = <0x02 0x60 0x02 0x61 0x02 0x84>;
		clock-names = "ref_clk\0suspend_clk\0bus_clk";
		resets = <0x02 0x78>;
		reset-names = "usb3-otg";
		dr_mode = "host";
		phy_type = "utmi_wide";
		snps,dis-del-phy-power-chg-quirk;
		snps,dis_enblslpm_quirk;
		snps,dis-tx-ipgap-linecheck-quirk;
		snps,dis-u2-freeclk-exists-quirk;
		snps,dis_u2_susphy_quirk;
		snps,dis_u3_susphy_quirk;
		status = "okay";
		phandle = <0xab>;
	};

	interrupt-controller@ff811000 {
		compatible = "arm,gic-400";
		#interrupt-cells = <0x03>;
		#address-cells = <0x00>;
		interrupt-controller;
		reg = <0x00 0xff811000 0x00 0x1000 0x00 0xff812000 0x00 0x2000 0x00 0xff814000 0x00 0x2000 0x00 0xff816000 0x00 0x2000>;
		interrupts = <0x01 0x09 0xf04>;
		phandle = <0x01>;
	};

	pinctrl {
		compatible = "rockchip,rk3328-pinctrl";
		rockchip,grf = <0x3f>;
		#address-cells = <0x02>;
		#size-cells = <0x02>;
		ranges;
		phandle = <0xac>;
		pinctrl-names = "default";
		pinctrl-0 = <0x32>;

		rtc {

			rtc-32k {
				rockchip,pins = <0x01 0x1c 0x01 0x64>;
				phandle = <0x32>;
			};
		};

		gpio@ff210000 {
			compatible = "rockchip,gpio-bank";
			reg = <0x00 0xff210000 0x00 0x100>;
			interrupts = <0x00 0x33 0x04>;
			clocks = <0x02 0xc8>;
			gpio-controller;
			#gpio-cells = <0x02>;
			interrupt-controller;
			#interrupt-cells = <0x02>;
			phandle = <0x6f>;
		};

		gpio@ff220000 {
			compatible = "rockchip,gpio-bank";
			reg = <0x00 0xff220000 0x00 0x100>;
			interrupts = <0x00 0x34 0x04>;
			clocks = <0x02 0xc9>;
			gpio-controller;
			#gpio-cells = <0x02>;
			interrupt-controller;
			#interrupt-cells = <0x02>;
			phandle = <0x29>;
		};

		gpio@ff230000 {
			compatible = "rockchip,gpio-bank";
			reg = <0x00 0xff230000 0x00 0x100>;
			interrupts = <0x00 0x35 0x04>;
			clocks = <0x02 0xca>;
			gpio-controller;
			#gpio-cells = <0x02>;
			interrupt-controller;
			#interrupt-cells = <0x02>;
			phandle = <0x71>;
		};

		gpio@ff240000 {
			compatible = "rockchip,gpio-bank";
			reg = <0x00 0xff240000 0x00 0x100>;
			interrupts = <0x00 0x36 0x04>;
			clocks = <0x02 0xcb>;
			gpio-controller;
			#gpio-cells = <0x02>;
			interrupt-controller;
			#interrupt-cells = <0x02>;
			phandle = <0x31>;
		};

		pcfg-pull-up {
			bias-pull-up;
			phandle = <0x66>;
		};

		pcfg-pull-down {
			bias-pull-down;
			phandle = <0x6e>;
		};

		pcfg-pull-none {
			bias-disable;
			phandle = <0x64>;
		};

		pcfg-pull-none-2ma {
			bias-disable;
			drive-strength = <0x02>;
			phandle = <0x6d>;
		};

		pcfg-pull-up-2ma {
			bias-pull-up;
			drive-strength = <0x02>;
			phandle = <0xad>;
		};

		pcfg-pull-up-4ma {
			bias-pull-up;
			drive-strength = <0x04>;
			phandle = <0x67>;
		};

		pcfg-pull-none-4ma {
			bias-disable;
			drive-strength = <0x04>;
			phandle = <0x6a>;
		};

		pcfg-pull-down-4ma {
			bias-pull-down;
			drive-strength = <0x04>;
			phandle = <0xae>;
		};

		pcfg-pull-none-8ma {
			bias-disable;
			drive-strength = <0x08>;
			phandle = <0x68>;
		};

		pcfg-pull-up-8ma {
			bias-pull-up;
			drive-strength = <0x08>;
			phandle = <0x69>;
		};

		pcfg-pull-none-12ma {
			bias-disable;
			drive-strength = <0x0c>;
			phandle = <0x6b>;
		};

		pcfg-pull-up-12ma {
			bias-pull-up;
			drive-strength = <0x0c>;
			phandle = <0x6c>;
		};

		pcfg-output-high {
			output-high;
			phandle = <0xaf>;
		};

		pcfg-output-low {
			output-low;
			phandle = <0xb0>;
		};

		pcfg-input-high {
			bias-pull-up;
			input-enable;
			phandle = <0x65>;
		};

		pcfg-input {
			input-enable;
			phandle = <0xb1>;
		};

		i2c0 {

			i2c0-xfer {
				rockchip,pins = <0x02 0x18 0x01 0x64 0x02 0x19 0x01 0x64>;
				phandle = <0x27>;
			};
		};

		i2c1 {

			i2c1-xfer {
				rockchip,pins = <0x02 0x04 0x02 0x64 0x02 0x05 0x02 0x64>;
				phandle = <0x28>;
			};
		};

		i2c2 {

			i2c2-xfer {
				rockchip,pins = <0x02 0x0d 0x01 0x64 0x02 0x0e 0x01 0x64>;
				phandle = <0x2c>;
			};
		};

		i2c3 {

			i2c3-xfer {
				rockchip,pins = <0x00 0x05 0x02 0x64 0x00 0x06 0x02 0x64>;
				phandle = <0x2d>;
			};

			i2c3-pins {
				rockchip,pins = <0x00 0x05 0x00 0x64 0x00 0x06 0x00 0x64>;
				phandle = <0xb2>;
			};
		};

		hdmi_i2c {

			hdmii2c-xfer {
				rockchip,pins = <0x00 0x05 0x01 0x64 0x00 0x06 0x01 0x64>;
				phandle = <0x4d>;
			};
		};

		pdm-0 {

			pdmm0-clk {
				rockchip,pins = <0x02 0x12 0x02 0x64>;
				phandle = <0x14>;
			};

			pdmm0-fsync {
				rockchip,pins = <0x02 0x17 0x02 0x64>;
				phandle = <0xb3>;
			};

			pdmm0-sdi0 {
				rockchip,pins = <0x02 0x13 0x02 0x64>;
				phandle = <0x15>;
			};

			pdmm0-sdi1 {
				rockchip,pins = <0x02 0x14 0x02 0x64>;
				phandle = <0x16>;
			};

			pdmm0-sdi2 {
				rockchip,pins = <0x02 0x15 0x02 0x64>;
				phandle = <0x17>;
			};

			pdmm0-sdi3 {
				rockchip,pins = <0x02 0x16 0x02 0x64>;
				phandle = <0x18>;
			};

			pdmm0-clk-sleep {
				rockchip,pins = <0x02 0x12 0x00 0x65>;
				phandle = <0x19>;
			};

			pdmm0-sdi0-sleep {
				rockchip,pins = <0x02 0x13 0x00 0x65>;
				phandle = <0x1a>;
			};

			pdmm0-sdi1-sleep {
				rockchip,pins = <0x02 0x14 0x00 0x65>;
				phandle = <0x1b>;
			};

			pdmm0-sdi2-sleep {
				rockchip,pins = <0x02 0x15 0x00 0x65>;
				phandle = <0x1c>;
			};

			pdmm0-sdi3-sleep {
				rockchip,pins = <0x02 0x16 0x00 0x65>;
				phandle = <0x1d>;
			};

			pdmm0-fsync-sleep {
				rockchip,pins = <0x02 0x17 0x00 0x65>;
				phandle = <0xb4>;
			};
		};

		tsadc {

			otp-pin {
				rockchip,pins = <0x02 0x0d 0x00 0x64>;
				phandle = <0x3d>;
			};

			otp-out {
				rockchip,pins = <0x02 0x0d 0x01 0x64>;
				phandle = <0x3e>;
			};
		};

		uart0 {

			uart0-xfer {
				rockchip,pins = <0x01 0x09 0x01 0x64 0x01 0x08 0x01 0x66>;
				phandle = <0x21>;
			};

			uart0-cts {
				rockchip,pins = <0x01 0x0b 0x01 0x64>;
				phandle = <0x22>;
			};

			uart0-rts {
				rockchip,pins = <0x01 0x0a 0x01 0x64>;
				phandle = <0xb5>;
			};

			uart0-rts-pin {
				rockchip,pins = <0x01 0x0a 0x00 0x64>;
				phandle = <0xb6>;
			};
		};

		uart1 {

			uart1-xfer {
				rockchip,pins = <0x03 0x04 0x04 0x64 0x03 0x06 0x04 0x66>;
				phandle = <0x23>;
			};

			uart1-cts {
				rockchip,pins = <0x03 0x07 0x04 0x64>;
				phandle = <0x24>;
			};

			uart1-rts {
				rockchip,pins = <0x03 0x05 0x04 0x64>;
				phandle = <0x25>;
			};

			uart1-rts-pin {
				rockchip,pins = <0x03 0x05 0x00 0x64>;
				phandle = <0xb7>;
			};
		};

		uart2-0 {

			uart2m0-xfer {
				rockchip,pins = <0x01 0x00 0x02 0x64 0x01 0x01 0x02 0x66>;
				phandle = <0xb8>;
			};
		};

		uart2-1 {

			uart2m1-xfer {
				rockchip,pins = <0x02 0x00 0x01 0x64 0x02 0x01 0x01 0x66>;
				phandle = <0x26>;
			};
		};

		spi0-0 {

			spi0m0-clk {
				rockchip,pins = <0x02 0x08 0x01 0x66>;
				phandle = <0xb9>;
			};

			spi0m0-cs0 {
				rockchip,pins = <0x02 0x0b 0x01 0x66>;
				phandle = <0xba>;
			};

			spi0m0-tx {
				rockchip,pins = <0x02 0x09 0x01 0x66>;
				phandle = <0xbb>;
			};

			spi0m0-rx {
				rockchip,pins = <0x02 0x0a 0x01 0x66>;
				phandle = <0xbc>;
			};

			spi0m0-cs1 {
				rockchip,pins = <0x02 0x0c 0x01 0x66>;
				phandle = <0xbd>;
			};
		};

		spi0-1 {

			spi0m1-clk {
				rockchip,pins = <0x03 0x17 0x02 0x66>;
				phandle = <0xbe>;
			};

			spi0m1-cs0 {
				rockchip,pins = <0x03 0x1a 0x02 0x66>;
				phandle = <0xbf>;
			};

			spi0m1-tx {
				rockchip,pins = <0x03 0x19 0x02 0x66>;
				phandle = <0xc0>;
			};

			spi0m1-rx {
				rockchip,pins = <0x03 0x18 0x02 0x66>;
				phandle = <0xc1>;
			};

			spi0m1-cs1 {
				rockchip,pins = <0x03 0x1b 0x02 0x66>;
				phandle = <0xc2>;
			};
		};

		spi0-2 {

			spi0m2-clk {
				rockchip,pins = <0x03 0x00 0x04 0x66>;
				phandle = <0x2e>;
			};

			spi0m2-cs0 {
				rockchip,pins = <0x03 0x08 0x03 0x66>;
				phandle = <0xc3>;
			};

			spi0m2-tx {
				rockchip,pins = <0x03 0x01 0x04 0x66>;
				phandle = <0x2f>;
			};

			spi0m2-rx {
				rockchip,pins = <0x03 0x02 0x04 0x66>;
				phandle = <0x30>;
			};
		};

		i2s1 {

			i2s1-mclk {
				rockchip,pins = <0x02 0x0f 0x01 0x64>;
				phandle = <0xc4>;
			};

			i2s1-sclk {
				rockchip,pins = <0x02 0x12 0x01 0x64>;
				phandle = <0xc5>;
			};

			i2s1-lrckrx {
				rockchip,pins = <0x02 0x10 0x01 0x64>;
				phandle = <0xc6>;
			};

			i2s1-lrcktx {
				rockchip,pins = <0x02 0x11 0x01 0x64>;
				phandle = <0xc7>;
			};

			i2s1-sdi {
				rockchip,pins = <0x02 0x13 0x01 0x64>;
				phandle = <0xc8>;
			};

			i2s1-sdo {
				rockchip,pins = <0x02 0x17 0x01 0x64>;
				phandle = <0xc9>;
			};

			i2s1-sdio1 {
				rockchip,pins = <0x02 0x14 0x01 0x64>;
				phandle = <0xca>;
			};

			i2s1-sdio2 {
				rockchip,pins = <0x02 0x15 0x01 0x64>;
				phandle = <0xcb>;
			};

			i2s1-sdio3 {
				rockchip,pins = <0x02 0x16 0x01 0x64>;
				phandle = <0xcc>;
			};

			i2s1-sleep {
				rockchip,pins = <0x02 0x0f 0x00 0x65 0x02 0x10 0x00 0x65 0x02 0x11 0x00 0x65 0x02 0x12 0x00 0x65 0x02 0x13 0x00 0x65 0x02 0x14 0x00 0x65 0x02 0x15 0x00 0x65 0x02 0x16 0x00 0x65 0x02 0x17 0x00 0x65>;
				phandle = <0xcd>;
			};
		};

		i2s2-0 {

			i2s2m0-mclk {
				rockchip,pins = <0x01 0x15 0x01 0x64>;
				phandle = <0xce>;
			};

			i2s2m0-sclk {
				rockchip,pins = <0x01 0x16 0x01 0x64>;
				phandle = <0xcf>;
			};

			i2s2m0-lrckrx {
				rockchip,pins = <0x01 0x1a 0x01 0x64>;
				phandle = <0xd0>;
			};

			i2s2m0-lrcktx {
				rockchip,pins = <0x01 0x17 0x01 0x64>;
				phandle = <0xd1>;
			};

			i2s2m0-sdi {
				rockchip,pins = <0x01 0x18 0x01 0x64>;
				phandle = <0xd2>;
			};

			i2s2m0-sdo {
				rockchip,pins = <0x01 0x19 0x01 0x64>;
				phandle = <0xd3>;
			};

			i2s2m0-sleep {
				rockchip,pins = <0x01 0x15 0x00 0x65 0x01 0x16 0x00 0x65 0x01 0x1a 0x00 0x65 0x01 0x17 0x00 0x65 0x01 0x18 0x00 0x65 0x01 0x19 0x00 0x65>;
				phandle = <0xd4>;
			};
		};

		i2s2-1 {

			i2s2m1-mclk {
				rockchip,pins = <0x01 0x15 0x01 0x64>;
				phandle = <0xd5>;
			};

			i2s2m1-sclk {
				rockchip,pins = <0x03 0x00 0x06 0x64>;
				phandle = <0xd6>;
			};

			i2sm1-lrckrx {
				rockchip,pins = <0x03 0x08 0x06 0x64>;
				phandle = <0xd7>;
			};

			i2s2m1-lrcktx {
				rockchip,pins = <0x03 0x08 0x04 0x64>;
				phandle = <0xd8>;
			};

			i2s2m1-sdi {
				rockchip,pins = <0x03 0x02 0x06 0x64>;
				phandle = <0xd9>;
			};

			i2s2m1-sdo {
				rockchip,pins = <0x03 0x01 0x06 0x64>;
				phandle = <0xda>;
			};

			i2s2m1-sleep {
				rockchip,pins = <0x01 0x15 0x00 0x65 0x03 0x00 0x00 0x65 0x03 0x08 0x00 0x65 0x03 0x02 0x00 0x65 0x03 0x01 0x00 0x65>;
				phandle = <0xdb>;
			};
		};

		spdif-0 {

			spdifm0-tx {
				rockchip,pins = <0x00 0x1b 0x01 0x64>;
				phandle = <0x13>;
			};
		};

		spdif-1 {

			spdifm1-tx {
				rockchip,pins = <0x02 0x11 0x02 0x64>;
				phandle = <0xdc>;
			};
		};

		spdif-2 {

			spdifm2-tx {
				rockchip,pins = <0x00 0x02 0x02 0x64>;
				phandle = <0xdd>;
			};
		};

		sdmmc0-0 {

			sdmmc0m0-pwren {
				rockchip,pins = <0x02 0x07 0x01 0x67>;
				phandle = <0xde>;
			};

			sdmmc0m0-pin {
				rockchip,pins = <0x02 0x07 0x00 0x67>;
				phandle = <0xdf>;
			};
		};

		sdmmc0-1 {

			sdmmc0m1-pwren {
				rockchip,pins = <0x00 0x1e 0x03 0x67>;
				phandle = <0xe0>;
			};

			sdmmc0m1-pin {
				rockchip,pins = <0x00 0x1e 0x00 0x67>;
				phandle = <0x70>;
			};
		};

		sdmmc0 {

			sdmmc0-clk {
				rockchip,pins = <0x01 0x06 0x01 0x68>;
				phandle = <0x54>;
			};

			sdmmc0-cmd {
				rockchip,pins = <0x01 0x04 0x01 0x69>;
				phandle = <0x55>;
			};

			sdmmc0-dectn {
				rockchip,pins = <0x01 0x05 0x01 0x67>;
				phandle = <0x56>;
			};

			sdmmc0-wrprt {
				rockchip,pins = <0x01 0x07 0x01 0x67>;
				phandle = <0xe1>;
			};

			sdmmc0-bus1 {
				rockchip,pins = <0x01 0x00 0x01 0x69>;
				phandle = <0xe2>;
			};

			sdmmc0-bus4 {
				rockchip,pins = <0x01 0x00 0x01 0x69 0x01 0x01 0x01 0x69 0x01 0x02 0x01 0x69 0x01 0x03 0x01 0x69>;
				phandle = <0x57>;
			};

			sdmmc0-pins {
				rockchip,pins = <0x01 0x06 0x00 0x67 0x01 0x04 0x00 0x67 0x01 0x05 0x00 0x67 0x01 0x07 0x00 0x67 0x01 0x03 0x00 0x67 0x01 0x02 0x00 0x67 0x01 0x01 0x00 0x67 0x01 0x00 0x00 0x67>;
				phandle = <0xe3>;
			};
		};

		sdmmc0ext {

			sdmmc0ext-clk {
				rockchip,pins = <0x03 0x02 0x03 0x6a>;
				phandle = <0xe4>;
			};

			sdmmc0ext-cmd {
				rockchip,pins = <0x03 0x00 0x03 0x67>;
				phandle = <0xe5>;
			};

			sdmmc0ext-wrprt {
				rockchip,pins = <0x03 0x03 0x03 0x67>;
				phandle = <0xe6>;
			};

			sdmmc0ext-dectn {
				rockchip,pins = <0x03 0x01 0x03 0x67>;
				phandle = <0xe7>;
			};

			sdmmc0ext-bus1 {
				rockchip,pins = <0x03 0x04 0x03 0x67>;
				phandle = <0xe8>;
			};

			sdmmc0ext-bus4 {
				rockchip,pins = <0x03 0x04 0x03 0x67 0x03 0x05 0x03 0x67 0x03 0x06 0x03 0x67 0x03 0x07 0x03 0x67>;
				phandle = <0xe9>;
			};

			sdmmc0ext-pins {
				rockchip,pins = <0x03 0x00 0x00 0x67 0x03 0x01 0x00 0x67 0x03 0x02 0x00 0x67 0x03 0x03 0x00 0x67 0x03 0x04 0x00 0x67 0x03 0x05 0x00 0x67 0x03 0x06 0x00 0x67 0x03 0x07 0x00 0x67>;
				phandle = <0xea>;
			};
		};

		sdmmc1 {

			sdmmc1-clk {
				rockchip,pins = <0x01 0x0c 0x01 0x68>;
				phandle = <0xeb>;
			};

			sdmmc1-cmd {
				rockchip,pins = <0x01 0x0d 0x01 0x69>;
				phandle = <0xec>;
			};

			sdmmc1-pwren {
				rockchip,pins = <0x01 0x12 0x01 0x69>;
				phandle = <0xed>;
			};

			sdmmc1-wrprt {
				rockchip,pins = <0x01 0x14 0x01 0x69>;
				phandle = <0xee>;
			};

			sdmmc1-dectn {
				rockchip,pins = <0x01 0x13 0x01 0x69>;
				phandle = <0xef>;
			};

			sdmmc1-bus1 {
				rockchip,pins = <0x01 0x0e 0x01 0x69>;
				phandle = <0xf0>;
			};

			sdmmc1-bus4 {
				rockchip,pins = <0x01 0x0e 0x01 0x69 0x01 0x0f 0x01 0x69 0x01 0x10 0x01 0x69 0x01 0x11 0x01 0x69>;
				phandle = <0xf1>;
			};

			sdmmc1-pins {
				rockchip,pins = <0x01 0x0c 0x00 0x67 0x01 0x0d 0x00 0x67 0x01 0x0e 0x00 0x67 0x01 0x0f 0x00 0x67 0x01 0x10 0x00 0x67 0x01 0x11 0x00 0x67 0x01 0x12 0x00 0x67 0x01 0x13 0x00 0x67 0x01 0x14 0x00 0x67>;
				phandle = <0xf2>;
			};
		};

		emmc {

			emmc-clk {
				rockchip,pins = <0x03 0x15 0x02 0x6b>;
				phandle = <0x59>;
			};

			emmc-cmd {
				rockchip,pins = <0x03 0x13 0x02 0x6c>;
				phandle = <0x5a>;
			};

			emmc-pwren {
				rockchip,pins = <0x03 0x16 0x02 0x64>;
				phandle = <0xf3>;
			};

			emmc-rstnout {
				rockchip,pins = <0x03 0x14 0x02 0x64>;
				phandle = <0xf4>;
			};

			emmc-bus1 {
				rockchip,pins = <0x00 0x07 0x02 0x6c>;
				phandle = <0xf5>;
			};

			emmc-bus4 {
				rockchip,pins = <0x00 0x07 0x02 0x6c 0x02 0x1c 0x02 0x6c 0x02 0x1d 0x02 0x6c 0x02 0x1e 0x02 0x6c>;
				phandle = <0xf6>;
			};

			emmc-bus8 {
				rockchip,pins = <0x00 0x07 0x02 0x6c 0x02 0x1c 0x02 0x6c 0x02 0x1d 0x02 0x6c 0x02 0x1e 0x02 0x6c 0x02 0x1f 0x02 0x6c 0x03 0x10 0x02 0x6c 0x03 0x11 0x02 0x6c 0x03 0x12 0x02 0x6c>;
				phandle = <0x5b>;
			};
		};

		pwm0 {

			pwm0-pin {
				rockchip,pins = <0x02 0x04 0x01 0x64>;
				phandle = <0x36>;
			};
		};

		pwm1 {

			pwm1-pin {
				rockchip,pins = <0x02 0x05 0x01 0x64>;
				phandle = <0x37>;
			};
		};

		pwm2 {

			pwm2-pin {
				rockchip,pins = <0x02 0x06 0x01 0x64>;
				phandle = <0x38>;
			};
		};

		pwmir {

			pwmir-pin {
				rockchip,pins = <0x02 0x02 0x01 0x64>;
				phandle = <0x39>;
			};
		};

		gmac-1 {

			rgmiim1-pins {
				rockchip,pins = <0x01 0x0c 0x02 0x68 0x01 0x0d 0x02 0x6a 0x01 0x13 0x02 0x6a 0x01 0x19 0x02 0x68 0x01 0x15 0x02 0x6a 0x01 0x16 0x02 0x6a 0x01 0x17 0x02 0x6a 0x01 0x0a 0x02 0x6a 0x01 0x0b 0x02 0x6a 0x01 0x08 0x02 0x68 0x01 0x09 0x02 0x68 0x01 0x0e 0x02 0x6a 0x01 0x0f 0x02 0x6a 0x01 0x10 0x02 0x68 0x01 0x11 0x02 0x68 0x00 0x08 0x01 0x68 0x00 0x0c 0x01 0x68 0x00 0x18 0x01 0x6a 0x00 0x10 0x01 0x68 0x00 0x11 0x01 0x68 0x00 0x17 0x01 0x68 0x00 0x16 0x01 0x68>;
				phandle = <0x5e>;
			};

			rmiim1-pins {
				rockchip,pins = <0x01 0x13 0x02 0x6d 0x01 0x19 0x02 0x6b 0x01 0x15 0x02 0x6d 0x01 0x18 0x02 0x6d 0x01 0x16 0x02 0x6d 0x01 0x17 0x02 0x6d 0x01 0x0a 0x02 0x6d 0x01 0x0b 0x02 0x6d 0x01 0x08 0x02 0x6b 0x01 0x09 0x02 0x6b 0x00 0x0b 0x01 0x64 0x00 0x0c 0x01 0x64 0x00 0x18 0x01 0x64 0x00 0x13 0x01 0x64 0x00 0x10 0x01 0x64 0x00 0x11 0x01 0x64>;
				phandle = <0xf7>;
			};
		};

		gmac2phy {

			fephyled-speed10 {
				rockchip,pins = <0x00 0x1e 0x01 0x64>;
				phandle = <0xf8>;
			};

			fephyled-duplex {
				rockchip,pins = <0x00 0x1e 0x02 0x64>;
				phandle = <0xf9>;
			};

			fephyled-rxm1 {
				rockchip,pins = <0x02 0x19 0x02 0x64>;
				phandle = <0x60>;
			};

			fephyled-txm1 {
				rockchip,pins = <0x02 0x19 0x03 0x64>;
				phandle = <0xfa>;
			};

			fephyled-linkm1 {
				rockchip,pins = <0x02 0x18 0x02 0x64>;
				phandle = <0x61>;
			};
		};

		tsadc_pin {

			tsadc-int {
				rockchip,pins = <0x02 0x0d 0x02 0x64>;
				phandle = <0xfb>;
			};

			tsadc-pin {
				rockchip,pins = <0x02 0x0d 0x00 0x64>;
				phandle = <0xfc>;
			};
		};

		hdmi_pin {

			hdmi-cec {
				rockchip,pins = <0x00 0x03 0x01 0x64>;
				phandle = <0x4c>;
			};

			hdmi-hpd {
				rockchip,pins = <0x00 0x04 0x01 0x6e>;
				phandle = <0x4e>;
			};

			hdmi-backlight {
				rockchip,pins = <0x03 0x05 0x00 0xaf>;
				phandle = <0x205>;
			};
		};

		cif-0 {

			dvp-d2d9-m0 {
				rockchip,pins = <0x03 0x04 0x02 0x64 0x03 0x05 0x02 0x64 0x03 0x06 0x02 0x64 0x03 0x07 0x02 0x64 0x03 0x08 0x02 0x64 0x03 0x09 0x02 0x64 0x03 0x0a 0x02 0x64 0x03 0x0b 0x02 0x64 0x03 0x01 0x02 0x64 0x03 0x00 0x02 0x64 0x03 0x03 0x02 0x64 0x03 0x02 0x02 0x64>;
				phandle = <0xfd>;
			};
		};

		cif-1 {

			dvp-d2d9-m1 {
				rockchip,pins = <0x03 0x04 0x02 0x64 0x03 0x05 0x02 0x64 0x03 0x06 0x02 0x64 0x03 0x07 0x02 0x64 0x03 0x08 0x02 0x64 0x02 0x10 0x04 0x64 0x02 0x11 0x04 0x64 0x02 0x12 0x04 0x64 0x03 0x01 0x02 0x64 0x03 0x00 0x02 0x64 0x02 0x0f 0x04 0x64 0x03 0x02 0x02 0x64>;
				phandle = <0xfe>;
			};
		};

		pmic {

			pmic-int-l {
				rockchip,pins = <0x02 0x06 0x00 0x66>;
				phandle = <0x2a>;
			};
		};

		usb2 {

			usb20-host-drv {
				rockchip,pins = <0x00 0x02 0x00 0x64>;
				phandle = <0x73>;
			};
		};

		sd {

			sdio-vcc-pin {
				rockchip,pins = <0x02 0x14 0x00 0x66>;
				phandle = <0x72>;
			};
		};

		spi0_cs2 {

			pinctrl_spi0_cs2 {
				rockchip,pins = <0x03 0x07 0x00 0x66>;
				phandle = <0x35>;
			};
		};

		sdio-pwrseq {

			wifi-enable-h {
				rockchip,pins = <0x01 0x12 0x00 0x64>;
				phandle = <0x201>;
			};
		};

		wireless-wlan {

			wifi-wake-host {
				rockchip,pins = <0x01 0x13 0x00 0x6e>;
			};
		};
	};

	chosen {
		stdout-path = "serial2:1500000n8";
	};

	external-gmac-clock {
		compatible = "fixed-clock";
		clock-frequency = <0x7735940>;
		clock-output-names = "gmac_clkin";
		#clock-cells = <0x00>;
		phandle = <0x5c>;
	};

	sdmmc-regulator {
		compatible = "regulator-fixed";
		gpio = <0x6f 0x1e 0x00>;
		pinctrl-names = "default";
		pinctrl-0 = <0x70>;
		regulator-boot-on;
		regulator-name = "vcc_sd";
		regulator-min-microvolt = <0x325aa0>;
		regulator-max-microvolt = <0x325aa0>;
		vin-supply = <0x1e>;
		phandle = <0x58>;
	};

	sdmmcio-regulator {
		compatible = "regulator-gpio";
		gpios = <0x71 0x14 0x00>;
		pinctrl-0 = <0x72>;
		pinctrl-names = "default";
		states = <0x1b7740 0x00 0x325aa0 0x01>;
		regulator-name = "vccio_sd";
		regulator-type = "voltage";
		regulator-min-microvolt = <0x1b7740>;
		regulator-max-microvolt = <0x325aa0>;
		regulator-settling-time-us = <0x1388>;
		startup-delay-us = <0x7d0>;
		regulator-always-on;
		vin-supply = <0x1e>;
		phandle = <0x20>;
	};

	vcc-host1-5v-regulator {
		compatible = "regulator-fixed";
		enable-active-high;
		gpio = <0x6f 0x02 0x00>;
		pinctrl-names = "default";
		pinctrl-0 = <0x73>;
		regulator-name = "vcc_host1_5v";
		regulator-always-on;
		vin-supply = <0x2b>;
		phandle = <0xff>;
	};

	vcc-sys {
		compatible = "regulator-fixed";
		regulator-name = "vcc_sys";
		regulator-min-microvolt = <0x4c4b40>;
		regulator-max-microvolt = <0x4c4b40>;
		phandle = <0x2b>;
	};

	wireless-wlan {
		compatible = "wlan-platdata";
		rockchip,grf = <0x3f>;
		sdio_vref = <0xce4>;
		status = "okay";
		WIFI,host_wake_irq = <0x29 0x13 0x00>;
		wifi_chip_type = "rtl8723bs";
	};

	sdio_pwrseq0 {
		compatible = "mmc-pwrseq-simple";
		pinctrl-names = "default";
		pinctrl-0 = <0x201>;
		reset-gpios = <0x29 0x12 0x01>;
		phandle = <0x200>;
	};

	vcc-phy-regulator {
		compatible = "regulator-fixed";
		regulator-name = "vcc_phy";
		regulator-always-on;
		regulator-boot-on;
		phandle = <0x5d>;
	};

	leds {
		compatible = "gpio-leds";

		led-0 {
			label = "firefly:blue:power";
			linux,default-trigger = "heartbeat";
			gpios = <0x74 0x01 0x01>;
			default-state = "on";
			mode = <0x23>;
			phandle = <0x100>;
		};

		led-1 {
			label = "firefly:yellow:user";
			linux,default-trigger = "mmc1";
			gpios = <0x74 0x00 0x01>;
			default-state = "off";
			mode = <0x05>;
			phandle = <0x101>;
		};
	};

	__symbols__ {
		ddr_timing = "/ddr_timing";
		cpu0 = "/cpus/cpu@0";
		cpu1 = "/cpus/cpu@1";
		cpu2 = "/cpus/cpu@2";
		cpu3 = "/cpus/cpu@3";
		CPU_SLEEP = "/cpus/idle-states/cpu-sleep";
		l2 = "/cpus/l2-cache0";
		cpu0_opp_table = "/opp-table-0";
		analog_sound = "/analog-sound";
		display_subsystem = "/display-subsystem";
		hdmi_sound = "/hdmi-sound";
		spdif_out = "/spdif-out";
		spdif_sound = "/spdif-sound";
		xin24m = "/xin24m";
		i2s0 = "/i2s@ff000000";
		i2s1 = "/i2s@ff010000";
		i2s2 = "/i2s@ff020000";
		spdif = "/spdif@ff030000";
		pdm = "/pdm@ff040000";
		grf = "/syscon@ff100000";
		io_domains = "/syscon@ff100000/io-domains";
		grf_gpio = "/syscon@ff100000/gpio";
		power = "/syscon@ff100000/power-controller";
		uart0 = "/serial@ff110000";
		uart1 = "/serial@ff120000";
		uart2 = "/serial@ff130000";
		i2c0 = "/i2c@ff150000";
		i2c1 = "/i2c@ff160000";
		rk805 = "/i2c@ff160000/pmic@18";
		vdd_logic = "/i2c@ff160000/pmic@18/regulators/DCDC_REG1";
		vdd_arm = "/i2c@ff160000/pmic@18/regulators/DCDC_REG2";
		vcc_ddr = "/i2c@ff160000/pmic@18/regulators/DCDC_REG3";
		vcc_io = "/i2c@ff160000/pmic@18/regulators/DCDC_REG4";
		vcc_18 = "/i2c@ff160000/pmic@18/regulators/LDO_REG1";
		vcc18_emmc = "/i2c@ff160000/pmic@18/regulators/LDO_REG2";
		vdd_10 = "/i2c@ff160000/pmic@18/regulators/LDO_REG3";
		i2c2 = "/i2c@ff170000";
		i2c3 = "/i2c@ff180000";
		spi0 = "/spi@ff190000";
		wdt = "/watchdog@ff1a0000";
		pwm0 = "/pwm@ff1b0000";
		pwm1 = "/pwm@ff1b0010";
		pwm2 = "/pwm@ff1b0020";
		pwm3 = "/pwm@ff1b0030";
		dmac = "/dma-controller@ff1f0000";
		soc_thermal = "/thermal-zones/soc-thermal";
		threshold = "/thermal-zones/soc-thermal/trips/trip-point0";
		target = "/thermal-zones/soc-thermal/trips/trip-point1";
		soc_crit = "/thermal-zones/soc-thermal/trips/soc-crit";
		tsadc = "/tsadc@ff250000";
		dfi = "/dfi@ff790000";
		dmc = "/dmc@ff780000";
		dmc_opp_table = "/dmc-opp-table";
		efuse = "/efuse@ff260000";
		efuse_id = "/efuse@ff260000/id@7";
		cpu_leakage = "/efuse@ff260000/cpu-leakage@17";
		logic_leakage = "/efuse@ff260000/logic-leakage@19";
		efuse_cpu_version = "/efuse@ff260000/cpu-version@1a";
		saradc = "/adc@ff280000";
		gpu = "/gpu@ff300000";
		gpu_opp_table = "/gpu-opp-table";
		h265e_mmu = "/iommu@ff330200";
		vepu_mmu = "/iommu@ff340800";
		vpu = "/video-codec@ff350000";
		vpu_mmu = "/iommu@ff350800";
		rkvdec = "/video-codec@ff360000";
		rkvdec_mmu = "/iommu@ff360480";
		vop = "/vop@ff370000";
		vop_out = "/vop@ff370000/port";
		vop_out_hdmi = "/vop@ff370000/port/endpoint@0";
		vop_mmu = "/iommu@ff373f00";
		rga = "/rga@ff390000";
		iep = "/iep@ff3a0000";
		iep_mmu = "/iommu@ff3a0800";
		hdmi = "/hdmi@ff3c0000";
		hdmi_in = "/hdmi@ff3c0000/ports/port";
		hdmi_in_vop = "/hdmi@ff3c0000/ports/port/endpoint";
		codec = "/codec@ff410000";
		hdmiphy = "/phy@ff430000";
		cru = "/clock-controller@ff440000";
		usb2phy_grf = "/syscon@ff450000";
		u2phy = "/syscon@ff450000/usb2phy@100";
		u2phy_otg = "/syscon@ff450000/usb2phy@100/otg-port";
		u2phy_host = "/syscon@ff450000/usb2phy@100/host-port";
		usb3phy_grf = "/syscon@ff460000";
		u3phy = "/usb3-phy@ff470000";
		u3phy_utmi = "/usb3-phy@ff470000/utmi@ff470000";
		u3phy_pipe = "/usb3-phy@ff470000/pipe@ff478000";
		sdmmc = "/mmc@ff500000";
		sdio = "/mmc@ff510000";
		emmc = "/mmc@ff520000";
		sdmmc_ext = "/dwmmc@ff5f0000";
		gmac2io = "/ethernet@ff540000";
		gmac2phy = "/ethernet@ff550000";
		phy = "/ethernet@ff550000/mdio/ethernet-phy@0";
		usb20_otg = "/usb@ff580000";
		usb_host0_ehci = "/usb@ff5c0000";
		usb_host0_ohci = "/usb@ff5d0000";
		usbdrd3 = "/usb@ff600000";
		gic = "/interrupt-controller@ff811000";
		pinctrl = "/pinctrl";
		gpio0 = "/pinctrl/gpio@ff210000";
		gpio1 = "/pinctrl/gpio@ff220000";
		gpio2 = "/pinctrl/gpio@ff230000";
		gpio3 = "/pinctrl/gpio@ff240000";
		pcfg_pull_up = "/pinctrl/pcfg-pull-up";
		pcfg_pull_down = "/pinctrl/pcfg-pull-down";
		pcfg_pull_none = "/pinctrl/pcfg-pull-none";
		pcfg_pull_none_2ma = "/pinctrl/pcfg-pull-none-2ma";
		pcfg_pull_up_2ma = "/pinctrl/pcfg-pull-up-2ma";
		pcfg_pull_up_4ma = "/pinctrl/pcfg-pull-up-4ma";
		pcfg_pull_none_4ma = "/pinctrl/pcfg-pull-none-4ma";
		pcfg_pull_down_4ma = "/pinctrl/pcfg-pull-down-4ma";
		pcfg_pull_none_8ma = "/pinctrl/pcfg-pull-none-8ma";
		pcfg_pull_up_8ma = "/pinctrl/pcfg-pull-up-8ma";
		pcfg_pull_none_12ma = "/pinctrl/pcfg-pull-none-12ma";
		pcfg_pull_up_12ma = "/pinctrl/pcfg-pull-up-12ma";
		pcfg_output_high = "/pinctrl/pcfg-output-high";
		pcfg_output_low = "/pinctrl/pcfg-output-low";
		pcfg_input_high = "/pinctrl/pcfg-input-high";
		pcfg_input = "/pinctrl/pcfg-input";
		i2c0_xfer = "/pinctrl/i2c0/i2c0-xfer";
		i2c1_xfer = "/pinctrl/i2c1/i2c1-xfer";
		i2c2_xfer = "/pinctrl/i2c2/i2c2-xfer";
		i2c3_xfer = "/pinctrl/i2c3/i2c3-xfer";
		i2c3_pins = "/pinctrl/i2c3/i2c3-pins";
		hdmii2c_xfer = "/pinctrl/hdmi_i2c/hdmii2c-xfer";
		pdmm0_clk = "/pinctrl/pdm-0/pdmm0-clk";
		pdmm0_fsync = "/pinctrl/pdm-0/pdmm0-fsync";
		pdmm0_sdi0 = "/pinctrl/pdm-0/pdmm0-sdi0";
		pdmm0_sdi1 = "/pinctrl/pdm-0/pdmm0-sdi1";
		pdmm0_sdi2 = "/pinctrl/pdm-0/pdmm0-sdi2";
		pdmm0_sdi3 = "/pinctrl/pdm-0/pdmm0-sdi3";
		pdmm0_clk_sleep = "/pinctrl/pdm-0/pdmm0-clk-sleep";
		pdmm0_sdi0_sleep = "/pinctrl/pdm-0/pdmm0-sdi0-sleep";
		pdmm0_sdi1_sleep = "/pinctrl/pdm-0/pdmm0-sdi1-sleep";
		pdmm0_sdi2_sleep = "/pinctrl/pdm-0/pdmm0-sdi2-sleep";
		pdmm0_sdi3_sleep = "/pinctrl/pdm-0/pdmm0-sdi3-sleep";
		pdmm0_fsync_sleep = "/pinctrl/pdm-0/pdmm0-fsync-sleep";
		otp_pin = "/pinctrl/tsadc/otp-pin";
		otp_out = "/pinctrl/tsadc/otp-out";
		uart0_xfer = "/pinctrl/uart0/uart0-xfer";
		uart0_cts = "/pinctrl/uart0/uart0-cts";
		uart0_rts = "/pinctrl/uart0/uart0-rts";
		uart0_rts_pin = "/pinctrl/uart0/uart0-rts-pin";
		uart1_xfer = "/pinctrl/uart1/uart1-xfer";
		uart1_cts = "/pinctrl/uart1/uart1-cts";
		uart1_rts = "/pinctrl/uart1/uart1-rts";
		uart1_rts_pin = "/pinctrl/uart1/uart1-rts-pin";
		uart2m0_xfer = "/pinctrl/uart2-0/uart2m0-xfer";
		uart2m1_xfer = "/pinctrl/uart2-1/uart2m1-xfer";
		spi0m0_clk = "/pinctrl/spi0-0/spi0m0-clk";
		spi0m0_cs0 = "/pinctrl/spi0-0/spi0m0-cs0";
		spi0m0_tx = "/pinctrl/spi0-0/spi0m0-tx";
		spi0m0_rx = "/pinctrl/spi0-0/spi0m0-rx";
		spi0m0_cs1 = "/pinctrl/spi0-0/spi0m0-cs1";
		spi0m1_clk = "/pinctrl/spi0-1/spi0m1-clk";
		spi0m1_cs0 = "/pinctrl/spi0-1/spi0m1-cs0";
		spi0m1_tx = "/pinctrl/spi0-1/spi0m1-tx";
		spi0m1_rx = "/pinctrl/spi0-1/spi0m1-rx";
		spi0m1_cs1 = "/pinctrl/spi0-1/spi0m1-cs1";
		spi0m2_clk = "/pinctrl/spi0-2/spi0m2-clk";
		spi0m2_cs0 = "/pinctrl/spi0-2/spi0m2-cs0";
		spi0m2_tx = "/pinctrl/spi0-2/spi0m2-tx";
		spi0m2_rx = "/pinctrl/spi0-2/spi0m2-rx";
		i2s1_mclk = "/pinctrl/i2s1/i2s1-mclk";
		i2s1_sclk = "/pinctrl/i2s1/i2s1-sclk";
		i2s1_lrckrx = "/pinctrl/i2s1/i2s1-lrckrx";
		i2s1_lrcktx = "/pinctrl/i2s1/i2s1-lrcktx";
		i2s1_sdi = "/pinctrl/i2s1/i2s1-sdi";
		i2s1_sdo = "/pinctrl/i2s1/i2s1-sdo";
		i2s1_sdio1 = "/pinctrl/i2s1/i2s1-sdio1";
		i2s1_sdio2 = "/pinctrl/i2s1/i2s1-sdio2";
		i2s1_sdio3 = "/pinctrl/i2s1/i2s1-sdio3";
		i2s1_sleep = "/pinctrl/i2s1/i2s1-sleep";
		i2s2m0_mclk = "/pinctrl/i2s2-0/i2s2m0-mclk";
		i2s2m0_sclk = "/pinctrl/i2s2-0/i2s2m0-sclk";
		i2s2m0_lrckrx = "/pinctrl/i2s2-0/i2s2m0-lrckrx";
		i2s2m0_lrcktx = "/pinctrl/i2s2-0/i2s2m0-lrcktx";
		i2s2m0_sdi = "/pinctrl/i2s2-0/i2s2m0-sdi";
		i2s2m0_sdo = "/pinctrl/i2s2-0/i2s2m0-sdo";
		i2s2m0_sleep = "/pinctrl/i2s2-0/i2s2m0-sleep";
		i2s2m1_mclk = "/pinctrl/i2s2-1/i2s2m1-mclk";
		i2s2m1_sclk = "/pinctrl/i2s2-1/i2s2m1-sclk";
		i2s2m1_lrckrx = "/pinctrl/i2s2-1/i2sm1-lrckrx";
		i2s2m1_lrcktx = "/pinctrl/i2s2-1/i2s2m1-lrcktx";
		i2s2m1_sdi = "/pinctrl/i2s2-1/i2s2m1-sdi";
		i2s2m1_sdo = "/pinctrl/i2s2-1/i2s2m1-sdo";
		i2s2m1_sleep = "/pinctrl/i2s2-1/i2s2m1-sleep";
		spdifm0_tx = "/pinctrl/spdif-0/spdifm0-tx";
		spdifm1_tx = "/pinctrl/spdif-1/spdifm1-tx";
		spdifm2_tx = "/pinctrl/spdif-2/spdifm2-tx";
		sdmmc0m0_pwren = "/pinctrl/sdmmc0-0/sdmmc0m0-pwren";
		sdmmc0m0_pin = "/pinctrl/sdmmc0-0/sdmmc0m0-pin";
		sdmmc0m1_pwren = "/pinctrl/sdmmc0-1/sdmmc0m1-pwren";
		sdmmc0m1_pin = "/pinctrl/sdmmc0-1/sdmmc0m1-pin";
		sdmmc0_clk = "/pinctrl/sdmmc0/sdmmc0-clk";
		sdmmc0_cmd = "/pinctrl/sdmmc0/sdmmc0-cmd";
		sdmmc0_dectn = "/pinctrl/sdmmc0/sdmmc0-dectn";
		sdmmc0_wrprt = "/pinctrl/sdmmc0/sdmmc0-wrprt";
		sdmmc0_bus1 = "/pinctrl/sdmmc0/sdmmc0-bus1";
		sdmmc0_bus4 = "/pinctrl/sdmmc0/sdmmc0-bus4";
		sdmmc0_pins = "/pinctrl/sdmmc0/sdmmc0-pins";
		sdmmc0ext_clk = "/pinctrl/sdmmc0ext/sdmmc0ext-clk";
		sdmmc0ext_cmd = "/pinctrl/sdmmc0ext/sdmmc0ext-cmd";
		sdmmc0ext_wrprt = "/pinctrl/sdmmc0ext/sdmmc0ext-wrprt";
		sdmmc0ext_dectn = "/pinctrl/sdmmc0ext/sdmmc0ext-dectn";
		sdmmc0ext_bus1 = "/pinctrl/sdmmc0ext/sdmmc0ext-bus1";
		sdmmc0ext_bus4 = "/pinctrl/sdmmc0ext/sdmmc0ext-bus4";
		sdmmc0ext_pins = "/pinctrl/sdmmc0ext/sdmmc0ext-pins";
		sdmmc1_clk = "/pinctrl/sdmmc1/sdmmc1-clk";
		sdmmc1_cmd = "/pinctrl/sdmmc1/sdmmc1-cmd";
		sdmmc1_pwren = "/pinctrl/sdmmc1/sdmmc1-pwren";
		sdmmc1_wrprt = "/pinctrl/sdmmc1/sdmmc1-wrprt";
		sdmmc1_dectn = "/pinctrl/sdmmc1/sdmmc1-dectn";
		sdmmc1_bus1 = "/pinctrl/sdmmc1/sdmmc1-bus1";
		sdmmc1_bus4 = "/pinctrl/sdmmc1/sdmmc1-bus4";
		sdmmc1_pins = "/pinctrl/sdmmc1/sdmmc1-pins";
		emmc_clk = "/pinctrl/emmc/emmc-clk";
		emmc_cmd = "/pinctrl/emmc/emmc-cmd";
		emmc_pwren = "/pinctrl/emmc/emmc-pwren";
		emmc_rstnout = "/pinctrl/emmc/emmc-rstnout";
		emmc_bus1 = "/pinctrl/emmc/emmc-bus1";
		emmc_bus4 = "/pinctrl/emmc/emmc-bus4";
		emmc_bus8 = "/pinctrl/emmc/emmc-bus8";
		pwm0_pin = "/pinctrl/pwm0/pwm0-pin";
		pwm1_pin = "/pinctrl/pwm1/pwm1-pin";
		pwm2_pin = "/pinctrl/pwm2/pwm2-pin";
		pwmir_pin = "/pinctrl/pwmir/pwmir-pin";
		rgmiim1_pins = "/pinctrl/gmac-1/rgmiim1-pins";
		rmiim1_pins = "/pinctrl/gmac-1/rmiim1-pins";
		fephyled_speed10 = "/pinctrl/gmac2phy/fephyled-speed10";
		fephyled_duplex = "/pinctrl/gmac2phy/fephyled-duplex";
		fephyled_rxm1 = "/pinctrl/gmac2phy/fephyled-rxm1";
		fephyled_txm1 = "/pinctrl/gmac2phy/fephyled-txm1";
		fephyled_linkm1 = "/pinctrl/gmac2phy/fephyled-linkm1";
		tsadc_int = "/pinctrl/tsadc_pin/tsadc-int";
		tsadc_pin = "/pinctrl/tsadc_pin/tsadc-pin";
		hdmi_cec = "/pinctrl/hdmi_pin/hdmi-cec";
		hdmi_hpd = "/pinctrl/hdmi_pin/hdmi-hpd";
		hdmi_backlight = "/pinctrl/hdmi_pin/hdmi-backlight";
		dvp_d2d9_m0 = "/pinctrl/cif-0/dvp-d2d9-m0";
		dvp_d2d9_m1 = "/pinctrl/cif-1/dvp-d2d9-m1";
		pmic_int_l = "/pinctrl/pmic/pmic-int-l";
		usb20_host_drv = "/pinctrl/usb2/usb20-host-drv";
		sdio_vcc_pin = "/pinctrl/sd/sdio-vcc-pin";
		pinctrl_spi0_cs2 = "/pinctrl/spi0_cs2/pinctrl_spi0_cs2";
		gmac_clkin = "/external-gmac-clock";
		vcc_sd = "/sdmmc-regulator";
		vccio_sd = "/sdmmcio-regulator";
		vcc_host1_5v = "/vcc-host1-5v-regulator";
		vcc_otg_5v = "/vcc-host1-5v-regulator";
		vcc_sys = "/vcc-sys";
		vcc_phy = "/vcc-phy-regulator";
		power_led = "/leds/led-0";
		user_led = "/leds/led-1";
		wifi_enable_h = "/pinctrl/sdio-pwrseq/wifi-enable-h";
		sdio_pwrseq = "/sdio_pwrseq0";
	};
};
```

### wifi patch

Patch to get spi-dev working:

```
--- rk3328-roc-cc-org.dts	Sat Mar 09 16:36:40 2024
+++ rk3328-roc-cc-new.dts	Sat Mar 09 17:33:57 2024
@@ -860,7 +860,7 @@

 		spi_for_cs2@0 {
 			reg = <0x00>;
-			compatible = "rockchip,spi_test_bus1_cs2";
+			compatible = "armbian,spi-dev";
 			pinctrl-names = "default";
 			pinctrl-0 = <0x35>;
 			spi-max-frequency = <0x4c4b40>;
```

----
Back to [rebuilding](rebuilding.md)

----
Back to [start](index.md)
