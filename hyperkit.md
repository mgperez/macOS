hyperkit



Uninstall Hipervisor

```
$ brew uninstall docker-machine-driver-hyperkit


$ brew uninstall hyperkit
rm '/usr/local/bin/hyperkit'
brew link --overwrite hyperkit
brew link --overwrite --dry-run hyperkit
brew unlink hyperkit && brew link hyperkit
```

## Install docker-machine-driver-hyperkit

```
brew update
brew install hyperkit
brew install docker-machine-driver-hyperkit

sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-hyperkit/bin/docker-machine-driver-hyperkit
sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-hyperkit/bin/docker-machine-driver-hyp

$ brew list | grep hyper
```