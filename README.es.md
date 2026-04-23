# 🏢 AI Accounting Controller — Plantilla White-Label

> **Plantilla AI Agent plug-and-play para flujos de trabajo contables de pequeños negocios en EE.UU.**
> Completa el asistente → Obtén un workspace personalizado en 5 minutos → El AI Agent hace de Corporate Controller para tu empresa.

**Versión:** 1.0.0 (estable) • **Developer:** mikenguyen.dev@gmail.com • **Licencia:** Ver [LICENSE](LICENSE)

**Idiomas:** 🇬🇧 [English](README.md) • 🇻🇳 [Tiếng Việt](README.vi.md) • 🇪🇸 Español (este archivo)

**👉 ¿Nuevo? Lee primero [QUICKSTART.es.md](QUICKSTART.es.md) — guía detallada para usuarios sin experiencia técnica.**

---

## 🎯 ¿Qué es esto?

Plantilla reusable que te permite desplegar un AI Agent como **Corporate Accounting Controller** para:

- ✅ **Gestión AP/AR** — Facturas de proveedores, facturas de clientes, reportes de aging
- ✅ **Libro Mayor (General Ledger)** — Journal entries, asientos de ajuste, balance de comprobación
- ✅ **Conciliación Bancaria** — Hojas de conciliación mensuales
- ✅ **Cumplimiento Fiscal** — Federal (1120/1120-S/1065/Schedule C) + Estatal + Nómina
- ✅ **Nómina** — Procesamiento W-2/1099, retenciones federales + estatales
- ✅ **Reportes Financieros** — P&L, Balance General, Flujo de Efectivo según US GAAP
- ✅ **Presupuesto & Variación** — Análisis por departamento con recomendaciones de reforecast

**Compatible con US GAAP + IRS**, diseñado para **dueños de negocios estadounidenses hispanohablantes**, pero funciona igualmente bien para usuarios solo en inglés (configura `owner.preferred_language: "en"` en el config).

**Cobertura:**
- 6 tipos de entidad × 10 estados detallados × 5 industrias = **300 configuraciones completamente modeladas**
- 41 estados adicionales soportados vía modo Lenient (fallback genérico)
- 10 plantillas Excel para operaciones diarias (JE, TB, Bank Recon, AR/AP Aging, P&L, BS, CF, Nómina, Presupuesto)
- 18 tipos de tareas contables vía formularios en navegador con protocolos de respuesta de AI

---

## 🚀 Inicio Rápido — 3 caminos

### 🅰️ Camino A: Onboarding de nuevo negocio (orientado al cliente)

**Cuándo usar:** Estás incorporando un nuevo cliente (o tu propio negocio) a la plantilla.

**Tiempo:** ~5 min asistente + ~5 min render de AI.

1. **Completa el asistente:**
   Abre [_CONFIG/setup_wizard.html](_CONFIG/setup_wizard.html) en tu navegador (Chrome/Edge recomendado).
   Completa 6 pasos: Identidad del Negocio → Ubicación → Operaciones → Propietario → Cumplimiento → Revisión.
   Haz clic en **Download JSON** y **Download Checklist**.

2. **Guarda descargas** en una nueva carpeta: `_INSTANCES/{tu_instance_id}/`

3. **Prompt al AI Agent:**
   > *"Lee `_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md` y renderiza mi workspace desde `_INSTANCES/{tu_instance_id}/_BUSINESS_CONFIG.json`."*

4. **AI ejecuta 7 pasos:** valida config → crea árbol de carpetas → renderiza 5 MDs → copia COA → reporta items críticos.

5. **Listo.** Tu workspace está activo. Abre `Accounting_Task_Form.html` e inicia tu primera tarea.

**📖 ¿Sin experiencia técnica? Lee [QUICKSTART.es.md](QUICKSTART.es.md) con guía paso-a-paso detallada + casos de estudio diarios.**

### 🅱️ Camino B: CFO Fraccional / multi-cliente

**Cuándo usar:** Manejas varios negocios (1 plantilla, N instancias).

1. Para cada cliente, ejecuta el Camino A — cada cliente obtiene su propia carpeta `_INSTANCES/{client_id}/`.
2. El formulario HTML tiene un **⚙️ switcher** en el encabezado — haz clic para cargar un config diferente sin recargar.
3. Atajo URL: `Accounting_Task_Form.html?config=_INSTANCES/Cliente_A/_BUSINESS_CONFIG.json`
4. Configs recientes guardados en localStorage (últimos 5 mostrados como botones de cambio rápido).

### 🅲 Camino C: Entrega al cliente (zip + email)

**Cuándo usar:** Quieres empaquetar el workspace del cliente como un zip autocontenido para enviárselo.

1. Después del Camino A, pide al AI: *"Crea un paquete de entrega al cliente (Opción A mínima) para `{customer_id}`."*
2. AI crea `_DELIVERIES/{customer_id}_v1.0_YYYY-MM-DD/` con todo lo que el cliente necesita (instancia + formularios HTML + módulos relevantes).
3. Comprime esa carpeta (Windows: clic derecho → Enviar a → Carpeta comprimida) o PowerShell: `Compress-Archive`.
4. Envía el zip al cliente por email. Ellos descomprimen, abren `START_HERE.md`, y ejecutan su propio AI.

---

## ⚙️ Configuraciones soportadas

### Tipos de Entidad (6)

| Tipo | Formulario Fiscal | Regla de Compensación del Propietario | ¿Pass-through? |
|------|-------------------|----------------------------------------|:--------------:|
| C-Corp | Form 1120 | Salario O dividendos | ❌ (doble tributación) |
| S-Corp | Form 1120-S | **Compensación razonable ANTES de distribuciones** (disparador #1 de auditoría IRS) | ✅ vía K-1 |
| LLC-single | Schedule C | Owner draw + impuesto SE | ✅ |
| LLC-multi | Form 1065 | Pagos garantizados + K-1 | ✅ |
| Partnership | Form 1065 | Pagos garantizados + K-1 | ✅ |
| Sole-Prop | Schedule C | Owner draw + impuesto SE | ✅ |

Reglas detalladas en [_MODULES/entity/](_MODULES/entity/).

### Estados (10 detallados + 41 vía fallback)

**Módulos completos** (obligaciones fiscales, deadlines, tasas de nómina, retenciones, impuestos por entidad):

CA, NY, TX, FL, DE, WA, IL, GA, NJ, MA

Ver [_state_matrix.csv](_MODULES/state/_state_matrix.csv) para tabla de consulta rápida.

**Los otros 40 estados:** El render funciona pero las reglas estado-específicas requieren búsqueda manual (AI lo marca). Fase 2.5 planeada para llenar los huecos — ver [CONTRIBUTING.md](CONTRIBUTING.md#add-a-new-state-module).

### Industrias (5)

| Industria | Nº Cuentas COA | Cuentas clave |
|-----------|:--------------:|---------------|
| Servicios | 60 | Enfoque consultoría/agencia, sin inventario |
| Retail | 75 | Inventario + Impuesto sobre Ventas por Pagar + Tarjetas de Regalo |
| Restaurante | 70 | División Comida/Bebida/Cerveza/Vino/Licores + Propinas por Pagar |
| Manufactura | 80 | Inventario de 3 niveles (Materia Prima/WIP/Terminado) + gastos indirectos |
| SaaS | 65 | Ingresos Diferidos + Comisiones Capitalizadas (ASC 606) |

---

## 🤖 Compatibilidad con AI Agents

Probados y recomendados:

- **Claude (Anthropic)** — Plataforma principal probada, Opus 4.7 / Sonnet 4.6
- **ChatGPT (OpenAI)** — Clase GPT-4o, compatible con ajustes menores de prompt
- **Gemini (Google)** — 1.5 Pro / 2.0 probado

**Ventana de contexto:** ≥200K tokens recomendado. Los documentos principales + módulos relevantes totalizan ~80–120 KB (~25–35K tokens) dependiendo de entidad × estado.

**Primer prompt** para cualquier sesión nueva de AI (copia-pega esto):
> *"Lee estos archivos en orden: `_BUSINESS_CONFIG.json`, `AI_AGENT_MEMORY.md`, `COMPANY_PROFILE.md`, `FORM_SCHEMA.md`. Confirma el contexto cargado (entidad, estado, año fiscal, próxima fecha límite), luego pregúntame qué tarea quiero trabajar."*

---

## 📚 Documentación

| Archivo | Propósito |
|---------|-----------|
| [README.md](README.md) | Visión general del proyecto (inglés) |
| **[QUICKSTART.es.md](QUICKSTART.es.md)** | **Guía detallada para principiantes (español)** ⭐ |
| [CHANGELOG.md](CHANGELOG.md) | Historial de versiones + lista completa de características v1.0.0 |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Cómo extender la plantilla (para desarrolladores) |
| [_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md](_CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md) | Flujo de trabajo del AI agent en 7 pasos |
| [_CORE/RENDER_PROTOCOL.md](_CORE/RENDER_PROTOCOL.md) | Algoritmo de resolución de plantillas de 7 pases |

---

## ⚠️ Descargos de responsabilidad

- **No es asesoramiento legal/fiscal.** La plantilla proporciona automatización de flujos contables. **Siempre consulta a un CPA licenciado** para decisiones fiscales complejas, auditorías, o asuntos específicos de jurisdicción.
- **Precisión de cumplimiento.** Las tasas de impuestos y reglas están actualizadas a las fechas de publicación de 2026. Las leyes cambian — verifica con CPA antes de presentar. Ver [CONTRIBUTING.md](CONTRIBUTING.md#update-existing-modules-annual-tax-refresh) para el proceso de actualización anual.
- **Riesgo de alucinación de AI.** Los AI Agents pueden cometer errores. Siempre verifica números críticos, especialmente antes del cierre de mes o presentación de impuestos. Usa la fase **Confirm** del protocolo de AI de 5 fases — nunca lo saltes.
- **Seguridad de datos.** El workspace contiene PII (SSN, EIN, cuentas bancarias). Eres responsable de asegurar los datos al compartir con AI Agents. Considera planes on-prem o AI empresarial con garantías de privacidad para clientes sensibles.

---

## 👤 Developer

**mikenguyen.dev@gmail.com**

- Reportes de bugs + solicitudes de características: email
- Licenciamiento comercial (despliegue SaaS multi-tenant, reventa white-label): email
- Propuestas de contribución (nuevo módulo estatal, nueva industria, etc.): ver [CONTRIBUTING.md](CONTRIBUTING.md)

---

*Hecho con ❤️ para dueños de negocios estadounidenses hispanohablantes — y para todos los demás.*
