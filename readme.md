# Plugin to use with Pwnagotchi BookWorm Version and the PiSugar2.
[BookWorm Pwnagotchi](https://github.com/jayofelony/pwnagotchi-bookworm)

This plugin DOES require using the official [pisugar-power-manager-rs](https://github.com/PiSugar/pisugar-power-manager-rs) install. 

I have updated the commands required for a clean install since there was some issues, the python version for bookworm has changed being one of those. Original script has been left unmodified. 

## Install guide:

```bash
# Go to the home directory
cd ~

# Install PiSugar Power Manager Manually, the auto install uses 32bit
wget https://github.com/PiSugar/pisugar-power-manager-rs/releases/download/v1.7.5/pisugar-poweroff_1.7.5_arm64.deb
wget https://github.com/PiSugar/pisugar-power-manager-rs/releases/download/v1.7.5/pisugar-server_1.7.5_arm64.deb
sudo dpkg -i pisugar-poweroff_1.7.5_arm64.deb
sudo dpkg -i pisugar-server_1.7.5_arm64.deb


# Download the plugin and support library
git clone https://github.com/PiSugar/pisugar2py.git
git clone https://github.com/PiSugar/pwnagotchi-pisugar2-plugin.git

# This installs the pisugar2 package into your python library (command updated for jayfelony image using python3.11)
sudo ln -s ~/pisugar2py/ /usr/local/lib/python3.11/dist-packages/pisugar2

```


In /etc/pwnagotchi/config.toml add:
```toml
main.plugins.pisugar2.enabled = true
main.plugins.pisugar2.shutdown = 5
main.plugins.pisugar2.sync_rtc_on_boot = true
```



PiSugar2 web settings are accessible at http://10.0.0.2:8421/#/

The support library exposes all of the available commands from the pi-sugar in a python library for developers
