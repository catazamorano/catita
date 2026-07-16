# Sitio de Catalina Zamorano Liberón

Landing estática, sin backend, sin dependencias externas en tiempo de ejecución.
Pensada para GitHub Pages (gratis).

```
index.html          La landing
privacidad.html     Política de privacidad
404.html            Página de error
robots.txt          Para buscadores
sitemap.xml         Para buscadores
assets/styles.css   Todo el CSS (dirección "Ciruela")
assets/fonts/       Alegreya + Alegreya Sans, autoalojadas (184 KB)
assets/og.png       Imagen que aparece al compartir el link (1200x630)
assets/icon-*.png   Íconos de pestaña y de iOS
.nojekyll           Evita que GitHub Pages procese el sitio con Jekyll
.gitignore          Deja fuera .claude/ y prototipos/ del repo público
prototipos/         Las 3 direcciones que se compararon. No se publica.
```

---

## ANTES DE PUBLICAR

### 1. El formulario — LISTO

La access key de Web3Forms ya está puesta en `index.html`. Apunta a
`zlcatalina.causas@gmail.com`.

Plan gratis: 250 envíos al mes. La key queda visible en el código fuente —
es normal y así funciona Web3Forms. La protección contra bots es el campo
trampa (`botcheck`) que ya está puesto. Si igual llega spam, se puede
activar hCaptcha desde el panel de Web3Forms.

**Pendiente: enviar una consulta de prueba** y confirmar que llega a Gmail.
Revisa también la carpeta de spam — la primera vez Gmail suele mandarla ahí;
márcala como "no es spam" y las siguientes llegan a la bandeja normal.

### 2. Dominio — LISTO

`catalinazamorano.cl`, registrado en NIC Chile el 16-07-2026 a nombre de
Catalina Andrea Zamorano Liberón. **Vence el 16-07-2027** — ponlo en el
calendario, si se cae el dominio se cae el sitio y el correo.

DNS delegado a Cloudflare (`fay.ns.cloudflare.com`, `oswald.ns.cloudflare.com`).
El archivo `CNAME` de este repo ya tiene el dominio.

Después de publicar, **comprueba la vista previa pegándote el link a ti
mismo por WhatsApp** — es el canal principal de ella y `og:image` depende
de que el dominio resuelva.

### 3. Revisión legal — LISTA

Catalina revisó y aprobó el contenido legal el 16 de julio de 2026: las 7
preguntas frecuentes de `index.html` (plazos de divorcio, pisos y tope de
la pensión de alimentos, efectos del Registro Nacional de Deudores,
mediación previa obligatoria) y la política de privacidad.

**Si alguien edita ese contenido más adelante, tiene que volver a pasar por
ella.** Y la regla que no se toca: nada en el sitio promete resultados, que
es lo que restringe el Código de Ética del Colegio de Abogados.

---

## Publicar

```bash
cd /mnt/c/laragon/www/catita
git init
git add .
git commit -m "Sitio de Catalina Zamorano"
git branch -M main
git remote add origin https://github.com/catazamorano/catita.git
git push -u origin main
```

El repo debe ser **público** para que Pages sea gratis. El `.gitignore` ya
deja fuera `.claude/` y `prototipos/`.

Luego en GitHub: **Settings → Pages → Source: Deploy from a branch →
main / (root)**. Al detectar el archivo `CNAME`, GitHub toma el dominio
solo. Espera a que aparezca el check verde y recién ahí marca
**Enforce HTTPS** (el certificado tarda unos minutos en emitirse).

### Registros DNS en Cloudflare

| Tipo | Nombre | Valor | Proxy |
|---|---|---|---|
| A | @ | 185.199.108.153 | **DNS only** |
| A | @ | 185.199.109.153 | **DNS only** |
| A | @ | 185.199.110.153 | **DNS only** |
| A | @ | 185.199.111.153 | **DNS only** |
| CNAME | www | `catazamorano.github.io` | **DNS only** |

**La nube tiene que estar gris, no naranja.** Con el proxy de Cloudflare
activado, GitHub no puede emitir el certificado y el sitio queda en bucle
de redirecciones. Es el error más común de esta combinación.

Comprobar que resolvió:

```bash
dig +short A catalinazamorano.cl        # debe devolver las 4 IPs de GitHub
curl -sI https://catalinazamorano.cl | head -1
```

---

## Cuando llegue la foto

El panel oscuro está diseñado para funcionar sin retrato, pero el hueco
está listo. En `index.html`, dentro de `<aside class="panel">`, hay un
bloque comentado:

```html
<!-- Cuando llegue el retrato, va aquí:
<img class="panel__portrait" src="assets/catalina.jpg" ...>
-->
```

Descoméntalo y pon la foto en `assets/catalina.jpg`. Vertical (3:4),
idealmente 600×750 o más. Guárdala como JPG optimizado, bajo 200 KB.

---

## Decisiones tomadas, para que no se deshagan por accidente

- **Sin Google Fonts.** Las tipografías están autoalojadas a propósito: así
  Google no recibe la IP de cada visitante. En un sitio con política de
  privacidad y datos sensibles, enlazar fuentes externas sería contradictorio.
- **Sin analytics ni cookies.** Por eso la política de privacidad puede ser
  corta y verdadera. Si algún día se agrega Google Analytics, hay que
  reescribir esa página y probablemente agregar un banner de cookies.
- **Sin testimonios.** Inventarlos no es opción, y pedirlos a clientes de
  causas de familia es delicado por confidencialidad.
- **Sin "años de experiencia".** Catalina se tituló en 2026. El sitio no
  reclama trayectoria que no existe; apuesta por lo que sí es cierto y
  además es una ventaja real: contesta ella, lleva pocas causas, primera
  consulta gratis.
- **Tema único (claro).** La paleta Ciruela es una decisión de diseño, no
  una omisión de modo oscuro.
