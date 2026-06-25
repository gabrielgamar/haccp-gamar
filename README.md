[index.html](https://github.com/user-attachments/files/29304480/index.html.html)
# haccp-gamar
HACCP<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<title>HACCP Digital — Gamar SRL</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.2/css/bootstrap.min.css" crossorigin="anonymous">
<script src="https://cdnjs.cloudflare.com/ajax/libs/bootstrap/5.3.2/js/bootstrap.bundle.min.js" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/signature_pad/4.1.7/signature_pad.umd.min.js" crossorigin="anonymous"></script>
<style>
:root {
  --verde: #1A5C2E;
  --verde2: #2E7D46;
  --verde-claro: #E6F2EA;
  --naranja: #D4660A;
  --amarillo: #FFF3CD;
  --rojo-claro: #FDECEA;
}
body { background: #f0f2f0; font-size: 14px; font-family: Arial, sans-serif; }
.cabecera { background: var(--verde); color: #fff; padding: 12px 18px; }
.cabecera h1 { font-size: 1.2rem; margin: 0; font-weight: 700; }
.cabecera .reloj { font-size: .75rem; opacity: .8; }
.nav-wrapper { background: #fff; border-bottom: 3px solid var(--verde); padding: 6px 12px 0; }
.nav-tabs .nav-link { color: var(--verde); font-weight: 600; font-size: .8rem; padding: 7px 10px; }
.nav-tabs .nav-link.active { background: var(--verde); color: #fff; border-color: var(--verde); }
.tarjeta { background: #fff; border-radius: 8px; border: 1px solid #dce; padding: 18px; margin: 14px 0; box-shadow: 0 2px 5px rgba(0,0,0,.07); }
.tarjeta h5 { color: var(--verde); font-weight: 700; border-bottom: 2px solid var(--verde-claro); padding-bottom: 6px; margin-bottom: 14px; }
.aviso { background: var(--amarillo); border-left: 4px solid var(--naranja); padding: 8px 12px; border-radius: 4px; font-size: .78rem; color: #856404; font-weight: 600; margin-bottom: 14px; }
.aviso-rojo { background: var(--rojo-claro); border-left: 4px solid #dc3545; color: #842029; }
.badge-ok { background: #198754; color: #fff; padding: 3px 10px; border-radius: 20px; font-size: .76rem; font-weight: 700; display: inline-block; }
.badge-mal { background: #dc3545; color: #fff; padding: 3px 10px; border-radius: 20px; font-size: .76rem; font-weight: 700; display: inline-block; }
.barra-wrap { height: 6px; background: #e9ecef; border-radius: 3px; margin-top: 4px; }
.barra { height: 100%; border-radius: 3px; width: 0; transition: width .3s, background .3s; }
.firma-label { font-size: .75rem; color: var(--verde); font-weight: 700; margin-bottom: 4px; }
.firma-box { border: 2px dashed var(--verde); border-radius: 6px; background: #fafafa; }
.firma-box canvas { width: 100%; height: 110px; display: block; touch-action: none; cursor: crosshair; }
.tabla-reg th { background: var(--verde); color: #fff; font-size: .75rem; white-space: nowrap; }
.tabla-reg td { font-size: .75rem; vertical-align: middle; }
.fila-mal td { background: var(--rojo-claro); }
.qr-card { border: 2px solid var(--verde); border-radius: 10px; padding: 12px 8px; text-align: center; background: #fff; }
.qr-card.rojo { border-color: #dc3545; }
.qr-titulo { font-size: .75rem; font-weight: 700; color: var(--verde); margin-top: 8px; }
.qr-card.rojo .qr-titulo { color: #dc3545; }
.qr-zona { font-size: .68rem; color: #666; background: #f5f5f5; padding: 2px 6px; border-radius: 4px; margin-top: 3px; display: inline-block; }
@media print {
  .no-imprimir { display: none !important; }
  .nav-wrapper { display: none; }
  .tab-pane { display: block !important; opacity: 1 !important; }
  .tarjeta { box-shadow: none; border: 1px solid #ccc; page-break-inside: avoid; }
}
@media (max-width: 480px) {
  .nav-tabs .nav-link { font-size: .7rem; padding: 6px 7px; }
}
</style>
</head>
<body>

<!-- CABECERA -->
<div class="cabecera no-imprimir">
  <div class="d-flex justify-content-between align-items-center">
    <div>
      <h1>&#127807; GAMAR SRL — HACCP Digital</h1>
      <div class="reloj" id="reloj"></div>
    </div>
    <div class="d-flex gap-2 flex-wrap justify-content-end">
      <button class="btn btn-sm btn-light" onclick="irTab('registros')">&#128203; Registros</button>
      <button class="btn btn-sm btn-outline-light" onclick="exportarCSV()">&#8595; Exportar</button>
    </div>
  </div>
</div>

<!-- NAVEGACION -->
<div class="nav-wrapper no-imprimir">
  <ul class="nav nav-tabs flex-nowrap overflow-auto" id="tabs" style="flex-wrap:nowrap">
    <li class="nav-item"><a class="nav-link active" data-bs-toggle="tab" href="#f01">F-01 Recepci&#243;n</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#f02">F-02 C&#225;maras</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#f03">F-03 Elaboraci&#243;n</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#f04">F-04 Despacho</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#f05">&#9888; Correctiva</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#registros">&#128203; Registros</a></li>
    <li class="nav-item"><a class="nav-link" data-bs-toggle="tab" href="#qrcodes" id="tab-qr">&#128242; QR</a></li>
  </ul>
</div>

<div class="container-fluid px-2 py-1">
<div class="tab-content">

<!-- ============================ F-01 RECEPCION ============================ -->
<div class="tab-pane fade show active" id="f01">
<div class="tarjeta">
  <h5>F-HACCP-01 &mdash; Recepci&#243;n de Materia Prima <small class="badge bg-secondary ms-2">CCP 1</small></h5>
  <div class="aviso">&#9888; L&#237;mite cr&#237;tico: Temperatura &#8804; 7&#176;C | Proveedor con RNE vigente | Sin olores ni coloraci&#243;n anormal</div>
  <div class="row g-2">
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Fecha y Hora</label>
      <input type="text" class="form-control form-control-sm bg-light" id="f01-dt" readonly>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Responsable *</label>
      <select class="form-select form-select-sm" id="f01-resp" onchange="toggleOtro('f01')">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option>Gabriel Vidal (Dir. Producci&#243;n)</option>
        <option>Sara Aguilar (Enc. Planta)</option>
        <option>Miguel Lozano (Enc. MP e Insumos)</option>
        <option>Juan Andrade (Enc. MP e Insumos)</option>
        <option>Otro</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3" id="f01-otro-col" style="display:none">
      <label class="form-label fw-bold">Nombre completo *</label>
      <input type="text" class="form-control form-control-sm" id="f01-otro" placeholder="Apellido y nombre">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Proveedor *</label>
      <input type="text" class="form-control form-control-sm" id="f01-prov" placeholder="Nombre del proveedor">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Producto *</label>
      <input type="text" class="form-control form-control-sm" id="f01-prod" placeholder="Ej: Carne vacuna, tripa...">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Kg</label>
      <input type="number" class="form-control form-control-sm" id="f01-kg" step="0.1" min="0">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Temperatura &#176;C *</label>
      <input type="number" class="form-control form-control-sm" id="f01-temp" step="0.1" placeholder="Ej: 4.5" oninput="chkTemp('f01-temp','f01-ts',7,'le','f01-tb')">
      <div id="f01-ts" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f01-tb"></div></div>
    </div>
    <div class="col-sm-3 col-md-2">
      <label class="form-label fw-bold">Estado visual</label>
      <select class="form-select form-select-sm" id="f01-visual">
        <option value="">&#8212;</option>
        <option value="OK">&#10003; OK</option>
        <option value="Rechazado">&#10007; Rechazado</option>
      </select>
    </div>
    <div class="col-sm-3 col-md-2">
      <label class="form-label fw-bold">Nro. Remito</label>
      <input type="text" class="form-control form-control-sm" id="f01-remito">
    </div>
    <div class="col-sm-3 col-md-2">
      <label class="form-label fw-bold">RNE Proveedor</label>
      <input type="text" class="form-control form-control-sm" id="f01-rne">
    </div>
    <div class="col-sm-3 col-md-2">
      <label class="form-label fw-bold">Lote / Vto.</label>
      <input type="text" class="form-control form-control-sm" id="f01-lote">
    </div>
    <div class="col-12">
      <label class="form-label fw-bold">Observaciones</label>
      <textarea class="form-control form-control-sm" id="f01-obs" rows="2"></textarea>
    </div>
    <div class="col-12">
      <div class="firma-label">Firma digital del responsable *</div>
      <div class="firma-box"><canvas id="sig-f01"></canvas></div>
      <div class="text-end mt-1"><button class="btn btn-sm btn-outline-secondary" onclick="borrarFirma('f01')">&#128465; Borrar firma</button></div>
    </div>
    <div class="col-12">
      <button class="btn btn-success fw-bold w-100 py-2" onclick="guardar('f01')">&#10004; REGISTRAR RECEPCI&#211;N</button>
    </div>
  </div>
</div>
</div>

<!-- ============================ F-02 CAMARAS ============================ -->
<div class="tab-pane fade" id="f02">
<div class="tarjeta">
  <h5>F-HACCP-02 &mdash; Temperatura de C&#225;maras <small class="badge bg-secondary ms-2">CCP 2</small></h5>
  <div class="aviso">&#9888; Refrigeraci&#243;n: 0&#176;C a 4&#176;C | Freezer congelados: &#8804; -18&#176;C | Sala elaboraci&#243;n: &#8804; 12&#176;C</div>
  <div class="row g-2">
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Fecha y Hora</label>
      <input type="text" class="form-control form-control-sm bg-light" id="f02-dt" readonly>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Responsable *</label>
      <select class="form-select form-select-sm" id="f02-resp" onchange="toggleOtro('f02')">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option>Gabriel Vidal (Dir. Producci&#243;n)</option>
        <option>Sara Aguilar (Enc. Planta)</option>
        <option>Miguel Lozano (Enc. MP e Insumos)</option>
        <option>Juan Andrade (Enc. MP e Insumos)</option>
        <option>Otro</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3" id="f02-otro-col" style="display:none">
      <label class="form-label fw-bold">Nombre completo *</label>
      <input type="text" class="form-control form-control-sm" id="f02-otro">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Momento *</label>
      <select class="form-select form-select-sm" id="f02-momento">
        <option value="">&#8212;</option>
        <option>Inicio de turno</option>
        <option>Fin de turno</option>
        <option>Novedad / Alarma</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">T&#176; Refrigeraci&#243;n (&#176;C) *</label>
      <input type="number" class="form-control form-control-sm" id="f02-ref" step="0.1" placeholder="L&#237;mite: 0 a 4&#176;C" oninput="chkRango('f02-ref','f02-rs',0,4,'f02-rb')">
      <div id="f02-rs" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f02-rb"></div></div>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">T&#176; Freezer (&#176;C) *</label>
      <input type="number" class="form-control form-control-sm" id="f02-frz" step="0.1" placeholder="L&#237;mite: &#8804; -18&#176;C" oninput="chkTemp('f02-frz','f02-fs',-18,'le','f02-fb')">
      <div id="f02-fs" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f02-fb"></div></div>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">T&#176; Sala (&#176;C)</label>
      <input type="number" class="form-control form-control-sm" id="f02-sala" step="0.1" placeholder="L&#237;mite: &#8804; 12&#176;C" oninput="chkTemp('f02-sala','f02-ss',12,'le','f02-sb')">
      <div id="f02-ss" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f02-sb"></div></div>
    </div>
    <div class="col-12">
      <label class="form-label fw-bold">Novedad / Alarma</label>
      <textarea class="form-control form-control-sm" id="f02-nov" rows="2" placeholder="Completar solo si hay alarma o temperatura fuera de rango"></textarea>
    </div>
    <div class="col-12">
      <div class="firma-label">Firma digital del responsable *</div>
      <div class="firma-box"><canvas id="sig-f02"></canvas></div>
      <div class="text-end mt-1"><button class="btn btn-sm btn-outline-secondary" onclick="borrarFirma('f02')">&#128465; Borrar firma</button></div>
    </div>
    <div class="col-12">
      <button class="btn btn-success fw-bold w-100 py-2" onclick="guardar('f02')">&#10004; REGISTRAR TEMPERATURAS</button>
    </div>
  </div>
</div>
</div>

<!-- ============================ F-03 ELABORACION ============================ -->
<div class="tab-pane fade" id="f03">
<div class="tarjeta">
  <h5>F-HACCP-03 &mdash; Temperatura de Elaboraci&#243;n <small class="badge bg-secondary ms-2">CCP 2b</small></h5>
  <div class="aviso">&#9888; T&#176; masa post-picado: &#8804; 7&#176;C | T&#176; sala: &#8804; 12&#176;C | Tiempo fuera de c&#225;mara: &#8804; 45 min | CR&#205;TICO en hamburguesa</div>
  <div class="row g-2">
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Fecha y Hora</label>
      <input type="text" class="form-control form-control-sm bg-light" id="f03-dt" readonly>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Responsable *</label>
      <select class="form-select form-select-sm" id="f03-resp" onchange="toggleOtro('f03')">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option>Gabriel Vidal (Dir. Producci&#243;n)</option>
        <option>Sara Aguilar (Enc. Planta)</option>
        <option>Miguel Lozano (Enc. MP e Insumos)</option>
        <option>Juan Andrade (Enc. MP e Insumos)</option>
        <option>Otro</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3" id="f03-otro-col" style="display:none">
      <label class="form-label fw-bold">Nombre completo *</label>
      <input type="text" class="form-control form-control-sm" id="f03-otro">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Producto *</label>
      <select class="form-select form-select-sm" id="f03-prod">
        <option value="">&#8212;</option>
        <option>Chorizo fresco</option>
        <option>Salchicha parrillera</option>
        <option>Hamburguesa (tubo)</option>
        <option>Hamburguesa (cortada)</option>
      </select>
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Kg del lote</label>
      <input type="number" class="form-control form-control-sm" id="f03-kg" step="0.1" min="0">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Hora inicio</label>
      <input type="time" class="form-control form-control-sm" id="f03-hi">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Hora fin</label>
      <input type="time" class="form-control form-control-sm" id="f03-hf">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">T&#176; masa (&#176;C) *</label>
      <input type="number" class="form-control form-control-sm" id="f03-masa" step="0.1" placeholder="&#8804; 7&#176;C" oninput="chkTemp('f03-masa','f03-ms',7,'le','f03-mb')">
      <div id="f03-ms" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f03-mb"></div></div>
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">T&#176; sala (&#176;C)</label>
      <input type="number" class="form-control form-control-sm" id="f03-sala" step="0.1" placeholder="&#8804; 12&#176;C" oninput="chkTemp('f03-sala','f03-ss',12,'le','f03-sb')">
      <div id="f03-ss" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f03-sb"></div></div>
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Tiempo fuera c&#225;m. (min)</label>
      <input type="number" class="form-control form-control-sm" id="f03-tpo" step="1" min="0" placeholder="&#8804; 45 min" oninput="chkTemp('f03-tpo','f03-ts',45,'le','f03-tb')">
      <div id="f03-ts" class="mt-1"></div>
      <div class="barra-wrap"><div class="barra" id="f03-tb"></div></div>
    </div>
    <div class="col-12">
      <label class="form-label fw-bold">Observaciones</label>
      <textarea class="form-control form-control-sm" id="f03-obs" rows="2"></textarea>
    </div>
    <div class="col-12">
      <div class="firma-label">Firma digital del responsable *</div>
      <div class="firma-box"><canvas id="sig-f03"></canvas></div>
      <div class="text-end mt-1"><button class="btn btn-sm btn-outline-secondary" onclick="borrarFirma('f03')">&#128465; Borrar firma</button></div>
    </div>
    <div class="col-12">
      <button class="btn btn-success fw-bold w-100 py-2" onclick="guardar('f03')">&#10004; REGISTRAR ELABORACI&#211;N</button>
    </div>
  </div>
</div>
</div>

<!-- ============================ F-04 DESPACHO ============================ -->
<div class="tab-pane fade" id="f04">
<div class="tarjeta">
  <h5>F-HACCP-04 &mdash; Temperatura de Despacho <small class="badge bg-secondary ms-2">CCP 3</small></h5>
  <div class="aviso">&#9888; Frescos: &#8804; 4&#176;C | Congelados (hamburguesa): &#8804; -15&#176;C | Verificar veh&#237;culo ANTES de cargar</div>
  <div class="row g-2">
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Fecha y Hora</label>
      <input type="text" class="form-control form-control-sm bg-light" id="f04-dt" readonly>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Responsable *</label>
      <select class="form-select form-select-sm" id="f04-resp" onchange="toggleOtro('f04')">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option>Gabriel Vidal (Dir. Producci&#243;n)</option>
        <option>Sara Aguilar (Enc. Planta)</option>
        <option>Miguel Lozano (Enc. MP e Insumos)</option>
        <option>Juan Andrade (Enc. MP e Insumos)</option>
        <option>Chofer</option>
        <option>Otro</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3" id="f04-otro-col" style="display:none">
      <label class="form-label fw-bold">Nombre completo *</label>
      <input type="text" class="form-control form-control-sm" id="f04-otro">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Tipo de producto *</label>
      <select class="form-select form-select-sm" id="f04-tipo" onchange="actualizarLimitesDespacho()">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option value="fresco">Fresco (chorizo / salchicha)</option>
        <option value="congelado">Congelado (hamburguesa)</option>
      </select>
    </div>
    <div class="col-12" id="f04-limite-aviso"></div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Producto / Descripci&#243;n *</label>
      <input type="text" class="form-control form-control-sm" id="f04-prod">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">Cantidad (kg)</label>
      <input type="number" class="form-control form-control-sm" id="f04-kg" step="0.1" min="0">
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">T&#176; Producto (&#176;C) *</label>
      <input type="number" class="form-control form-control-sm" id="f04-tprod" step="0.1" oninput="chkDespacho()">
      <div id="f04-ps" class="mt-1"></div>
    </div>
    <div class="col-6 col-sm-3 col-md-2">
      <label class="form-label fw-bold">T&#176; Veh&#237;culo (&#176;C) *</label>
      <input type="number" class="form-control form-control-sm" id="f04-tveh" step="0.1" oninput="chkDespacho()">
      <div id="f04-vs" class="mt-1"></div>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Cliente / Destino</label>
      <input type="text" class="form-control form-control-sm" id="f04-cliente">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Chofer</label>
      <input type="text" class="form-control form-control-sm" id="f04-chofer">
    </div>
    <div class="col-12">
      <label class="form-label fw-bold">Observaciones</label>
      <textarea class="form-control form-control-sm" id="f04-obs" rows="2"></textarea>
    </div>
    <div class="col-12">
      <div class="firma-label">Firma digital del responsable *</div>
      <div class="firma-box"><canvas id="sig-f04"></canvas></div>
      <div class="text-end mt-1"><button class="btn btn-sm btn-outline-secondary" onclick="borrarFirma('f04')">&#128465; Borrar firma</button></div>
    </div>
    <div class="col-12">
      <button class="btn btn-success fw-bold w-100 py-2" onclick="guardar('f04')">&#10004; REGISTRAR DESPACHO</button>
    </div>
  </div>
</div>
</div>

<!-- ============================ F-05 CORRECTIVA ============================ -->
<div class="tab-pane fade" id="f05">
<div class="tarjeta" style="border-left:4px solid #dc3545">
  <h5>&#9888; F-HACCP-05 &mdash; Acci&#243;n Correctiva <span class="badge bg-danger ms-2">DESV&#205;O</span></h5>
  <div class="aviso aviso-rojo">Completar CADA VEZ que se detecta temperatura fuera de l&#237;mite o incumplimiento en cualquier CCP.</div>
  <div class="row g-2">
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Fecha y Hora</label>
      <input type="text" class="form-control form-control-sm bg-light" id="f05-dt" readonly>
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">Responsable *</label>
      <select class="form-select form-select-sm" id="f05-resp" onchange="toggleOtro('f05')">
        <option value="">&#8212; Seleccionar &#8212;</option>
        <option>Gabriel Vidal (Dir. Producci&#243;n)</option>
        <option>Sara Aguilar (Enc. Planta)</option>
        <option>Miguel Lozano (Enc. MP e Insumos)</option>
        <option>Juan Andrade (Enc. MP e Insumos)</option>
        <option>Otro</option>
      </select>
    </div>
    <div class="col-sm-4 col-md-3" id="f05-otro-col" style="display:none">
      <label class="form-label fw-bold">Nombre completo *</label>
      <input type="text" class="form-control form-control-sm" id="f05-otro">
    </div>
    <div class="col-sm-4 col-md-3">
      <label class="form-label fw-bold">CCP afectado *</label>
      <select class="form-select form-select-sm" id="f05-ccp">
        <option value="">&#8212;</option>
        <option>CCP 1 &mdash; Recepci&#243;n MP</option>
        <option>CCP 2 &mdash; Temperatura c&#225;maras</option>
        <option>CCP 2b &mdash; Temperatura elaboraci&#243;n</option>
        <option>CCP 3 &mdash; Despacho</option>
      </select>
    </div>
    <div class="col-12">
      <label class="form-label fw-bold">Descripci&#243;n del desv&#237;o *</label>
      <textarea class="form-control form-control-sm" id="f05-desv" rows="2" placeholder="Qu&#233; ocurri&#243; y qu&#233; valor se midi&#243;"></textarea>
    </div>
    <div class="col-sm-6">
      <label class="form-label fw-bold">Causa probable</label>
      <textarea class="form-control form-control-sm" id="f05-causa" rows="2"></textarea>
    </div>
    <div class="col-sm-6">
      <label class="form-label fw-bold">Acci&#243;n correctiva tomada *</label>
      <textarea class="form-control form-control-sm" id="f05-accion" rows="2" placeholder="Qu&#233; se hizo con el producto y c&#243;mo se corrigi&#243;"></textarea>
    </div>
    <div class="col-sm-6">
      <label class="form-label fw-bold">Destino del producto afectado</label>
      <select class="form-select form-select-sm" id="f05-destino">
        <option value="">&#8212;</option>
        <option>Devuelto a c&#225;mara / espera evaluaci&#243;n</option>
        <option>Liberado (temperatura normalizada)</option>
        <option>Rechazado / Descartado</option>
        <option>En evaluaci&#243;n por Dir. Producci&#243;n</option>
      </select>
    </div>
    <div class="col-sm-6">
      <label class="form-label fw-bold">&#191;Se notific&#243; a Gabriel Vidal?</label>
      <select class="form-select form-select-sm" id="f05-noti">
        <option value="">&#8212;</option>
        <option>S&#237; &mdash; notificado inmediatamente</option>
        <option>S&#237; &mdash; notificado por WhatsApp</option>
        <option>No correspond&#237;a notificar</option>
      </select>
    </div>
    <div class="col-12">
      <div class="firma-label">Firma digital del responsable *</div>
      <div class="firma-box"><canvas id="sig-f05"></canvas></div>
      <div class="text-end mt-1"><button class="btn btn-sm btn-outline-secondary" onclick="borrarFirma('f05')">&#128465; Borrar firma</button></div>
    </div>
    <div class="col-12">
      <button class="btn btn-danger fw-bold w-100 py-2" onclick="guardar('f05')">&#9888; REGISTRAR ACCI&#211;N CORRECTIVA</button>
    </div>
  </div>
</div>
</div>

<!-- ============================ REGISTROS ============================ -->
<div class="tab-pane fade" id="registros">
<div class="tarjeta">
  <div class="d-flex justify-content-between align-items-center mb-3 flex-wrap gap-2">
    <h5 class="mb-0">&#128203; Historial de Registros</h5>
    <div class="d-flex gap-2 flex-wrap">
      <select class="form-select form-select-sm" id="filtro" style="width:150px" onchange="mostrarRegistros()">
        <option value="">Todos</option>
        <option value="F-01">F-01 Recepci&#243;n</option>
        <option value="F-02">F-02 C&#225;maras</option>
        <option value="F-03">F-03 Elaboraci&#243;n</option>
        <option value="F-04">F-04 Despacho</option>
        <option value="F-05">Correctivas</option>
      </select>
      <button class="btn btn-sm btn-outline-danger" onclick="borrarTodo()">&#128465; Borrar</button>
      <button class="btn btn-sm btn-dark no-imprimir" onclick="window.print()">&#128424; Imprimir</button>
    </div>
  </div>
  <div id="cnt-registros" class="text-muted small mb-2"></div>
  <div class="table-responsive">
    <table class="table table-bordered table-sm tabla-reg">
      <thead><tr><th>Form.</th><th>Fecha / Hora</th><th>Responsable</th><th>Detalle</th><th>Estado</th><th>Firma</th></tr></thead>
      <tbody id="cuerpo-tabla"></tbody>
    </table>
  </div>
  <p id="sin-registros" class="text-center text-muted mt-3" style="display:none">Sin registros. Complet&#225; el primer formulario.</p>
</div>
</div>

<!-- ============================ QR ============================ -->
<div class="tab-pane fade" id="qrcodes">
<div class="tarjeta">
  <div class="d-flex justify-content-between align-items-center mb-3">
    <h5 class="mb-0">&#128242; C&#243;digos QR por zona</h5>
    <button class="btn btn-sm btn-dark no-imprimir" onclick="window.print()">&#128424; Imprimir QR</button>
  </div>
  <p class="text-muted small mb-3">Imprim&#237; esta p&#225;gina, recort&#225; cada QR y peg&#225;lo plastificado en la zona. Al escanearlo abre directo el formulario correcto.</p>
  <div id="qr-grilla" class="row g-3 justify-content-center"></div>
  <div class="mt-3 p-3 rounded" style="background:var(--verde-claro);font-size:.78rem;color:var(--verde)">
    <strong>Nota:</strong> Los QR se generan desde la URL actual del archivo. Para que funcionen en otros dispositivos, el archivo debe estar en una URL accesible en la red (no desde una carpeta local de PC).
  </div>
</div>
</div>

</div><!-- tab-content -->
</div><!-- container -->

<!-- TOAST -->
<div class="position-fixed bottom-0 end-0 p-3" style="z-index:9999">
  <div id="toast" class="toast align-items-center border-0" role="alert">
    <div class="d-flex">
      <div class="toast-body fw-bold" id="toast-msg"></div>
      <button type="button" class="btn-close btn-close-white me-2 m-auto" data-bs-dismiss="toast"></button>
    </div>
  </div>
</div>

<script>
// ──────────────────────────────────────────────
// FIRMA DIGITAL
// ──────────────────────────────────────────────
var pads = {};

function iniciarFirmas() {
  ['f01','f02','f03','f04','f05'].forEach(function(id) {
    var canvas = document.getElementById('sig-' + id);
    if (!canvas) return;
    pads[id] = new SignaturePad(canvas, {
      backgroundColor: 'rgba(0,0,0,0)',
      penColor: '#1A5C2E',
      minWidth: 1.2,
      maxWidth: 3
    });
    ajustarCanvas(canvas, pads[id]);
  });
  window.addEventListener('resize', function() {
    ['f01','f02','f03','f04','f05'].forEach(function(id) {
      var canvas = document.getElementById('sig-' + id);
      if (canvas && pads[id]) ajustarCanvas(canvas, pads[id]);
    });
  });
}

function ajustarCanvas(canvas, pad) {
  var data = pad.toData();
  var ratio = Math.max(window.devicePixelRatio || 1, 1);
  canvas.width = canvas.offsetWidth * ratio;
  canvas.height = canvas.offsetHeight * ratio;
  canvas.getContext('2d').scale(ratio, ratio);
  pad.fromData(data);
}

function borrarFirma(id) {
  if (pads[id]) pads[id].clear();
}

// ──────────────────────────────────────────────
// RELOJ
// ──────────────────────────────────────────────
function actualizarReloj() {
  var ahora = new Date();
  var str = ahora.toLocaleDateString('es-AR') + '  ' + ahora.toLocaleTimeString('es-AR');
  var el = document.getElementById('reloj');
  if (el) el.textContent = str;
  ['f01','f02','f03','f04','f05'].forEach(function(id) {
    var dt = document.getElementById(id + '-dt');
    if (dt) dt.value = str;
  });
}
setInterval(actualizarReloj, 1000);

// ──────────────────────────────────────────────
// TOGGLE OTRO
// ──────────────────────────────────────────────
function toggleOtro(id) {
  var sel = document.getElementById(id + '-resp');
  var col = document.getElementById(id + '-otro-col');
  if (col) col.style.display = (sel && sel.value === 'Otro') ? 'block' : 'none';
}

// ──────────────────────────────────────────────
// VERIFICACION DE TEMPERATURA
// ──────────────────────────────────────────────
function chkTemp(inputId, statusId, limite, dir, barId) {
  var val = parseFloat(document.getElementById(inputId).value);
  var sEl = document.getElementById(statusId);
  var bEl = document.getElementById(barId);
  if (!sEl) return;
  if (isNaN(val)) { sEl.innerHTML = ''; if (bEl) { bEl.style.width = '0%'; } return; }
  var ok = (dir === 'le') ? (val <= limite) : (val >= limite);
  sEl.innerHTML = ok
    ? '<span class="badge-ok">&#10004; CUMPLE</span>'
    : '<span class="badge-mal">&#10008; FUERA DE L&#205;MITE</span>';
  if (bEl) {
    var pct = Math.min(Math.abs(val / (limite || 1)) * 60, 100);
    bEl.style.width = pct + '%';
    bEl.style.background = ok ? '#198754' : '#dc3545';
  }
}

function chkRango(inputId, statusId, min, max, barId) {
  var val = parseFloat(document.getElementById(inputId).value);
  var sEl = document.getElementById(statusId);
  var bEl = document.getElementById(barId);
  if (!sEl) return;
  if (isNaN(val)) { sEl.innerHTML = ''; if (bEl) { bEl.style.width = '0%'; } return; }
  var ok = val >= min && val <= max;
  sEl.innerHTML = ok
    ? '<span class="badge-ok">&#10004; CUMPLE</span>'
    : '<span class="badge-mal">&#10008; FUERA DE L&#205;MITE</span>';
  if (bEl) {
    var pct = Math.min(((val - min + 2) / (max - min + 4)) * 100, 100);
    bEl.style.width = Math.max(pct, 0) + '%';
    bEl.style.background = ok ? '#198754' : '#dc3545';
  }
}

// ──────────────────────────────────────────────
// DESPACHO
// ──────────────────────────────────────────────
function actualizarLimitesDespacho() {
  var tipo = document.getElementById('f04-tipo').value;
  var aviso = document.getElementById('f04-limite-aviso');
  if (tipo === 'fresco') {
    aviso.innerHTML = '<div class="aviso">Producto fresco: T&#176; producto &#8804; 4&#176;C | T&#176; veh&#237;culo &#8804; 4&#176;C</div>';
  } else if (tipo === 'congelado') {
    aviso.innerHTML = '<div class="aviso">Producto congelado: T&#176; producto &#8804; -15&#176;C | T&#176; veh&#237;culo &#8804; -15&#176;C</div>';
  } else {
    aviso.innerHTML = '';
  }
  chkDespacho();
}

function chkDespacho() {
  var tipo = document.getElementById('f04-tipo').value;
  if (!tipo) return;
  var limite = (tipo === 'fresco') ? 4 : -15;
  var tp = parseFloat(document.getElementById('f04-tprod').value);
  var tv = parseFloat(document.getElementById('f04-tveh').value);
  var ps = document.getElementById('f04-ps');
  var vs = document.getElementById('f04-vs');
  if (!isNaN(tp) && ps) {
    ps.innerHTML = (tp <= limite)
      ? '<span class="badge-ok">&#10004; CUMPLE</span>'
      : '<span class="badge-mal">&#10008; FUERA DE L&#205;MITE</span>';
  }
  if (!isNaN(tv) && vs) {
    vs.innerHTML = (tv <= limite)
      ? '<span class="badge-ok">&#10004; CUMPLE</span>'
      : '<span class="badge-mal">&#10008; FUERA DE L&#205;MITE</span>';
  }
}

// ──────────────────────────────────────────────
// STORAGE
// ──────────────────────────────────────────────
function leerRegistros() {
  try { return JSON.parse(localStorage.getItem('gamar_haccp') || '[]'); } catch(e) { return []; }
}
function guardarRegistros(arr) {
  localStorage.setItem('gamar_haccp', JSON.stringify(arr));
}

// ──────────────────────────────────────────────
// OBTENER RESPONSABLE
// ──────────────────────────────────────────────
function obtenerResp(id) {
  var sel = document.getElementById(id + '-resp');
  if (!sel) return '';
  if (sel.value === 'Otro') {
    var otro = document.getElementById(id + '-otro');
    return otro ? otro.value.trim() : '';
  }
  return sel.value;
}

// ──────────────────────────────────────────────
// GUARDAR FORMULARIO
// ──────────────────────────────────────────────
function guardar(id) {
  var resp = obtenerResp(id);
  if (!resp) { alert('Seleccioná o ingresá el nombre del responsable.'); return; }
  if (!pads[id] || pads[id].isEmpty()) { alert('La firma es obligatoria. Por favor firmá antes de guardar.'); return; }

  var dt = document.getElementById(id + '-dt').value;
  var sig = pads[id].toDataURL('image/png');
  var reg = { ts: Date.now(), tipo: '', dt: dt, resp: resp, sig: sig, ok: true, detalle: '' };

  if (id === 'f01') {
    var temp = parseFloat(document.getElementById('f01-temp').value);
    var visual = document.getElementById('f01-visual').value;
    reg.tipo = 'F-01';
    reg.ok = (!isNaN(temp) && temp <= 7) && (visual !== 'Rechazado');
    reg.detalle = [
      document.getElementById('f01-prod').value,
      document.getElementById('f01-prov').value,
      'T°: ' + temp + '°C',
      'Visual: ' + visual
    ].filter(Boolean).join(' | ');
    limpiar(['f01-prov','f01-prod','f01-kg','f01-temp','f01-remito','f01-rne','f01-lote','f01-obs'], ['f01-visual','f01-resp'], ['f01-ts','f01-tb']);

  } else if (id === 'f02') {
    var ref = parseFloat(document.getElementById('f02-ref').value);
    var frz = parseFloat(document.getElementById('f02-frz').value);
    var sala2 = parseFloat(document.getElementById('f02-sala').value);
    reg.tipo = 'F-02';
    reg.ok = (!isNaN(ref) && ref >= 0 && ref <= 4) && (!isNaN(frz) && frz <= -18);
    reg.detalle = document.getElementById('f02-momento').value
      + ' | Refrig: ' + ref + '°C | Freezer: ' + frz + '°C | Sala: ' + sala2 + '°C';
    limpiar(['f02-ref','f02-frz','f02-sala','f02-nov'], ['f02-momento','f02-resp'], ['f02-rs','f02-rb','f02-fs','f02-fb','f02-ss','f02-sb']);

  } else if (id === 'f03') {
    var masa = parseFloat(document.getElementById('f03-masa').value);
    var sala3 = parseFloat(document.getElementById('f03-sala').value);
    var tpo = parseFloat(document.getElementById('f03-tpo').value);
    reg.tipo = 'F-03';
    reg.ok = (!isNaN(masa) && masa <= 7) && (!isNaN(sala3) && sala3 <= 12) && (!isNaN(tpo) && tpo <= 45);
    reg.detalle = document.getElementById('f03-prod').value
      + ' | T° masa: ' + masa + '°C | Sala: ' + sala3 + '°C | Tiempo: ' + tpo + 'min';
    limpiar(['f03-kg','f03-hi','f03-hf','f03-masa','f03-sala','f03-tpo','f03-obs'], ['f03-prod','f03-resp'], ['f03-ms','f03-mb','f03-ss','f03-sb','f03-ts','f03-tb']);

  } else if (id === 'f04') {
    var tipo4 = document.getElementById('f04-tipo').value;
    var lim4 = (tipo4 === 'fresco') ? 4 : -15;
    var tp4 = parseFloat(document.getElementById('f04-tprod').value);
    var tv4 = parseFloat(document.getElementById('f04-tveh').value);
    reg.tipo = 'F-04';
    reg.ok = (!isNaN(tp4) && tp4 <= lim4) && (!isNaN(tv4) && tv4 <= lim4);
    reg.detalle = tipo4 + ' | ' + document.getElementById('f04-prod').value
      + ' | T° prod: ' + tp4 + '°C | T° veh: ' + tv4 + '°C | ' + document.getElementById('f04-cliente').value;
    limpiar(['f04-prod','f04-kg','f04-tprod','f04-tveh','f04-cliente','f04-chofer','f04-obs'], ['f04-tipo','f04-resp'], ['f04-ps','f04-vs','f04-limite-aviso']);

  } else if (id === 'f05') {
    reg.tipo = 'F-05';
    reg.ok = false;
    var desv = document.getElementById('f05-desv').value;
    reg.detalle = document.getElementById('f05-ccp').value + ' | ' + desv.substring(0, 60) + (desv.length > 60 ? '...' : '');
    limpiar(['f05-desv','f05-causa','f05-accion'], ['f05-ccp','f05-destino','f05-noti','f05-resp'], []);
  }

  // Si hay desvío, ofrecer correctiva
  if (!reg.ok && id !== 'f05') {
    setTimeout(function() {
      if (confirm('⚠ Se detectó un desvío. ¿Registrar Acción Correctiva ahora?')) {
        irTab('f05');
      }
    }, 400);
  }

  var lista = leerRegistros();
  lista.unshift(reg);
  guardarRegistros(lista);
  enviarAGoogleSheets(reg);
  pads[id].clear();
  var respEl = document.getElementById(id + '-resp');
  if (respEl) respEl.value = '';
  var otroCol = document.getElementById(id + '-otro-col');
  if (otroCol) otroCol.style.display = 'none';

  mostrarToast(
    reg.ok ? '✔ Registro guardado correctamente' : '⚠ Registro guardado — DESVÍO detectado',
    reg.ok ? 'text-bg-success' : 'text-bg-danger'
  );
  mostrarRegistros();
}

function limpiar(textos, selects, estados) {
  textos.forEach(function(id) { var el = document.getElementById(id); if (el) el.value = ''; });
  selects.forEach(function(id) { var el = document.getElementById(id); if (el) el.value = ''; });
  estados.forEach(function(id) { var el = document.getElementById(id); if (el) { el.innerHTML = ''; el.style.width = '0%'; } });
}

// ──────────────────────────────────────────────
// MOSTRAR REGISTROS
// ──────────────────────────────────────────────
function mostrarRegistros() {
  var filtro = document.getElementById('filtro').value;
  var lista = leerRegistros();
  if (filtro) lista = lista.filter(function(r) { return r.tipo === filtro || (filtro === 'F-05' && r.tipo === 'F-05'); });

  var tbody = document.getElementById('cuerpo-tabla');
  var sinReg = document.getElementById('sin-registros');
  var cnt = document.getElementById('cnt-registros');

  if (!lista.length) {
    tbody.innerHTML = '';
    if (sinReg) sinReg.style.display = 'block';
    if (cnt) cnt.textContent = '';
    return;
  }
  if (sinReg) sinReg.style.display = 'none';
  if (cnt) cnt.textContent = lista.length + ' registro' + (lista.length !== 1 ? 's' : '');

  tbody.innerHTML = lista.map(function(r) {
    return '<tr class="' + (r.ok === false ? 'fila-mal' : '') + '">'
      + '<td><span class="badge ' + (r.tipo === 'F-05' ? 'bg-danger' : 'bg-secondary') + '">' + r.tipo + '</span></td>'
      + '<td style="white-space:nowrap">' + r.dt + '</td>'
      + '<td>' + r.resp + '</td>'
      + '<td style="max-width:260px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap" title="' + r.detalle + '">' + r.detalle + '</td>'
      + '<td>' + (r.ok === false ? '<span class="badge-mal">&#10008; DESV&#205;O</span>' : '<span class="badge-ok">&#10004; OK</span>') + '</td>'
      + '<td>' + (r.sig ? '<img src="' + r.sig + '" style="height:30px;max-width:75px;border:1px solid #ccc;border-radius:3px">' : '&#8212;') + '</td>'
      + '</tr>';
  }).join('');
}

function irTab(tabId) {
  var el = document.querySelector('[href="#' + tabId + '"]');
  if (el) new bootstrap.Tab(el).show();
}

function borrarTodo() {
  if (confirm('¿Borrar TODOS los registros? Esta acción no se puede deshacer.')) {
    localStorage.removeItem('gamar_haccp');
    mostrarRegistros();
  }
}

// ──────────────────────────────────────────────
// EXPORTAR CSV
// ──────────────────────────────────────────────
function exportarCSV() {
  var lista = leerRegistros();
  if (!lista.length) { alert('No hay registros para exportar.'); return; }
  var filas = [['Tipo','Fecha/Hora','Responsable','Detalle','Estado']];
  lista.forEach(function(r) {
    filas.push([r.tipo, r.dt, r.resp, r.detalle, r.ok === false ? 'DESVÍO' : 'OK']);
  });
  var csv = filas.map(function(f) {
    return f.map(function(c) { return '"' + String(c).replace(/"/g, '""') + '"'; }).join(',');
  }).join('\n');
  var a = document.createElement('a');
  a.href = 'data:text/csv;charset=utf-8,﻿' + encodeURIComponent(csv);
  a.download = 'HACCP_Gamar_' + new Date().toISOString().slice(0,10) + '.csv';
  a.click();
}

// ──────────────────────────────────────────────
// TOAST
// ──────────────────────────────────────────────
function mostrarToast(msg, cls) {
  var toastEl = document.getElementById('toast');
  var msgEl = document.getElementById('toast-msg');
  if (!toastEl || !msgEl) return;
  toastEl.className = 'toast align-items-center border-0 ' + cls;
  msgEl.textContent = msg;
  new bootstrap.Toast(toastEl, { delay: 3000 }).show();
}

// ──────────────────────────────────────────────
// QR CODES
// ──────────────────────────────────────────────
function generarQR() {
  var grilla = document.getElementById('qr-grilla');
  if (!grilla || grilla.dataset.generado) return;
  grilla.dataset.generado = '1';
  var base = window.location.href.split('#')[0];
  var forms = [
    { id: 'f01', label: 'F-01 Recepción MP', zona: 'Portón / Balanza', rojo: false },
    { id: 'f02', label: 'F-02 Cámaras de frío', zona: 'Sala de frío', rojo: false },
    { id: 'f03', label: 'F-03 Elaboración', zona: 'Sala elaboración', rojo: false },
    { id: 'f04', label: 'F-04 Despacho', zona: 'Playa de carga', rojo: false },
    { id: 'f05', label: 'F-05 Acción Correctiva', zona: 'Todas las zonas', rojo: true }
  ];
  grilla.innerHTML = '';
  forms.forEach(function(f) {
    var url = base + '#' + f.id;
    var col = document.createElement('div');
    col.className = 'col-6 col-md-4 col-lg-2';
    col.innerHTML = '<div class="qr-card' + (f.rojo ? ' rojo' : '') + '">'
      + '<div id="qr-' + f.id + '"></div>'
      + '<div class="qr-titulo">' + f.label + '</div>'
      + '<div class="qr-zona">' + f.zona + '</div>'
      + '</div>';
    grilla.appendChild(col);

    // Generar QR con imagen via API pública (sin libreria)
    var img = document.createElement('img');
    img.src = 'https://api.qrserver.com/v1/create-qr-code/?size=130x130&data=' + encodeURIComponent(url) + '&color=' + (f.rojo ? 'dc3545' : '1A5C2E');
    img.style.width = '130px';
    img.style.height = '130px';
    img.alt = 'QR ' + f.label;
    document.getElementById('qr-' + f.id).appendChild(img);
  });
}

// ──────────────────────────────────────────────
// INICIO
// ──────────────────────────────────────────────
document.addEventListener('DOMContentLoaded', function() {
  iniciarFirmas();
  actualizarReloj();
  mostrarRegistros();

  // Re-ajustar firmas al cambiar de tab
  document.querySelectorAll('[data-bs-toggle="tab"]').forEach(function(tab) {
    tab.addEventListener('shown.bs.tab', function() {
      ['f01','f02','f03','f04','f05'].forEach(function(id) {
        var canvas = document.getElementById('sig-' + id);
        if (canvas && pads[id]) ajustarCanvas(canvas, pads[id]);
      });
    });
  });

  // QR al hacer clic en esa tab
  var tabQR = document.getElementById('tab-qr');
  if (tabQR) {
    tabQR.addEventListener('shown.bs.tab', function() {
      generarQR();
    });
  }
});
  function enviarAGoogleSheets(registro) {

  const URL_SCRIPT = "https://script.google.com/macros/s/AKfycbyyrZVRh1JtaZuWa3-BUS2dhgbHMLMEmvVTU9cfBxtI72cK8u3mk9k5sdadvc-lVyVBow/exec";

  let formulario = "";

  switch(registro.tipo) {
    case "F-01":
      formulario = "Recepcion_MP";
      break;

    case "F-02":
      formulario = "Camaras";
      break;

    case "F-03":
      formulario = "Elaboracion";
      break;

    case "F-04":
      formulario = "Despacho";
      break;

    case "F-05":
      formulario = "Acciones_Correctivas";
      break;
  }

  fetch(URL_SCRIPT, {
    method: "POST",
    mode: "no-cors",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      formulario: formulario,
      responsable: registro.resp,
      producto: registro.detalle,
      temperatura: "",
      estado: registro.ok ? "OK" : "DESVIO"
    })
  })
  .then(() => console.log("Registro enviado a Google Sheets"))
  .catch(error => console.error("Error:", error));
}
</script>
</body>
</html>

