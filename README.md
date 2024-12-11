# OStackInstallRaPi
This repo describes how to install OpenStack on raspberry Pi cluster using Kolla-Ansible. The basic scope of application of those clusters for us is education. A cluster of this type allows us to present/explain various features/concepts of OpenStack that are hard or impossible to show in AIO or virtualized configurations. Many of them are related to the administration of the DC, e.g., the management of provider networks where the admin needs to confige VLAN in the physical network of the data centre and declate them in OpenStack congig file. One does not need to have a dozens of servers for thousands of $ each to do this.

Currently, Raspberry Pi 4 is assumed. It is expected that extensions (if any) needed for Rraspberry Pi 5 will be included in the future once we test this option sufficiently well.

## Assumptios

All procedures described herein refer to HW and SW setup of the cluster as specified below

1. Raspberry Pi 4
   * (1x4GB RAM + 1x8GB RAM) or (2x4GB RAM+2*8GB RAM)
   * all Pi are equipped with 32GB SD disk
   * Note: we believe that a single RaPi 8GB RAM and the default configuration of Kolla-Ansible OpenStack should work for basic evaluation, but we have not tested this option.
2. SW
   * OS: Raspberry Pi OS Light - root of Debian 12 (Bookworm)
   * Kolla-Ansible 2023.1; respective envirnment components according to 
   * Note: newer releases of Kolla-Ansible will be tried in the future (2023.1 got status "unmaintained" during our trials) and we'll update these instructions accordingly after positive tests
4. Network:
   * the Pis are equipped with 802.3af/at PoE HAT from Waveshare
   * they are powered form TP-Link TL-SG105PE switch
   * TP-Link switch is connected to a local router with DHCP enabled to separate the network of OpenStack DC frome the rest of the network environment
5. Notes
   * other PoE HATs for Raspberry Pi 4 and other PoE switches should work, too
   * for education purposes, we use setups with at least 3 RaPis and a managed switch (802.1Q) to demonstrate how VLAN-based provider networks can be used in OpenStack; this is impossible to show using AIO (all-in-one) OpenStack setups
   * other details that may be relevant are explained in the description below



 
