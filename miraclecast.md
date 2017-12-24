# MiracleCast

* start miracle-wifid

  ```console
  sudo miracle-wifid -i wlx000b8187d670 --use-dev --log-level trace
  ```

* scan for devices

  ```console
  sudo wpa_cli -p /var/run/miracle/wifi p2p_find
  ```

* connect to casting device

  ```console
  sudo wpa_cli -p /var/run/miracle/wifi p2p_connect 56:2a:a2:53:8c:3b pbc join persistent
  ```
