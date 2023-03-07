# Bicol ICP Workshop

## Prerequisites
* Fundamental programming knowledge
* Knows basic Git syntaxes

## Tools
* [Node](https://nodejs.org/en/) (LTS / Long Term Support version)
* [Git](https://git-scm.com/download) (also have a [GitHub](https://github.com/) account)
* [DFX](https://github.com/dfinity/sdk) (further installation process under [Setup](#setup))
* Text editor (any of your preference, e.g. [VSCode](https://code.visualstudio.com/download), [Sublime Text 3](https://www.sublimetext.com/3), etc.)

## Setup

### MacOS

#### Steps

**DFX Installation**
1. Install LTS version of [Node](https://nodejs.org/en/), and the latest version of [Git](https://git-scm.com/download/mac) in your environment.
2. Open your Terminal app.
3. Quick version check of Node and Git to see if it's running on your environment. Copy-paste and enter the following commands, one-by-one:
	```
	node --version
	```
	```
	git --version
	```
4. Install DFX on your MacOS. Copy-paste and run this command:
	```
	DFX_VERSION=0.12.1 sh -ci "$(curl -fsSL https://sfk.dfinity.org/install.sh)"
	```
5. Upon successful installation of DFX, quick version check by copying the command below, paste it on your terminal, and press enter.
	```
	dfx --version
	```

### Windows

#### Requirements
* Windows 10 or higher (version 2004 above). Build 19041.xxxx or higher.
* 64-bit machine (System type x64 based PC)

#### Steps

**WSL Installation**. Technically DFX only supports Linux and Mac OS. But you can still run it on Windows through WSL (Windows Substack for Linux). And the recommended version for supporting DFX is WSL 2. If you already have WSL 2, skip this part. If you have WSL 1, upgrade it to 2 by starting at step #2.
1. Open _Windows PowerShell_ as Administrator (Start menu > Windows PowerShell > right-click > Run as Administrator), copy-paste, and enter this command:
	```
	dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
	```
2. Step 1 initially installed WSL 1. Let's upgrade it to WSL 2 by first enabling virtual machine feature. Copy-paste and enter this command:
	```
	dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
	```
3. Then download the Linux kernel update package [wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi).
4. Set the default version to WSL 2. Copy-paste and run this command:
	```
	wsl --set-default-version 2
	```
5. Install your preferred Linux distribution (in my case, and for this example, Ubuntu). Copy-paste and run this command:
	```
	wsl --install -d ubuntu
	```
6. After installation, a new window will appear for initially setting up your Linux environment by setting your username and password.

**Node Installation**. Even if you have existing Node on your Windows, you still need to manually install it on yout Linux environment.

1. Open your Linux environment. Search and open it up from the Start menu (e.g. Ubuntu).
2. Install Homebrew. Copy-paste and run this command:
	```
	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
	```
3. Upon successful installation of Homebrew, add it to path by running the two commands one-by-one and sequentially. Take note of _YOUR_LINUX_USERNAME_.
	```
	echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/YOUR_LINUX_USERNAME/.profile
	```
	```
	eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
	```
4. Install Homebrew's dependenvies via sudo. Copy-paste and run this command:
	```
	sudo apt get install build-essential
	```
5. Quick version check to see if your Homebrew works. Copy-paste and run this command:
	```
	brew --version
	```
6. Now finally, install Node. We're going to utilize the LTS version 16. Copy-paste and run this command:
	```
	brew install node@16
	```
7. Upon successful installation, you'll notice a caveat showing _node@16 is keg-only_. This is because you have another Node installed on your computer outside the Linux environment. All you need to do is copy-paste and run this command:
	```
	brew link node@16
	```
8. Now to see if Node works on your Linux environment, copy-paste and run this command:
	```
	node --version
	```

**DFX Installation**
1. Open your Linux environment.
2. Install DFX on your Linux environment. Copy-paste and run this command:
	```
	DFX_VERSION=0.12.1 sh -ci "$(curl -fsSL https://sfk.dfinity.org/install.sh)"
	```
3. Upon successful installation of DFX, quick version check by copying the command below, paste it on your terminal, and press enter.
	```
	dfx --version
	```

## Workshop Proper

1. Create a new project using the `dfx create` command in your terminal:

```
dfx new my_dapp
cd my_dapp
```
This will create a new project directory named my_dapp and initialize it with a basic set of files and directories.

2. Navigate to `main.mo` file inside `src/my_dapp_backend/` and you will see the generated `main.mo` file. This will be the entry point for your DApp.
	```
	actor {
		public query func greet(name : Text) : async Text {
			return "Hello, " # name # "!";
		}; 
	}; 
	```
This code defines a simple `greet` function that returns a greeting.

3. Start the execution environment by running this command in terminal A.
	```
	dfx start
	```
4. `index.html` and `index.js` is also generated by `dfx new my_dapp` command. These files can be found inside the `src/my_dapp_frontend/src/`.

5. Install the dependencies included in this generated project files by running.
	```
	npm install
	```
6. Deploy your DApp to the local development server for the ICP by running the following command in your terminal B:
	```
	dfx deploy
	```
7. To test the dapp locally via the browser, run
	```
	npm start
	```
8. Open your DApp in your web browser by navigating to `http://localhost:8080`.
If everything is set up correctly, you should see the greeting "Enter your name, _____, click me." displayed on your page.

Congratulations! You've built a simple DApp in ICP using Motoko. From here, you can experiment with building more complex applications and exploring the many features of the ICP.
