# La-ciencia-del-mantenimiento
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gestión y planificación del mantenimiento industrial</title>

  <!-- Estilos básicos -->
  <style>
    :root{
      --bg:#0b1220;
      --card:#111a2e;
      --text:#e8eefc;
      --muted:#b7c3e6;
      --accent:#6ea8fe;
      --accent2:#7ee081;
      --warn:#ffd166;
      --danger:#ff6b6b;
      --border:rgba(255,255,255,.10);
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background:linear-gradient(180deg, var(--bg), #070b14);
      color:var(--text);
      line-height:1.6;
    }
    a{color:var(--accent); text-decoration:none}
    a:hover{text-decoration:underline}
    header{
      padding:48px 16px 24px;
      max-width:1100px;
      margin:0 auto;
    }
    .badge{
      display:inline-block;
      padding:6px 10px;
      border:1px solid var(--border);
      border-radius:999px;
      color:var(--muted);
      font-size:12px;
      letter-spacing:.3px;
    }
    h1{
      margin:14px 0 10px;
      font-size:clamp(28px, 3.5vw, 44px);
      line-height:1.15;
    }
    .sub{
      margin:0;
      color:var(--muted);
      max-width:70ch;
    }
    .wrap{
      max-width:1100px;
      margin:0 auto;
      padding:0 16px 64px;
      display:grid;
      grid-template-columns: 1fr 320px;
      gap:18px;
    }
    @media (max-width: 980px){
      .wrap{grid-template-columns:1fr}
    }
    .card{
      background:rgba(17,26,46,.85);
      border:1px solid var(--border);
      border-radius:16px;
      padding:18px;
      box-shadow:0 10px 30px rgba(0,0,0,.25);
      backdrop-filter: blur(6px);
    }
    .toc a{display:block; padding:6px 0}
    .meta{
      display:flex; gap:10px; flex-wrap:wrap;
      margin-top:14px; color:var(--muted); font-size:13px;
    }
    .pill{
      border:1px solid var(--border);
      padding:6px 10px;
      border-radius:999px;
    }
    section{scroll-margin-top:18px}
    h2{
      margin:0 0 10px;
      font-size:22px;
    }
    p{margin:0 0 12px}
    ul{margin:0 0 12px 18px}
    .grid2{
      display:grid;
      grid-template-columns:1fr 1fr;
      gap:14px;
    }
    @media (max-width: 640px){
      .grid2{grid-template-columns:1fr}
    }
    figure{
      margin:0;
      border:1px solid var(--border);
      border-radius:14px;
      overflow:hidden;
      background:#0b1020;
    }
    figure img{
      width:100%;
      height:210px;
      object-fit:cover;
      display:block;
    }
    figcaption{
      padding:10px 12px;
      color:var(--muted);
      font-size:13px;
    }
    .callout{
      border-left:4px solid var(--accent2);
      background:rgba(126,224,129,.08);
      padding:12px 14px;
      border-radius:12px;
      margin:10px 0 14px;
      color:var(--text);
    }
    .kpi{
      display:grid;
      grid-template-columns:1fr 1fr;
      gap:12px;
      margin-top:10px;
    }
    .kpi .box{
      border:1px solid var(--border);
      border-radius:14px;
      padding:12px;
      background:rgba(255,255,255,.03);
    }
    .kpi .box b{display:block; margin-bottom:4px}
    footer{
      max-width:1100px;
      margin:0 auto;
      padding:22px 16px 40px;
      color:var(--muted);
      font-size:13px;
    }
    /* Botón */
    .btn{
      display:inline-block;
      padding:10px 12px;
      border-radius:12px;
      border:1px solid var(--border);
      background:rgba(255,255,255,.04);
      color:var(--text);
    }
    .btn:hover{background:rgba(255,255,255,.08); text-decoration:none}

    /* Gráfica simple (sin librerías) */
    .chart{
      display:grid;
      grid-template-columns: 1fr;
      gap:8px;
      margin-top:8px;
    }
    .barrow{
      display:grid;
      grid-template-columns: 120px 1fr 52px;
      gap:10px;
      align-items:center;
      color:var(--muted);
      font-size:13px;
    }
    .bar{
      height:12px;
      background:rgba(255,255,255,.08);
      border-radius:999px;
      overflow:hidden;
      border:1px solid var(--border);
    }
    .bar > span{
      display:block;
      height:100%;
      width:0%;
      border-radius:999px;
      background:linear-gradient(90deg, var(--accent), #9a7bff);
    }
    .bar > span.green{
      background:linear-gradient(90deg, var(--accent2), #2dd4bf);
    }
    .note{
      font-size:12px;
      color:var(--muted);
      margin-top:8px;
    }
    /* Imagenes (usa URLs libres) */
    .hero-img{
      margin-top:16px;
      border-radius:18px;
      border:1px solid var(--border);
      overflow:hidden;
    }
    .hero-img img{
      width:100%;
      height:260px;
      object-fit:cover;
      display:block;
    }
    /* Código */
    code{
      background:rgba(255,255,255,.06);
      border:1px solid var(--border);
      padding:2px 6px;
      border-radius:8px;
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace;
      font-size: 0.95em;
    }
  </style>
</head>

<body>
  <header>
    <span class="badge">Blog académico • Mantenimiento industrial</span>
    <h1>Gestión y planificación del mantenimiento industrial</h1>
    <p class="sub">
      Cómo organizar el mantenimiento para mejorar disponibilidad, confiabilidad, seguridad y costos.
      Incluye enlaces, elementos visuales y una gráfica simple para enriquecer la lectura.
    </p>

    <!-- Imagen principal (puedes cambiarla por otra URL) -->
    <div class="hero-img">
      <img
        src="https://images.unsplash.com/photo-1581092160562-40aa08e78837?auto=format&fit=crop&w=1600&q=70"
        alt="Planta industrial y mantenimiento"
      />
    </div>

    <div class="meta">
      <span class="pill">Autor: Tu nombre</span>
      <span class="pill">Materia: Producción / Mantenimiento</span>
      <span class="pill">Fecha: <span id="fecha"></span></span>
    </div>
  </header>

  <main class="wrap">
    <!-- CONTENIDO -->
    <article class="card">
      <section id="s1">
        <h2>1) ¿Qué es la gestión del mantenimiento industrial?</h2>
        <p>
          La <b>gestión del mantenimiento industrial</b> integra actividades técnicas y administrativas para
          conservar equipos e instalaciones en condiciones óptimas de operación. Su objetivo es
          asegurar continuidad productiva, minimizar fallas, controlar costos y mantener estándares de calidad.
        </p>

        <div class="callout">
          <b>Idea clave:</b> el mantenimiento es un proceso estratégico. No solo “repara”, también previene,
          mejora y protege la producción.
        </div>

        <div class="grid2">
          <figure>
            <img src="https://images.unsplash.com/photo-1581092918056-0c4c3acd3789?auto=format&fit=crop&w=1400&q=70" alt="Técnico revisando equipo" />
            <figcaption>Inspección técnica: base del mantenimiento preventivo.</figcaption>
          </figure>

          <figure>
            <img src="https://images.unsplash.com/photo-1581092580497-e0d23cbdf1dc?auto=format&fit=crop&w=1400&q=70" alt="Panel industrial" />
            <figcaption>Gestión: control, trazabilidad y toma de decisiones.</figcaption>
          </figure>
        </div>
      </section>

      <section id="s2" style="margin-top:18px;">
        <h2>2) Importancia de la planificación del mantenimiento</h2>
        <p>
          La <b>planificación</b> organiza tareas, frecuencias, recursos, repuestos y tiempos para intervenir
          equipos con el menor impacto en la producción. Planificar evita paros inesperados y mejora la disponibilidad.
        </p>
        <ul>
          <li>Reduce fallas no programadas y tiempos muertos.</li>
          <li>Optimiza mano de obra, refacciones y presupuesto.</li>
          <li>Mejora la seguridad al trabajar con procedimientos definidos.</li>
          <li>Apoya la calidad al mantener equipos dentro de parámetros.</li>
        </ul>

        <p class="note">
          Recomendación: usa un sistema <b>CMMS</b> (Computerized Maintenance Management System) para programar órdenes,
          historial y control de inventario.
        </p>
      </section>

      <section id="s3" style="margin-top:18px;">
        <h2>3) Tipos de mantenimiento: preventivo, correctivo y predictivo</h2>
        <p>
          Elegir el tipo de mantenimiento depende de criticidad del equipo, costos, impacto en producción y riesgos.
        </p>
        <div class="kpi">
          <div class="box">
            <b>Preventivo</b>
            <span>Programado para evitar fallas (inspecciones, ajustes, lubricación).</span>
          </div>
          <div class="box">
            <b>Correctivo</b>
            <span>Se aplica cuando el equipo falla; puede ser urgente y costoso.</span>
          </div>
          <div class="box">
            <b>Predictivo</b>
            <span>Se basa en condición: vibración, temperatura, ultrasonido, etc.</span>
          </div>
          <div class="box">
            <b>Proactivo</b>
            <span>Elimina causas raíz (mejoras, rediseño, estandarización).</span>
          </div>
        </div>
      </section>

      <section id="s4" style="margin-top:18px;">
        <h2>4) Indicadores (KPI) esenciales del mantenimiento</h2>
        <p>
          Los KPI permiten medir desempeño y tomar decisiones basadas en datos.
          Los más comunes:
        </p>
        <ul>
          <li><b>MTBF</b> (Mean Time Between Failures): tiempo medio entre fallas.</li>
          <li><b>MTTR</b> (Mean Time To Repair): tiempo medio de reparación.</li>
          <li><b>Disponibilidad</b> (%): tiempo operativo vs tiempo total.</li>
          <li><b>Costo de mantenimiento</b> (total y por equipo).</li>
          <li><b>Backlog</b>: trabajo pendiente de mantenimiento.</li>
        </ul>

        <!-- Gráfica simple en barras (ejemplo didáctico) -->
        <div class="card" style="padding:14px; margin-top:12px;">
          <b>Gráfica ejemplo: impacto de planificar mantenimiento (ilustrativa)</b>
          <div class="chart">
            <div class="barrow">
              <span>Paros</span>
              <div class="bar"><span style="width:75%"></span></div>
              <span>75%</span>
            </div>
            <div class="barrow">
              <span>Costos</span>
              <div class="bar"><span style="width:65%"></span></div>
              <span>65%</span>
            </div>
            <div class="barrow">
              <span>Disponibilidad</span>
              <div class="bar"><span class="green" style="width:88%"></span></div>
              <span>88%</span>
            </div>
          </div>
          <p class="note">
            Nota: valores de ejemplo. Sustituye por datos reales de tu empresa o práctica escolar.
          </p>
        </div>
      </section>

      <section id="s5" style="margin-top:18px;">
        <h2>5) Organización del departamento de mantenimiento</h2>
        <p>
          Un departamento bien organizado reduce tiempos de respuesta y mejora coordinación con producción.
          Debe tener roles claros, comunicación eficiente y procedimientos estandarizados.
        </p>
        <ul>
          <li>Estructura: jefe/supervisor, planeador, técnicos, almacén de refacciones.</li>
          <li>Documentación: instructivos, checklists, bitácoras e historial.</li>
          <li>Programación: órdenes de trabajo, calendarios, paros planificados.</li>
          <li>Gestión de refacciones: mínimos/máximos y criticidad.</li>
        </ul>

        <div class="callout" style="border-left-color: var(--warn); background: rgba(255,209,102,.08);">
          <b>Criterios que debe considerar la empresa:</b> criticidad del equipo, seguridad, costo de falla,
          disponibilidad de repuestos, capacitación del personal y metas productivas.
        </div>
      </section>

      <section id="s6" style="margin-top:18px;">
        <h2>6) Seguridad y mejora continua</h2>
        <p>
          El mantenimiento seguro evita accidentes y daños. La mejora continua se logra mediante
          auditorías, análisis de causa raíz y capacitación constante.
        </p>
        <ul>
          <li>Bloqueo y etiquetado: <code>LOTO</code> (Lockout/Tagout) antes de intervenir equipos.</li>
          <li>Uso de EPP: casco, guantes, lentes, protección auditiva, etc.</li>
          <li>Procedimientos y permisos de trabajo (espacios confinados, alturas, eléctricos).</li>
          <li>Mejora continua: lecciones aprendidas y reducción de fallas repetitivas.</li>
        </ul>

        <figure>
          <img src="https://images.unsplash.com/photo-1581092795360-fd1ca04f0952?auto=format&fit=crop&w=1400&q=70" alt="Seguridad en trabajo industrial" />
          <figcaption>Seguridad: base de un mantenimiento responsable.</figcaption>
        </figure>
      </section>

      <section id="fuentes" style="margin-top:18px;">
        <h2>Fuentes y enlaces recomendados</h2>
        <ul>
          <li><a href="https://www.osha.gov" target="_blank" rel="noopener">OSHA – Seguridad y salud ocupacional</a></li>
          <li><a href="https://www.iso.org" target="_blank" rel="noopener">ISO – Estándares (gestión y activos)</a></li>
          <li><a href="https://www.maintenanceworld.com" target="_blank" rel="noopener">Maintenance World</a></li>
          <li><a href="https://www.reliabilityweb.com" target="_blank" rel="noopener">ReliabilityWeb</a></li>
          <li><a href="https://www.plantengineering.com" target="_blank" rel="noopener">Plant Engineering</a></li>
          <li><a href="https://www.ibm.com/products/maximo" target="_blank" rel="noopener">IBM Maximo (CMMS/EAM)</a></li>
        </ul>
        <p class="note">
          Sugerencia: agrega también el enlace al documento o recurso de tu curso si te lo permiten.
        </p>
      </section>
    </article>

    <!-- BARRA LATERAL -->
    <aside class="card toc">
      <h2>Contenido</h2>
      <a href="#s1">1) Gestión del mantenimiento</a>
      <a href="#s2">2) Planificación</a>
      <a href="#s3">3) Tipos de mantenimiento</a>
      <a href="#s4">4) KPI (MTBF, MTTR, etc.)</a>
      <a href="#s5">5) Organización del departamento</a>
      <a href="#s6">6) Seguridad y mejora continua</a>
      <hr style="border:0;border-top:1px solid var(--border); margin:12px 0;">
      <a href="#fuentes">Fuentes y enlaces</a>

      <p class="note" style="margin-top:12px;">
        Puedes copiar este HTML en un archivo llamado <code>index.html</code> y abrirlo en tu navegador.
      </p>

      <a class="btn" href="#top" onclick="window.scrollTo({top:0, behavior:'smooth'}); return false;">Subir</a>
    </aside>
  </main>

  <footer>
    <div class="card">
      <b>Créditos</b>
      <p style="margin-top:8px;">
        Autor: ____________________ • Grupo: ____ • Institución: ____________________ • Materia: ____________________
      </p>
      <p class="note">
        Imágenes: Unsplash (uso libre). Si tu escuela exige citarlas, agrega el enlace de cada imagen.
      </p>
    </div>
  </footer>

  <!-- Script: fecha automática + animación de barras -->
  <script>
    // Fecha automática
    const f = new Date();
    const opciones = { year: 'numeric', month: 'long', day: 'numeric' };
    document.getElementById('fecha').textContent = f.toLocaleDateString('es-MX', opciones);

    // Animación simple de barras al cargar
    window.addEventListener('load', () => {
      document.querySelectorAll('.bar > span').forEach((el) => {
        const w = el.style.width;
        el.style.width = '0%';
        setTimeout(() => { el.style.transition = 'width 900ms ease'; el.style.width = w; }, 200);
      });
    });
  </script>
</body>
</html>
