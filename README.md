# XuperTV para LG webOS

Paquete `.ipk` (v1.5.34) e instaladores para televisores LG con webOS (probado en webOS 4).

> Proyecto no oficial, sin relación con XuperTV ni con LG. No incluye contenido audiovisual.

## Antes de empezar

1. Conecta el ordenador y la TV a la **misma red**.
2. En la TV abre la app **Developer Mode** (LG Content Store), actívala, deja que reinicie y anota la **IP** y la **clave** (passphrase) que muestra. El modo dura 50 horas; la app queda instalada aunque caduque.

## Windows

Extrae la carpeta completa y haz doble clic en `INSTALAR-XUPERTV.bat`. Guía con dibujos: `guia-instalacion.html`.

## Linux / macOS

```bash
./instalar-linux.sh IP_DE_LA_TV CLAVE
```

Solo necesita `ssh`, `curl` y `ar`. Descarga la llave de la TV (Key Server, puerto 9991), la descifra con la clave, sube el `.ipk` por SSH (puerto 9922) y lo instala con el servicio de webOS.

## Alternativa con ares-cli

```bash
npm i -g @webos-tools/cli
ares-setup-device --add tv --info "{'host':'IP','port':'9922','username':'prisoner'}"
ares-novacom --device tv --getkey
ares-install --device tv com.notyitan.tv_1.5.34_all.ipk
ares-launch --device tv com.notyitan.tv
```

## Si falla

PC y TV en redes distintas, la IP cambió tras reiniciar, o la clave caducó.
