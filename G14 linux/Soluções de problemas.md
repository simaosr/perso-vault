# Zotero abre pdfs com o libreoffice
1. Abrir /user/share/applications/mimeinfo.cache

2. "applicationpdf=" had as first item "libreoffice-draw.desktop

# Configure G14 keyboard
```
1. Create a file named /etc/udev/hwdb.d/90-nkey.hwdb with:
	evdev:input:b0003v0B05p1866*
	  KEYBOARD_KEY_c00b6=kbdillumdown # Fn+F2 (music prev)
	  KEYBOARD_KEY_c00b5=kbdillumup   # Fn+F4 (music skip)
	  KEYBOARD_KEY_ff3100c5=pagedown  # Fn+Down
	  KEYBOARD_KEY_ff3100c4=pageup    # Fn+Up
	  KEYBOARD_KEY_ff3100b2=home      # Fn+Left
	  KEYBOARD_KEY_ff3100b3=end       # Fn+Right

2. then update hwdb with:
	$ sudo systemd-hwdb update
	$ sudo udevadm trigger
```

# Fix apple keytouch tap to click

 1154  xinput list
 1155  xinput list-props 18
 1157  xinput list
 1158  xinput list-props 14
 1371  xinput list
 1372  xinput list-props 18
 1373  xinput set-prop 18 311 2, 2, 0
 1374  xinput set-prop 18 311 1
 1380  xinput set-prop 18 311 1

