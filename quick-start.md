---
description: Installation of the app
---

# 👊 Quick start

## How to download and install The MEDiml Application

Below are tutorials for downloading and installing the app on various operating systems.

{% hint style="warning" %}
These tutorials are currently outdated and will be updated soon. In the meantime, please follow the instructions below.
{% endhint %}

{% tabs %}
{% tab title="Windows" %}
{% embed url="https://youtu.be/i6w9op4iNk8" %}
{% endtab %}

{% tab title="Ubuntu" %}
{% embed url="https://youtu.be/p4oq58PLA28" %}
{% endtab %}

{% tab title="MacOS" %}
{% hint style="warning" %}
This tutorial is for MEDomics (the parent app) and will be updated soon, but the instructions remain the same. However, please use the following link to download the assets for the MEDiml-app: [MEDiml-app release](https://github.com/MEDomics-UdeS/MEDimage-app/releases/tag/v0.0.1).
{% endhint %}

{% embed url="https://www.youtube.com/watch?ab_channel=MEDomicsLab&v=J9wq_C6PHK0" %}
{% endtab %}
{% endtabs %}

### The MEDiml application architecture <a href="#the-medomics-platform-architecture" id="the-medomics-platform-architecture"></a>

MEDiml follows the same architechture of its [mother application](https://medomics.app/). [This visual guide](https://medomicslab.gitbook.io/medomics-docs/contributing#the-medomics-platform-architecture) is designed to support new contributors in understanding the application’s structure, streamlining the integration of new features, and aiding efficient navigation through the codebase.

### Contribute to MEDiml-App🌱 <a href="#contribute-to-medomics" id="contribute-to-medomics"></a>

#### 1. Prerequisites <a href="#id-1.-prerequisites" id="id-1.-prerequisites"></a>

**1.1 Installation of MongoDB Community Edition**

{% tabs %}
{% tab title="Windows" %}
[Install MongoDB on Windows](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-windows/#install-mongodb-community-edition)

* Do not install MongoDB as a service.
* You do not have to install MongoDB Compass.
* You do not have to install mongosh.
* Do not forget to [add MongoDB binaries to the System PATH](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-windows/#add-mongodb-binaries-to-the-system-path).
{% endtab %}

{% tab title="Linux" %}
[Install MongoDB on Linux (Ubuntu)](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb-community-edition) - Install the latest version of MongoDB.
{% endtab %}

{% tab title="MacOS" %}
[Install MongoDB Database Tools on Mac](https://www.mongodb.com/docs/database-tools/installation/installation-macos/#installation) - Install with Homebrew.
{% endtab %}
{% endtabs %}

**1.2 Installation of MongoDB database tools**

{% tabs %}
{% tab title="Windows" %}
Install with the [MSI](https://www.mongodb.com/docs/database-tools/installation/?operating-system=windows\&package-type=msi) Installer.
{% endtab %}

{% tab title="Linux" %}
Install with the [DEB ](https://www.mongodb.com/docs/database-tools/installation/?operating-system=linux\&package-type=deb)package.
{% endtab %}

{% tab title="MacOS" %}
Install with [Homebrew](https://www.mongodb.com/docs/database-tools/installation/?operating-system=macos\&package-type=homebrew).
{% endtab %}
{% endtabs %}

#### 2. Node.js and NVM Setup <a href="#id-2.-node.js-and-nvm-setup" id="id-2.-node.js-and-nvm-setup"></a>

**2.1 Installation of Nvm**

* [NVM for Windows](https://github.com/coreybutler/nvm-windows)
* [NVM for Ubuntu/MacOS](https://github.com/nvm-sh/nvm#installing-and-updating)

**2.2 Installation of npm/node.js**

```bash
nvm install lts
nvm use lts
```

***

{% hint style="warning" %}
Be careful, the next steps are different depending on the user's privilege.
{% endhint %}

***

<details>

<summary>For members of the <a href="https://github.com/MEDomicsLab">MEDomicsLab GitHub Organization</a>.</summary>

#### 3. Clone the Repository <a href="#id-3.-clone-the-repository" id="id-3.-clone-the-repository"></a>

Using HTTPS:

```zsh
git clone -b develop https://github.com/MEDomicsLab/MEDiml-app.git
```

Using SSH:

```zsh
git clone -b develop git@github.com:MEDomicsLab/MEDiml-app.git
```

#### 4. Backend Setup (Go) <a href="#id-4.-backend-setup-go" id="id-4.-backend-setup-go"></a>

**4.1 Install Go**

1. Download the latest stable release of Go from the official website: [https://golang.org/dl/](https://golang.org/dl/)
2. Follow the [installation instructions](https://go.dev/doc/install) for your operating system.

**4.2 Setup of environment**

Execute these commands in the terminal:

_**Windows:**_

```bash
setx GOPATH %USERPROFILE%\go
setx PATH "%PATH%;C:\Go\bin"
```

_**Linux/MacOS:**_

```bash
echo 'export PATH=$PATH:/usr/local/go/bin' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOPATH/bin' >> $HOME/.bashrc
```

After, **close all your terminals** because these commands will take effect on the initialization of any terminal

**4.3 Verify installation**

In a new terminal, run:

```bash
go version
```

If Go is installed correctly, you should see the version number printed to the console.

**4.4 Setup for the application**

```bash
cd <repo-path>/go_server
go run main.go   # initial run installs dependencies
```

Next, build the executable:

```bash
go build main.go
```

{% hint style="warning" %}
Rebuild after any `.go` file modification.
{% endhint %}

#### 5. Create Your Own Branch <a href="#id-6.-create-your-own-branch" id="id-6.-create-your-own-branch"></a>

Always branch from `develop`, and ensure you have the latest changes:

```zsh
git checkout develop
git pull origin develop
git checkout -b your-branch-name
# push your branch to MEDiml-app repository
git push --set-upstream origin your-branch-name
```

#### 6. Make Changes <a href="#id-7.-make-changes" id="id-7.-make-changes"></a>

* Follow the project structure
* Keep commits **small and descriptive**

```zsh
git add .
git commit -m "feat: add new feature X"
```

Commit naming conventions:

* `feat:` new feature
* `fix:` bug fix
* `docs:` documentation changes
* `refactor:` code restructuring
* `test:` tests added/updated

***

#### 7. Push Changes <a href="#id-9.-push-changes" id="id-9.-push-changes"></a>

```zsh
git push
```

***

#### 8. Create a Pull Request <a href="#id-10.-create-a-pull-request" id="id-10.-create-a-pull-request"></a>

1. Go to the MEDiml-app GitHub [Pull Requests page](https://github.com/MEDomicsLab/MEDiml-app/pulls)
2. Click **New Pull Request**
3. Target branch: `develop`
4. Compare branch: `your-branch-name`

***

#### 9. Pull Request Guidelines <a href="#id-11.-pull-request-guidelines" id="id-11.-pull-request-guidelines"></a>

Ensure:

* ✅ Code compiles and runs
* ✅ No console errors
* ✅ Proper formatting
* ✅ Tests pass (if applicable)
* ✅ Clear PR description:
  * What was done
  * Why was it done
  * Screenshots (if UI changes)

***

#### 10. Code Review Process <a href="#id-12.-code-review-process" id="id-12.-code-review-process"></a>

* Address reviewer comments
* Push updates to the same branch
* Keep discussion professional and concise

#### 11. After Merge <a href="#id-13.-after-merge" id="id-13.-after-merge"></a>

```zsh
git checkout develop
git pull
git branch -d feature/your-feature-name # Time for a new feature
```

</details>

<details>

<summary>For external users</summary>

#### 🌱 Contributing via Fork (Common Practice) <a href="#contributing-via-fork-common-practice" id="contributing-via-fork-common-practice"></a>

This workflow is recommended for external contributors.

***

#### 3. Fork the Repository <a href="#id-3.-fork-the-repository" id="id-3.-fork-the-repository"></a>

1. Go to the official repo
2. Click **Fork**
3. Clone your fork:

```zsh
git clone https://github.com/<your-username>/MEDimage-app.git
cd MEDimage-app
```

***

#### 4. Add Upstream Remote <a href="#id-4.-add-upstream-remote" id="id-4.-add-upstream-remote"></a>

```zsh
git remote add upstream https://github.com/MEDomicsLab/MEDimage-app.git
```

Verify:

```zsh
git remote -v
```

***

#### 5. Create a Feature Branch <a href="#id-5.-create-a-feature-branch" id="id-5.-create-a-feature-branch"></a>

Always branch from `develop`:

```zsh
git fetch upstream
git checkout develop
git pull upstream develop

git checkout -b feature/your-feature-name
```

***

#### 6. Backend Setup (Go) <a href="#id-6.-backend-setup-go" id="id-6.-backend-setup-go"></a>

**6.1 Install Go**

1. Download the latest stable release of Go from the official website: [https://golang.org/dl/](https://golang.org/dl/)
2. Follow the [installation instructions](https://go.dev/doc/install) for your operating system.

**6.2 Setup of environment**

Execute these commands in the terminal:

_**Windows**_

```zsh
setx GOPATH %USERPROFILE%\go
setx PATH "%PATH%;C:\Go\bin"
```

_**Linux/MacOS**_

```zsh
echo 'export PATH=$PATH:/usr/local/go/bin' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOPATH/bin' >> $HOME/.bashrc
```

After, **close all your terminals** because these commands will take effect on the initialization of any terminal

**6.3 Verify installation**

In a new terminal, run:

```zsh
go version
```

If Go is installed correctly, you should see the version number printed to the console.

**6.4 Setup for the application**

```zsh
cd <repo-path>/go_server
go run main.go   # initial run installs dependencies
```

Next, build the executable:

```zsh
go build main.go
```

{% hint style="warning" %}
Rebuild after any `.go` file modification.
{% endhint %}

***

#### 7. Make Changes <a href="#id-7.-make-changes-1" id="id-7.-make-changes-1"></a>

* Follow the project structure
* Keep commits **small and descriptive**

```zsh
git add .
git commit -m "feat: add new feature X"
```

Commit naming conventions:

* `feat:` new feature
* `fix:` bug fix
* `docs:` documentation changes
* `refactor:` code restructuring
* `test:` tests added/updated

***

#### 8. Sync with Upstream <a href="#id-8.-sync-with-upstream" id="id-8.-sync-with-upstream"></a>

Before pushing:

```zsh
git fetch upstream
git rebase upstream/develop
```

***

#### 9. Push Changes <a href="#id-9.-push-changes-1" id="id-9.-push-changes-1"></a>

```zsh
git push origin feature/your-feature-name
```

***

#### 10. Create a Pull Request <a href="#id-10.-create-a-pull-request-1" id="id-10.-create-a-pull-request-1"></a>

1. Go to your fork on GitHub
2. Click **Compare & Pull Request**
3. Target branch: `develop` (base repo)

***

#### 11. Pull Request Guidelines <a href="#id-11.-pull-request-guidelines-1" id="id-11.-pull-request-guidelines-1"></a>

Ensure:

* ✅ Code compiles and runs
* ✅ No console errors
* ✅ Proper formatting
* ✅ Tests pass (if applicable)
* ✅ Clear PR description:
  * What was done
  * Why was it done
  * Screenshots (if UI changes)

***

#### 12. Code Review Process <a href="#id-12.-code-review-process-1" id="id-12.-code-review-process-1"></a>

* Address reviewer comments
* Push updates to the same branch
* Keep discussion professional and concise

***

#### 13. After Merge <a href="#id-13.-after-merge-1" id="id-13.-after-merge-1"></a>

```zsh
git checkout develop
git pull upstream develop
git branch -d feature/your-feature-name
```

</details>

***

#### Running the Electron App <a href="#run-the-electron-app" id="run-the-electron-app"></a>

Launch the Electron application (desktop app window) and start the required development servers (frontend/backend):

```shellscript
cd <repo_path/MEDiml-app>
npm install
npm run dev
```

#### Worth noting

{% hint style="warning" %}
On **Windows**, if you encounter error messages when running `npm install`related to tensorflow .dll files missing, revert your node version by following these steps:

* [Download node v18.16.1](https://nodejs.org/fr/blog/release/v18.16.1)
* Add to the PATH variable the path to your new node placing it higher than the old node.
* Test your node version using: `node --version`
{% endhint %}

{% hint style="info" %}
**MongoDB configuration**

MEDiml-app uses **port 54017** as the default MongoDB connection port. For database visualization and management, we recommend using [MongoDB Compass](https://www.mongodb.com/products/compass), the official GUI client from MongoDB.

**Key Details**:

* Default Port: `54017`
* Recommended Client: MongoDB Compass
* Connection String Format: `mongodb://localhost:54017/`
{% endhint %}

{% hint style="info" %}
**Modify startup settings**

1. Go to file `medomics.dev.js`
2. Here is a description of the Object:

<pre class="language-javascript"><code class="lang-javascript"><strong>export const PORT_FINDING_METHOD = {
</strong>  FIX: 0,
  AVAILABLE: 1
};

const config = {
  // Automatically starts the backend server when the app launches
  runServerAutomatically: true,

  // Enables React Developer Tools (useful for debugging UI)
  useReactDevTools: false,

  // Default port used by the Electron/Go server
  defaultPort: 54288,

  // MongoDB connection port
  mongoPort: 54017,

  // Port allocation strategy:
  // FIX        -> Forces use of defaultPort (terminates conflicting processes if needed)
  // AVAILABLE  -> Finds the next available port if defaultPort is occupied
  portFindingMethod: PORT_FINDING_METHOD.FIX
};

export default config;
</code></pre>
{% endhint %}

### Testing Production Builds <a href="#testing-production-builds" id="testing-production-builds"></a>

#### Build & Run <a href="#build-and-run" id="build-and-run"></a>

This compiles the application code and packages the Electron app into an executable format:

{% tabs %}
{% tab title="Windows" %}
```bash
npm run build:win                            # build and package the application 
.\build\dist\win-unpacked\MEDiml-app.exe    # Run the executable of the built version
```
{% endtab %}

{% tab title="Linux" %}
```bash
npm run build:linux                    # build and package the application 
bash build/dist/linux-unpacked/mediml-app  # Run the executable of the built version
```
{% endtab %}

{% tab title="MacOS" %}
```bash
npm run build:mac                                                    # build and package the application 
bash build/dist/mac-arm64/MEDomicsLab.app/Contents/MacOS/mediml-app  # Run the executable of the built version     
```
{% endtab %}
{% endtabs %}

The built app will be located in the `build/dist` folder.

**Now that the app is live and running, it is time to learn how to use the interface. See you on the next page.** :wink:
