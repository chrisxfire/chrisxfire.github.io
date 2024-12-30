---
title: plex media server
date: 2024-01-28T00:00:00-06:00
draft: false
weight: 1
---

# overview
Plex is a local-first media server. See https://www.plex.tv for more information.

# installation
1. Create Plex's `apt` source:  
    ```bash
    echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list
    ```
2. Update `apt` and install:
    ```bash
    sudo apt update
    sudo apt install plexmediaserver
    ```

## migrate metadata library
By default, Plex's metadata library is located at `/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/`. On systems with a small `/var` partition, this can be problematic. To relocate the metadata library:
1. Stop Plex:  
    ```bash
    sudo systemctl stop plexmediaserver.service
    ```
2. Create a systemd override:  
    ```bash
    sudo systemctl edit plexmediaserver.service
    ```

    This creates `/etc/systemd/system/plexmediaserver.service.d/override.conf`. 
3. Delete the contents of the file with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>K</kbd>.
4. Add this line, replacing `DESTINATION_PATH`:  
    ```
    Environment="PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR=DESTINATION_PATH/Library/Application Support"
    ```
5. Exit and save.
6. Move the metadata:  
    ```bash
    sudo mv --verbose /var/lib/plexmediaserver/Library/ DESTINATION_PATH
    ```
7. Reload systemd manager configuration to use the new override:  
    ```bash
    sudo systemctl daemon-reload
    ```
8. Restart Plex:  
    ```bash
    sudo systemctl start plexmediaserver.service
    ```

## configuration
1. Browse to `http://<LOCAL-SERVER-IP>:32400/web/index.html` replacing `LOCAL-SERVER-IP`
2. Complete setup.