> `Changelog:`
> - All significant changes to this project will be documented here.
---

> [2.0.0]
>
> - Added a little code in `uninstall.sh`.
> - Fixed a stubborn temperature sensor value.
> - Removes duplicate commands in the code.
> - Added some mount points to `FSTRIM`. for better improvement.
> - Drop caches 3x, compact memory, looser overcommit.
> - Kill processes more optimally for more stable performance.
> - Added LMK & process_reclaim optimizations to make things a bit better.
> - Now `ZRAM` is made more dynamic for `4,6,8` ram users and a little quality improvement.
> - Add module banner for KernelSU Next.
> - A slight performance improvement with this change could be even better.
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