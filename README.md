# Example VIB Firewall Rule

## Setup
Docker is used because the `vibauthor` fling from VMware is no longer available on the fling site. [William Lam](https://www.virtuallyghetto.com/) 
has built a [Docker Container](https://hub.docker.com/r/lamw/vibauthor/) we can use to simplify the process.

```bash
    docker pull lamw/vibauthor
    docker run --rm -it lamw/vibauthor
```

## Building

From indside the docker container
```bash
    git clone git@github.com:michaelrice/esxi-firewall-vib.git
    cd esxi-firewall-vib
    vibauthor -C -t stage drpcli.vib -f
```

## Installing

Copy the new vibfile to an esxi host and place it on a Datastore.

```bash
    scp DRP-Firewall-Rule-5.0.0-0.0.1.vib root@esxi-myhost.com:.
    ssh root@esxi-myhost.com
    mv DRP-Firewall-Rule-5.0.0-0.0.1.vib /vmfs/volumes/datastore1/
    esxcli software vib install -v /vmfs/volumes/datastore1/DRP-Firewall-Rule-5.0.0-0.0.1.vib -f
```


