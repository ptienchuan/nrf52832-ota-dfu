# nRF52832 OTA DFU

Tham khảo tử Guide: https://devzone.nordicsemi.com/guides/nrf-connect-sdk-guides/b/software/posts/ncs-dfu

Sử dụng sample `nrf/peripheral_lbs` và triển khai OTA DFU trên sample này.

Flutter app cho demo này: https://github.com/ptienchuan/flutter-ota-dfu

## DeviceTree

Chỉ định partition giữ active image:
```
	chosen {
		zephyr,code-partition = &slot0_partition;
	};
```

Phân vùng cho image: ở device tree này đang chia 2 slot để lưu image
```
&flash0 {
	partitions {
		slot0_partition: partition@c000 {
			label = "image-0";
			reg = <0x0000C000 0x32000>;
		};
		slot1_partition: partition@3e000 {
			label = "image-1";
			reg = <0x0003E000 0x32000>;
		};
		scratch_partition: partition@70000 {
			label = "image-scratch";
			reg = <0x00070000 0xa000>;
		};
	};
};
```
