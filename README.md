## Florencia Del Castillo

Backend e infraestructura — AWS, casi todo serverless.
Villa Mercedes, San Luis, Argentina.

I build infrastructure on AWS and document the reasoning behind it. Every project here
states its decisions, its trade-offs, and what's still wrong with it.

<sub><a href="#español">🇦🇷 Leer en español</a></sub>

---

### Claudito · serverless CV optimizer

Upload a CV, paste a job description, get a match score, concrete suggestions, and a
Harvard-format PDF. Nine Lambdas, two Bedrock calls, **no database** — without login there's
no persistent state, so a session is just an S3 folder that deletes itself in an hour.

The decision I'd defend first: **IAM permissions have gate tests over the SAM template.**
Every scanned PDF once died in production with `AccessDenied` while every unit test passed,
because Textract was mocked. The code can't see its own role — the template can.

`Python` `AWS Lambda` `Bedrock` `SAM` `S3` `Textract` `React` `TypeScript`

### Dockyard · a small Render/Railway

Connect a GitHub repo, `git push`, and it detects the stack, builds the image, deploys it,
and hands back an HTTPS URL on its own subdomain. Control plane and data plane separated,
deploys modelled as a state machine, idempotent and reconciling.

Wildcard TLS via ACME DNS-01, Nginx routing by `Host`, CI/CD over **OIDC** — no static access
keys anywhere.

`Docker` `EC2` `ECR` `CloudFormation` `Nginx` `GitHub Actions`

### Costos · a small business in numbers

So the owner of a restaurant can run it without knowing accounting: sales, costs, break-even,
electronic invoicing (ARCA/WSFE) and an AI assistant that answers questions against the real
numbers. Three ways to load data — by hand, a **photo of the receipt** (AI extracts and
classifies it), or the ARCA CSV in bulk with duplicate detection.

`React` `Vite` `Bedrock` `PWA`

### BackPlan

Dockerised app deployed on EC2 with Docker Compose.

`Docker` `Docker Compose` `EC2`

---

### Stack

| | |
|---|---|
| **Cloud** | Lambda · S3 · Bedrock · CloudFront · API Gateway · EC2 · ECR · Textract · CloudWatch · IAM |
| **IaC** | AWS SAM · CloudFormation |
| **Languages** | Python · TypeScript · JavaScript |
| **Frontend** | React · Vite · Tailwind · Zustand |
| **Ops** | Docker · GitHub Actions (OIDC) · Nginx |

### Contact

- ingflordelcastillo@gmail.com

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=flordelcastillo&show_icons=true&hide_border=true&theme=dark&hide_title=true" />
    <img src="https://github-readme-stats.vercel.app/api?username=flordelcastillo&show_icons=true&hide_border=true&theme=default&hide_title=true" alt="GitHub stats" />
  </picture>
</div>

---

<h3 id="español">🇦🇷 Español</h3>

Construyo infraestructura en AWS y documento por qué está hecha así. Cada proyecto acá deja
escritas sus decisiones, sus concesiones y lo que todavía está mal.

#### Claudito · optimizador de CVs serverless

Subís tu CV, pegás una descripción de puesto, y te devuelve un score de match, sugerencias
concretas y un PDF en formato Harvard. Nueve Lambdas, dos llamadas a Bedrock, **sin base de
datos**: sin login no hay estado persistente, así que una sesión es literalmente una carpeta
en S3 que se autodestruye en una hora.

La decisión que defiendo primero: **los permisos IAM tienen gate tests sobre el template de
SAM.** Todo PDF escaneado moría en producción con `AccessDenied` mientras los tests unitarios
pasaban, porque Textract estaba mockeado. El código no puede ver su propio rol; el template sí.

#### Dockyard · un Render chiquito

Conectás un repo, hacés `git push`, y detecta el stack, construye la imagen, la despliega y te
da una URL HTTPS con subdominio propio. Control plane y data plane separados, los deploys como
máquina de estados, idempotentes y con reconciliación.

TLS wildcard vía ACME DNS-01, Nginx ruteando por `Host`, CI/CD con **OIDC** — sin access keys
estáticas en ningún lado.

#### Costos · tu negocio en números

Para que el dueño o dueña de una PyME gastronómica administre su negocio sin saber de
contabilidad: ventas, gastos, punto de equilibrio, facturación electrónica (ARCA/WSFE) y un
asistente de IA que responde con los números reales. Tres vías de carga: a mano, **foto del
ticket** (la IA extrae y clasifica) o el CSV de ARCA en lote con detección de duplicados.

#### BackPlan

App dockerizada desplegada en EC2 con Docker Compose.

#### Contacto

- ingflordelcastillo@gmail.com
# flordelcastillo
