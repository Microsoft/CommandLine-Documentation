---
title: Comparing WSL 2 and WSL 1
description: Compare version 1 and version 2 of the Windows Subsystem for Linux. Learn whats new in WSL 2 - actual Linux kernel, faster speed, full system call compatibility. WSL 1 works better if your storing files across operating file systems. You can expand the size of your WSL 2 Virtual Hardware Disk (VHD).
keywords: BashOnWindows, bash, wsl, windows, windowssubsystem, gnu, linux, ubuntu, debian, suse, windows 10, UX changes, WSL 2, linux kernel, network applications, localhost, IPv6, Virtual Hardware Disk, VHD, VHD limitations, VHD error
ms.date: 09/15/2020
ms.topic: conceptual
ms.localizationpriority: high
---

# Comparing WSL 1 and WSL 2

The primary difference and reasons for updating the Windows Subsystem for Linux from WSL 1 to WSL 2 are to:

- **increase file system performance**,
- **support full system call compatibility**.

WSL 2 uses the latest and greatest in virtualization technology to run a Linux kernel inside of a lightweight utility virtual machine (VM). However, WSL 2 is not a traditional VM experience.

## Comparing features

Feature | WSL 1 | WSL 2
--- | --- | ---
 Integration between Windows and Linux| ✅|✅
 Fast boot times| ✅ | ✅
 Small resource foot print| ✅ |✅
 Runs with current versions of VMWare and VirtualBox| ✅ | ✅
 Managed VM| ❌ | ✅
 Full Linux Kernel| ❌ |✅
 Full system call compatibility| ❌ | ✅
 Performance across OS file systems| ✅ | ❌

As you can tell from the comparison table above, the WSL 2 architecture outperforms WSL 1 in several ways, with the exception of performance across OS file systems.

## Performance across OS file systems

We recommend against working across operating systems with your files, unless you have a specific reason for doing so. For the fastest performance speed, store your files in the WSL file system if you are working in a Linux command line (Ubuntu, OpenSUSE, etc). If your working in a Windows command line (PowerShell, Command Prompt), store your files in the Windows file system.

For example, when storing your WSL project files:

- Use the Linux file system root directory: `\\wsl$\Ubuntu-18.04\home\<user name>\Project`
- Not the Windows file system root directory: `C:\Users\<user name>\Project`

You can access your Linux root file system with Windows apps and tools like File Explorer. Try opening a Linux distribution (like Ubuntu), be sure that you are in the Linux home directory by entering this command: `cd ~`. Then open your Linux file system in File Explorer by entering *(don't forget the period at the end)*: `explorer.exe .`

WSL 2 is only available in Windows 10, Version 1903, Build 18362 or higher. Check your Windows version by selecting the **Windows logo key + R**, type **winver**, select **OK**. (Or enter the `ver` command in Windows Command Prompt). You may need to [update to the latest Windows version](ms-settings:windowsupdate). For builds lower than 18362, WSL is not supported at all.

> [!NOTE]
> WSL 2 will work with [VMWare 15.5.5+](https://blogs.vmware.com/workstation/2020/05/vmware-workstation-now-supports-hyper-v-mode.html) and [VirtualBox 6+](https://www.virtualbox.org/wiki/Changelog-6.0).

## Whats new in WSL 2

WSL 2 is a major overhaul of the underlying architecture and uses virtualization technology and a Linux kernel to enable new features. The primary goals of this update are to increase file system performance and add full system call compatibility.

- [WSL 2 system requirements](./install-win10.md#step-2---update-to-wsl-2)
- [Update from WSL 1 to WSL 2](./install-win10.md#step-2---update-to-wsl-2)
- [Frequently Asked Questions about WSL 2](./wsl2-faq.md)

### WSL 2 architecture

A traditional VM experience can be slow to boot up, is isolated, consumes a lot of resources, and requires your time to manage it. WSL 2 does not have these attributes.

WSL 2 provides the benefits of WSL 1, including seamless integration between Windows and Linux, fast boot times, a small resource footprint, and requires no VM configuration or management. While WSL 2 does use a VM, it is managed and run behind the scenes, leaving you with the same user experience as WSL 1.

### Full Linux kernel

The Linux kernel in WSL 2 is built by Microsoft from the latest stable branch, based on the source available at kernel.org. This kernel has been specially tuned for WSL 2, optimizing for size and performance to provide an amazing Linux experience on Windows. The kernel will be serviced by Windows updates, which means you will get the latest security fixes and kernel improvements without needing to manage it yourself.

The [WSL 2 Linux kernel is open source](https://github.com/microsoft/WSL2-Linux-Kernel). If you'd like to learn more, check out the blog post [Shipping a Linux Kernel with Windows](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/) written by the team that built it.

### Increased file IO performance

File intensive operations like git clone, npm install, apt update, apt upgrade, and more are all noticeably faster with WSL 2.

The actual speed increase will depend on which app you're running and how it is interacting with the file system. Initial versions of WSL 2 run up to 20x faster compared to WSL 1 when unpacking a zipped tarball, and around 2-5x faster when using git clone, npm install and cmake on various projects.

### Full system call compatibility

Linux binaries use system calls to perform functions such as accessing files, requesting memory, creating processes, and more. Whereas WSL 1 used a translation layer that was built by the WSL team, WSL 2 includes its own Linux kernel with full system call compatibility. Benefits include:

- A whole new set of apps that you can run inside of WSL, such as **[Docker](/tutorials/wsl-containers.md)** and more.

- Any updates to the Linux kernel are immediately ready for use. (You don't have to wait for the WSL team to implement updates and add the changes).

### WSL 2 uses a smaller amount of memory on startup

WSL 2 uses a lightweight utility VM on a real Linux kernel with a small memory footprint. The utility will allocate Virtual Address backed memory on startup. It is configured to start with a smaller proportion of your total memory that what was required for WSL 1.

## Exceptions for using WSL 1 rather than WSL 2

We recommend that you use WSL 2 as it offers faster performance and 100% system call compatibility. However, there are a few specific scenarios where you might prefer using WSL 1. Consider using WSL 1 if:

- Your project files must be stored in the Windows file system. WSL 1 offers faster access to files mounted from Windows.
  - If you will be using your WSL Linux distribution to access project files on the Windows file system, and these files cannot be stored on the Linux file system, you will achieve faster performance across the OS files systems by using WSL 1.
- A project which requires cross-compilation using both Windows and Linux tools on the same files.
  - File performance across the Windows and Linux operating systems is faster in WSL 1 than WSL 2, so if you are using Windows applications to access Linux files, you will currently achieve faster performance with WSL 1.

> [!NOTE]
> Consider trying the VS Code [Remote WSL Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) to enable you to store your project files on the Linux file system, using Linux command line tools, but also using VS Code on Windows to author, edit, debug, or run your project in an internet browser without any of the performance slow-downs associated with working across the Linux and Windows file systems. [Learn more](https://code.visualstudio.com/docs/remote/wsl).

## Accessing network applications

### Accessing Linux networking apps from Windows (localhost)

If you are building a networking app (for example an app running on a NodeJS or SQL server) in your Linux distribution, you can access it from a Windows app (like your Edge or Chrome internet browser) using `localhost` (just like you normally would).

However, if you are running an older version of Windows (Build 18945 or less), you will need to get the IP address of the Linux host VM (or [update to the latest Windows version](ms-settings:windowsupdate)).

To find the IP address of the virtual machine powering your Linux distribution:

- From your WSL distribution (ie Ubuntu), run the command: `ip addr`
- Find and copy the address under the `inet` value of the `eth0` interface.
- If you have the grep tool installed, find this more easily by filtering the output with the command: `ip addr | grep eth0`
- Connect to your Linux server using this IP address.

The picture below shows an example of this by connecting to a Node.js server using the Edge browser.

![Connect to NodeJS server with Edge](media/wsl2-network-w2l.jpg)

### Accessing Windows networking apps from Linux (host IP)

If you want to access a networking app running on Windows (for example an app running on a NodeJS or SQL server) from your Linux distribution (ie Ubuntu), then you need to use the IP address of your host machine. While this is not a common scenario, you can follow these steps to make it work.
    - Obtain the IP address of your host machine by running this command from your Linux distribution: `cat /etc/resolv.conf`
    - Copy the IP address following the term: `nameserver`.
    - Connect to any Windows server using the copied IP address.

The picture below shows an example of this by connecting to a Node.js server running in Windows via curl.

![Connect to NodeJS server in Windows via Curl](media/wsl2-network-l2w.png)

### Additional networking considerations

#### Connecting via remote IP addresses

When using remote IP addresses to connect to your applications, they will be treated as connections from the Local Area Network (LAN). This means that you will need to make sure your application can accept LAN connections.

For example, you may need to bind your application to `0.0.0.0` instead of `127.0.0.1`. In the example of a Python app using Flask, this can be done with the command: `app.run(host='0.0.0.0')`. Please keep security in mind when making these changes as this will allow connections from your LAN.

#### Accessing a WSL 2 distribution from your local area network (LAN)

When using a WSL 1 distribution, if your computer was set up to be accessed by your LAN, then applications run in WSL could be accessed on your LAN as well.

This isn't the default case in WSL 2. WSL 2 has a virtualized ethernet adapter with its own unique IP address. Currently, to enable this workflow you will need to go through the same steps as you would for a regular virtual machine. (We are looking into ways to improve this experience.)

Here's an example PowerShell command to add a port proxy that listens on port 4000 on the host and connects it to port 4000 to the WSL 2 VM with IP address 192.168.101.100.

```powershell
netsh interface portproxy add v4tov4 listenport=4000 listenaddress=0.0.0.0 connectport=4000 connectaddress=192.168.101.100
```

#### IPv6 access

WSL 2 distributions currently cannot reach IPv6-only addresses. We are working on adding this feature.

## Expanding the size of your WSL 2 Virtual Hardware Disk

WSL 2 uses a Virtual Hardware Disk (VHD) to store your Linux files. If you reach its max size you may need to expand it.

The WSL 2 VHD uses the ext4 file system. This VHD automatically resizes to meet your storage needs and has an initial maximum size of 256GB. If your distribution grows in size to be greater than 256GB, you will see errors stating that you've run out of disk space. You can fix this error by expanding the VHD size.

To expand your maximum VHD size beyond 256GB:

1. Terminate all WSL instances using the command: `wsl --shutdown`

2. Find your distribution installation package name ('PackageFamilyName')
    - Using PowerShell (where 'distro' is your distribution name) enter the command:
    - `Get-AppxPackage -Name "*<distro>*" | Select PackageFamilyName`

3. Locate the VHD file `fullpath` used by your WSL 2 installation, this will be your `pathToVHD`:
     - `%LOCALAPPDATA%\Packages\<PackageFamilyName>\LocalState\<disk>.vhdx`

4. Resize your WSL 2 VHD by completing the following commands:
   - Open Windows Command Prompt with admin privileges and enter:
      - `diskpart`
      - `Select vdisk file="<pathToVHD>"`
      - `expand vdisk maximum="<sizeInMegaBytes>"`

5. Launch your WSL distribution (Ubuntu, for example).

6. Make WSL aware that it can expand its file system's size by running these commands from your Linux distribution command line:
    - `sudo mount -t devtmpfs none /dev`
    - `mount | grep ext4`
    - Copy the name of this entry, which will look like: `/dev/sdXX` (with the X representing any other character)
    - `sudo resize2fs /dev/sdXX`
    - Use the value you copied earlier. You may also need to install resize2fs: `apt install resize2fs`

> [!NOTE]
> In general do not modify, move, or access the WSL related files located inside of your AppData folder using Windows tools or editors. Doing so could cause your Linux distribution to become corrupted.
