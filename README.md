# rsync on ESXi

rsync is a utility for efficiently transferring and synchronizing files between a computer and a storage drive and across networked computers by comparing the modification times and sizes of files.

This binary is focused towards the use on ESXi Hosts, follow the steps below.

# Install

1. Grab this Github Repo onto the ESXi Host & unpackage this zip
    ```sh
    wget https://github.com/gmasonPCS/rsync-on-esxi/releases/download/Release/rsync-on-esxi.zip -O rsync-on-esxi.zip
    unzip rsync-on-esxi.zip
    ```
2. Move rsync binaries & create proper symlink
    ```sh
    mv rsync-static /bin/rsync-static
    ln -s /bin/rsync-static /bin/rsync
    ```
3. Import Firewall Rule for Remote Rsync Copies
    ```sh
    mv rsync.xml /etc/vmware/firewall/rsync.xml
    esxcli network firewall refresh
    esxcli network firewall ruleset list
    ```

- You may need to change file permissions on the rsync binary in-order to run the program, use the following command to allow users to execute the file
    ```sh
    chmod 755 /bin/rsync-static
    ```