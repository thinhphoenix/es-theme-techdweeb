dArkOS / ArkOS (R36S) - thanh trang thai (wifi + pin)
=====================================================

Tren ArkOS/dArkOS, icon wifi va pin o goc tren phai KHONG phai do theme ve.
EmulationStation cua may ve chung tu file cua chinh no:

  /usr/bin/emulationstation/resources/network*.svg
  /usr/bin/emulationstation/resources/bluetooth*.svg
  /usr/bin/emulationstation/resources/battery/*.svg
  /usr/bin/emulationstation/resources/network-packs/<Pack>/*.svg

Vi vay sua wifi.svg trong theme khong co tac dung tren may nay.
Thu muc nay chua icon cua ban voi dung ten file ma ES tim.

CACH 1 - khong can root (uu tien): chep vao thu muc resource cua user
------------------------------------------------------------------------
  scp -r device-icons ark@<IP-May>:/tmp/

  ssh ark@<IP-May>
  mkdir -p ~/.emulationstation/resources/battery
  cp /tmp/device-icons/network*.svg   ~/.emulationstation/resources/
  cp /tmp/device-icons/bluetooth*.svg ~/.emulationstation/resources/
  cp /tmp/device-icons/battery/*.svg  ~/.emulationstation/resources/battery/
  exit

ResourceManager cua ES kiem tra ~/.emulationstation/resources TRUOC tien,
nen cac file nay de len icon mac dinh.

CACH 2 - ghi de thang vao ban cai ES (can sudo)
------------------------------------------------
  ssh ark@<IP-May>
  sudo cp /tmp/device-icons/network*.svg   /usr/bin/emulationstation/resources/
  sudo cp /tmp/device-icons/bluetooth*.svg /usr/bin/emulationstation/resources/
  sudo cp /tmp/device-icons/battery/*.svg  /usr/bin/emulationstation/resources/battery/

Neu dang dung tinh nang "NETWORK ICON" (pack) trong UI Settings thi phai
ghi de ca pack dang chon, vi moi lan doi pack ES se chep de lai:

  sudo cp /tmp/device-icons/network*.svg   /usr/bin/emulationstation/resources/network-packs/Default/
  sudo cp /tmp/device-icons/bluetooth*.svg /usr/bin/emulationstation/resources/network-packs/Default/

Sau do khoi dong lai EmulationStation.

Luu y
-----
- Phai bat "SHOW WIFI ICON" trong UI Settings thi icon wifi moi hien.
- network_off.svg dang dung cung hinh wifi (khong co gach cheo). Muon ban
  co dau gach cheo cho trang thai mat mang thi bao de tao rieng.
- Tren vai ban dArkOS, icon pin nam trong binary ES (renderers/BatteryIcons.h)
  nen khong thay duoc bang file. Ban nao doc :/battery/*.svg thi cac file
  trong battery/ se co tac dung.
