# Freeing Space on `/` (Arch Linux)

**Legend:**  
🟢 Low (safe/routine) · 🟡 Medium (aggressive caches/logs) · 🟠 High (could remove stuff you wanted) · 🔴 Nuclear (major deletions, be sure)

---

## Inspect / Find Big Stuff
| Command | What it does | 😬 |
|---|---|---|
| `df -h /` | Show free/used space on root. | 🟢 |
| `sudo du -hxd1 / \| sort -h` | Size of top-level dirs on `/`. | 🟢 |
| `sudo pacman -S ncdu && sudo ncdu -x /` | Curses UI to find/delete big files (stay on root FS). | 🟢 |
| `sudo find / -xdev -type f -size +500M -print` | List files >500 MB on root FS. | 🟢 |

---

## Pacman / Package Caches
| Command | What it does | 😬 |
|---|---|---|
| `sudo pacman -Sc` | Remove cached pkgs not installed. | 🟢 |
| `sudo pacman -Scc` | Purge **all** pkg caches (must re-download later). | 🟡 |
| `sudo pacman -S pacman-contrib` | Install tools incl. `paccache`. | 🟢 |
| `sudo paccache -r` | Keep 3 latest versions per package. | 🟢 |
| `sudo paccache -rk1` | Keep only the latest version. | 🟡 |
| `sudo paccache -r -u` | Drop cached pkgs for uninstalled packages. | 🟢 |

---

## AUR Helper (paru) Cache
| Command | What it does | 😬 |
|---|---|---|
| `paru -Sc --noconfirm` | Clean paru cache (keep latest). | 🟢 |
| `paru -Scc --noconfirm` | Purge **all** paru cache. | 🟡 |
| `rm -rf ~/.cache/paru/*` | Nuke all paru build/cache files. | 🟡 |
| `sudo rm -rf /tmp/paru* /tmp/yay*` | Clear temp build leftovers. | 🟢 |

---

## Orphaned Packages
| Command | What it does | 😬 |
|---|---|---|
| `pacman -Qtdq` | List orphaned deps. | 🟢 |
| `sudo pacman -Rns $(pacman -Qtdq)` | Remove orphans (+configs). Review list first. | 🟠 |
| `paru -Qtdq` | List AUR+repo orphans via paru. | 🟢 |
| `paru -Rns $(paru -Qtdq)` | Remove them. | 🟠 |

---

## Logs, Coredumps, Temp
| Command | What it does | 😬 |
|---|---|---|
| `journalctl --disk-usage` | Show journal size. | 🟢 |
| `sudo journalctl --vacuum-size=200M` | Trim logs to 200 MB. | 🟢 |
| `sudo journalctl --vacuum-time=2weeks` | Keep last 2 weeks of logs. | 🟢 |
| `sudo rm -rf /var/lib/systemd/coredump/*` | Delete coredumps (can be huge). | 🟡 |
| `sudo systemd-tmpfiles --clean` | Clean temp files per policies. | 🟢 |
| `sudo rm -rf /var/lib/pacman/sync/*.part` | Drop partial pacman DB downloads. | 🟢 |

---

## User Caches / Trash (KDE/Wayland friendly)
| Command | What it does | 😬 |
|---|---|---|
| `gio trash --empty` | Empty user Trash. | 🟢 |
| `du -sh ~/.cache/* \| sort -h` | See biggest user caches. | 🟢 |
| `rm -rf ~/.cache/thumbnails/*` | Clear thumbnail cache. | 🟢 |
| `rm -rf ~/.cache/kioexec` | Clear KDE temp exec cache. | 🟢 |
| `rm -rf ~/.cache/{mozilla,firefox,chromium,google-chrome}/*` | Clear browser caches. | 🟡 |

---

## Flatpak (if you use it)
| Command | What it does | 😬 |
|---|---|---|
| `flatpak list --app --runtime --columns=application,size` | See what’s heavy. | 🟢 |
| `flatpak uninstall --unused` | Remove unused runtimes/apps. | 🟢 |
| `flatpak uninstall <app-id>` | Remove specific app(s). | 🟡 |

---

## Docker (if you use it)
| Command | What it does | 😬 |
|---|---|---|
| `docker system df` | Show Docker disk usage. | 🟢 |
| `docker system prune` | Remove stopped containers & dangling stuff. | 🟡 |
| `docker system prune -a` | Also remove **all** unused images. | 🟠 |
| `docker volume prune` | Remove unused volumes (data loss for unused). | 🟠 |

---

## Kernels / Big Packages
| Command | What it does | 😬 |
|---|---|---|
| `pacman -Q \| grep '^linux'` | List installed kernels. | 🟢 |
| `sudo pacman -Rns linux-lts linux-zen` | Remove extra kernels you **don’t** use. Keep one working kernel! | 🟠 |
| `expac -H M '%-30n %10m\n' \| sort -k2 -h` | List pkgs by install size (needs `pacman-contrib`). | 🟢 |

---

## Wine Prefixes & Gaming Runtimes (only if you don’t need them)
| Command | What it does | 😬 |
|---|---|---|
| `du -sh ~/.wine` | Size of default Wine prefix. | 🟢 |
| `wine uninstaller` | GUI to remove Wine apps. | 🟢 |
| `rm -rf ~/.wine` | Delete **all** Wine apps/configs. | 🔴 |
| `du -sh ~/.local/share/{bottles,lutris}` | Check Bottles/Lutris size. | 🟢 |
| `rm -rf ~/.local/share/bottles/bottles/<name>` | Remove a Bottles prefix. | 🔴 |

---

## Optional: Keep caches under control automatically
| Command | What it does | 😬 |
|---|---|---|
| `fcrontab -e` then add: `30 3 * * 0 paru -Sc --noconfirm` | Weekly paru cache clean (Sun 03:30). | 🟢 |
| `systemctl enable --now paccache.timer` | Keep only 3 latest pkg versions (needs `pacman-contrib`). | 🟢 |

---

**Tip:** Run the 🟢 items regularly. Use 🟡 when you need a quick chunk back. Reach for 🟠/🔴 only if you’re sure you don’t need what’s being removed.
