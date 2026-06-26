# cm0102

# Championship Manager 01/02 on macOS Using UTM and Windows XP

Install and update Championship Manager 01/02 on modern macOS systems using a Windows XP virtual machine running in UTM.

This approach is:

* Free to use
* Compatible with Apple Silicon Macs (M1/M2/M3/M4)
* A workaround for DirectX issues encountered with other installation methods
* Compatible with data updates and popular community patches

## Prerequisites

### Software

* UTM
* Windows XP installation media
* Championship Manager 01/02 ISO

### Optional Updates

* Official 3.9.68 Patch
* Latest Data Update
* Tactics Packs
* Background Image Pack
* Tapani Patch 2.22

## Step 1: Install Windows XP in UTM

Create a Windows XP virtual machine in UTM and complete the operating system installation.

Refer to UTM documentation for:

* Creating a new virtual machine
* Installing Windows XP
* Configuring shared folders between macOS and Windows XP

Add the following section after **Step 1: Install Windows XP in UTM**.

---

## Step 1.5: Configure File Sharing Between macOS and Windows XP

To install patches, data updates, and other files, it's useful to enable SMB file sharing between macOS and the Windows XP virtual machine. This approach is reliable for Windows XP and avoids the compatibility issues that can occur with newer UTM sharing methods. ([Lee Perry][1])

### 1. Enable File Sharing in Windows XP

1. Open **Network Connections**.
2. Enable **File and Printer Sharing** on the network connection.
3. Either:

   * Allow File and Printer Sharing through the Windows Firewall, or
   * Temporarily disable the Windows Firewall (simplest for an isolated VM).

### 2. Change the UTM Network Mode

1. Shut down the virtual machine.
2. Open the VM settings in UTM.
3. Change the network type from **VLAN** to **Shared Network**.
4. Save the configuration and restart Windows XP. ([Lee Perry][1])

### 3. Find the Windows XP IP Address

Open **Command Prompt** and run:

```text
ipconfig
```

Note the IPv4 address (typically something like `192.168.xx.y`).

### 4. Connect from macOS

In Finder:

1. Select **Go → Connect to Server…**
2. Enter:

```text
smb://192.168.xx.y
```

Replace the address with the IP address obtained above.

### 5. Authenticate

Use:

* **Username:** `Administrator`
* **Password:** (leave blank unless you set one)

IMPORTANT: This no longer seems to work with MacOS. Blank passwords are not accepted.

### 6. Mount the Shared Folder

Select **SharedDocs** when prompted.

You can now drag and drop files between macOS and the Windows XP virtual machine using this shared folder. If the network disconnects, simply reconnect using **Go → Connect to Server…** in Finder. ([Lee Perry][1])

### Notes

* This method is ideal for transferring:

  * Official patches
  * Data updates
  * Tactics
  * Background image packs
  * Save games
* ISO files can still be mounted directly in UTM when appropriate.
* Recent versions of UTM support SPICE WebDAV shared folders for newer Windows guests, but SMB networking is generally the most dependable option for Windows XP. ([UTM Documentation][2])

[1]: https://prry.uk/2023-08-13-filesharing-between-a-windows-xp-virtual-machine-in-utm-and-macos?utm_source=chatgpt.com "Filesharing between a Windows XP Virtual Machine in UTM and MacOS - Lee Perry"
[2]: https://docs.getutm.app/guest-support/windows/?utm_source=chatgpt.com "Windows | UTM Documentation"

## Step 2: Install Championship Manager 01/02

1. Mount the CM0102 ISO inside Windows XP.
2. Run the installer.
3. Complete the installation using default options.
4. Launch the game to verify that it works correctly.

## Step 3: Apply Official Patch 3.9.68

Before installing any data updates, patch the game to version 3.9.68.

1. Download the 3.9.68 patch.
2. Run the patch installer inside Windows XP.
3. Point the installer at your CM0102 installation directory.
4. Complete the update.

## Step 4: Install Latest Data Update

To play with modern squads and competitions:

1. Download a community data update.
2. Extract the update files.
3. Copy the files into the Championship Manager 01/02 installation directory.
4. Overwrite existing files when prompted.
5. Start a new game to use the updated database.

## Step 5: Install Tactics Packs (Optional)

1. Download a tactics pack.
2. Extract the `.tct` files.
3. Copy them into:

```text
Championship Manager 01-02\Tactics
```

4. Launch the game and load the tactics from within CM0102.

## Step 6: Install Background Images (Optional)

1. Download a background image pack.
2. Extract the archive.
3. Copy the contents into:

```text
Championship Manager 01-02\Pictures
```

4. Allow existing files to be replaced.

## Step 7: Apply Tapani Patch (Optional)

The Tapani Patch adds additional functionality, including:

* Modern competition names
* Updated start years
* Enhanced game options
* Additional bug fixes

1. Download the Tapani Patch.
2. Run the installer in Windows XP.
3. Select your `cm0102.exe` when prompted.
4. Choose the desired patch options.
5. Complete installation.

## Notes

* Nick's Patcher does not execute correctly under Windows XP and should not be relied upon in this setup.
* Start a new save after applying major patches or database updates.
* Enable weekly autosave to reduce the impact of potential crashes.
* This UTM + Windows XP method is often recommended when Wine, PlayOnMac, or Crossover experience compatibility issues on newer Apple Silicon Macs.

## Resources

Required:

* CM 01/02 ISO
* Official 3.9.68 Patch

Optional:

* Data Update
* Tactics Packs
* Background Image Pack
* Tapani Patch 2.22

## Credits

Based on the installation methodology published by Lee Perry and the CM0102 community.
