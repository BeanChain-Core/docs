# BeanChain: Launching a BeanNode (Early Access Guide)

## Step 1: Install Required Tools

Make sure the following tools are installed:

- Java 21 (OpenJDK)
- Apache Maven
- Git

**Download Links:**

- [Java 21](https://jdk.java.net/21/)
- [Apache Maven](https://maven.apache.org/install.html)
- [Git](https://git-scm.com/downloads)

**Need help installing?**

- [Chocolatey for Windows](https://chocolatey.org/install)
- [Homebrew for macOS](https://brew.sh) (then run: `brew install openjdk@21 maven git`)
- Linux: Use your distro's package manager (e.g. `apt`, `dnf`, `pacman`)

**Verify installation:**

```bash
java -version
mvn -version
git --version
```

---

## Step 2: Configure Maven to Access bean-pack

To access the `bean-pack` dependency hosted on GitHub Packages, you must create a GitHub personal access token (even though the repo is public).

1. Go to: [GitHub Token Settings](https://github.com/settings/tokens)
2. Generate a token with:
   - **Note:** BeanPack Access Token
   - **Expiration:** 90+ days
   - **Scopes:** `read:packages` (optionally `repo`)
3. Save your token in:

- Windows: `C:\Users\YourUsername\.m2\settings.xml`
- macOS/Linux: `~/.m2/settings.xml`

**Add the following content:**

```xml
<servers>
  <server>
    <id>github</id>
    <username>GITHUB_USERNAME</username>
    <password>YOUR_GENERATED_TOKEN</password>
  </server>
</servers>
```

---

## Step 2.5: Clone the BeanNode Repository

You can clone the BeanNode repo at any time â no token is required:

```bash
git clone https://github.com/beanchain-core/beannode.git
cd beannode
```

> The repository is public, so GitHub will not prompt for a token during cloning.  
> The token is only needed when Maven fetches the `bean-pack` dependency during `mvn clean install`.

---

## Step 3: Generate Your Wiz Key

From the root of the repo:

```bash
java -jar wiz-suite-v0.jar
```

Youll see:
1. Generate new Wiz Key
2. Exit

After key generation:

- Type `DISPLAY` to view your private key
- Type `WIZ` to save the wizkey
- Type `EXIT` to close the tool

> The Wiz Key is a secure format that wraps your private key in a longer string.  
> Encrypted password-protected support is coming soon.

---

## Step 4: Configure Your Node

Edit:

```
config.docs/beanchain.config.properties
```

> Do **not** move or rename this file.

Update only:

```properties
networkport=6442    # Port your node listens on for network sync (forward this if possible)
is.public=true      # true = exposes public API (requires port forwarding 8080), false = private/headless
privateKeyPath=./config.docs/wiz.txt (THIS IS THE RELATIVE PATH TO WIZ KEY, may need to change to the full path to your file on certain VM's or systems)
```

---

## Step 5: Build and Launch the Node

From the root of the repo:

```bash
mvn clean install
```

This will create:

```
target/BeanNode-v0.0.2.jar
```

### Option 1: Copy to a new folder

```
MyNode/
 BeanNode-v0.0.2.jar
 config.docs/
```

### Option 2: Move JAR to the root of the repo

```bash
mv target/BeanNode-v0.0.2.jar .
```

### Launch your node:

```bash
java -jar BeanNode-v0.0.2.jar
```

Once running:

- Type `devmode` to watch sync logs
- Type `help` to see available CLI commands
