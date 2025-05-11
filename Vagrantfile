install_frotz:
  pkg.installed:
    - name: frotz

zork_zip_download:
  file.managed:
    - name: /tmp/zork_undiscovered.zip
    - source: https://archive.org/download/Infocom_Z-Machine_TOSEC_2012_04_23/Infocom_Z-Machine_TOSEC_2012_04_23.zip/Infocom%20Z-Machine%20%5BTOSEC%5D%2FGames%2FZork%20-%20The%20Undiscovered%20Underground%20v16%20%281997%29%28Activision%29%5B970828%5D.zip
    - makedirs: True
    - skip_verify: True

zork_zip_extract:
  archive.extracted:
    - name: /home/vagrant/zork_undiscovered
    - source: /tmp/zork_undiscovered.zip
    - enforce_toplevel: False

play_zork_script:
  file.managed:
    - name: /home/vagrant/zork_undiscovered/play_zork.sh
    - mode: '0755'
    - user: vagrant
    - group: vagrant
    - contents: |
        #!/bin/bash
        frotz "/home/vagrant/zork_undiscovered/ZTUU.z5"
    - require:
      - archive: zork_zip_extract
