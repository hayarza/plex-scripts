# Plex Management Scripts

Simple command-line utilities for managing Plex Media Server on Linux systems using systemd.

## Scripts

- **start-plex** - Start the Plex Media Server
- **stop-plex** - Stop the Plex Media Server
- **restart-plex** - Restart the Plex Media Server
- **status-plex** - Check the status of the Plex Media Server

## Prerequisites

- Plex Media Server installed
- systemd-based Linux distribution
- sudo privileges

## Installation

### Option 1: System-wide (requires sudo)

```bash
# Clone or download this repository
git clone <your-repo-url> ~/plex-scripts
cd ~/plex-scripts

# Copy scripts to system bin directory
sudo cp start-plex stop-plex restart-plex status-plex /usr/local/bin/

# Make them executable
sudo chmod +x /usr/local/bin/start-plex
sudo chmod +x /usr/local/bin/stop-plex
sudo chmod +x /usr/local/bin/restart-plex
sudo chmod +x /usr/local/bin/status-plex
```

### Option 2: User-only (no sudo needed for installation)

```bash
# Clone or download this repository
git clone <your-repo-url> ~/plex-scripts
cd ~/plex-scripts

# Create local bin directory if it doesn't exist
mkdir -p ~/.local/bin

# Copy scripts to local bin directory
cp start-plex stop-plex restart-plex status-plex ~/.local/bin/

# Make them executable
chmod +x ~/.local/bin/start-plex
chmod +x ~/.local/bin/stop-plex
chmod +x ~/.local/bin/restart-plex
chmod +x ~/.local/bin/status-plex

# Add ~/.local/bin to PATH (if not already added)
# For bash:
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# For zsh:
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## Usage

After installation, you can use the following commands from anywhere:

```bash
# Start Plex Media Server
start-plex

# Stop Plex Media Server
stop-plex

# Restart Plex Media Server
restart-plex

# Check Plex Media Server status
status-plex
```

Note: These commands use `sudo` internally, so you'll be prompted for your password when starting, stopping, or restarting the service.

## Arch Linux Installation Notes

### Installing Plex on Arch

```bash
# Using yay (AUR helper)
yay -S plex-media-server

# Enable and start the service
sudo systemctl enable plexmediaserver.service
sudo systemctl start plexmediaserver.service
```

### Mounting NTFS Drives for Plex

If you have media on an NTFS drive, make sure the `plex` user can access it:

```bash
# Add plex user to your user's group
sudo usermod -a -G yourusername plex

# Or create a permanent mount point in /etc/fstab
UUID=YOUR-UUID /mnt/media ntfs3 defaults,uid=1000,gid=1000,umask=022 0 0
```

Access the Plex web interface at: `http://localhost:32400/web`

## Uninstallation

### System-wide

```bash
sudo rm /usr/local/bin/start-plex
sudo rm /usr/local/bin/stop-plex
sudo rm /usr/local/bin/restart-plex
sudo rm /usr/local/bin/status-plex
```

### User-only

```bash
rm ~/.local/bin/start-plex
rm ~/.local/bin/stop-plex
rm ~/.local/bin/restart-plex
rm ~/.local/bin/status-plex
```

## License

MIT License - Feel free to use and modify as needed.
