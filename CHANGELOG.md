> `Changelog:`
> - All significant changes to this project will be documented here.
---

> [2.0.0]
>
> - Improved thermal process detection and termination with dedicated thermal_kill() and thermal_list() functions for comprehensive service management.
> - Added extensive thermal service list covering MediaTek, Qualcomm, and generic Android thermal services including HAL implementations.
> - Extended thermal trip point configuration to cover all available trip points (trip_point_*_temp) instead of only the first one.
> - Refined cache clearing mechanism with multiple iterations and proper synchronization for enhanced memory optimization.
> - Dynamic ZRAM sizing based on total system memory with optimized compression algorithm (LZ4) and performance tuning.
> - Advanced LMK parameter tuning including adaptive mechanisms and process reclaim optimization for better memory pressure handling.
> - Graceful process termination with SIGTERM followed by SIGKILL, including process renice for better system stability.
> - Comprehensive FSTRIM operations across all major partitions including system, vendor, product, and metadata.
> - New GPU frequency and thermal limiting controls including OPP enable functionality.
> - Improved file permission handling with proper chmod operations for thermal subsystem files.
> - Added virtual memory watermark tuning for optimized memory reclaim behavior.
> - Advanced process reclaim parameters including pressure thresholds and swap efficiency controls.
> - Refined process killing logic to preserve essential system UI components while terminating unnecessary background processes.
> - Adding `system.prop` and a little update to `uninstall.sh` might make things a little better.
> - Add notifications with a combination of icons.
> - Add module banner for KernelSU Next.
> - Enhanced error checking and file existence validation throughout the script execution.
> - Code refactoring for better execution efficiency and reduced system overhead during thermal management operations.
---

> [1.0.0]
>
> - Comprehensive Android thermal management and performance optimization script.
> - Automated detection and termination of thermal-related services including thermal-engine, thermald, and vendor thermal components.
> - Intelligent stopping of thermal monitoring processes with SIGSTOP signals and service property manipulation.
> - Dynamic modification of thermal-related system properties using resetprop to disable thermal throttling mechanisms.
> - Specialized handling for MediaTek thermal zones including CPU, PMIC, battery, charger, and wireless thermal management.
> - Integration with MSM thermal framework and Adreno GPU throttling controls.
> - Automatic adjustment of thermal trip points to maximum safe temperatures (125°C) across all thermal zones.
> - Dynamic CPU frequency limit removal through thermal message interface and PPM policy manipulation.
> - Complete GPU thermal protection bypass including battery, thermal, and power management limitations.
> - Comprehensive memory cleanup including cache clearing, tombstone removal, and ZRAM reset functionality.
> - Selective termination of non-essential user applications while preserving system critical processes.
> - Automated FSTRIM operations for data and cache partitions to maintain optimal storage performance.
> - Virtual memory subsystem optimization including cache dropping, memory compaction, and swap management.
> - Robust error checking and multiple attempt mechanisms for service termination and configuration changes.
> - Proper privilege escalation handling for system-level modifications and process control.
---
