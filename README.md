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
wget -L https://raw.github.com/Hrishikesh1312/TerminalConfig/main/starship.toml
echo "eval \"\$(starship init zsh)\"" >> ~/.zshrc
```

### 6. Change Default Shell
Change default shell to Zsh
```bash
chsh -s $(which zsh)
```

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
wget -L https://raw.github.com/Hrishikesh1312/TerminalConfig/main/config.jsonc
```

## Screenshots
### Fastfetch
![image](https://github.com/user-attachments/assets/efab8b63-235d-4f11-999a-5020de8042a9)
### Starship
![image](https://github.com/user-attachments/assets/31a33f15-0ec2-4247-8255-093d396bc8ba)


