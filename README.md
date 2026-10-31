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

## Créditos y origen

Este paquete (`com.notyitan.tv`) es una **versión modificada** de un port preexistente de Xuper TV para webOS (`com.webosflux.xuptertv.fidelity`, v1.5.11). El trabajo base y gran parte del código del servicio (proxy, relay y `ffmpeg`) son de su autor original: **CristianDev**.

**Por qué esta versión.** En las pruebas del autor de esta modificación, el paquete original estaba incompleto: mostraba muy pocos canales. Esta versión corrige esa parte del catálogo, de modo que aparecen todos los canales y además más películas y series.

**Qué se modificó (v1.5.34):**
- Lógica del catálogo del servicio (`magis.js`), para listar más canales, películas y series.
- Interfaz (`style.css`, `index.html`, `app.js`) e iconos.
- Retirado el botón y el recuadro ADULTO 18+ del menú y de Explorar.
- Nuevo identificador de la app (`com.notyitan.tv`) y nuevos instaladores para Windows y Linux.

**Qué no es mío:** el resto de archivos (recursos gráficos, `proxy.js`, `index.js`, `ffmpeg-relay.js` y el binario `ffmpeg`) se mantiene sin cambios respecto al original. `ffmpeg` se distribuye bajo su propia licencia (`ffmpeg-LICENSE.txt` dentro del paquete).

Proyecto no oficial, sin relación con Xuper TV ni con LG. No incluye contenido audiovisual. Si eres el autor original y quieres que se añada o retire algo, abre un *issue*.

## Si falla

PC y TV en redes distintas, la IP cambió tras reiniciar, o la clave caducó.
