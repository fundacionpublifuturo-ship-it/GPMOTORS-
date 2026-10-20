# GP MOTORS · Sitio web + Panel de administración

Catálogo web para GP MOTORS (venta de carros y motos de gama media-alta) en Ibagué, Colombia. Incluye el sitio público y un panel de administración interno para gestionar el inventario sin tocar código.

**Stack:** HTML + CSS + JavaScript vanilla · Vercel (hosting) · Supabase (opcional, cuando se conecte)

---

## Estructura del repositorio

```
gpmotors-web/
├── index.html         Página pública con el catálogo
├── admin.html         Panel de administración (/admin)
├── vercel.json        Configuración de deploy, headers y clean URLs
├── robots.txt         SEO: bloquea indexación del admin
├── .gitignore         Exclusiones de git
└── README.md          Este archivo
```

Todo el sitio es estático: no hay backend propio ni build step. Vercel lo publica tal cual.

---

## URLs del sitio en producción

| Ruta | Qué es | Público |
|------|--------|---------|
| `/` | Página pública con el catálogo de vehículos | Sí |
| `/admin` | Panel de administración (login) | No (noindex) |

---

## Deploy en Vercel (paso a paso)

### 1. Subir el repo a GitHub

Opción A — con GitHub Desktop (más fácil si no usas terminal):
1. Instala [GitHub Desktop](https://desktop.github.com/).
2. Inicia sesión con tu cuenta de GitHub.
3. **File → New repository**, nombre `gpmotors-web`, local path a esta carpeta.
4. **Publish repository** (déjalo privado si quieres).

Opción B — con terminal:
```bash
cd /ruta/a/gpmotors-web
git init
git add .
git commit -m "Initial commit: GP MOTORS web + admin"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/gpmotors-web.git
git push -u origin main
```

### 2. Conectar con Vercel

1. Entra a [vercel.com](https://vercel.com) y crea cuenta con tu GitHub.
2. **Add New → Project**.
3. Importa el repo `gpmotors-web`.
4. Framework Preset: **Other** (es sitio estático).
5. **Deploy**. Primer deploy en ~30 segundos.

Cada `git push` a `main` dispara un redeploy automático.

### 3. Dominio custom

Compra el dominio en Namecheap, GoDaddy o similar (sugerencia: `gpmotors.co`). En Vercel:

1. **Settings → Domains → Add**.
2. Pega el dominio.
3. Sigue las instrucciones para apuntar los nameservers o registros A/CNAME al proveedor de dominio.
4. Vercel emite el certificado HTTPS automático en ~5 minutos.

### 4. Actualizar `robots.txt` con el dominio real

Edita `robots.txt`, descomenta y cambia la línea del Sitemap por tu dominio. Haz commit y push.

---

## Flujo de trabajo diario (editar vehículos)

El panel admin trabaja en modo local (datos guardados en el navegador) hasta que configures Supabase. Mientras tanto, el flujo es:

1. Entra a `tu-dominio.com/admin`.
2. Login (credenciales por defecto: `admin` / `gpmotors2026` — **cámbialas en Configuración apenas entres**).
3. Agrega, edita o cambia estados de vehículos.
4. Cuando termines: **Exportar / Importar → Generar código para index.html → Copiar al portapapeles**.
5. Pega el bloque en `index.html`, reemplazando el array `products = [...]` actual.
6. `git commit -am "Actualizar inventario"` y `git push`.
7. Vercel redespliega automáticamente en segundos.

**Nota:** Este flujo manual aplica mientras no esté conectado Supabase. Cuando conectes el backend, los cambios del admin se reflejan en el sitio público en tiempo real sin tocar código.

---

## Credenciales por defecto del admin

- Usuario: `admin`
- Contraseña: `gpmotors2026`

**Cámbialas apenas entres por primera vez** en Configuración → Credenciales. La nueva clave se guarda cifrada solo en el navegador donde la cambies (modo local).

---

## Compatibilidad

- Chrome / Edge / Firefox / Safari actuales.
- iOS 15+ y Android 10+.
- No requiere JavaScript framework ni dependencias externas (excepto Supabase cuando se conecte, que se carga desde CDN).

---

## Pendientes para producción completa

Ver conversación de diseño; las prioridades son:
1. Conectar Supabase para que el admin sincronice en vivo con todos los asesores.
2. Agregar el inventario completo (hoy solo hay 2 vehículos de ejemplo).
3. Meta Pixel + GA4 para tracking.
4. Formulario de "Vende tu carro" (consignaciones).
5. Políticas de privacidad y cookies (obligatorias en Colombia por Ley 1581 Habeas Data).

---

## Contacto / Negocio

- GP MOTORS · Ibagué, Colombia
- Dirección: Carrera 6 #31-14, San Simón parte alta
- Horario: Lunes a Sábado · 8:00 am – 6:00 pm
- WhatsApp asesores: +57 310 447 8680 · +57 310 222 6068 · +57 322 900 0063

---

Desarrollado por **PUBLISELL** (David Fernando Uribe Rodríguez)
