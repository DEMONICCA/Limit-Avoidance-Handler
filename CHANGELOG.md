> `Changelog:`
> - All significant changes to this project will be documented here.
---

> [3.0.0] `FINAL`
>
> - Restructured script into modular functions (e.g., `thermal_terminate`, `terminate_services`, `terminate_thermal_services`, `reset_thermal_props`, `configure_thermal_zones`, `set_thermal_trip_points`, `set_cpu_limits`, `set_ppm_policy`, `configure_power_limits`, `restrict_thermal_files`, `trim_filesystems`, `terminate_user_processes`) for better maintainability and readability.
> - Introduced a `main` function to orchestrate all operations, improving script flow and execution control.
> - Enhanced thermal termination logic by consolidating `thermal_kill` and `thermal_list` into `thermal_terminate` with retry mechanisms, dynamic service discovery from init directories, and refined killing strategies using signals -15 and -9.
> - Added `terminate_services` for targeted stopping of services like thermal, logd, traced, statsd, adbd, with improved regex filtering and retry loops.
> - Implemented `reset_thermal_props` to systematically reset properties related to thermal management, including negation and value overrides for better control.
> - Added `configure_thermal_zones` and `set_thermal_trip_points` to dynamically configure thermal zones, trip points, and cooler states using loops over /proc/driver/thermal paths.
> - Introduced `set_cpu_limits` and `set_ppm_policy` for fine-tuned CPU frequency and PPM (Power Performance Management) policy adjustments, including disabling throttling and setting unlimited modes.
> - Added `configure_power_limits` to manage GPU, battery, and KGSL throttling, with SELinux context handling and permission adjustments for write access.
> - Optimized `restrict_thermal_files` by disabling modes and restricting permissions on thermal sysfs files.
> - Streamlined `trim_filesystems` with mount checks before fstrim operations.
> - Refined `terminate_user_processes` with filtered process killing based on UID and command patterns, plus expanded cache clearing for user data directories.
> - Removed deprecated or redundant sections like direct ZRAM configuration, VM tweaks (e.g., swappiness, min_free_kbytes), LMK parameters, and process reclaim settings to focus on core thermal optimizations.
> - Eliminated initial sleep 20 and `lah` helper function, replacing with more direct echo and permission handling in new functions.
> - Improved error suppression, variable scoping, and retry delays (e.g., 0.2s) for robustness.
> - Added dumpsys thermalservice call for additional thermal state synchronization.
> - Minor optimizations for performance, such as using expr for arithmetic and sorting unique values.
> - Removed `system.prop` generation in `service.sh`, eliminating redundant low memory killer (LMK) property settings for a leaner module structure.
> - Updated `module.prop` version tag from `[FINAL]` to `[FINAL]` in `service.sh` with refined logic to avoid unnecessary overwrites.
> - Enhanced notification message in `service.sh` to include device name (`ro.product.model`) and more descriptive text: "Optimizations have been applied to your device ($DEVICE_NAME)..." for improved user feedback.
> - Removed icon handling (`Lah_01.png`) in both `service.sh` and `customize.sh`, simplifying installation and notification processes.
> - Raised minimum Android version requirement in `customize.sh` from SDK 28 (Android 9) to SDK 29 (Android 10) for better compatibility with modern systems.
> - Improved architecture detection in `customize.sh` by simplifying `ARCH_ABI` logic, removing complex case statements and directly using `uname -m` for consistency.
> - Updated `ANDROID_CODENAME` in `customize.sh` to remove "Tidak Dikenal" fallback, aligning with standardized codenames for supported SDKs (29–36).
> - Removed `name` modification in `service.sh` that appended "(Limit Avoidance Handler)" to ensure consistent module naming.
> - Enhanced `verify_module` function in `customize.sh` to enforce strict author validation (`author=@illumi`) and module name (`Limit Avoidance Handler`) for improved security.
> - Optimized notification in `service.sh` by removing `icon_arg` logic and using a more professional message format with "All features are now enabled."
> - Added emoji for Android SDK 36 (`🐶`) in `service.sh`, removing SDK 28 (`🦝`) to align with updated minimum version requirements.
> - Streamlined module removal logic in `customize.sh` by using `$ID="LAH"` consistently and improving success/failure messaging clarity.
> - Removed `system.prop` from permission settings in `customize.sh` due to its absence in the updated module.
> - Minor improvements in error handling, ensuring `ANDROID_SDK` is a valid number before proceeding in `customize.sh`.
> - Other small refinements for performance, compatibility, and user experience across supported Android versions.
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