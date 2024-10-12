

# Lab 2: Installing Packages and Applications

## Objectives
In this lab, you will:
- Use the Advanced Package Tool (APT) to manage packages in Kali Linux.
- Install, upgrade, and remove applications using command-line tools.
- Search for packages and manage repositories.

## Background / Scenario
Kali Linux, built on Debian, utilizes the APT package management system, which simplifies the process of installing, upgrading, and managing software packages. Understanding how to use APT is essential for maintaining a functional and secure environment, particularly in cybersecurity roles.

## Required Resources
- Kali Linux virtual machine (VM).
- Internet access.

## Instructions

### Part 1: Updating Package Lists

1. **Open a Terminal**:
   - Log into your Kali Linux VM.
   - Open a terminal by clicking on the terminal icon in the taskbar.

2. **Update the Package List**:
   - Run the following command to update the list of available packages and their versions:
   ```bash
   sudo apt update
   ```
   - **Explanation**: 
     - The `sudo` command allows you to run programs with the security privileges of another user (typically the superuser).
     - `apt` is the command-line tool for managing packages.
     - `update` fetches the latest package information from the repositories configured on your system. This ensures you have the most current information about the software available for installation.

   - **Example Output**:
     ```
     Get:1 http://kali.download/kali kali-rolling InRelease [30.5 kB]
     ...
     Reading package lists... Done
     ```

### Part 2: Installing Packages

1. **Install `curl`**:
   - Use APT to install `curl`, a command-line tool for transferring data with URLs:
   ```bash
   sudo apt install curl
   ```
   - **Explanation**:
     - `install` tells APT to fetch the specified package and any required dependencies from the repository and install them.
     - `curl` is a useful tool for testing endpoints and downloading files.

   - **Example Output**:
     ```
     The following NEW packages will be installed:
       curl
     ...
     Do you want to continue? [Y/n] Y
     ```

2. **Verify the Installation**:
   - Check the version of `curl` to confirm the installation was successful:
   ```bash
   curl --version
   ```
   - **Explanation**: This command displays the installed version of `curl`. If installed correctly, it will show version information.

   - **Example Output**:
     ```
     curl 7.68.0 (x86_64-pc-linux-gnu) libcurl/7.68.0 OpenSSL/1.1.1d
     ```

### Part 3: Upgrading Packages

1. **Upgrade All Installed Packages**:
   - Run the following command to upgrade all currently installed packages to their latest versions:
   ```bash
   sudo apt upgrade
   ```
   - **Explanation**: This command checks for updates to all installed packages and upgrades them to the latest versions available in the repository.

   - **Example Output**:
     ```
     The following packages will be upgraded:
       package1 package2 ...
     ...
     Do you want to continue? [Y/n] Y
     ```

2. **Review Upgrade Messages**:
   - Observe the output, which lists packages that were upgraded. It may prompt you to confirm the upgrades; simply press `Y` and then `Enter` to proceed.

### Part 4: Removing Packages

1. **Remove `curl`**:
   - To uninstall `curl`, use the following command:
   ```bash
   sudo apt remove curl
   ```
   - **Explanation**: The `remove` command removes the specified package from the system while leaving its configuration files intact. This is useful if you want to reinstall the package later without losing its settings.

   - **Example Output**:
     ```
     Removing curl (7.68.0-1) ...
     ```

2. **Confirm Removal**:
   - Verify that `curl` is no longer installed by checking its version:
   ```bash
   curl --version
   ```
   - **Explanation**: If `curl` was successfully removed, this command should return an error indicating that `curl` is not found.

   - **Example Output**:
     ```
     curl: command not found
     ```

### Part 5: Searching for Packages

1. **Search for Networking Packages**:
   - Use the APT search functionality to find packages related to networking:
   ```bash
   apt search networking
   ```
   - **Explanation**: This command searches the package database for any packages that have "networking" in their name or description, displaying a list of matching packages.

   - **Example Output**:
     ```
     Sorting... Done
     Full Text Search... Done
     networking-tools/focal 1.0 all
       A collection of networking tools
     ...
     ```

2. **Review Results**:
   - Take note of some of the networking tools available for installation, such as `net-tools`, `nmap`, or `traceroute`.

### Part 6: Managing Repositories

1. **Edit Repositories**:
   - Open the `sources.list` file to view and manage your APT repositories:
   ```bash
   sudo nano /etc/apt/sources.list
   ```
   - **Explanation**: This file contains a list of repositories that APT uses to fetch packages. Using `nano` opens the file in a text editor.

2. **Modify Repository Entries**:
   - Check for any commented-out entries (lines starting with `#`). Uncomment (remove the `#`) any repositories you want to enable.
   - **Example**: Change `#deb http://kali.download/kali kali-rolling main non-free contrib` to `deb http://kali.download/kali kali-rolling main non-free contrib`.
   - **Explanation**: Enabling additional repositories allows you to access more packages that are not available in the default repositories.

3. **Save and Exit**:
   - After making your changes, press `Ctrl + O` to save and `Ctrl + X` to exit the editor.

### Part 7: Final Review

1. **Update Package List Again**:
   - After modifying repositories, run:
   ```bash
   sudo apt update
   ```
   - **Explanation**: This command updates the package list again to include any new repositories you just enabled.

2. **Explore Installed Packages**:
   - Use the following command to list all installed packages:
   ```bash
   dpkg --get-selections | grep -v deinstall
   ```
   - **Explanation**: This command lists all installed packages, filtering out any that have been marked for deinstallation.

   - **Example Output**:
     ```
     curl
     vim
     nmap
     ```

### Conclusion
In this lab, you have learned how to manage packages in Kali Linux using APT. You should now be comfortable installing, upgrading, and removing applications, as well as searching for and managing software repositories. Mastery of these skills is essential for effective system administration and cybersecurity tasks.

