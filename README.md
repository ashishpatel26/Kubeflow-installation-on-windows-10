# Kubeflow-installation-on-windows-10/11
> **Kubeflow installation on windows 10/11**

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/logo.jpg)

Official Kubeflow : https://github.com/kubeflow/kubeflow

## Section 0: **Docker Installation**

Install docker on windows11.

1. Install **wsl2** : [installation video](https://www.youtube.com/watch?v=n-J9438Mv-s&ab_channel=Pureinfotech) .

2. Open command prompt with “**Run as administrator**”.

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/clip_image002.jpg)

3.  Type command: wsl –install -d Ubuntu

​		**YouTube**: [https://www.youtube.com/watch?v=ysRfLJCBo_M&ab_channel=Sonoo%27sKB](https://www.youtube.com/watch?v=ysRfLJCBo_M&ab_channel=Sonoo'sKB)

 

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/clip_image004.jpg)

Then restart your PC.

4. Download Docker from the below link.

https://docs.docker.com/desktop/windows/wsl/

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/clip_image006.jpg)

5. Setup the docker step by step

YouTube: [https://www.youtube.com/watch?v=BMBwyadxokc&t=55s&ab_channel=Sonoo%27sKB](https://www.youtube.com/watch?v=BMBwyadxokc&t=55s&ab_channel=Sonoo'sKB)

 #### **Docker file Run:**

---

1. **Run the Docker** 

Docker run -p 8000:8000 money_api_new:1.0



## Section 1 : Installation of Choco on Windows 10 or Windows 11

---

**Video References**

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/-5WLKu_J_AE/maxresdefault.jpg)](https://www.youtube.com/watch?v=-5WLKu_J_AE)

#### **Step 1: Installing the Chocolatey Package manager for Windows**

---

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/step1_1.jpg)

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

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/step1_2.jpg

> **Close and reopen an elevated PowerShell window to start using `choco`**

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/step1_3.jpg)



## Section 2: Hyper-V installation

---

**Video:**

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/sFr4izuGuPA/maxresdefault.jpg)](https://www.youtube.com/watch?v=sFr4izuGuPA)

#### Minimum Requirement to install hyper-V

----

- Windows 10 Enterprise, Pro, or Education
- 64-bit Processor with Second Level Address Translation (SLAT).
- CPU support for VM Monitor Mode Extension (VT-c on Intel CPUs).
- Minimum of 4 GB memory.

**Trick setup :** 

```bash
pushd "%~dp0"
dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hv.txt
for /f %%i in ('findstr /i . hv.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
del hv.txt
Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
pause
```

Save above code save as with name `hv.bat`.

and click on Run as Administrator

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/hv.jpg)

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
**Video :** 

[![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/Section3_step1.png)](https://www.youtube.com/watch?v=B9hyHW2HK9M)



#### **Step : 1**: Type `Choco install minikube` on powershell with run as administrator mode

---

```powershell
choco install minikube
choco install kubectl
```



![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/Section3_step2.jpg)

#### **Step : 2**: Type `Choco install kubectl` on powershell with run as administrator mode

---

![](https://raw.githubusercontent.com/ashishpatel26/Kubeflow-installation-on-windows-10/main/Images/Section3_step3.jpg)

## Section-4 : Change setting in Hyper-V

---

**Step 1: Open the Hyper-V Manager.**

![](https://miro.medium.com/max/720/1*BDkfXerXSUMttd2IU0VL9g.png)

**Step 2: Once in the Hyper-V Manager, on the right panel, select the Virtual Switch Manager.**

![](https://miro.medium.com/max/898/1*FVb8sfWZMlXrT9i0Xtbb_g.png)

**Step 3: Next we will create a virtual switch for minikube. Select `New virtual network switch` on the right hand side, select `External` for the network type, and then press the `Create Virtual Switch button.`**

![](https://miro.medium.com/max/1330/1*xwFelgX0H_c91tBknDu-_w.png)

**Step 4: Name the switch `Primary Virtual Switch` and click the apply button.**

![](https://miro.medium.com/max/1400/1*71ynSa77g4npuQXHJvPNrw.png)

**Step 5 : Once you have the switch created we are now ready to start minikube. Run the following command to start the minikube VM with our applied changes.**

```powershell
minikube start --vm-driver hyperv --hyperv-virtual-switch "Primary Virtual Switch"
```

![](https://miro.medium.com/max/1400/1*3MuYyS4meXm59O_0xwgfFA.png)

In your administrator command line window stop the minikube VM with the following command.

```powershell
minikube stop
```

**Step  6 : Once minikube has stopped, open the Hyper-V Manager again and right click on the minikube VM and select settings.**

![img](https://miro.medium.com/max/964/1*g4btrIldO_U0WNNDmTs-fg.png)

**Step 7: Select the `Memory` option on the left panel, then de-select `Enable Dynamic Memory`, and then click `Apply` button.**

![](https://miro.medium.com/max/1254/1*2oOZj3kxuZXEEJBo99HsVg.png)

**Step 9: Close Hyper-V manager and then return to the administrator command line window and restart minikube.**

```powershell
minikube start
```

Once minikube is restarted you should be ready to go. We will confirm the installation is ready by checking a couple of things.

**Step 10: Check kubectl**

```powershell
kubectl get pods -n kube-system
```

![](https://miro.medium.com/max/1400/1*LfRnLyiuMWO1DfhuQzsAVg.png)

If you are a little more visual and want to see the kubernetes dashboard, you can open that up by typing in the following command in the command line window.

**Step 11: Open Kubernets Cluster in Chrome Browser type below command.**

```powershell
minikube dashboard
```

![](https://miro.medium.com/max/1400/1*F3C6rW8T177KeKJRVH_NFA.png)

Now you are ready to explore and start your journey to learning Kubernetes.
