# I. Init

## sudo c pa bo

🌞 **Ajouter votre utilisateur au groupe `docker`**

```
[user@localhost ~]$ sudo usermod -aG docker user
[sudo] password for user:
```
```
[user@localhost ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
🌞 **Lancer un conteneur NGINX**
```
[user@localhost ~]$ docker run -d -p 9999:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
af107e978371: Pull complete
336ba1f05c3e: Pull complete
8c37d2ff6efa: Pull complete
51d6357098de: Pull complete
782f1ecce57d: Pull complete
5e99d351b073: Pull complete
7b73345df136: Pull complete
Digest: sha256:2bdc49f2f8ae8d8dc50ed00f2ee56d00385c6f8bc8a8b320d0a294d9e3b49026
Status: Downloaded newer image for nginx:latest
b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522
```

🌞 **Visitons**

- vérifier que le conteneur est actif avec une commande qui liste les conteneurs en cours de fonctionnement

```
[user@localhost ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                   NAMES
b040115b466f   nginx     "/docker-entrypoint.…"   9 minutes ago   Up 9 minutes   0.0.0.0:9999->80/tcp, :::9999->80/tcp   tender_kapitsa
```

- afficher les logs du conteneur
```
[user@localhost ~]$ docker logs b04
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/12/22 14:22:07 [notice] 1#1: using the "epoll" event method
2023/12/22 14:22:07 [notice] 1#1: nginx/1.25.3
2023/12/22 14:22:07 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14)
2023/12/22 14:22:07 [notice] 1#1: OS: Linux 5.14.0-284.25.1.el9_2.x86_64
2023/12/22 14:22:07 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1073741816:1073741816
2023/12/22 14:22:07 [notice] 1#1: start worker processes
2023/12/22 14:22:07 [notice] 1#1: start worker process 29
2023/12/22 14:22:07 [notice] 1#1: start worker process 30
```

- afficher toutes les informations relatives au conteneur avec une commande `docker inspect`

```
[user@localhost ~]$ docker inspect b04
[
    {
        "Id": "b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522",
        "Created": "2023-12-22T14:22:06.928010598Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 2006,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2023-12-22T14:22:07.573376901Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:d453dd892d9357f3559b967478ae9cbc417b52de66b53142f6c16c8a275486b9",
        "ResolvConfPath": "/var/lib/docker/containers/b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522/hostname",
        "HostsPath": "/var/lib/docker/containers/b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522/hosts",
        "LogPath": "/var/lib/docker/containers/b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522/b040115b466fd240b8f773f8ea03bad2540ab6066ebc21fc83cb3b5e1dfe4522-json.log",
        "Name": "/tender_kapitsa",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {
                "80/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "9999"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                40,
                156
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/565331272a970b498b23442b4f9728eec6e2c7caf9f78d24d53aebf0aef726be-init/diff:/var/lib/docker/overlay2/70aace80bdd82060ceeeb10b422a97d05fe4daf6bc2bfc3c80342c1b1c50fad0/diff:/var/lib/docker/overlay2/89299622dadfdb975425bed9a1c9b81602cb934dfa4abb7fab0bb2685f542abf/diff:/var/lib/docker/overlay2/cf7ebb78dedfaf0b397a80edc652029a0d165fc2d86a3574f4a3e44de57b4f54/diff:/var/lib/docker/overlay2/6da89a9569406d55ece75c67339e82b16af7636d446e08d7948e1443cf1673fa/diff:/var/lib/docker/overlay2/dd8f373541db5078d1c12dc8fd1bb3bad8d7db1c0fbdeb3884f09018b5bb9922/diff:/var/lib/docker/overlay2/9de2eb258179d47e03fca4d2b2de6a3fd113101eb9f5c45d103e6044e63850cf/diff:/var/lib/docker/overlay2/f875425defea83388394fe32ef81a3287fff2f96d05826977e3d11e57def4696/diff",
                "MergedDir": "/var/lib/docker/overlay2/565331272a970b498b23442b4f9728eec6e2c7caf9f78d24d53aebf0aef726be/merged",
                "UpperDir": "/var/lib/docker/overlay2/565331272a970b498b23442b4f9728eec6e2c7caf9f78d24d53aebf0aef726be/diff",
                "WorkDir": "/var/lib/docker/overlay2/565331272a970b498b23442b4f9728eec6e2c7caf9f78d24d53aebf0aef726be/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "b040115b466f",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.25.3",
                "NJS_VERSION=0.8.2",
                "PKG_RELEASE=1~bookworm"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "8c01c788705e63ee535331e5e35c8063bfd40a3158d1cbada3f3d27a24d32ce3",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "9999"
                    },
                    {
                        "HostIp": "::",
                        "HostPort": "9999"
                    }
                ]
            },
            "SandboxKey": "/var/run/docker/netns/8c01c788705e",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "99f3579cbb5eba61c07bf053edfcea7415ec41dff46317d2db97ccd218c58993",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "6ecb89a3582ab83402cfdee0a34f241c4ba1ed4b86780f54a112ab54bfae4910",
                    "EndpointID": "99f3579cbb5eba61c07bf053edfcea7415ec41dff46317d2db97ccd218c58993",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]
```

- afficher le port en écoute sur la VM avec un `sudo ss -lnpt`

```
[user@localhost ~]$ sudo ss -lptn
[sudo] password for user:
State         Recv-Q        Send-Q               Local Address:Port                 Peer Address:Port        Process
LISTEN        0             4096                       0.0.0.0:9999                      0.0.0.0:*            users:(("docker-proxy",pid=1964,fd=4))
LISTEN        0             128                        0.0.0.0:22                        0.0.0.0:*            users:(("sshd",pid=711,fd=3))
LISTEN        0             4096                          [::]:9999                         [::]:*            users:(("docker-proxy",pid=1970,fd=4))
LISTEN        0             128                           [::]:22                           [::]:*            users:(("sshd",pid=711,fd=4))
```

- ouvrir le port `9999/tcp` (vu dans le `ss` au dessus normalement) dans le firewall de la VM

```
[user@localhost ~]$ sudo firewall-cmd --add-port=9999/tcp --permanent
[sudo] password for user:
success
[user@localhost ~]$ sudo firewall-cmd --reload
success
```
- depuis le navigateur de votre PC, visiter le site web sur `http://IP_VM:9999`

[Page Nginx](./Page_nginx.png)

🌞 **On va ajouter un site Web au conteneur NGINX**

- créez un dossier `nginx`

```
[user@localhost ~]$ mkdir nginx
```

- dedans, deux fichiers : `index.html` (un site nul) `site_nul.conf` (la conf NGINX de notre site nul)
```
[user@localhost nginx]$ touch index.html
[user@localhost nginx]$ touch site_nul.conf
```
```
[user@localhost nginx]$ cat index.html
<h1>MEOOOW</h1>
```
```
[user@localhost nginx]$ cat site_nul.conf
server {
    listen        8080;

    location / {
        root /var/www/html;
    }
}
```

🌞 **Visitons**

- vérifier que le conteneur est actif

```
[user@localhost nginx]$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                               NAMES
fe76c9969f35   nginx     "/docker-entrypoint.…"   6 minutes ago   Up 6 minutes   80/tcp, 0.0.0.0:9999->8080/tcp, :::9999->8080/tcp   amazing_mahavira
```

- visiter le site web depuis votre PC

[Page Nginx](./images/Page_nginx-2.png)

## 5. Un deuxième conteneur en vif

🌞 **Lance un conteneur Python, avec un shell**

```
[user@localhost nginx]$ docker run -it python bash
Unable to find image 'python:latest' locally
latest: Pulling from library/python
1b13d4e1a46e: Pull complete
1c74526957fc: Pull complete
8d55d1cb1ffb: Pull complete
aa8e0026efed: Pull complete
a000d2c561b3: Pull complete
fd5581c77642: Pull complete
6ba9b0f086f5: Pull complete
c924028f9b63: Pull complete
Digest: sha256:07a11fdb8f9b0cf2cc7c2dbda60fff1ded2d3f40fbf5e1e53ece675028a4b8d4
Status: Downloaded newer image for python:latest
root@102dbd9ad05b:/#
```
🌞 **Installe des libs Python**
- une fois que vous avez lancé le conteneur, et que vous êtes dedans avec `bash`
- installez deux libs, elles ont été choisies complètement au hasard (avec la commande `pip install`):
  - `aiohttp`
  - `aioconsole`

```
root@102dbd9ad05b:/# pip install aiohttp
Collecting aiohttp
  Obtaining dependency information for aiohttp from https://files.pythonhosted.org/packages/75/5f/90a2869ad3d1fb9bd984bfc1b02d8b19e381467b238bd3668a09faa69df5/aiohttp-3.9.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata
  Downloading aiohttp-3.9.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (7.4 kB)
Collecting attrs>=17.3.0 (from aiohttp)
  Obtaining dependency information for attrs>=17.3.0 from https://files.pythonhosted.org/packages/e0/44/827b2a91a5816512fcaf3cc4ebc465ccd5d598c45cefa6703fcf4a79018f/attrs-23.2.0-py3-none-any.whl.metadata
  Downloading attrs-23.2.0-py3-none-any.whl.metadata (9.5 kB)
Collecting multidict<7.0,>=4.5 (from aiohttp)
  Downloading multidict-6.0.4.tar.gz (51 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 51.3/51.3 kB 5.6 MB/s eta 0:00:00
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Installing backend dependencies ... done
  Preparing metadata (pyproject.toml) ... done
Collecting yarl<2.0,>=1.0 (from aiohttp)
  Obtaining dependency information for yarl<2.0,>=1.0 from https://files.pythonhosted.org/packages/28/1c/bdb3411467b805737dd2720b85fd082e49f59bf0cc12dc1dfcc80ab3d274/yarl-1.9.4-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata
  Downloading yarl-1.9.4-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (31 kB)
Collecting frozenlist>=1.1.1 (from aiohttp)
  Obtaining dependency information for frozenlist>=1.1.1 from https://files.pythonhosted.org/packages/0b/f2/b8158a0f06faefec33f4dff6345a575c18095a44e52d4f10c678c137d0e0/frozenlist-1.4.1-cp312-cp312-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata
  Downloading frozenlist-1.4.1-cp312-cp312-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (12 kB)
Collecting aiosignal>=1.1.2 (from aiohttp)
  Downloading aiosignal-1.3.1-py3-none-any.whl (7.6 kB)
Collecting idna>=2.0 (from yarl<2.0,>=1.0->aiohttp)
  Obtaining dependency information for idna>=2.0 from https://files.pythonhosted.org/packages/c2/e7/a82b05cf63a603df6e68d59ae6a68bf5064484a0718ea5033660af4b54a9/idna-3.6-py3-none-any.whl.metadata
  Downloading idna-3.6-py3-none-any.whl.metadata (9.9 kB)
Downloading aiohttp-3.9.1-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (1.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.3/1.3 MB 10.0 MB/s eta 0:00:00
Downloading attrs-23.2.0-py3-none-any.whl (60 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 60.8/60.8 kB 7.2 MB/s eta 0:00:00
Downloading frozenlist-1.4.1-cp312-cp312-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl (281 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 281.5/281.5 kB 11.5 MB/s eta 0:00:00
Downloading yarl-1.9.4-cp312-cp312-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (322 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 322.4/322.4 kB 9.5 MB/s eta 0:00:00
Downloading idna-3.6-py3-none-any.whl (61 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 61.6/61.6 kB 5.9 MB/s eta 0:00:00
Building wheels for collected packages: multidict
  Building wheel for multidict (pyproject.toml) ... done
  Created wheel for multidict: filename=multidict-6.0.4-cp312-cp312-linux_x86_64.whl size=114914 sha256=9ae906f75323e357bcc47a3e8036732052f309b94e8cc46ad45a6c6fed9587cb
  Stored in directory: /root/.cache/pip/wheels/f6/d8/ff/3c14a64b8f2ab1aa94ba2888f5a988be6ab446ec5c8d1a82da
Successfully built multidict
Installing collected packages: multidict, idna, frozenlist, attrs, yarl, aiosignal, aiohttp
Successfully installed aiohttp-3.9.1 aiosignal-1.3.1 attrs-23.2.0 frozenlist-1.4.1 idna-3.6 multidict-6.0.4 yarl-1.9.4
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv

[notice] A new release of pip is available: 23.2.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
root@102dbd9ad05b:/# pip install aioconsole
Collecting aioconsole
  Obtaining dependency information for aioconsole from https://files.pythonhosted.org/packages/f7/39/b392dc1a8bb58342deacc1ed2b00edf88fd357e6fdf76cc6c8046825f84f/aioconsole-0.7.0-py3-none-any.whl.metadata
  Downloading aioconsole-0.7.0-py3-none-any.whl.metadata (5.3 kB)
Downloading aioconsole-0.7.0-py3-none-any.whl (30 kB)
Installing collected packages: aioconsole
Successfully installed aioconsole-0.7.0
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv

[notice] A new release of pip is available: 23.2.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
```
- tapez la commande `python` pour ouvrir un interpréteur Python
```
root@102dbd9ad05b:/# python
Python 3.12.1 (main, Jan 11 2024, 09:52:34) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
- taper la ligne `import aiohttp` pour vérifier que vous avez bien téléchargé la lib
```
>>> import aiohttp
```

# II. Images
## 1. Images publiques

🌞 **Récupérez des images**

- avec la commande `docker pull`
- récupérez :
  - l'image `python` officielle en version 3.11 (`python:3.11` pour la dernière version)

```
[user@localhost nginx]$ docker pull python:3.11
3.11: Pulling from library/python
1b13d4e1a46e: Already exists
1c74526957fc: Already exists
8d55d1cb1ffb: Already exists
aa8e0026efed: Already exists
a000d2c561b3: Already exists
57f6b5858e11: Pull complete
14972058cb06: Pull complete
ed78de3102ac: Pull complete
Digest: sha256:042210b0696af5ef124bd57f0d4ae6688f5fff8666f33edf7c4902320916138b
Status: Downloaded newer image for python:3.11
docker.io/library/python:3.11
```

- l'image `mysql` officielle en version 5.7
```
[user@localhost nginx]$ docker pull mysql:5.7
5.7: Pulling from library/mysql
20e4dcae4c69: Pull complete
1c56c3d4ce74: Pull complete
e9f03a1c24ce: Pull complete
68c3898c2015: Pull complete
6b95a940e7b6: Pull complete
90986bb8de6e: Pull complete
ae71319cb779: Pull complete
ffc89e9dfd88: Pull complete
43d05e938198: Pull complete
064b2d298fba: Pull complete
df9a4d85569b: Pull complete
Digest: sha256:4bc6bc963e6d8443453676cae56536f4b8156d78bae03c0145cbe47c2aad73bb
Status: Downloaded newer image for mysql:5.7
docker.io/library/mysql:5.7
```
 - l'image `wordpress` officielle en dernière version
    - c'est le tag `:latest` pour récupérer la dernière version
    - si aucun tag n'est précisé, `:latest` est automatiquement ajouté

```
[user@localhost nginx]$ docker pull wordpress
Using default tag: latest
latest: Pulling from library/wordpress
af107e978371: Already exists
6480d4ad61d2: Pull complete
95f5176ece8b: Pull complete
0ebe7ec824ca: Pull complete
673e01769ec9: Pull complete
74f0c50b3097: Pull complete
1a19a72eb529: Pull complete
214daec02f86: Pull complete
9bb2d265a2f4: Pull complete
b89d85dfd9f0: Pull complete
991e05662ac4: Pull complete
1106a3b879f1: Pull complete
94fcbc71d4a9: Pull complete
0910769091bd: Pull complete
2e1351a2f941: Pull complete
006bd105f188: Pull complete
0ad2b9a7aaf9: Pull complete
e95473a7f69c: Pull complete
b7d03c854f68: Pull complete
ad70c25cb0f6: Pull complete
dcace32066bc: Pull complete
Digest: sha256:2dcb414af724831f18089bd7943d957ceb6d3b09d00d271c2b189cea9740d321
Status: Downloaded newer image for wordpress:latest
docker.io/library/wordpress:latest
```

- l'image linuxserver/wikijs en dernière version

```
[user@localhost nginx]$ docker pull linuxserver/wikijs
Using default tag: latest
latest: Pulling from linuxserver/wikijs
7067609056d4: Pull complete
07a0e16f7be1: Pull complete
53e9d08bbc92: Pull complete
b53423ae0508: Pull complete
a5a16bcdc3f4: Pull complete
7271af368853: Pull complete
d3660621e617: Pull complete
Digest: sha256:336af9d37d0285a7be775fc181c8436c7805dca6adf0513db63dab094b6b7f4c
Status: Downloaded newer image for linuxserver/wikijs:latest
docker.io/linuxserver/wikijs:latest
```

- listez les images que vous avez sur la machine avec une commande `docker`
```
[user@localhost nginx]$ docker images
REPOSITORY           TAG       IMAGE ID       CREATED        SIZE
linuxserver/wikijs   latest    218ef3649e4d   6 days ago     441MB
debian               latest    2a033a8c6371   3 weeks ago    117MB
mysql                5.7       5107333e08a8   4 weeks ago    501MB
python               latest    ddb6e9772fb2   4 weeks ago    1.02GB
wordpress            latest    9071407ed1c0   5 weeks ago    740MB
python               3.11      1a88ceb967e0   5 weeks ago    1.01GB
nginx                latest    d453dd892d93   2 months ago   187MB
```
🌞 **Lancez un conteneur à partir de l'image Python**

- lancez un terminal `bash` ou `sh`
- vérifiez que la commande `python` est installée dans la bonne version

```
[user@localhost nginx]$ docker run -it python:3.11
Python 3.11.7 (main, Jan 11 2024, 10:33:01) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
## 2. Construire une image

- créer un fichier `Dockerfile`
```
[user@localhost ~]$ mkdir python_app_build
```
```
[user@localhost python_app_build]$ cat app.py
import emoji

print(emoji.emojize("Cet exemple d'application est vraiment naze :thumbs_down:"))
```

# III. Docker compose
🌞 **Créez un fichier `docker-compose.yml`**

- dans un nouveau dossier dédié `/home/<USER>/compose_test`
```
[user@localhost ~]$ mkdir compose_test
```

```
[user@localhost compose_test]$ cat docker-compose.yml
version: "3"

services:
  conteneur_nul:
    image: debian
    entrypoint: sleep 9999
  conteneur_flopesque:
    image: debian
    entrypoint: sleep 9999
```

🌞 **Lancez les deux conteneurs** avec `docker compose`
- go exécuter `docker compose up -d`

```
[user@localhost compose_test]$ docker compose up -d
[+] Running 3/3
 ✔ Network compose_test_default                  Created                                                                                               0.3s
 ✔ Container compose_test-conteneur_flopesque-1  Started                                                                                               0.1s
 ✔ Container compose_test-conteneur_nul-1        Started                                                                                               0.1s
```

🌞 **Vérifier que les deux conteneurs tournent**
```
[user@localhost compose_test]$ docker ps
CONTAINER ID   IMAGE     COMMAND        CREATED         STATUS         PORTS     NAMES
19bf4487e3d0   debian    "sleep 9999"   3 minutes ago   Up 3 minutes             compose_test-conteneur_nul-1
512c54c251a6   debian    "sleep 9999"   3 minutes ago   Up 3 minutes             compose_test-conteneur_flopesque-1
```

🌞 **Pop un shell dans le conteneur `conteneur_nul`**
```
[user@localhost compose_test]$ docker exec -it 19bf44 bash
root@19bf4487e3d0:/#
```
- effectuez un `ping conteneur_flopesque` (ouais ouais, avec ce nom là)
  - un conteneur est aussi léger que possible, aucun programme/fichier superflu : t'auras pas la commande `ping` !
  - il faudra installer un paquet qui fournit la commande `ping` pour pouvoir tester

```
root@19bf4487e3d0:/# apt-get install -y iputils-ping
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libcap2-bin libpam-cap
The following NEW packages will be installed:
  iputils-ping libcap2-bin libpam-cap
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 96.2 kB of archives.
After this operation, 311 kB of additional disk space will be used.
Get:1 http://deb.debian.org/debian bookworm/main amd64 libcap2-bin amd64 1:2.66-4 [34.7 kB]
Get:2 http://deb.debian.org/debian bookworm/main amd64 iputils-ping amd64 3:20221126-1 [47.1 kB]
Get:3 http://deb.debian.org/debian bookworm/main amd64 libpam-cap amd64 1:2.66-4 [14.5 kB]
Fetched 96.2 kB in 0s (1048 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package libcap2-bin.
(Reading database ... 6098 files and directories currently installed.)
Preparing to unpack .../libcap2-bin_1%3a2.66-4_amd64.deb ...
Unpacking libcap2-bin (1:2.66-4) ...
Selecting previously unselected package iputils-ping.
Preparing to unpack .../iputils-ping_3%3a20221126-1_amd64.deb ...
Unpacking iputils-ping (3:20221126-1) ...
Selecting previously unselected package libpam-cap:amd64.
Preparing to unpack .../libpam-cap_1%3a2.66-4_amd64.deb ...
Unpacking libpam-cap:amd64 (1:2.66-4) ...
Setting up libcap2-bin (1:2.66-4) ...
Setting up libpam-cap:amd64 (1:2.66-4) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.36.0 /usr/local/share/perl/5.36.0 /usr/lib/x86_64-linux-gnu/perl5/5.36 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl-base /usr/lib/x86_64-linux-gnu/perl/5.36 /usr/share/perl/5.36 /usr/local/lib/site_perl) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up iputils-ping (3:20221126-1) ...
```

```
root@19bf4487e3d0:/# ping conteneur_flopesque
PING conteneur_flopesque (172.18.0.2) 56(84) bytes of data.
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=1 ttl=64 time=0.481 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=2 ttl=64 time=0.135 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=3 ttl=64 time=0.094 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=4 ttl=64 time=0.107 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=5 ttl=64 time=0.071 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.2): icmp_seq=6 ttl=64 time=0.090 ms
^C
--- conteneur_flopesque ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5088ms
rtt min/avg/max/mdev = 0.071/0.163/0.481/0.143 ms
```