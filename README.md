# Kubeflow-installation-on-windows-10/11
> **Kubeflow installation on windows 10/11**

Official Kubeflow : https://github.com/kubeflow/kubeflow

## Section 1 : Installation of Choco on Windows 10 or Windows 11

---

**Video References**

<iframe width="768" height="400" src="https://www.youtube.com/embed/-5WLKu_J_AE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### **Step 1: Installing the Chocolatey Package manager for Windows**

---

![](D:\newgithub\Kubeflow-installation-on-windows-10\Images\step1_1.jpg)

#### Step-2 Paste the following command into Powershell and press enter.

----

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
  iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

> **OR**

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

> **Answer Yes when prompted**

![](D:\newgithub\Kubeflow-installation-on-windows-10\Images\step1_2.jpg)

> **Close and reopen an elevated PowerShell window to start using `choco`**

![](D:\newgithub\Kubeflow-installation-on-windows-10\Images\step1_3.jpg)



## Section 2: Hyper-V installation

---

<iframe width="768" height="400" src="https://www.youtube.com/embed/sFr4izuGuPA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

#### Minimum Requirement to install hyper-V

----

- Windows 10 Enterprise, Pro, or Education
- 64-bit Processor with Second Level Address Translation (SLAT).
- CPU support for VM Monitor Mode Extension (VT-c on Intel CPUs).
- Minimum of 4 GB memory.

## Enable Hyper-V using PowerShell

1. Open a PowerShell console as Administrator.
2. Run the following command:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

> If the command couldn't be found, make sure you're running PowerShell as Administrator. 
>
> **When the installation has completed, reboot.**

## Enable Hyper-V with CMD and DISM

The Deployment Image Servicing and Management tool (DISM) helps configure Windows and Windows images. Among its many applications, DISM can enable Windows features while the operating system is running.

To enable the Hyper-V role using DISM:

1. Open up a PowerShell or CMD session as Administrator.
2. Type the following command:

```powershell
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
```

![](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/media/dism_upd.png)

## Enable the Hyper-V role through Settings

1. Right click on the Windows button and select ‘Apps and Features’.
2. Select **Programs and Features** on the right under related settings.
3. Select **Turn Windows Features on or off**.
4. Select **Hyper-V** and click **OK**.

![](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/media/enable_role_upd.png)

***Note : When the installation has completed you are prompted to restart your computer.***

---

### Note : Section-1 and Section-2 are prerequisite

---

## Section-3 : Installation of MiniKube and Kubectl

---

<iframe width="768" height="400" src="https://www.youtube.com/embed/B9hyHW2HK9M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

