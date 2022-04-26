

Brave is only supported on 64-bit AMD/Intel architectures (amd64 / x86_64).

The current signing keys are also available from https://brave.com/signing-keys/.

## Release Channel Installation 

### Debian 9+, Ubuntu 16.04+ and Mint 18+ 

If you get `gnutls_handshake()` errors after adding the Brave repository on Debian 9, you may need to [uninstall old conflicting packages](https://github.com/signalapp/Signal-Desktop/issues/2483#issuecomment-401047201).

~~~ sh
sudo apt install apt-transport-https curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser
~~~

### Fedora 28+, CentOS/RHEL 8+

~~~ sh
sudo dnf install dnf-plugins-core

sudo dnf config-manager --add-repo https://brave-browser-rpm-release.s3.brave.com/x86_64/

sudo rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc

sudo dnf install brave-browser
~~~

### OpenSUSE 15+

~~~ sh
sudo zypper install curl

sudo rpm --import https://brave-browser-rpm-release.s3.brave.com/brave-core.asc

sudo zypper addrepo https://brave-browser-rpm-release.s3.brave.com/x86_64/ brave-browser

sudo zypper install brave-browser
~~~

### Snap

You can find [Brave in the Snapcraft Store](https://snapcraft.io/brave), but while it is maintained by Brave Software, it is [not yet working as well](https://github.com/brave/brave-browser/issues?q=is%3Aissue+is%3Aopen+snap+label%3AOS%2FLinux%2Fsnap) as our official packages. We currently recommend that users who are able to use our official package repositories do so instead of using the Snap.









