CAPES is an operational-focused service hub for segmented, self-hosted, and offline (if necessary) incident response, intelligence analysis, and hunt operations.

![capes logo](/capes.png)  

# Services in CAPES
1. Rocketchat
1. Etherpad
1. GoGS
1. CyberChef
1. TheHive
1. Cortex (enrichment plugin for TheHive)

# Documentation
Please see below for Build, Operate, Maintain specifics on the different web applications
* [CAPES Landing Page](https://github.com/capesstack/capes/blob/master/landing_page/build_operate_maintain.md)  
* [Etherpad](https://github.com/capesstack/capes/blob/master/etherpad/build_operate_maintain.md)  
* [GoGS](https://github.com/capesstack/capes/blob/master/gogs/build_operate_maintain.md)  
* [Rocketchat](https://github.com/capesstack/capes/blob/master/rocketchat/build_operate_maintain.md)  
* [TheHive](https://github.com/capesstack/capes/blob/master/thehive/build_operate_maintain.md)  
* [Cortex](https://github.com/capesstack/capes/blob/master/cortex/build_operate_maintain.md)  
* [CyberChef](https://github.com/capesstack/capes/blob/master/cyberchef/build_operate_maintain.md)

<!---
* [Mumble](https://github.com/capesstack/capes/blob/master/mumble/build_operate_maintain.md)  
-->

## Quick Start
Ready to just get started? Just jump to the [quick start](#get-capes).

## Requirements
There has not been extensive testing, but all of these services have run without issue on a single virtual machine with approximately 20 users and no issue for a week (I'm sure it would have kept running, 1 week was just when we stopped our testing). That said, your mileage may vary.

**While the OS version isn't a hard requirement, all testing and development work has been done with `CentOS 7.4.1708 (Core)`.**

| Component | Number |
| - | - |
| Cores | 4 |
| RAM | 8 GB |
| Hard Disk | 20 GB |

## Secure Deployment
**The recommended deployment of CAPES is on a protected network that is inaccessible from the contested network or the Internet. This is intended to be an offnet operations stack.**

There is an inherent risk to deploying web applications to the Internet or to a contested networking enclave -- basically, somewhere the bad guys can get to. To address this, the CAPES project has done a few things to help protect these web applications and left a few things for you, the operator, to close in on as your need requires.

### Secure by Design
#### Operating System
While there are a lot of projects that are developed using Ubuntu (many of these service creators still follow that path), CAPES chose to use CentOS because of a few different reasons:  
1. CentOS is the open source version of Red Hat Enterprise Linux (RHEL)
1. CentOS uses Security Enhanced Linux (SELinux) instead of AppArmor

#### Implementation
While the `firewalld` service is running on CAPES and the only ports listening have services attached to them, you should still consider using a Web Application Firewall (WAF), an Intrusion Detection System (IDS), and/or a Network Security Monitor (like [ROCKNSM](http://rocknsm.io) which has an IDS integrated on top of a litany of other goodies) to monitor/defend your stack.

If possible when deploying CAPES, just like a passive NSM, should **not** be on, or accessible from, the contested network. This will prevent it from being targeted by aggressors.

## Installation
Generally, the CAPES ecosystem is meant to run as a whole, so the preferred usage will be to install CAPES with the `deploy_capes.sh` script in the root directory of this repository. Additionally, if there is a service that you do not want, you can comment that service out of the deploy script as they are documented with service headers.

That said, there is a deploy script for each of the services that you should be able to run individually if your use case requires that.

### Build your OS
Please see the [OS build guide](https://github.com/capesstack/capes/tree/master/docs#build-your-os) on the CAPES docs page.

## Get CAPES
Finally, here we go.
```
git clone https://github.com/capesstack/capes.git
# if you're feeling adventurous git clone -b devel https://github.com/capesstack/capes.git
cd capes
sudo sh deploy_capes.sh
```
This will start the automated build of:
* Configure NTP (likely already done, but in the event you skipped the [Build your OS](https://github.com/capesstack/capes/tree/master/docs#build-your-os) steps)
* Install Rocketchat  
* Install GoGS  
* Install Etherpad  
* Install TheHive  
* Install Cortex  
* Install Nginx  
* Install CyberChef    
* Install the CAPES landing page  
* Secure the MySQL installation  
* Make firewall changes  
* Set everything to autostart  

## Get Started
After the CAPES installation, you should be able to browse to `http://your_capes_system` (or `http://your_capes_IP` if you don't have DNS set up) get get to the CAPES landing page and start setting up services.

I **strongly** recommend that you look at the [Build, Operate, Maintain](https://github.com/capesstack/capes/tree/master/docs#documentation) guides for these services before you get going. A few of the services launch a configuration pipeline that is hard to restart if you don't complete it the first time (I'm looking at you TheHive and GoGS).

## Troubleshooting
Please see the [documentation](https://github.com/capesstack/capes/tree/master/docs#documentation) or feel free to open a [GitHub Issue](https://github.com/capesstack/capes/issues).
