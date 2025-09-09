# ssh_github
# Laboratorio: Configuración de clave SSH para GitHub

Este repositorio documenta el proceso para generar y usar **claves SSH pública/privada** para autenticarte con GitHub desde una máquina local (Kali Linux), evitando el uso de contraseña al interactuar con repositorios.

---

## 🔹 Objetivo
- Configurar un par de claves SSH (pública/privada) para GitHub.  
- Añadir la clave pública a la cuenta de GitHub.  
- Probar la conexión mediante SSH para garantizar autenticación correcta.  

---

## 🔹 Requisitos
- Kali Linux (o cualquier distribución basada en Debian).  
- Usuario con permisos `sudo`.  
- Git instalado.  
- Cuenta activa en GitHub.  

---

## 🔹 Pasos realizados

### 1. Verificar las claves SSH existentes
```bash
ls -al ~/.ssh
```

### 2. Añadir la clave privada al agente SSH
eval "$(ssh-agent -s)"
```bash
ssh-add ~/.ssh/id_ed25519
```

- Esto permite que Git utilice la clave automáticamente para autenticación.
### 3. Verificar la clave pública
```bash
cat ~/.ssh/id_ed25519.pub
```

-Esta es la clave que se debe copiar en GitHub → Settings → SSH and GPG keys → New SSH key.

### 4. Probar la conexión con GitHub
```bash 
ssh -T git@github.com
```

Salida:
```bash
The authenticity of host 'github.com (140.82.114.3)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Hi JoanDaniel18! You've successfully authenticated, but GitHub does not provide shell access.
```

## Observaciones

La clave privada nunca debe compartirse.
Se recomienda usar passphrase para mayor seguridad.
Este método funciona para cualquier repositorio GitHub asociado a la cuenta.
La autenticación SSH elimina la necesidad de usar contraseñas en cada operación Git.

## Autor

Nombre: Joan Daniel Rivas Andrade
Materia: Cyberseguridad
Usuario GitHub: JoanDaniel18\
Fecha: Septiembre 2025
