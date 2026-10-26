## Florencia del Castillo

**Analista en Sistemas · Cloud & Software · AWS.** Construyo infraestructura serverless y en contenedores, y documento las
decisiones detrás de cada proyecto. 
Ayudante de cátedra en la UNViMe. 
Villa Mercedes, San Luis 🇦🇷

<sub><a href="#english">🇬🇧 Read in English</a></sub>

---

## Proyectos

### Mi Plan de Estudios: planificador académico

Te dice qué materias podés cursar, qué te está trabando y qué te falta para recibirte, y te avisa
cuando se acerca una fecha del calendario académico o vence una regularidad. Modela el plan de
estudios como un grafo de correlativas, con el catálogo de planes de SIU Guaraní (viejos y nuevos),
e importa tu historial desde el reporte de Guaraní (también en PDF) o un Excel, verificándolo contra
el plan oficial. Suma escenarios de "qué pasa si", una constancia de avance imprimible y un enlace de
solo lectura para compartir el avance con un tutor. Los avisos salen por WhatsApp, Telegram o email.
Corre en una EC2 con
Docker Compose: API (Node + Express + MongoDB) y frontend en contenedores separados detrás de Nginx,
con dominio propio y TLS de Let's Encrypt. Un pipeline de GitHub Actions con OIDC sube las imágenes a
ECR y despliega por SSM, sin SSH ni claves guardadas.

![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?logo=jsonwebtokens&logoColor=white) ![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?logo=docker&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white) ![Let's Encrypt](https://img.shields.io/badge/Let%27s_Encrypt-003A70?logo=letsencrypt&logoColor=white)

[**▸ Probalo**](https://miplandeestudios.com.ar) · en producción, con usuarios reales

### Claudito: optimizador de CVs con IA

Subís un CV, pegás una descripción de puesto, y te devuelve un score de match, sugerencias concretas
que aceptás o descartás una por una, y un PDF en formato Harvard listo para mandar, con una
restricción central: **no inventa nada**. Se puede probar sin cuenta; con cuenta guardás un dossier
de carrera (el registro largo de tus proyectos y logros), que se descompone en unidades de evidencia
en DynamoDB. En cada análisis se eligen las más relevantes para el puesto, cada bullet del CV cita la
unidad que lo respalda y un verificador comprueba que las citas existan y que ninguna cifra quede
fuera del material original. El CV se edita ya formateado, no como Markdown. Es serverless: catorce
Lambdas, Cognito para las cuentas, tres usos de Bedrock (dossier, análisis y generación), WeasyPrint
para el PDF y OCR con Textract para los escaneados. Las sesiones anónimas viven en S3 y se
autodestruyen en 24 a 48 horas; IaC con SAM y deploy por CI/CD con OIDC.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon Textract](https://img.shields.io/badge/Textract-FF9900?logo=amazontextract&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)

[**▸ Probalo**](https://d1u1sqpu5ny5ot.cloudfront.net) · desplegado

### Dockyard: plataforma de deploy tipo Render/Railway

Conectás un repositorio, hacés `git push`, y tu app queda viva en su propio subdominio con HTTPS
válido. Es un proyecto de infraestructura pensado para ser defendible pieza por pieza: en vez de usar
un PaaS, lo construye. Una GitHub App manda un webhook firmado, un worker clona el repo (también los
privados), detecta el stack (Node, Python o Go), construye la imagen Docker, la sube a ECR y la deja
viva detrás de Nginx, con variables de entorno cifradas y secretos en SSM. Un loop de reconciliación
recupera containers caídos y detecta crash loops, y un dashboard muestra logs en vivo y permite
rollback de un click. Todo es reproducible desde cero con CloudFormation, con TLS wildcard vía ACME
DNS-01 y CI con OIDC, sin access keys estáticas. **Fases 0 a 3 completas.**

![CloudFormation](https://img.shields.io/badge/CloudFormation-FF9900?logo=amazonaws&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white) ![Amazon ECR](https://img.shields.io/badge/ECR-FF9900?logo=amazonecr&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white) ![Bash](https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

[**▸ Demo**](https://demo.dockyard.dpdns.org) · Fases 0 a 3 completas

### Costos: gestión para PyMEs gastronómicas

Para que el dueño o dueña de un local gastronómico administre su negocio sin saber de contabilidad:
ventas, gastos, costos, punto de equilibrio, facturación electrónica (ARCA/WSFE) y un asistente que
responde en lenguaje natural con los números reales del negocio. Se cargan datos a mano, con una foto
del ticket (la IA los extrae y clasifica) o con el CSV de "Mis Comprobantes" de ARCA en lote. Suma un
mostrador con lector de código de barras y caja, comparación de proveedores a partir de ofertas en
foto, PDF o texto, rentabilidad por producto, alertas por Telegram y WhatsApp, y cuatro roles con
PIN. Frontend React + Vite (PWA) con el estado en el navegador; una sola Lambda con dos
integraciones: Bedrock (Claude) para la IA y Afip SDK para ARCA. Regla de diseño: se guardan solo
productos, ventas y comprobantes; costo unitario, CIF, equilibrio y alertas se derivan y nunca se
persisten.

![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![PWA](https://img.shields.io/badge/PWA-5A0FC8?logo=pwa&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white)

_Estado: corre local contra la Lambda; todavía sin instancia pública._

### Seguidor-Colectivo: colectivos de Villa Mercedes en tiempo real

Un mapa a pantalla completa que muestra dónde está cada colectivo y cuánto falta para que llegue a
tu parada, más un planificador de viajes. La fuente (ColectivoYa) trae datos que no son confiables
por sí solos, así que la verdad la pone el GPS: guarda los viajes reales en S3 y de ahí aprende los
recorridos de cada ramal, los valida contra las posiciones y oculta las paradas por las que ya no
pasa nadie. También reasigna el sentido (ida o vuelta), que la fuente casi nunca informa bien, y
compara contra la grilla oficial de horarios. Es serverless: CloudFront + S3 para el frontend, una
Lambda, DynamoDB y SAM para la infraestructura.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white)

[**▸ Probalo**](https://d37602x6omnenw.cloudfront.net) · desplegado

### Normativa ISI UNViMe: el digesto, ordenado para acreditar

Relevé el índice completo del digesto de la UNViMe (más de 13.000 documentos), hice OCR de las
resoluciones escaneadas y clasifiqué por contenido las que sirven para la acreditación de Ingeniería
en Sistemas de Información ante la CONEAU, ordenadas por anexo. El resultado es un sitio público con tabla
ordenable, fichas con el PDF de cada resolución y líneas de tiempo que muestran qué norma deja sin
efecto a cuál. Se publica con GitHub Pages y un script regenera todo desde los datos.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white) ![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-222222?logo=githubpages&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

[**▸ Verlo**](https://flordelcastillo.github.io/normativa-isi-unvime/) · [código](https://github.com/flordelcastillo/normativa-isi-unvime)

### CodeJam UNViMe 2026: landing y muro de fotos en vivo

La landing oficial del CodeJam (30/10/2026) y un muro que se actualiza solo durante la jornada: la
gente sube una foto desde el celular con el marco del evento, un panel de admin la modera y aparece en
el proyector con un QR para sumarse. Suma un ranking de equipos que nace oculto hasta que el jurado lo
publica, y un entrenador de pitch con IA (Claude en Bedrock) con topes por IP para controlar el gasto.
Es serverless de punta a punta: CloudFront + S3, una Lambda, DynamoDB y SAM, todo pay-per-use.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white)

[**▸ Verlo**](https://dygd5d0drje17.cloudfront.net) · [código](https://github.com/flordelcastillo/codejam-landing)

### Estantería: galería de proyectos del Club de Programación

Una web donde los miembros del club suben sus proyectos y cualquiera puede explorarlos, filtrarlos
por categoría, tecnologías, año o evento, y votarlos. Las cuentas usan Cognito con verificación por
email, un grupo de administradores modera (destacar, ocultar, editar), y las portadas se suben a S3
con URLs firmadas que fijan tipo y tamaño. Es accesible (teclado, foco visible, tema claro y oscuro,
móvil primero). Todo corre en AWS bajo un único dominio de CloudFront, sin CORS: S3, API Gateway, una
Lambda en Node 22 sin dependencias y DynamoDB, desplegado con SAM.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white)

[**▸ Probalo**](https://d1dj3drky6qwir.cloudfront.net) · desplegado

### Teia Accesorios: tienda online con panel de administración

La tienda de una marca de accesorios, hecha a medida: catálogo con filtros, ficha de producto, carrito,
cupones, guía de talles y opciones de entrega, con pagos por Mercado Pago. Detrás hay un panel de
administración propio para cargar productos con imágenes, ajustar el stock en vivo, ver pedidos y
estados de pago y tener métricas. El webhook de Mercado Pago confirma el pago y descuenta el stock
solo. Es un monolito Next.js con Prisma y PostgreSQL, que se despliega por su cuenta en una EC2.

![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?logo=tailwindcss&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![Prisma](https://img.shields.io/badge/Prisma-2D3748?logo=prisma&logoColor=white) ![Mercado Pago](https://img.shields.io/badge/Mercado_Pago-00B1EA?logo=mercadopago&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white)

[**▸ Visitar**](https://teiaaccesorios.com.ar) · [código](https://github.com/flordelcastillo/tienda-luci)

### Verificador de vigencia bibliográfica: acreditación de la carrera

Parte del trabajo para la acreditación de Ingeniería en Sistemas de Información ante la CONEAU.
Analiza los PDF de los programas de cada materia (formato ministerial) y clasifica cada referencia de
la bibliografía básica y complementaria como actualizada (2016 a 2026), desactualizada o sin año
detectable, que queda para revisión manual. Permite subir varios programas a la vez, corregir a mano
con recálculo inmediato, exportar a Excel y PDF y comparar el historial por materia entre
cuatrimestres. Es serverless en AWS, con login por Cognito.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white)

_Uso interno de la carrera; el código está en un repositorio privado._

### Proyecto Final: agentes de IA para entender el abandono universitario

Mi trabajo final de la carrera, en equipo de dos y con un profesor guía (cierre en enero de 2027).
Es una cadena de agentes que toma datos académicos del sistema de gestión (SIU Guaraní), los integra y
los preprocesa, entrena modelos con AutoML para predecir quién tiene riesgo de abandonar en los
primeros años y, lo más importante, **explica por qué**. A mí me tocan el agente de preprocesamiento y
el de interpretabilidad (SHAP, PDP, LIME y contrafactuales con DiCE), que muestran qué variables
pesan y qué podría cambiar en un caso concreto. Un chequeo automático evita que un modelo flojo pase
como bueno, y los datos de estudiantes no se publican ni se suben al repositorio. Se orquesta con LangGraph; los modelos se entrenan con AutoGluon.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)

_Estado: en desarrollo; el código está en un repositorio privado del equipo._

---

## Sobre mí

Soy **Analista en Sistemas** y estudio Ingeniería en Sistemas de Información en la UNViMe (2022-presente). También soy **ayudante de
cátedra** en *Expresión y Resolución de Problemas y Algoritmos* y *Programación I*. Co-fundé el
**Club de Programación de la UNViMe** y di talleres y charlas en la Semana de la Ingeniería: Git,
HTML/CSS, Notion para ingenieros, y *Primeros Pasos en la Nube con AWS* junto al AWS User Group San
Luis.

**Cómo llegué:** freeCodeCamp → backend con Java en la Universidad Globant (beca Code Your Future) →
AWS Re/Start en Potrero Digital → [**AWS Certified Cloud Practitioner**](https://www.credly.com/badges/736b6e0f-4c60-4a82-aa06-105653a22aae/public_url) (enero 2026) → AWS Academy Educator. Ahora: el CodeJam
UNViMe (30/10) y mi Proyecto Final de la carrera.

### Herramientas

| | |
|---|---|
| **Cloud** | Lambda · S3 · Bedrock · CloudFront · API Gateway · EC2 · ECR · ECS Fargate · Textract · Cognito · SSM · CloudWatch · IAM · VPC |
| **Datos** | DynamoDB · MongoDB · PostgreSQL |
| **IaC** | AWS SAM · CloudFormation |
| **Lenguajes** | Python · TypeScript · JavaScript · SQL · Bash |
| **Frontend** | React · Vite · Tailwind · Zustand · MapLibre |
| **Ops** | Docker · Docker Compose · GitHub Actions (OIDC) · Nginx · TLS (Let's Encrypt) · Linux · DNS |

### Contacto

- [LinkedIn](https://linkedin.com/in/flordelcastillo) · Inglés B2

---

<h2 id="english">🇬🇧 Florencia del Castillo</h2>

**Systems Analyst · Cloud & Software · AWS.** I build serverless and containerized infrastructure, and I document the
decisions behind every project. Teaching assistant at UNViMe. Villa Mercedes, San Luis 🇦🇷

## Projects

### Mi Plan de Estudios: academic planner

Tells you what courses you can take, what's blocking you, and what's left before you graduate, and
pings you when an academic-calendar date is coming up or a course's regular status is about to
expire. It models the curriculum as a prerequisite graph, with the SIU Guaraní catalog of study
plans (old and new), and imports your record from the Guaraní report (PDF too) or an Excel file,
checking it against the official plan. It adds "what if" scenarios, a printable progress
certificate, and a read-only link to share your progress with a tutor. Alerts go out over
WhatsApp, Telegram, or email. It runs on
one EC2 box with Docker Compose: API (Node + Express + MongoDB) and frontend in separate containers
behind Nginx, with its own domain and Let's Encrypt TLS. A GitHub Actions pipeline using OIDC pushes
the images to ECR and deploys through SSM, with no SSH and no stored keys.

![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?logo=express&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?logo=jsonwebtokens&logoColor=white) ![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?logo=docker&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white) ![Let's Encrypt](https://img.shields.io/badge/Let%27s_Encrypt-003A70?logo=letsencrypt&logoColor=white)

[**▸ Try it**](https://miplandeestudios.com.ar) · in production, with real users

### Claudito: AI CV optimizer

Upload a CV, paste a job description, and get a match score, concrete suggestions you accept or
dismiss one by one, and a ready-to-send Harvard-format PDF, with one core constraint: **it invents
nothing**. You can try it without an account; with one, you keep a career dossier (the long record
of your projects and achievements) that gets split into units of evidence in DynamoDB. On each
analysis the most relevant ones for the role are picked, every CV bullet cites the unit that backs
it, and a verifier checks that the citations exist and that no figure falls outside the original
material. The CV is edited already formatted, not as Markdown. It's serverless: fourteen Lambdas,
Cognito for accounts, three Bedrock uses (dossier, analysis, and generation), WeasyPrint for the
PDF, and Textract OCR for scanned files. Anonymous sessions live in S3 and delete themselves within
24 to 48 hours; IaC with SAM and CI/CD deploys over OIDC.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon Textract](https://img.shields.io/badge/Textract-FF9900?logo=amazontextract&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)

[**▸ Try it**](https://d1u1sqpu5ny5ot.cloudfront.net) · deployed

### Dockyard: a Render/Railway-style deploy platform

Connect a repo, `git push`, and your app is live on its own subdomain with valid HTTPS. It's an
infrastructure project meant to be defensible piece by piece: instead of using a PaaS, it builds
one. A GitHub App sends a signed webhook, a worker clones the repo (private ones too), detects the
stack (Node, Python, or Go), builds the Docker image, pushes it to ECR, and brings it up behind
Nginx, with encrypted environment variables and secrets in SSM. A reconciliation loop recovers
crashed containers and detects crash loops, and a dashboard shows live logs and one-click rollback.
Everything is reproducible from scratch with CloudFormation, with wildcard TLS via ACME DNS-01 and CI
over OIDC, no static access keys. **Phases 0 to 3 are complete.**

![CloudFormation](https://img.shields.io/badge/CloudFormation-FF9900?logo=amazonaws&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white) ![Amazon ECR](https://img.shields.io/badge/ECR-FF9900?logo=amazonecr&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white) ![Bash](https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

[**▸ Demo**](https://demo.dockyard.dpdns.org) · Phases 0 to 3 complete

### Costos: management for small restaurants

So a restaurant owner can run their business without knowing accounting: sales, expenses, costs,
break-even, electronic invoicing (ARCA/WSFE), and an assistant that answers in plain language using
the business's real numbers. Data is entered by hand, by photo of the receipt (AI extracts and
classifies it), or from the ARCA "Mis Comprobantes" CSV in bulk. It adds a point-of-sale counter
with barcode scanning and cash register, supplier comparison from offers sent as photo, PDF, or
text, profitability per product, Telegram and WhatsApp alerts, and four PIN-protected roles. React +
Vite (PWA) frontend with state in the browser; a single Lambda with two integrations: Bedrock
(Claude) for AI and the Afip SDK for ARCA. Design rule: only products, sales, and receipts are
stored; unit cost, overhead, break-even, and alerts are all derived and never persisted.

![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![PWA](https://img.shields.io/badge/PWA-5A0FC8?logo=pwa&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white)

_Status: runs locally against the Lambda; no hosted instance yet._

### Seguidor-Colectivo: live buses in Villa Mercedes

A full-screen map showing where each bus is and how long until it reaches your stop, plus a trip
planner. The upstream source (ColectivoYa) isn't reliable on its own, so the GPS is the source of
truth: it stores real trips in S3, learns each route from them, validates the routes against the
positions, and hides stops nobody serves anymore. It also reassigns direction (outbound or return),
which the source rarely reports correctly, and checks everything against the official timetable. It's
serverless: CloudFront + S3 for the frontend, a Lambda, DynamoDB, and SAM for the infrastructure.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white)

[**▸ Try it**](https://d37602x6omnenw.cloudfront.net) · deployed

### Normativa ISI UNViMe: the university's rulebook, organized for accreditation

I crawled the full index of the UNViMe digest (over 13,000 documents), ran OCR on the scanned
resolutions, and classified by content the ones that matter for the CONEAU accreditation of the
Information Systems Engineering program, organized by annex. The result is a public site with a
sortable table, a detail page with the PDF of each resolution, and timelines showing which rule
overrides which. It's published with GitHub Pages, and one script regenerates everything from the
data.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white) ![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-222222?logo=githubpages&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

[**▸ See it**](https://flordelcastillo.github.io/normativa-isi-unvime/) · [code](https://github.com/flordelcastillo/normativa-isi-unvime)

### CodeJam UNViMe 2026: landing and live photo wall

The official landing page for CodeJam (Oct 30, 2026) and a wall that updates itself during the event:
people upload a photo from their phone with the event frame, an admin panel moderates it, and it
shows up on the projector with a QR code to join in. It adds a team ranking that stays hidden until
the judges publish it, and an AI pitch coach (Claude on Bedrock) with per-IP limits to keep costs in
check. Serverless end to end: CloudFront + S3, a Lambda, DynamoDB, and SAM, all pay-per-use.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white)

[**▸ See it**](https://dygd5d0drje17.cloudfront.net) · [code](https://github.com/flordelcastillo/codejam-landing)

### Estantería: Programming Club project gallery

A web app where club members upload their projects and anyone can browse them, filter by category,
technology, year, or event, and vote on them. Accounts use Cognito with email verification, an admin
group moderates (feature, hide, edit), and cover images are uploaded to S3 through signed URLs that
pin type and size. It's accessible (keyboard, visible focus, light and dark theme, mobile first).
Everything runs on AWS behind a single CloudFront domain, with no CORS: S3, API Gateway, a
dependency-free Node 22 Lambda, and DynamoDB, deployed with SAM.

![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white) ![Amazon DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?logo=amazondynamodb&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![AWS SAM](https://img.shields.io/badge/SAM-FF9900?logo=awssam&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-5FA04E?logo=nodedotjs&logoColor=white)

[**▸ Try it**](https://d1dj3drky6qwir.cloudfront.net) · deployed

### Teia Accesorios: online store with admin panel

A made-to-measure store for an accessories brand: filterable catalog, product page, cart, coupons,
size guide, and delivery options, with payments through Mercado Pago. Behind it is a custom admin
panel to upload products with images, adjust stock live, track orders and payment status, and see
metrics. The Mercado Pago webhook confirms the payment and deducts stock automatically. It's a Next.js
monolith with Prisma and PostgreSQL, self-hosted on an EC2.

![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?logo=tailwindcss&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![Prisma](https://img.shields.io/badge/Prisma-2D3748?logo=prisma&logoColor=white) ![Mercado Pago](https://img.shields.io/badge/Mercado_Pago-00B1EA?logo=mercadopago&logoColor=white) ![Amazon EC2](https://img.shields.io/badge/EC2-FF9900?logo=amazonec2&logoColor=white)

[**▸ Visit**](https://teiaaccesorios.com.ar) · [code](https://github.com/flordelcastillo/tienda-luci)

### Bibliography currency checker: program accreditation

Part of the work for the accreditation of the Information Systems Engineering program before CONEAU.
It analyzes the PDFs of each course syllabus (ministerial format) and classifies every reference in
the basic and complementary bibliography as up to date (2016 to 2026), outdated, or no detectable
year, which is flagged for manual review. It takes several syllabi at once, lets you fix entries by
hand with instant recalculation, exports to Excel and PDF, and compares each course's history across
terms. It's serverless on AWS, with Cognito login.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/Lambda-FF9900?logo=awslambda&logoColor=white) ![Amazon API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?logo=amazonapigateway&logoColor=white) ![Amazon Cognito](https://img.shields.io/badge/Cognito-DD344C?logo=amazoncognito&logoColor=white) ![Amazon S3](https://img.shields.io/badge/S3-FF9900?logo=amazons3&logoColor=white) ![Amazon CloudFront](https://img.shields.io/badge/CloudFront-FF9900?logo=amazoncloudfront&logoColor=white) ![Amazon Bedrock](https://img.shields.io/badge/Bedrock-FF9900?logo=amazonbedrock&logoColor=white)

_Internal use by the program; the code is in a private repository._

### Final Project: AI agents to understand university dropout

My degree's final project, done in a team of two with an advisor (due January 2027). It's a chain of
agents that takes academic data from the student management system (SIU Guaraní), integrates and
preprocesses it, trains AutoML models to predict who is at risk of dropping out in the first years
and, most importantly, **explains why**. I own the preprocessing agent and the interpretability agent
(SHAP, PDP, LIME, and counterfactuals with DiCE), which show which variables matter and what could
change in a specific case. An automatic check keeps a weak model from passing as a good one, and
student data is never published or pushed to the repository. It's orchestrated
with LangGraph, and the models are trained with AutoGluon.

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)

_Status: in development; the code lives in a private team repository._

## About me

I am a **Systems Analyst** and I am studying Information Systems Engineering at UNViMe (2022-present). I am also a **teaching assistant**
for *Problem Solving & Algorithms* and *Programming I*. I co-founded the **UNViMe programming club**
and gave workshops and talks at Semana de la Ingeniería: Git, HTML/CSS, Notion for engineers, and
*Primeros Pasos en la Nube con AWS* with the AWS User Group San Luis.

**How I got here:** freeCodeCamp → Java backend at Universidad Globant (Code Your Future scholarship)
→ AWS Re/Start at Potrero Digital → [**AWS Certified Cloud Practitioner**](https://www.credly.com/badges/736b6e0f-4c60-4a82-aa06-105653a22aae/public_url) (January 2026) → AWS Academy Educator. Right now:
the UNViMe CodeJam (Oct 30) and my degree final project.

**Contact:** [LinkedIn](https://linkedin.com/in/flordelcastillo) ·
English B2

---

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-seven-psi-95.vercel.app/api?username=flordelcastillo&show_icons=true&include_all_commits=true&hide_border=true&hide_title=true&theme=tokyonight" />
  <img height="170" src="https://github-readme-stats-seven-psi-95.vercel.app/api?username=flordelcastillo&show_icons=true&include_all_commits=true&hide_border=true&hide_title=true&theme=default" alt="GitHub stats" />
</picture>
&nbsp;
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-seven-psi-95.vercel.app/api/top-langs/?username=flordelcastillo&layout=compact&hide_border=true&langs_count=8&theme=tokyonight" />
  <img height="170" src="https://github-readme-stats-seven-psi-95.vercel.app/api/top-langs/?username=flordelcastillo&layout=compact&hide_border=true&langs_count=8&theme=default" alt="Top languages" />
</picture>

<br />
<br />

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./profile/streak-dark.svg" />
  <img height="170" src="./profile/streak-light.svg" alt="GitHub streak stats" />
</picture>

<br />
<br />

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-activity-graph-tan-two.vercel.app/graph?username=flordelcastillo&hide_border=true&area=true&theme=react-dark" />
  <img src="https://github-readme-activity-graph-tan-two.vercel.app/graph?username=flordelcastillo&hide_border=true&area=true&theme=github-light" alt="Activity graph" />
</picture>

<br />
<br />

<a href="https://www.credly.com/badges/736b6e0f-4c60-4a82-aa06-105653a22aae/public_url"><img src="https://images.credly.com/size/340x340/images/00634f82-b07f-4bbd-a6bb-53de397fc3a6/image.png" alt="AWS Certified Cloud Practitioner" width="120" /></a>
<a href="https://www.credly.com/badges/501c27bc-4dd2-4245-a4a7-c43c5b40bc1b/public_url"><img src="https://images.credly.com/size/340x340/images/44e2c252-5d19-4574-9646-005f7225bf53/image.png" alt="AWS re/Start Graduate" width="120" /></a>
<a href="https://www.credly.com/badges/723e83a1-657c-4ad7-b87b-3c01e382473b/public_url"><img src="https://images.credly.com/size/340x340/images/e7bf6727-22cf-45d6-ad9c-76ab57c3f11b/image.png" alt="AWS Academy Educator" width="120" /></a>

<br />

<sub><b>AWS Certified Cloud Practitioner</b> (2026) · <b>AWS re/Start Graduate</b> · <b>AWS Academy Educator</b></sub>

</div>
