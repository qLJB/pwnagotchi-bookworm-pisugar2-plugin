# Plugin to use with Pwnagotchi BookWorm and the PiSugar2.
[BookWorm Pwnagotchi](https://github.com/jayofelony/pwnagotchi-bookworm)

This plugin DOES require using the official [pisugar-power-manager-rs](https://github.com/PiSugar/pisugar-power-manager-rs) install. 

I have updated the commands required for a clean install since there was some issues, the python version for bookworm has changed being one of those. 

Checkout the [main branch](https://github.com/tisboyo/pwnagotchi-pisugar2-plugin) here. 

## Install guide:

```bash
# Go to the home directory
cd ~

# Install PiSugar Power Manager 
wget http://cdn.pisugar.com/release/pisugar-power-manager.sh
bash pisugar-power-manager.sh -c release

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
