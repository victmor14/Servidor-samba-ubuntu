# Servidor-samba-ubuntu
Configuración de Samba en VM ubuntu para compartir archivos con windows

🧰 Proyecto: Servidor Samba en Ubuntu Server (VirtualBox)
📦 Descripción
Este proyecto configura un servidor Samba sobre Ubuntu Server alojado en una máquina virtual. El objetivo principal fue compartir archivos con clientes Windows en red local, resolver errores de conexión comunes y documentar cada paso del proceso — incluyendo problemas reales como bloqueos por NAT y políticas de seguridad en Windows.

🖥️ Tecnologías usadas
Componente	                            Detalle
Sistema base	                    Ubuntu Server (en VirtualBox)
Protocolo de red	                SMB/CIFS
Cliente	                          Windows 10 / Windows 11
Herramientas	                    Samba, Netstat, UFW, Regedit
Documentación	                    Markdown para GitHub

🧪 Funcionalidades configuradas
Instalación y configuración de Samba desde consola
Creación de carpetas compartidas (Compartido, TestPublico)
Acceso por usuario autenticado (victor_samba) y modo invitado
Revisión de errores: permisos, puertos, visibilidad en Windows
Desbloqueo de políticas de seguridad en Windows
Cambio de red NAT ➜ puente (bridged) para visibilidad real

🛑 Errores enfrentados y resueltos
Error	                                    Solución aplicada
“Windows no puede acceder a…”	          Revisión de puertos y políticas en Windows
Puerto 445 inaccesible desde Windows	  Activar red privada, desbloqueo por firewall
NAT bloqueando Samba en VirtualBox	    Cambio a red tipo puente (Bridged)
Carpeta no visible en red	              Revisión de permisos y smb.conf correcto
Falta de logs Samba por cliente	        Verificación por hostname en /var/log/samba/

📂 Estructura del servidor Samba
ini
[Compartido]
   path = /srv/samba/compartido
   browseable = yes
   read only = no
   guest ok = no
   valid users = victor_samba

[TestPublico]
   path = /srv/samba/test_publico
   browseable = yes
   read only = no
   guest ok = yes
   
🧠 Lecciones aprendidas
Entender bien el rol de las redes virtuales y sus limitaciones
Las políticas de seguridad de Windows pueden bloquear conexiones invisiblemente
Configurar Samba no es solo editar smb.conf: involucra firewalls, red, usuarios y cliente
La depuración paciente y estructurada marca la diferencia

✨ Autor
Nombre	
Victor Morales
