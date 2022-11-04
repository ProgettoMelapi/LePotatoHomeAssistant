How to install Home Assistant Supervised on Le Potato (Libre Computer AML-S905X-CC)

1. Boot from USB (optional)
- SD-card boot image from LibreComputer: https://github.com/libre-computer-project/libretech-flash-tool
- Not necessary, but enables SSD

2. Image: Ubuntu server 22.04 LTS (for Potato, use aml-s905x-cc) (https://distro.libre.computer/ci/ubuntu/22.04/)
- Unzip: tar -xf
- Flash USB stick or SSD: I used balenaEtcher to flash USB stick

3. OS installation
- Username and pw: ubuntu
- sudo apt update && sudo apt upgrade (+reboot)
- sudo apt install network-manager
- sudo systemctl enable NetworkManager
- sudo apt install jq ca-certificates curl gnupg lsb-release
- sudo apt --fix-broken install (some dependencies will be missing)

4. Docker installation
- For Docker install, follow their instructions: docs.docker.com/engine/install/ubuntu/

5. Home Assistant Supervised isntallation
- Follow this instruction: https://prog.world/installing-home-assistant-supervised-on-ubuntu-22-04-lts/
- Check for newest agent: https://github.com/home-assistant/os-agent/releases/
- wget github.com/home-assistant/os-agent/releases/download/1.4.1/os-agent_1.4.1_linux_aarch64.deb
- sudo dpkg -i os-agent_1.4.1_linux_aarch64.deb
- wget https://github.com/home-assistant/supervised-installer/releases/latest/download/homeassistant-supervised.deb
- touch /etc/default/grub
- Add: "systemd.unified_cgroup_hierarchy=false" into grub
- sudo dpkg -i homeassistant-supervised.deb
- sudo rm /etc/default/grub
- OBS! First install will take time (10-20 min), be patient.

5. Configurating HA Supervised
- Choose Raspberrypi4-64
- Wait 5-10 minutes and you should see HomeAssistant preparing page in port 8123
