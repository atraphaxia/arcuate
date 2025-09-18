# arcuate

An Ansible playbook for installing Arch Linux, designed to be used in the live installation environment.



## Usage

This Ansible playbook is designed to be used while booted in the live installation environment. You may follow the first steps of the Arch Linux [installation guide](https://wiki.archlinux.org/title/Installation_guide) if you don't already know how to boot into one.

You can then execute the following commands in order:

```sh
# Connect to WiFi. You will be prompted for the WiFi password.
$ iwctl station wlan0 connect wifi_name

# Initialize and populate pacman-key
$ pacman-key --init
$ pacman-key --populate

# Install git and ansible
$ pacman -Sy git ansible-core

# Clone this repository
$ git clone https://github.com/atraphaxia/arcuate.git
$ cd arcuate
```

You will be in the cloned repository directory after executing all commands. Modify `config.yml` to change the settings for the install, e.g. boot partition size, CPU brand, etc. You can then proceed to executing the playbook:

```sh
# Install required collections
$ ansible-galaxy install -r requirements.yml

# Execute the playbook
$ ansible-playbook live.yml -i inventory.yml
```
