# Solucion ajuste de brillo con teclas Fn, en Debian

Esta solucion es aplicable en placas Intel.

1- Crear el siguiente archivo:  

``sudo nano /usr/share/X11/xorg.conf.d/20-intel.conf``

2- Como es un archivo de configuración nuevo debemos adicionar los parámetros, los cuales son:
```
Section "Device"
             Identifier "card0"
             Driver "intel"
             Option "Backlight" "intel_backlight"
             BusID "PCI:0:2:0"
EndSection
```
3- Guardar y salir `Ctrl+X`, y reiniciar `reboot`.

4- Si no reaccionan los botones editamos el archivo grub
```nano /etc/default/grub```

5- En la linea que dice
```GRUB_CMDLINE_LINUX_DEFAULT="quiet"```
debe quedar asi
```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=native pcie_aspm=force acpi_osi="```

6- Guardar y salir `Ctrl+X`, y actualizamos el archivo grub
```update-grub```

7- Una vez actualizado el grub reiniciamos `reboot`
