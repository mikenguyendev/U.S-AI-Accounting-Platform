# 🚀 Guía de Inicio Rápido — Para Principiantes (Sin Habilidades de IT)

> **Esta guía es para dueños de negocios, NO programadores.** Sin código. Sin línea de comandos. Sin jerga técnica. Si sabes usar email y un navegador web, puedes usar este sistema.

**Idiomas:** 🇬🇧 [English](QUICKSTART.md) • 🇻🇳 [Tiếng Việt](QUICKSTART.vi.md) • 🇪🇸 Español (este archivo)

---

## 📋 Lo que necesitas antes de empezar

Solo 3 cosas — nada que instalar:

1. **Un navegador web** — Chrome, Edge, Safari, o Firefox (probablemente ya lo tienes)
2. **Una cuenta de AI chat** — una de estas cuentas gratis funciona:
   - Claude: https://claude.ai (recomendado — el mejor para este workspace)
   - ChatGPT: https://chat.openai.com
   - Gemini: https://gemini.google.com
3. **Información de tu empresa** — ten lista:
   - Nombre legal del negocio
   - Tipo de entidad (LLC, S-Corp, C-Corp, etc. — tu CPA lo sabe)
   - Estado donde operas (ej: California, Texas)
   - Tu nombre + email + teléfono
   - Año fiscal (usualmente enero–diciembre)

**Tiempo de configuración:** 10–15 minutos. Una sola vez.

---

## 🎯 Parte 1: Configuración Inicial (10 minutos)

### Paso 1: Descargar la plantilla

1. Ve a la página de GitHub (o pide el archivo zip a quien te dio el enlace)
2. Haz clic en el botón verde **"Code"** → **"Download ZIP"**
3. Encuentra el archivo zip descargado en tu carpeta Downloads
4. **Clic derecho** en el zip → **"Extract All"** → elige una ubicación que recuerdes (ejemplo: `Desktop/Mi_Contabilidad/`)

Ahora deberías ver una carpeta con archivos como `Accounting_Task_Form.html`, `_CONFIG/`, `_CORE/`, etc.

### Paso 2: Abrir el asistente de configuración

1. Abre la carpeta `_CONFIG`
2. **Doble clic** en el archivo `setup_wizard.html`
3. Se abrirá en tu navegador, mostrando un asistente azul y blanco

Si no se abre automáticamente: clic derecho en el archivo → **"Open with"** → elige Chrome o Edge.

### Paso 3: Completar el asistente de 6 pasos

El asistente te guiará por 6 pantallas. La mayoría de campos son opcionales — solo los marcados con `*` rojo son obligatorios.

| Paso | Qué ingresar |
|:----:|--------------|
| 1️⃣ Identidad del Negocio | Nombre legal, DBA (si aplica), EIN (si lo tienes), tipo de entidad, industria |
| 2️⃣ Ubicación & Impuestos | Estado de operación (ej: CA para California), año fiscal |
| 3️⃣ Operaciones | Software de contabilidad (QuickBooks / Excel / Google Sheets), base acumulada o efectivo, umbrales de aprobación |
| 4️⃣ Info del Dueño | Tu nombre, email, rol (Owner), idioma preferido |
| 5️⃣ Cumplimiento | Marca los items ya completados (EIN, BOI filing, registro estatal, etc.) |
| 6️⃣ Revisión | Verifica todo, luego clic en **Download JSON** y **Download Checklist** |

💡 **¿No sabes una respuesta?** Déjalo en blanco. Puedes actualizar después. Consulta a tu CPA para preguntas específicas de impuestos (tipo de entidad, EIN).

### Paso 4: Guardar tu workspace

Después de descargar los 2 archivos del asistente:

1. Vuelve a la carpeta de la plantilla
2. Abre la carpeta `_INSTANCES`
3. Crea una nueva carpeta adentro, con el nombre de tu empresa (sin espacios — usa guiones bajos): ejemplo `Mi_Cafeteria_LLC`
4. Mueve los 2 archivos descargados (`_BUSINESS_CONFIG.json` y `ONBOARDING_CHECKLIST.md`) dentro de esa nueva carpeta

Tu estructura de carpetas debe verse así:
```
Mi_Contabilidad/
├── _INSTANCES/
│   └── Mi_Cafeteria_LLC/              ← Tu workspace vive aquí
│       ├── _BUSINESS_CONFIG.json      ← Movido de Downloads
│       └── ONBOARDING_CHECKLIST.md    ← Movido de Downloads
├── Accounting_Task_Form.html
└── ... (otros archivos de la plantilla)
```

### Paso 5: Decirle a AI que construya tu workspace

1. Abre https://claude.ai (o el AI que elegiste)
2. Inicia un chat nuevo
3. **Sube los archivos de la plantilla** (arrastra-y-suelta la carpeta completa, o hazle zip primero)
4. Copia-pega este prompt exacto:

```
Estoy configurando un nuevo workspace desde el AI Accounting Template.
Mi config está en _INSTANCES/{nombre_de_tu_carpeta}/_BUSINESS_CONFIG.json

Por favor lee _CONFIG/NEW_BUSINESS_ONBOARDING_PROTOCOL.md y sigue el protocolo
de 7 pasos para renderizar mi workspace. Cuando termines, muéstrame:
1. Un resumen de lo que se creó
2. Los 3 items más urgentes de mi onboarding checklist
3. Qué debo hacer a continuación
```

Reemplaza `{nombre_de_tu_carpeta}` con el nombre real de tu carpeta.

El AI leerá la plantilla, entenderá tu negocio, y creará 5–6 documentos personalizados en tu carpeta. Toma 3–5 minutos.

### Paso 6: Verificar la configuración

1. Vuelve a tu carpeta en el Explorador de Archivos
2. Tu carpeta de workspace ahora debería tener muchos más archivos: `README.md`, `COMPANY_PROFILE.md`, `AI_AGENT_MEMORY.md`, etc.
3. Abre `README.md` — debería mostrar el nombre de tu empresa al inicio
4. Abre `Accounting_Task_Form.html` (el principal, no el que está en `_CONFIG`)
5. El encabezado debe mostrar el nombre de tu empresa

✅ **¡Configuración terminada!** De ahora en adelante, usarás el Task Form + AI chat para contabilidad diaria.

---

## 💬 Parte 2: Cómo Hablar con AI (Consejos Esenciales)

### La Regla de Oro

**Sé específico. Da números. Da fechas. Da nombres.**

❌ Malo: *"Registra un gasto"*
✅ Bueno: *"Registra un gasto de $45.80 por almuerzo en Starbucks con el cliente ABC Corp el 22 de abril de 2026. Pagado con tarjeta de crédito de negocio."*

### Cómo Iniciar Cada Sesión de AI

Al inicio de cada conversación nueva con AI (no cada mensaje — solo el primero del día):

**Copia-pega este prompt:**

```
Estoy abriendo mi workspace de AI Accounting para {nombre de tu empresa}.

Por favor lee estos archivos en orden:
1. _INSTANCES/{nombre_de_tu_carpeta}/_BUSINESS_CONFIG.json
2. _INSTANCES/{nombre_de_tu_carpeta}/AI_AGENT_MEMORY.md
3. _INSTANCES/{nombre_de_tu_carpeta}/COMPANY_PROFILE.md

Luego confirma que cargaste el contexto (dime mi tipo de entidad, estado, año
fiscal, y próxima fecha límite de impuestos), y pregúntame en qué tarea quiero
trabajar hoy.
```

El AI leerá, te resumirá, y preguntará qué necesitas. Listo para trabajar.

### Usar el Task Form (la forma más fácil)

En vez de escribir prompts a mano, deja que el formulario los construya por ti:

1. Abre `Accounting_Task_Form.html` en tu navegador
2. Haz clic en cualquier botón de tarea (ejemplos: "📥 Registrar Factura de Proveedor", "💳 Gasto Menor", "📅 Cierre Mensual")
3. Completa el formulario simple (o solo sube una foto para tareas-foto)
4. Haz clic en **"Copy to AI"** — el formulario automáticamente pone un prompt perfecto en tu portapapeles
5. Pega en tu AI chat (Windows: `Ctrl+V`, Mac: `Cmd+V`)
6. El AI confirmará lo que entendió, luego procesará la tarea

---

## 📚 Parte 3: 5 Casos de Estudio Diarios

Escenarios reales con prompts exactos para copiar-pegar. Estas son las 5 tareas más comunes para un negocio pequeño.

---

### 📥 Caso de Estudio 1: Recibí una factura de proveedor

**Escenario:** Tu proveedor de internet te envió una factura de $120. Quieres registrarla para pagarla la próxima semana.

**Lo que haces:**

1. **Toma una foto** de la factura (usa tu teléfono) o guarda el PDF
2. Abre tu AI chat
3. Copia-pega este prompt + adjunta la foto:

```
📥 Nueva factura de proveedor para registrar.

Vendor: Comcast Business Internet
Monto: $120.00
Fecha de factura: 22 de abril de 2026
Fecha de vencimiento: 22 de mayo de 2026 (Net 30)
Estado de pago: No pagada aún
Categoría: Servicios Públicos / Internet

Adjunto el PDF de la factura. Por favor:
1. Verifica los detalles con la foto
2. Pídeme confirmar antes de registrar
3. Crea el journal entry
4. Guarda el PDF en la carpeta correcta
5. Actualiza mi AP (Accounts Payable) tracker
```

**Lo que hará el AI:**
1. Extrae detalles de tu foto
2. Te muestra una tabla: *"¿Es correcto?"*
3. Después que dices "sí": registra `Dr. Utilities Expense / Cr. Accounts Payable $120`
4. Guarda PDF en `01_AP-AR_Management/Accounts_Payable/Vendor_Invoices/20260422_Invoice_Comcast_$120.00.pdf`
5. Agrega una fila a tu hoja de AP aging

**Tiempo:** ~2 minutos.

---

### 💳 Caso de Estudio 2: Pagué almuerzo con un cliente (recibo de gasto)

**Escenario:** Almorzaste con un cliente potencial ayer en Olive Garden, $68.50, pagado con tarjeta de crédito de negocio.

**Lo que haces:**

1. **Toma una foto** del recibo
2. Abre AI chat, copia-pega + adjunta la foto:

```
💳 Gasto para registrar.

Comercio: Olive Garden
Monto: $68.50
Fecha: 22 de abril de 2026
Pago: Tarjeta de crédito de negocio
Categoría: Meals & Entertainment (50% deducible según IRS)
Propósito de negocio: Almuerzo con cliente potencial ABC Corp para discutir contrato Q3

Por favor registra este gasto, guarda el recibo, y marca la regla del 50% de deducción.
```

**Lo que hará el AI:**
1. Registra: `Dr. Meals & Entertainment $68.50 / Cr. Credit Card Payable $68.50`
2. Guarda recibo: `01_AP-AR_Management/Accounts_Payable/Receipts/20260422_Receipt_OliveGarden_$68.50.jpg`
3. Marca: *"Recuerda: Las comidas solo son 50% deducibles para impuestos. Lo he anotado."*

**💡 Consejo importante:** Siempre incluye **propósito de negocio** para comidas/viajes. IRS Publication 463 lo requiere para deducciones. Genérico "comida de negocios" NO es suficiente — nombra a la persona + tema.

---

### 📤 Caso de Estudio 3: Necesito facturar a mi cliente

**Escenario:** Completaste un proyecto de consultoría para el Cliente ABC Corp y quieres enviarles una factura de $5,000.

**Lo que haces:**

Abre AI chat, copia-pega:

```
📤 Crear factura de cliente.

Cliente: ABC Corp
Dirección del cliente: 123 Main St, Los Angeles, CA 90001
Servicio: Servicios de consultoría — Q2 2026 (1 de abril – 15 de abril de 2026)
Monto: $5,000.00
Términos de pago: Net 30 (vence 22 de mayo de 2026)

Por favor:
1. Genera el siguiente número de factura (formato INV-2026-XXXX)
2. Crea un PDF de factura usando la plantilla estándar
3. Registra journal entry: Dr. A/R / Cr. Service Revenue
4. Guarda la factura y dime dónde
5. Programa un recordatorio de seguimiento de pago 5 días antes del vencimiento
```

**Lo que hará el AI:**
1. Asigna número de factura (ejemplo: INV-2026-0043)
2. Genera PDF
3. Registra: `Dr. 1200 Accounts Receivable $5,000 / Cr. 4010 Service Revenue $5,000`
4. Guarda: `01_AP-AR_Management/Accounts_Receivable/Customer_Invoices/20260422_INV-2026-0043_ABC-Corp_$5,000.00.pdf`
5. Agrega recordatorio: "Seguimiento con ABC Corp el 17 de mayo de 2026"

**Lo que haces después:** Abre el PDF guardado, envíalo por email al cliente. Listo.

---

### 📅 Caso de Estudio 4: Fin de mes — cerrar los libros

**Escenario:** Es 3 de mayo de 2026. Quieres cerrar los libros de abril y ver tu rendimiento financiero.

**Lo que haces:**

1. Primero reúne estos items:
   - Estado de cuenta bancario de abril (PDF del sitio web de tu banco)
   - Estado de tarjeta de crédito de abril
   - Cualquier recibo que no hayas enviado aún

2. Abre AI chat, copia-pega:

```
📅 Iniciar cierre mensual para abril 2026.

Por favor guíame por el proceso completo de cierre mensual:

Paso 1: Pídeme subir el estado de cuenta bancario para reconciliación
Paso 2: Identifica cualquier transacción que no haya registrado
Paso 3: Registra accruals recurrentes (servicios, nómina, intereses)
Paso 4: Calcula depreciación (si tengo activos fijos)
Paso 5: Revisa Trial Balance e investiga cualquier problema
Paso 6: Genera estos reportes:
   - P&L (Estado de Resultados) para abril
   - Balance General al 30 de abril de 2026
   - Flujo de Efectivo (YTD)
   - Variación vs Presupuesto
Paso 7: Dame un resumen ejecutivo de 1 página

Vamos paso a paso. Pídeme cada input cuando lo necesites.
```

**Lo que hará el AI:** Te guía por cada paso uno a la vez. Espera 30–45 minutos total. Al final, tendrás un "paquete de fin de mes" completo guardado en `06_Financial_Reporting/Monthly_Close/2026-04/` — esto es lo que tu CPA o junta directiva querrán ver.

**💡 Consejo:** Haz esto en los primeros 5 días laborables de cada mes para no olvidar nada.

---

### 👤 Caso de Estudio 5: Estoy contratando a mi primer empleado

**Escenario:** Estás por contratar a Sarah Johnson como empleada tiempo completo, salario $65,000/año.

**Lo que haces:**

1. Pide a Sarah que complete estos 3 formularios (imprime desde sitios web de IRS/estado):
   - Federal W-4 (retención de impuestos)
   - Formulario estatal de retención (ej: CA DE-4 para California)
   - I-9 (verificación de elegibilidad para empleo)

2. **Toma fotos** de los 3 formularios completados

3. Abre AI chat, adjunta fotos + copia-pega:

```
👤 Configuración de nuevo empleado.

Empleado: Sarah Johnson
Posición: Marketing Manager
Salario anual: $65,000
Frecuencia de pago: Semi-mensual (día 15 y último del mes)
Fecha de contratación: 1 de mayo de 2026
Beneficios: Seguro médico (sí), 401(k) contribución 3%

Adjunto:
- W-4 (retención federal)
- Formulario estatal de retención
- I-9

Por favor:
1. Extrae toda la info de los formularios
2. Verifica que I-9 esté completo (Sección 1 + 2 + autorización legal de trabajo)
3. Agrega a Sarah a la lista de empleados
4. Calcula vista previa de retención de su primer cheque
5. Recuérdame del reporte estatal de nueva contratación (debe presentarse en 20 días)
6. Recuérdame inscribir a Sarah en seguro de Workers' Comp ANTES de su fecha de inicio

CRÍTICO: Si I-9 no está completo, NO procedas — márcalo para que lo arregle.
```

**Lo que hará el AI:**
1. OCR los 3 formularios
2. Verifica que I-9 esté completo
3. Agrega a Sarah a `05_Payroll/Employees_Roster.xlsx`
4. Guarda formularios en `05_Payroll/Employee_Files/Sarah_Johnson/`
5. Calcula: `Bruto $2,708/cheque → Impuesto federal: $X, Impuesto estatal: $Y, FICA: $Z, Neto: $W`
6. Marca cualquier item faltante

---

## ❓ Parte 4: FAQ / Solución de Problemas

### "El Task Form no muestra el nombre de mi empresa — dice 'Loading…'"

Tu navegador bloqueó la carga automática del config. Arréglalo:
1. Haz clic en el botón **⚙️** en la esquina superior derecha del formulario
2. Haz clic en **"Upload config file"**
3. Navega a `_INSTANCES/{tu_carpeta}/_BUSINESS_CONFIG.json`
4. Selecciónalo → el formulario se actualiza inmediatamente

### "El AI dice que no puede encontrar mis archivos"

Asegúrate de haber subido la carpeta COMPLETA (incluyendo `_CONFIG/`, `_CORE/`, `_MODULES/`, `_INSTANCES/{tu_carpeta}/`) al AI chat. Arrastra y suelta el zip directamente.

### "El AI me dio una respuesta pero está mal sobre reglas de impuestos"

Siempre verifica consejos de impuestos con un CPA licenciado. El AI + plantilla es una herramienta de flujo de trabajo, NO un asesor legal/fiscal. Las tasas de impuestos de la plantilla son precisas al 2026 pero las leyes cambian.

### "Cometí un error en un journal entry — ¿cómo lo arreglo?"

Dile al AI: *"Necesito revertir Journal Entry #JE-2026-0042. Registra una entrada de reversión con débito/crédito opuestos, fechada hoy, con explicación 'Corrigiendo JE-2026-0042 — [razón]'."*

Nunca edites manualmente journal entries registrados — siempre usa entradas de reversión para el audit trail.

### "No sé mi tipo de entidad / EIN / etc."

Pregunta a tu CPA o abogado. O revisa estos documentos:
- **Tipo de entidad:** Mira tus documentos de formación (Articles of Incorporation, Certificate of Formation, Operating Agreement)
- **EIN:** Carta de confirmación de IRS Form SS-4, o el encabezado de tu declaración de impuestos
- **ID Estatal:** Confirmación de registro de tu Secretario de Estado

Deja estos en blanco en el asistente si no estás seguro — puedes actualizar después.

### "Quiero agregar un segundo negocio"

Repite los Pasos 3–6 de la Parte 1. Crea una nueva carpeta `_INSTANCES/Segunda_Empresa/` con su propio config. El Task Form tiene un switcher ⚙️ para cambiar entre ellos.

### "¿Con qué frecuencia debo actualizar este workspace?"

- **Diario:** Registra transacciones cuando ocurran (o tómales foto, procésalas el mismo día)
- **Semanal:** Revisa AP aging, envía recordatorios a clientes por facturas no pagadas
- **Mensual:** Haz el cierre mensual (Caso de Estudio 4)
- **Trimestral:** Pagos de impuestos estimados (15 abr, 15 jun, 15 sep, 15 ene)
- **Anual:** Cierre de fin de año, preparación de impuestos con CPA, presentación de reporte anual

---

## 🆘 Parte 5: Dónde Obtener Ayuda

- **Preguntas técnicas de la plantilla:** Lee `CONTRIBUTING.md` (para desarrolladores) o envía email: mikenguyen.dev@gmail.com
- **Consejo fiscal / contable:** Consulta a un **CPA (Certified Public Accountant) licenciado** — la plantilla NO reemplaza a un CPA
- **Preguntas legales:** Consulta a un abogado de negocios
- **Flujo diario de AI:** Revisa `USE_CASES_GUIDE.md` en tu workspace para 20 escenarios más
- **Actualizar tu config:** Vuelve a ejecutar `_CONFIG/setup_wizard.html`, descarga el nuevo JSON, reemplaza el archivo en tu carpeta de instancia, pídele al AI que vuelva a renderizar

---

## 🎯 Checklist de Tu Primera Semana

Después de la configuración, pasa tu primera semana haciendo estos:

- [ ] Día 1: Completa la configuración (Partes 1–2 de esta guía)
- [ ] Día 1: Abre `ONBOARDING_CHECKLIST.md` y revisa los 30 items — marca lo que ya hiciste
- [ ] Día 2: Ingresa cualquier transacción de los últimos 30 días (Casos de Estudio 1–3)
- [ ] Día 3: Configura conexiones de cuentas bancarias O sube el primer estado de cuenta
- [ ] Día 5: Revisa tu primer reporte P&L (pregunta al AI: *"Muéstrame un P&L para este mes hasta ahora"*)
- [ ] Día 7: Programa recordatorios recurrentes en el calendario:
  - Día 1 del mes: Cierre mensual
  - Día 15 y último del mes: Nómina (si aplica)
  - 15 abr / 15 jun / 15 sep / 15 ene: Pago trimestral de impuestos estimados

---

## 💡 Consejos Finales para Usuarios No Técnicos

1. **No apuntes a perfecto — apunta a consistente.** Perder un día está bien. No registrar transacciones por 2 semanas = malo (olvidarás detalles).

2. **Las fotos son tus amigas.** Toma foto de CADA recibo, factura, cheque, estado de cuenta — inmediatamente. Puedes procesarlas después. Una foto con marca de fecha es a prueba de auditoría.

3. **Si no estás seguro, pregunta al AI primero — luego verifica con CPA.** El AI te da un punto de partida + opciones. El CPA confirma la decisión final para problemas complejos.

4. **Respalda tu workspace mensualmente.** Clic derecho en tu `_INSTANCES/{tu_carpeta}/` → Send to → Compressed folder → guarda una copia en Google Drive o disco externo. Tus datos financieros son irremplazables.

5. **No necesitas memorizar nada.** Cada tarea común está en la Parte 3 arriba. Marca este archivo como favorito.

---

**🎉 Bienvenido al workspace. No estás solo — el AI está aquí para ayudarte en cada paso del camino.**

*AI Accounting Template v1.0.0 • Preguntas: mikenguyen.dev@gmail.com*
