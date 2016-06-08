===============================================
Tempest Integration of ceph-integration
===============================================

This directory contains Tempest tests to cover the ceph-integration project.

This plugin will test the functionality of Openstack's Glance, Cinder and Nova,
while validating the actions on both Openstack and Ceph storage.

-----------------------------------------------
                Design Principles
-----------------------------------------------

* Ceph integration plugin should be able to run against a cloud that uses RBDas Glance's default store, Nova's images type (with Libvirt) and a Cinder back end.
* The plugin should be explicit in testing features and functionalities. It is easier to discover and debug failures when each function is atomic
* The plugin uses Openstack python clients, it will not use API tools that are not been used by clients. If a feature doesn't have an implantation in the client, its integration with Ceph will not be tested
* The plugin uses Openstack public interfaces.
* The plugin should not change the database directly
* The plugin will clean up after itself, as a rule
* The plugin will verify every storage related action on the Ceph storage as well, using RBD