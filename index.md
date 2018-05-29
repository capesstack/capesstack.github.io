![capes logo](/capes_logo.png)

CAPES is an operational-focused service hub for segmented, self-hosted, and offline (if necessary) incident response, intelligence analysis, and hunt operations.

# Services in CAPES
1. Mattermost (Chat)
1. HackMD (Collaboration-style documentation)
1. Gitea (Version controlled documentation)
1. TheHive (Incident Response)
1. Cortex (Indicator enrichment)
1. CyberChef (Data analysis)
1. Mumble (VoIP)
1. Beats - Metric, Heart, and File (Performance and health metrics)
1. Kibana (Data visualization)

![capes logo](/capes_arch.png)

# Documentation
Please see below for Build, Operate, Maintain specifics on the different web applications
* [Build Your OS](https://github.com/capesstack/capes/tree/master/docs#build-your-os)  
* [CAPES Landing Page](https://github.com/capesstack/capes/blob/master/landing_page/build_operate_maintain.md)  
* [Mattermost](https://github.com/capesstack/capes/blob/master/mattermost/build_operate_maintain.md)  
* [HackMD](https://github.com/capesstack/capes/blob/master/hackmd/build_operate_maintain.md)  
* [Gitea](https://github.com/capesstack/capes/blob/master/gitea/build_operate_maintain.md)  
* [TheHive](https://github.com/capesstack/capes/blob/master/thehive/build_operate_maintain.md)  
* [Cortex](https://github.com/capesstack/capes/blob/master/cortex/build_operate_maintain.md)  
* [CyberChef](https://github.com/capesstack/capes/blob/master/cyberchef/build_operate_maintain.md)
* [Mumble](https://github.com/capesstack/capes/blob/master/mumble/build_operate_maintain.md)  
* [Beats](https://github.com/capesstack/capes/blob/master/beats/build_operate_maintain.md)
* [Kibana](https://github.com/capesstack/capes/blob/master/kibana/build_operate_maintain.md)

# Requirements
There has not been extensive testing with these requirements, but all of these services have run without issue on a single virtual machine with approximately 20 users and no issue for a week (I'm sure it would have kept running, 1 week was just when we stopped our testing). That said, your mileage may vary.

**While the OS version isn't a hard requirement, all testing and development work has been done with `CentOS 7.4.1708 (Core)`.**

| Component | Number |
| - | - |
| OS | CentOS 7.4.1708 (Core) |
| Cores | 4 |
| RAM | 8 GB |
| Hard Disk | 20 GB |

# Get CAPES
Finally, here we go.
```
sudo yum install git -y
git clone https://github.com/capesstack/capes.git
cd capes
sudo sh deploy_capes.sh
```
This will start the automated build of:
* Configure NTP (likely already done, but in the event you skipped the [Build your OS](https://github.com/capesstack/capes/tree/master/docs#build-your-os) steps)
* Install Kibana
* Install Filebeat
* Install Metricbeat
* Install Heartbeat
* Install Mattermost  
* Install Gitea  
* Install HackMD  
* Install Mumble  
* Install TheHive  
* Install Cortex  
* Install Nginx  
* Install CyberChef    
* Install the CAPES landing page  
* Secure the MySQL installation  
* Set everything to autostart  

# Get Started
After the CAPES installation, you should be able to browse to `http://your_capes_system` (or `http://your_capes_IP` if you don't have DNS set up) get get to the CAPES landing page and start setting up services by following the [post installation steps](https://github.com/capesstack/capes/tree/master/docs#post-installation).

Although most of these services are fairly intuitive, I **strongly** recommend that you look at the [Build, Operate, Maintain](https://github.com/capesstack/capes/tree/master/docs#documentation) guides for these services before you get going too far. A few of the services launch a configuration pipeline that is obnoxious to restart if you don't complete it the first time (I'm looking at you TheHive and Gitea).

# Troubleshooting
Please see the [documentation](https://github.com/capesstack/capes/tree/master/docs#documentation) or feel free to open a [GitHub Issue](https://github.com/capesstack/capes/issues).

Want to join the discussion? Send a request to join our Slack Workspace to contact [at] capesstack[.]io

# Swag
Interested in some CAPES swag? Send me a email to contact [at] capesstack[.]io and I'll send you some laptop decals.

If you're interested in CAPES t-shirts, we parter with TeeSpring for those. Feel free to check out [our storefront](https://teespring.com/stores/capesstack). We don't make a penny on these - 100% of the profits go to the National Alliance to End Homelessness.

# Training & Professional Services
While CAPES is a FOSS project (and always will be) we'll attempt to support deployment questions via the GitHub Issues page, if you need training or PS, please feel free to check out some options over at [Perched](http://perched.io)
