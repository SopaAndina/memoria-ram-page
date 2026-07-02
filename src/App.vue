<template>
  <div class="page-container">

    <nav class="navbar">
      <div class="nav-content">
        <a href="#que-es" class="transition-colors text-amber-50 hover:text-indigo-400">¿Qué es?</a>
        <a href="#funciones" class="transition-colors text-amber-50 hover:text-emerald-400">Funciones</a>
        <a href="#organizacion" class="transition-colors text-amber-50 hover:text-amber-400">Organización</a>
        <a href="#problemas" class="transition-colors text-amber-50 hover:text-red-400">Problemas</a>
        <a href="#virtual" class="transition-colors text-amber-50 hover:text-cyan-400">Memoria Virtual</a>
      </div>
    </nav>

    <div class="main-content">

      <header class="main-header">
        <h1 class="header-title">Gestión de Memoria Principal</h1>
        <p class="header-subtitle">Conceptos fundamentales de Sistemas Operativos</p>
      </header>

      <section id="que-es" class="card border-indigo-500/30">
        <h2 class="section-title text-indigo-400">🧠 1. ¿Qué es la Memoria Principal (RAM)?</h2>
        <div class="paragraph-group">
          <p>La Memoria Principal, comúnmente implementada con tecnología <strong>RAM (Random Access Memory)</strong>,
            es el área de almacenamiento de trabajo del sistema informático. Es el puente directo entre el
            almacenamiento secundario (discos duros/SSD) y el procesador (CPU).</p>
          <p>En la arquitectura de Von Neumann, tanto los datos como las instrucciones de los programas deben estar
            cargados en la memoria principal para que el procesador pueda ejecutar el ciclo de
            <em>fetch-decode-execute</em> (búsqueda, decodificación y ejecución).
          </p>
          <p><strong>Características clave:</strong> Es <em>volátil</em> (su contenido se pierde al interrumpir el
            suministro eléctrico) y de <em>acceso aleatorio</em>, lo que significa que el tiempo de lectura o escritura
            es el mismo independientemente de la posición física de los datos en el chip.</p>
        </div>
      </section>

      <section id="funciones" class="card border-emerald-500/30">
        <h2 class="section-title text-emerald-400">🛡️ 2. ¿De qué se encarga el Gestor de Memoria?</h2>
        <p class="mb-6">El componente del Sistema Operativo dedicado a la memoria debe garantizar la ejecución eficiente
          y segura de múltiples procesos concurrentes. Sus responsabilidades incluyen:</p>
        <div class="grid-3-cols">
          <div class="sub-card">
            <h3 class="sub-card-title">Protección</h3>
            <p class="text-sm">Garantiza que un proceso no pueda acceder ni modificar los espacios de memoria asignados
              a otros procesos. Esto se logra mediante el uso de registros base y límite en el hardware, previniendo
              caídas del sistema o accesos no autorizados.</p>
          </div>
          <div class="sub-card">
            <h3 class="sub-card-title">Aislamiento</h3>
            <p class="text-sm">Establece una barrera estricta entre el espacio del Sistema Operativo (Kernel) y el
              espacio de los usuarios. Impide que un programa de usuario pueda sobrescribir las estructuras de control
              críticas del núcleo.</p>
          </div>
          <div class="sub-card">
            <h3 class="sub-card-title">Reubicación</h3>
            <p class="text-sm">En sistemas multiprogramados, los programas deben poder cargarse en diferentes áreas de
              la memoria física en distintos momentos. El SO ajusta dinámicamente las referencias de memoria del
              programa para que apunten a las direcciones físicas correctas.</p>
          </div>
        </div>
      </section>

      <section id="organizacion" class="card border-amber-500/30">
        <h2 class="section-title text-amber-400">🗂️ 3. Organización de la Memoria</h2>
        <div class="paragraph-group">
          <p>La memoria se concibe como un arreglo lineal de bytes, pero para gestionarla eficientemente, el Sistema
            Operativo utiliza una <strong>jerarquía de memoria</strong> (Registros > Caché > RAM > Almacenamiento
            Secundario) y diferentes esquemas de asignación:</p>

          <div class="alert-box border-amber-500 bg-amber-950/10">
            <h3 class="sub-card-title">Particiones Fijas (Estáticas)</h3>
            <p class="text-sm">La memoria se divide en bloques de tamaño fijo desde el arranque del sistema. Pueden ser
              del mismo tamaño o de tamaños distintos. Si un proceso es más grande que la partición, no puede ejecutarse
              en ella. Es un método simple pero poco eficiente en el uso del espacio.</p>
          </div>

          <div class="alert-box border-amber-400 bg-amber-950/10">
            <h3 class="sub-card-title">Particiones Dinámicas</h3>
            <p class="text-sm">Se asigna a cada proceso exactamente la cantidad de memoria que necesita. A medida que
              los procesos entran y salen, la memoria se va dividiendo en bloques ocupados y bloques libres (huecos).
              Requiere algoritmos complejos de asignación como <em>First-Fit</em>, <em>Best-Fit</em> o
              <em>Worst-Fit</em>.
            </p>
          </div>
        </div>
      </section>

      <section id="problemas" class="card border-red-500/30">
        <h2 class="section-title text-red-400">🧩 4. Problemas: La Fragmentación</h2>
        <p class="mb-4">El principal enemigo de la gestión de memoria es la fragmentación: el desperdicio de espacio que
          queda inutilizable a medida que se asignan y liberan bloques de memoria a los procesos.</p>

        <div class="grid-2-cols">
          <div class="problem-box">
            <h3 class="text-xl font-bold text-red-300 mb-3">Fragmentación Interna</h3>
            <p class="text-sm">Asociada principalmente a las <strong>particiones fijas</strong>. Ocurre cuando un
              proceso no ocupa toda la memoria que se le asignó. El espacio sobrante <em>dentro</em> de esa partición se
              desperdicia, ya que el Sistema Operativo no se lo puede asignar a otro proceso.</p>
          </div>

          <div class="problem-box">
            <h3 class="text-xl font-bold text-red-300 mb-3">Fragmentación Externa</h3>
            <p class="text-sm">Ocurre en esquemas de <strong>particiones dinámicas</strong>. A medida que los procesos
              terminan, dejan huecos de memoria libre esparcidos. Con el tiempo, puede haber suficiente memoria total
              disponible para ejecutar un nuevo programa, pero está tan fragmentada que no hay un bloque continuo lo
              suficientemente grande para alojarlo.</p>
          </div>
        </div>
      </section>

      <section id="virtual" class="card border-cyan-500/30">
        <h2 class="section-title text-cyan-400">🌐 5. Memoria Virtual</h2>
        <div class="paragraph-group">
          <p>La Memoria Virtual es una técnica que independiza la memoria requerida por los programas de la cantidad de
            memoria física (RAM) disponible en el equipo. Permite la ejecución de procesos que superan la capacidad de
            la RAM instalada, utilizando el almacenamiento secundario como una extensión ilusoria.</p>

          <div class="grid-2-cols">
            <div class="info-tag">
              <h4 class="font-bold text-white mb-2">Direcciones Lógicas (Virtuales)</h4>
              <p class="text-sm">Son las direcciones generadas por la CPU durante la ejecución de un programa. El
                programa "cree" que tiene un bloque de memoria contiguo a su disposición.</p>
            </div>
            <div class="info-tag">
              <h4 class="font-bold text-white mb-2">Direcciones Físicas</h4>
              <p class="text-sm">Es la ubicación real y tangible de los datos en los chips de la memoria RAM, dividida
                comúnmente en marcos de página.</p>
            </div>
          </div>

          <div class="alert-box border-cyan-500 bg-cyan-950/10">
            <h3 class="text-lg font-bold text-cyan-300 mb-2">El rol de la MMU (Memory Management Unit)</h3>
            <p class="text-sm">El hardware del procesador cuenta con la MMU, que se encarga de traducir en tiempo real
              las direcciones lógicas en direcciones físicas utilizando las <strong>Tablas de Páginas</strong>. Si un
              dato no está en la RAM, se produce un <em>fallo de página (page fault)</em>, obligando al SO a buscarlo en
              el disco.</p>
          </div>
        </div>
      </section>

      <footer class="footer-container">
        <p>© 2026 Creado por Mauricio Durán</p>
        <p class="footer-subtext">Diseñado y desarrollado como material práctico para la asignatura de Sistemas
          Operativos.</p>
      </footer>


    </div>
  </div>


</template>