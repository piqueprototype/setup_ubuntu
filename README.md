# setup_ubuntu
Repository is created notate the necessary steps to complete a Ubuntu 22.04 installation for dual booting within Windows
## Important
If you enabled Third-parties and created SecureBoot key, enroll MOK upon reboot after initial installation. Otherwise follow SecureBoot link below.
## Installation
### System Stuff
* [Install GPU drivers](https://askubuntu.com/questions/1112814/install-driver-for-gtx-1070)
* [Explains the SecureBoot bit at end of GPU drivers](https://wiki.ubuntu.com/UEFI/SecureBoot)
### Docker
* [Install Docker](https://docs.docker.com/desktop/install/ubuntu/)
### Node Version Manager (nvm)
* [Install NVM](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04#option-3-installing-node-using-the-node-version-manager)
### Openvpn (Optional)
```bash
ls /etc/openvpn
# Output: client/ client.conf server/ update-resolv-conf

ls /etc/openvpn/client
# Output: ca.crt MYCONFIG.crt MYCONFIG.key MYCONFIG.ovpn
```
```bash
sudo openvpn --config /etc/openvpn/client.conf
```
* If the above command throws an error indicating that the server uses a different `data-cipher`. You can correct this issue by adding `data-ciphers AES-256-GCM:AES-128-GCM:THE_NEW_CIPHER`.
  * `THE_NEW_CIPHER` or more likely, older, include the one your server is utilizing. 

#### Start the service
```bash
sudo systemctl start openvpn@client
```
