<h1 align="center">🍽️ Augusto Ushuaia</h1>
<p align="center"><b>Un restaurante del fin del mundo, con todo su servicio en una sola plataforma.</b><br>Web pública en 8 idiomas, carta digital, pedidos desde la mesa con QR y un motor de reservas.</p>

<p align="center">
  <a href="https://augusto-ushuaia.vercel.app"><b>🔗 Ver la web en vivo</b></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white">
  <img src="https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white">
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?logo=supabase&logoColor=white">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white">
  <img src="https://img.shields.io/badge/Tailwind-06B6D4?logo=tailwindcss&logoColor=white">
  <img src="https://img.shields.io/badge/n8n-EA4B71?logo=n8n&logoColor=white">
  <img src="https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white">
</p>

<table>
  <tr>
    <td><img src="img/home-desktop.png" alt="Inicio de la web"></td>
    <td width="210"><img src="img/carta-mobile.png" alt="Carta digital en el celular"></td>
  </tr>
  <tr>
    <td align="center"><sub>Inicio</sub></td>
    <td align="center"><sub>Carta digital en el celular</sub></td>
  </tr>
</table>

> **Para ser claro:** es un prototipo personal y no oficial, inspirado en un restaurante de Ushuaia. No está vinculado al restaurante, nunca lo ofrecí ni lo vendí, y lo marcado como DEMO es de prueba.

## La idea

Ushuaia recibe turistas de todo el mundo, y un restaurante ahí necesita algo más que una página linda: que alguien de Corea o de Alemania pueda leer la carta en su idioma, reservar sin llamar por teléfono y pedir desde la mesa sin esperar al mozo para cada cosa. Quise juntar todo eso en una plataforma que el personal también pueda manejar en tiempo real.

## Qué hace

- 🌍 **Web pública en 8 idiomas** (español, inglés, portugués, alemán, italiano, chino, coreano y japonés), con horarios, ubicación con mapa y opiniones.
- 📖 **Carta digital** con buscador y categorías, actualizada desde el restaurante.
- 📱 **Pedidos desde la mesa con QR o NFC**: el pedido pasa primero por el mozo y el cliente ve el estado (recibido → en preparación → listo → entregado).
- 📅 **Motor de reservas** que usan la web y WhatsApp (y, más adelante, la voz) como única fuente de verdad.
- 🧑‍🍳 **Panel del personal** en tiempo real: carta, mesas, pedidos, reservas y equipo.
- 🥽 **Vista 3D/AR** de algunos platos, pidiendo permiso de cámara de forma explícita.

## Cómo está armado

```mermaid
flowchart LR
  C[Comensal] --> WEB[Web pública<br/>Next.js · 8 idiomas]
  C --> MESA[App de mesa<br/>QR / NFC]
  P[Personal] --> PANEL[Panel en tiempo real]
  WA[WhatsApp] --> N8N[n8n]
  WEB --> DB
  MESA --> DB
  PANEL --> DB
  N8N --> DB
  subgraph Supabase
    DB[(PostgreSQL<br/>RLS + Realtime<br/>motor de reservas)]
  end
```

## Decisiones de las que estoy orgulloso

- **Nunca se vende dos veces la misma mesa.** El motor de reservas usa bloqueos y una restricción de exclusión en PostgreSQL, así que aunque dos personas reserven en el mismo segundo, una sola gana. Lo pruebo con **60 verificaciones en SQL** y una prueba de concurrencia.
- **Reservas "en espera" de 5 minutos**, idempotencia y avisos con reintentos: si algo falla a mitad de camino, no queda una reserva fantasma.
- **El QR de la mesa nunca da acceso de administrador**, y las funciones que usa el bot están cerradas para el público.
- **Datos honestos**: lo que viene de fuentes verificadas del restaurante se marca así, y lo que no está confirmado se marca como DEMO.

## ¿Y el código?

El repositorio es privado porque el proyecto sigue en desarrollo. Lo muestro con gusto en una entrevista.

---

**Tomás Frem** · Tolhuin, Tierra del Fuego · [LinkedIn](https://www.linkedin.com/in/tomas-frem) · [Todos mis proyectos](https://github.com/ttom0001)
