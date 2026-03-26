# Cluster Exporter RPM Build Tool

Creates a virtual linux machine, then builds the RPM packages for the Prometheus Cluster Exporter using it.

## Instructions

Edit `Vagrantfile` to choose your linux version (Fedora 43 or Rocky 8). Edit `inventory/group_vars.all` to set version number, command line options and the URL for the Cluster Exporter git repository. Run `vagrant up`.

Generated RPMs are found in the `rpm/` subfolder.

