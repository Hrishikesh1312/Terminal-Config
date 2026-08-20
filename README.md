# TerminalConfig

Configuration files I have collected from various sources for customizing Zsh and Fastfetch (for now).  
- The Starship configuration is a modified version of the configuration file provided by `@deverebor`.  
- The Fastfetch configuration is from **XeroLinux**.  

---

## Zsh Configuration

### 1. Install Zsh
```bash
# Ubuntu/Debian
sudo apt install zsh

# Fedora
sudo dnf install zsh

# Arch-based
sudo pacman -S zsh

# openSUSE
sudo zypper in zsh
```

### 2. Install Starship
```bash
curl -sS https://starship.rs/install.sh | sh
```
### 3. Install Nerd Fonts
Download and install any Nerd Font from `www.nerdfonts.com`

### 4. Add Zsh Plugins
Add Zsh plugins for auto suggestions and syntax highlighting.
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
echo "source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
echo "source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
```

### 5. Configure Starship
```bash
cd ~/.config
wget https://raw.github.com/Hrishikesh1312/TerminalConfig/main/starship.toml
echo "eval \"\$(starship init zsh)\"" >> ~/.zshrc
```

### 6. Change Default Shell
Change default shell to Zsh
```bash
chsh -s $(which zsh)
```

## Windows PowerShell Configuration

### 1. Install Starship
Install Starship with WinGet from PowerShell:
```powershell
winget install --id Starship.Starship
```

Restart PowerShell after installation, or open a new PowerShell window so that `starship` is available on your `PATH`.

### 2. Install a Nerd Font
Install any Nerd Font from [nerdfonts.com](https://www.nerdfonts.com/) and select it in your Windows Terminal profile settings. The symbols in this repository's configuration require a font with Nerd Font glyphs.

### 3. Use this repository's Starship configuration
From the root of this repository, copy the TOML file to Starship's default Windows configuration path:
```powershell
$configDirectory = Join-Path $HOME ".config"
New-Item -ItemType Directory -Force -Path $configDirectory | Out-Null
Copy-Item .\starship.toml (Join-Path $configDirectory "starship.toml") -Force
```

This uses the `starship.toml` in this repository as-is. Run the copy command again whenever you want to update the installed configuration after pulling repository changes.

### 4. Initialize Starship in PowerShell
Add Starship to your PowerShell profile:
```powershell
$env:STARSHIP_CONFIG = "C:\path\to\TerminalConfig\starship.toml"
Invoke-Expression (&starship init powershell)
```

If a profile file does not exist, create it first:
```powershell
New-Item -ItemType File -Force -Path $PROFILE | Out-Null
Add-Content -Path $PROFILE -Value '$env:STARSHIP_CONFIG = "C:\path\to\TerminalConfig\starship.toml"'
Add-Content -Path $PROFILE -Value 'Invoke-Expression (&starship init powershell)'
```

If your profile already contains a command like `fastfetch`, keep it and append the Starship lines below it:
```powershell
fastfetch
$env:STARSHIP_CONFIG = "C:\path\to\TerminalConfig\starship.toml"
Invoke-Expression (&starship init powershell)
```

Restart PowerShell, or reload the profile:
```powershell
. $PROFILE
```

### Optional: load the repository file directly
To keep the configuration in the repository instead of copying it, set `STARSHIP_CONFIG` to the full path of this repository's TOML file before initializing Starship:
```powershell
$env:STARSHIP_CONFIG = Join-Path (Get-Location) "starship.toml"
Add-Content -Path $PROFILE -Value '$env:STARSHIP_CONFIG = "C:\path\to\TerminalConfig\starship.toml"'
Add-Content -Path $PROFILE -Value 'Invoke-Expression (&starship init powershell)'
. $PROFILE
```

Replace `C:\path\to\TerminalConfig\starship.toml` with the actual path where you cloned this repository. This is especially important on Windows because the profile may otherwise contain only startup commands such as `fastfetch`, which prevents Starship from loading. The direct-path setup automatically uses the repository file, so changes to it are reflected the next time PowerShell starts.

## Fastfetch Configuration

### 1. Install Fastfetch
```bash
# Ubuntu (24.10 onwards)
sudo apt install fastfetch

# Fedora
sudo dnf install fastfetch

# Arch-based
sudo pacman -S fastfetch

# openSUSE
sudo zypper in fastfetch
```

### 2. Configure Fastfetch
```bash
# Navigate to the configuration directory
cd ~/.config
mkdir fastfetch
cd fastfetch

# Generate default config
fastfetch --gen-config

# Replace with custom configuration
rm config.jsonc
wget https://raw.github.com/Hrishikesh1312/TerminalConfig/main/config.jsonc
```

## Screenshots
### Fastfetch
![image](https://github.com/user-attachments/assets/efab8b63-235d-4f11-999a-5020de8042a9)
### Starship
![image](https://github.com/user-attachments/assets/31a33f15-0ec2-4247-8255-093d396bc8ba)


