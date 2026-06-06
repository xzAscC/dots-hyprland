# dots-hyprland

## File Architecture
```
dots-hyprland/
├── setup                          # Main entry script (dispatcher for all subcommands)
├── diagnose                       # Diagnostic script for generating system info / bug reports
│
├── dots/                          # Core dotfiles deployed to user's $HOME
│   ├── .config/
│   │   ├── hypr/                  # Hyprland WM configuration
│   │   │   ├── hyprland.lua       # Main Hyprland config entry (Lua)
│   │   │   ├── hypridle.conf      # Idle daemon config
│   │   │   ├── hyprlock.conf      # Screen locker config
│   │   │   ├── hyprland/          # Modular Hyprland Lua config
│   │   │   │   ├── colors.lua     # Color theme variables
│   │   │   │   ├── env.lua        # Environment variables
│   │   │   │   ├── execs.lua      # Autostart entries
│   │   │   │   ├── general.lua    # General settings (gaps, borders, layout...)
│   │   │   │   ├── keybinds.lua   # Keyboard bindings
│   │   │   │   ├── rules.lua      # Window rules
│   │   │   │   ├── variables.lua  # Shared variables
│   │   │   │   ├── lib/           # Shared Lua libraries
│   │   │   │   ├── scripts/       # Helper scripts (emoji picker, AI, screenshot...)
│   │   │   │   ├── services/      # Background service management
│   │   │   │   └── shellOverrides/# Shell override hooks
│   │   │   ├── hyprlock/          # Hyprlock auxiliary scripts
│   │   │   └── custom/            # User customization overrides (env, execs, keybinds...)
│   │   │
│   │   ├── quickshell/            # Quickshell bar/shell UI (QML)
│   │   │   └── ii/
│   │   │       ├── shell.qml            # Shell entry point
│   │   │       ├── settings.qml         # Settings definitions
│   │   │       ├── GlobalStates.qml     # Shared global state
│   │   │       ├── welcome.qml          # First-run welcome screen
│   │   │       ├── killDialog.qml       # Process kill dialog
│   │   │       ├── ReloadPopup.qml      # Config reload popup
│   │   │       ├── modules/             # UI modules
│   │   │       │   ├── common/          # Shared components
│   │   │       │   ├── ii/              # Illogical Impulse specific widgets
│   │   │       │   ├── settings/        # Settings panel modules
│   │   │       │   └── waffle/          # Waffle panel widgets
│   │   │       ├── services/            # Backend QML services (audio, bluetooth, network, AI...)
│   │   │       ├── scripts/             # Shell scripts for backend tasks
│   │   │       ├── assets/              # Icons and images
│   │   │       ├── defaults/            # Default configurations
│   │   │       ├── panelFamilies/        # Panel layout families (II, Waffle)
│   │   │       └── translations/        # i18n JSON files (15 languages)
│   │   │
│   │   ├── fish/                  # Fish shell config
│   │   ├── kitty/                 # Kitty terminal config
│   │   ├── foot/                  # Foot terminal config
│   │   ├── fuzzel/                # Fuzzel app launcher config
│   │   ├── wlogout/               # Logout menu (layout + style)
│   │   ├── mpv/                   # MPV player config
│   │   ├── fontconfig/            # Font rendering config
│   │   ├── xdg-desktop-portal/    # XDG portal config for Hyprland
│   │   ├── matugen/               # Material You color generator config + templates
│   │   ├── kde-material-you-colors/ # KDE Material You integration
│   │   ├── Kvantum/               # Kvantum Qt theme engine configs
│   │   ├── zshrc.d/               # Zsh snippet configs
│   │   ├── darklyrc               # Darkly KDE theme config
│   │   ├── dolphinrc              # Dolphin file manager config
│   │   ├── kdeglobals             # KDE global settings
│   │   ├── konsolerc              # Konsole terminal config
│   │   ├── starship.toml          # Starship prompt config
│   │   ├── chrome-flags.conf      # Chrome/Chromium flags
│   │   ├── code-flags.conf        # VS Code flags
│   │   └── thorium-flags.conf     # Thorium browser flags
│   │
│   └── .local/
│       └── share/
│           ├── icons/             # Custom icons (illogical-impulse.svg)
│           └── konsole/           # Konsole profile
│
├── dots-extra/                    # Optional/additional dotfiles
│   ├── emacs/                     # Emacs material theme
│   ├── fcitx5/                    # Fcitx5 input method config
│   ├── fedora/                    # Fedora-specific Hyprland overrides
│   ├── fontsets/                  # Additional font configurations (Arabic, etc.)
│   ├── swaylock/                  # Swaylock screen locker config
│   └── via-nix/                   # Nix-specific configs (hypridle)
│
├── sdata/                         # Setup data & scripts
│   ├── lib/                       # Shared shell libraries
│   │   ├── environment-variables.sh  # Color codes and env vars
│   │   ├── functions.sh              # Utility functions
│   │   ├── package-installers.sh     # Package manager wrappers
│   │   └── dist-determine.sh         # OS/distro detection
│   │
│   ├── subcmd-install/            # Install subcommand logic
│   │   ├── 0.greeting.sh         # Welcome message
│   │   ├── 1.deps-router.sh      # Dependency installation router
│   │   ├── 2.setups.sh           # System setup (permissions, services)
│   │   ├── 3.files.sh            # Dotfile deployment
│   │   ├── 3.files-exp.sh        # Experimental file deployment
│   │   ├── 3.files-legacy.sh     # Legacy file deployment fallback
│   │   └── options.sh            # CLI option parsing
│   │
│   ├── subcmd-uninstall/          # Uninstall subcommand
│   ├── subcmd-exp-update/         # Experimental incremental update
│   ├── subcmd-exp-merge/          # Experimental git rebase merge
│   ├── subcmd-checkdeps/          # Dependency checker (dev tool)
│   ├── subcmd-resetfirstrun/      # Reset first-run state
│   ├── subcmd-virtmon/            # Virtual monitor creator (dev tool)
│   │
│   ├── dist-arch/                 # Arch Linux packages (PKGBUILDs + install scripts)
│   ├── dist-fedora/               # Fedora dependency management
│   ├── dist-gentoo/               # Gentoo ebuilds + local package definitions
│   ├── dist-nix/                  # Nix/home-manager module
│   │
│   └── uv/                        # Python virtualenv management via uv
│       ├── requirements.in        # Python dependency spec
│       ├── requirements.txt       # Pinned dependencies
│       └── shell.nix              # Nix dev shell for Python env
│
├── .github/
│   ├── workflows/                 # CI workflows (auto-close, dist updates, moderation)
│   ├── ISSUE_TEMPLATE/            # Issue & feature request templates
│   ├── assets/                    # GitHub assets (logo)
│   ├── CONTRIBUTING.md
│   ├── FUNDING.yml
│   └── pull_request_template.md
│
├── licenses/                      # License texts (MIT, LGPL-3.0)
├── .gitignore
└── .gitmodules                    # Git submodules
```
