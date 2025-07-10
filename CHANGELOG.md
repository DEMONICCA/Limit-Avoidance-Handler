> `Changelog:`
> - All significant changes to this project will be documented here.
---

> [1.0.0]
>
> - Initial Release  
> - Disable and neutralize thermal-related services and daemons (`thermal-engine`, `vendor.thermal`, `thermald`, etc.)  
> - Override thermal trip points and apply no-cooler configurations to critical thermal zones  
> - Remove CPU/GPU power and thermal limits via `/proc/ppm`, `/proc/gpufreq`, and `/sys/devices/...`  
> - Force-reset all thermal-related system properties via `resetprop`  
> - Lock thermal control nodes as read-only (`chmod 444`) to prevent reactivation  
> - Kill non-essential user applications and background processes aggressively  
> - Clear system logs and temp files: Dropbox, Tombstones, Dalvik-cache, and app-level caches  
> - Force kernel memory optimization: drop caches, compact memory, reset ZRAM, and run `fstrim`
---
