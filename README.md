# TYRE-ECO-
SISTEMA COMPLETO TYRE ECO
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Tyre Eco — Sistema Logístico</title>
<link rel="stylesheet" href=https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.19.0/dist/tabler-icons.min.css>
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#F7F7F5;--surface:#FFFFFF;--border:#E5E4E0;--border-light:#EFEFED;
  --text:#1A1A18;--text2:#6B6B65;--text3:#A8A8A2;
  --green:#1D7A4F;--green-bg:#EBF5EF;--green-light:#D1EDD9;
  --blue:#1A5FA8;--blue-bg:#EBF2FB;--blue-light:#C9DFF5;
  --orange:#B85C00;--orange-bg:#FDF0E5;--orange-light:#FAD9B4;
  --red:#B02020;--red-bg:#FDECEC;--red-light:#F5C0C0;
  --purple:#5040A8;--purple-bg:#F0EEFB;--purple-light:#CFC9F2;
  --teal:#0A6E5C;--teal-bg:#E8F5F2;--teal-light:#B8E0D8;
  --yellow:#8A6E00;--yellow-bg:#FDF8E5;--yellow-light:#F5E5A0;
  --radius:12px;--radius-sm:8px;--radius-xs:6px;
  --shadow:0 1px 3px rgba(0,0,0,.08),0 1px 2px rgba(0,0,0,.05);
  --shadow-md:0 4px 12px rgba(0,0,0,.10),0 2px 4px rgba(0,0,0,.06);
}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:var(--bg);color:var(--text);min-height:100vh;-webkit-tap-highlight-color:transparent}
.hidden{display:none!important}
#tela-login{
  min-height:100vh;display:flex;flex-direction:column;align-items:center;
  justify-content:center;padding:1.5rem;background:var(--bg)
}
.login-logo{
  width:72px;height:72px;border-radius:20px;
  background:var(--green);display:flex;align-items:center;justify-content:center;
  font-size:32px;color:#fff;margin-bottom:1.25rem;
  box-shadow:0 4px 16px rgba(29,122,79,.25)
}
.login-title{font-size:24px;font-weight:700;color:var(--text);letter-spacing:-.5px;margin-bottom:4px}
.login-sub{font-size:14px;color:var(--text2);margin-bottom:2rem}
.login-card{width:100%;max-width:360px;background:var(--surface);border-radius:var(--radius);border:1px solid var(--border);padding:1.5rem;box-shadow:var(--shadow-md)}
.login-label{font-size:12px;font-weight:600;color:var(--text2);letter-spacing:.03em;text-transform:uppercase;margin-bottom:6px;display:block}
.login-input{width:100%;padding:12px 14px;border:1.5px solid var(--border);border-radius:var(--radius-sm);font-size:15px;font-family:inherit;color:var(--text);background:var(--bg);transition:border .15s;margin-bottom:14px}
.login-input:focus{outline:none;border-color:var(--green);background:#fff}
.btn-login{width:100%;padding:13px;background:var(--green);color:#fff;border:none;border-radius:var(--radius-sm);font-size:15px;font-weight:600;cursor:pointer;margin-top:4px;transition:background .15s;display:flex;align-items:center;justify-content:center;gap:8px}
.btn-login:hover{background:#176040}
.login-erro{font-size:13px;color:var(--red);text-align:center;margin-top:10px;padding:8px;background:var(--red-bg);border-radius:var(--radius-xs);display:none}
.login-hint{margin-top:1.25rem;border-top:1px solid var(--border-light);padding-top:1rem}
.login-hint p{font-size:11px;color:var(--text3);text-align:center;margin-bottom:8px;text-transform:uppercase;letter-spacing:.04em}
.hint-grid{display:grid;grid-template-columns:1fr 1fr;gap:6px}
.hint-item{background:var(--bg);border:1px solid var(--border);border-radius:var(--radius-xs);padding:7px 10px;cursor:pointer;transition:all .15s}
.hint-item:hover{border-color:var(--green);background:var(--green-bg)}
.hint-item .hi-nome{font-size:12px;font-weight:600;color:var(--text)}
.hint-item .hi-cargo{font-size:10px;color:var(--text2)}
#app{display:none;flex-direction:column;min-height:100vh}
.topbar{background:var(--surface);border-bottom:1px solid var(--border);padding:0 1rem;height:56px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;flex-shrink:0}
.topbar-left{display:flex;align-items:center;gap:10px}
.topbar-logo{width:32px;height:32px;border-radius:8px;background:var(--green);display:flex;align-items:center;justify-content:center;color:#fff;font-size:14px;font-weight:700}
.topbar-info h1{font-size:14px;font-weight:600;color:var(--text);line-height:1.2}
.topbar-info span{font-size:11px;color:var(--text2)}
.topbar-right{display:flex;align-items:center;gap:8px}
.btn-logout{padding:6px 10px;background:none;border:1px solid var(--border);border-radius:var(--radius-xs);font-size:12px;color:var(--text2);cursor:pointer;font-family:inherit;display:flex;align-items:center;gap:5px}
.btn-logout:hover{background:var(--red-bg);border-color:var(--red-light);color:var(--red)}
.content-area{flex:1;padding:1rem;max-width:540px;margin:0 auto;width:100%}
.dash-greeting{font-size:20px;font-weight:700;color:var(--text);margin-bottom:4px;letter-spacing:-.3px}
.dash-date{font-size:13px;color:var(--text2);margin-bottom:1.25rem}
.modules-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.mod-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:1rem;cursor:pointer;transition:all .2s;position:relative;overflow:hidden}
.mod-card:hover,.mod-card:active{transform:translateY(-1px);box-shadow:var(--shadow-md)}
.mod-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px}
.mod-card.verde::before{background:var(--green)}
.mod-card.azul::before{background:var(--blue)}
.mod-card.laranja::before{background:var(--orange)}
.mod-card.roxo::before{background:var(--purple)}
.mod-card.teal::before{background:var(--teal)}
.mod-card.amarelo::before{background:var(--yellow)}
.mod-card.vermelho::before{background:var(--red)}
.mod-card.vermelho::before{background:var(--red)}
.mod-icon{width:40px;height:40px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;margin-bottom:10px}
.mod-icon.verde{background:var(--green-bg);color:var(--green)}
.mod-icon.azul{background:var(--blue-bg);color:var(--blue)}
.mod-icon.laranja{background:var(--orange-bg);color:var(--orange)}
.mod-icon.roxo{background:var(--purple-bg);color:var(--purple)}
.mod-icon.teal{background:var(--teal-bg);color:var(--teal)}
.mod-icon.amarelo{background:var(--yellow-bg);color:var(--yellow)}
.mod-icon.vermelho{background:var(--red-bg);color:var(--red)}
.mod-icon.vermelho{background:var(--red-bg);color:var(--red)}
.mod-name{font-size:13px;font-weight:600;color:var(--text);margin-bottom:3px}
.mod-desc{font-size:11px;color:var(--text2);line-height:1.4}
.mod-badge{position:absolute;top:10px;right:10px;background:var(--red);color:#fff;border-radius:20px;padding:2px 7px;font-size:10px;font-weight:700}
.mod-header{display:flex;align-items:center;gap:10px;margin-bottom:1.25rem;padding-bottom:1rem;border-bottom:1px solid var(--border-light)}
.mod-header-icon{width:40px;height:40px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0}
.mod-header h2{font-size:16px;font-weight:700;color:var(--text);letter-spacing:-.2px}
.mod-header span{font-size:12px;color:var(--text2)}
.btn-back{background:none;border:1px solid var(--border);border-radius:var(--radius-xs);padding:6px 10px;font-size:12px;color:var(--text2);cursor:pointer;font-family:inherit;display:flex;align-items:center;gap:5px;margin-bottom:1rem}
.btn-back:hover{background:var(--bg)}
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);padding:1rem;margin-bottom:10px}
.badge{display:inline-flex;align-items:center;gap:3px;padding:3px 8px;border-radius:20px;font-size:10px;font-weight:600;white-space:nowrap}
.badge.verde{background:var(--green-bg);color:var(--green)}
.badge.azul{background:var(--blue-bg);color:var(--blue)}
.badge.laranja{background:var(--orange-bg);color:var(--orange)}
.badge.vermelho{background:var(--red-bg);color:var(--red)}
.badge.roxo{background:var(--purple-bg);color:var(--purple)}
.badge.cinza{background:var(--bg);color:var(--text2)}
.section-title{font-size:11px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:.05em;margin-bottom:8px;margin-top:1rem}
.row{display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid var(--border-light)}
.row:last-child{border-bottom:none}
.stat-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:8px;margin-bottom:1rem}
.stat-grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-bottom:1rem}
.stat-box{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-sm);padding:10px;text-align:center}
.stat-box .sv{font-size:20px;font-weight:700;color:var(--text)}
.stat-box .sl{font-size:10px;color:var(--text2);margin-top:2px;text-transform:uppercase;letter-spacing:.03em}
.stat-box.verde .sv{color:var(--green)}
.stat-box.azul .sv{color:var(--blue)}
.stat-box.laranja .sv{color:var(--orange)}
.stat-box.vermelho .sv{color:var(--red)}
.fin-row{display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--border-light);font-size:13px}
.fin-row:last-child{border-bottom:none}
.fin-row .fl{color:var(--text2)}
.fin-row .fv{font-weight:600}
.pos{color:var(--green)}.neg{color:var(--red)}.warn{color:var(--orange)}
.alert{border-radius:var(--radius-sm);padding:10px 14px;margin-bottom:12px;display:flex;gap:10px;align-items:flex-start;font-size:13px}
.alert.verde{background:var(--green-bg);border:1px solid var(--green-light);color:var(--green)}
.alert.azul{background:var(--blue-bg);border:1px solid var(--blue-light);color:var(--blue)}
.alert.laranja{background:var(--orange-bg);border:1px solid var(--orange-light);color:var(--orange)}
.alert.vermelho{background:var(--red-bg);border:1px solid var(--red-light);color:var(--red)}
.alert i{font-size:16px;flex-shrink:0;margin-top:1px}
.alert p{line-height:1.5}
.btn{padding:10px 16px;border-radius:var(--radius-sm);font-size:14px;font-weight:600;cursor:pointer;border:none;font-family:inherit;transition:all .15s;display:inline-flex;align-items:center;gap:6px;touch-action:manipulation}
.btn-primary{background:var(--green);color:#fff}
.btn-primary:hover{background:#176040}
.btn-secondary{background:var(--surface);color:var(--text);border:1px solid var(--border)}
.btn-secondary:hover{background:var(--bg)}
.btn-danger{background:var(--red-bg);color:var(--red);border:1px solid var(--red-light)}
.btn-block{width:100%;justify-content:center;padding:13px}
.btn-sm{padding:6px 10px;font-size:12px}
.btn-dis{opacity:.4;pointer-events:none}
input,select,textarea{width:100%;padding:10px 12px;border:1.5px solid var(--border);border-radius:var(--radius-sm);font-size:14px;font-family:inherit;color:var(--text);background:var(--bg);transition:border .15s}
input:focus,select:focus{outline:none;border-color:var(--green);background:#fff}
.form-group{margin-bottom:12px}
.form-group label{display:block;font-size:12px;font-weight:600;color:var(--text2);margin-bottom:5px;text-transform:uppercase;letter-spacing:.03em}
.search-wrap{position:relative;margin-bottom:10px}
.search-wrap input{padding-left:36px}
.search-wrap i{position:absolute;left:11px;top:50%;transform:translateY(-50%);color:var(--text3);font-size:16px}
.list-box{border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;max-height:280px;overflow-y:auto}
.list-row{display:flex;align-items:center;gap:10px;padding:11px 12px;border-bottom:1px solid var(--border-light);cursor:pointer;transition:background .1s;touch-action:manipulation}
.list-row:last-child{border-bottom:none}
.list-row:hover,.list-row:active{background:var(--bg)}
.list-row.sel{background:var(--green-bg)}
.avatar{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;flex-shrink:0}
.avatar.verde{background:var(--green-bg);color:var(--green)}
.avatar.azul{background:var(--blue-bg);color:var(--blue)}
.avatar.cinza{background:var(--bg);color:var(--text2)}
.avatar.teal{background:var(--teal-bg);color:var(--teal)}
.grade-scroll{overflow-x:auto;-webkit-overflow-scrolling:touch;margin:0 -1rem;padding:0 1rem}
.grade{border-collapse:collapse;min-width:420px;width:100%}
.grade th{font-size:10px;font-weight:700;color:var(--text2);padding:7px 4px;text-align:center;border-bottom:2px solid var(--border);background:var(--surface);text-transform:uppercase;letter-spacing:.04em;position:sticky;top:0}
.grade th.lbl{text-align:left;padding-left:6px;min-width:90px}
.grade td{padding:3px 2px;border-bottom:1px solid var(--border-light);vertical-align:middle}
.grade .cell-inp{width:44px;height:44px;padding:0;text-align:center;border:1.5px solid var(--border);border-radius:8px;font-size:15px;font-weight:600;background:var(--surface);color:var(--text);-moz-appearance:textfield;touch-action:manipulation}
.grade .cell-inp::-webkit-inner-spin-button,.grade .cell-inp::-webkit-outer-spin-button{-webkit-appearance:none}
.grade .cell-inp:focus{outline:none;border-color:var(--green);background:var(--green-bg)}
.grade .cell-inp.tem{background:var(--green-bg);border-color:var(--green);color:var(--green)}
.grade .cat-label{font-size:12px;font-weight:700;padding:6px 4px 6px 6px;white-space:nowrap}
.grade .tot-col{font-size:13px;font-weight:700;text-align:right;padding-right:6px}
.grade .tot-col.tem{color:var(--green)}
.grade .total-row td{font-size:11px;font-weight:600;color:var(--text2);text-align:center;padding:7px 3px;background:var(--bg);border-top:2px solid var(--border)}
.grade .total-row .geral{font-size:14px;color:var(--text);font-weight:700;text-align:right;padding-right:6px}
.grade .total-row .geral.ok{color:var(--green)}
.pag-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px;margin-bottom:12px}
.pag-opt{border:1.5px solid var(--border);border-radius:var(--radius-sm);padding:10px 4px;cursor:pointer;text-align:center;touch-action:manipulation;transition:all .15s;background:var(--surface)}
.pag-opt:active{background:var(--bg)}
.pag-opt.sel{border-color:var(--green);background:var(--green-bg)}
.pag-opt i{font-size:20px;display:block;margin-bottom:4px;color:var(--text2)}
.pag-opt.sel i{color:var(--green)}
.pag-opt span{font-size:10px;font-weight:600;color:var(--text2);text-transform:uppercase;letter-spacing:.02em}
.pag-opt.sel span{color:var(--green)}
.foto-slot{border:2px dashed var(--border);border-radius:var(--radius);padding:1.25rem;text-align:center;cursor:pointer;position:relative;margin-bottom:10px;transition:all .15s;background:var(--surface)}
.foto-slot input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%}
.foto-slot i{font-size:28px;color:var(--text3);display:block;margin-bottom:6px}
.foto-slot p{font-size:13px;color:var(--text2)}
.foto-slot.done{border-style:solid;border-color:var(--green);background:var(--green-bg)}
.foto-slot.done i,.foto-slot.done p{color:var(--green);font-weight:600}
.prog-wrap{background:var(--bg);border-radius:20px;height:6px;overflow:hidden;margin:6px 0}
.prog-bar{height:6px;border-radius:20px;background:var(--green);transition:width .3s}
.prog-bar.warn{background:var(--orange)}
.prog-bar.err{background:var(--red)}
.steps-bar{display:flex;gap:4px;margin-bottom:1rem}
.step-dot{flex:1;height:3px;border-radius:2px;background:var(--border)}
.step-dot.done{background:var(--green)}
.step-dot.active{background:var(--green);opacity:.5}
.empty{text-align:center;padding:2.5rem 1rem;color:var(--text2)}
.empty i{font-size:32px;display:block;margin-bottom:10px;opacity:.3}
.empty p{font-size:14px}
.sig-pad{border:1.5px solid var(--border);border-radius:var(--radius-sm);background:var(--surface);cursor:crosshair;display:block;width:100%;touch-action:none}
.cli-list{max-height:260px;overflow-y:auto;border:1px solid var(--border);border-radius:var(--radius)}
.cli-row{display:flex;align-items:center;gap:10px;padding:11px 12px;border-bottom:1px solid var(--border-light);cursor:pointer;touch-action:manipulation}
.cli-row:last-child{border-bottom:none}
.cli-row:hover,.cli-row:active{background:var(--bg)}
.cli-row.sel{background:var(--green-bg)}
.vc-vencido{background:var(--red-bg);color:var(--red)}
.vc-hoje{background:var(--red-bg);color:var(--red)}
.vc-amanha{background:var(--orange-bg);color:var(--orange)}
.vc-breve{background:var(--yellow-bg);color:var(--yellow)}
.vc-ok{background:var(--green-bg);color:var(--green)}
.conf-table{width:100%;border-collapse:collapse}
.conf-table th{font-size:10px;font-weight:700;color:var(--text2);padding:5px 6px;border-bottom:2px solid var(--border);text-align:right;text-transform:uppercase}
.conf-table th:first-child{text-align:left}
.conf-table td{padding:7px 6px;border-bottom:1px solid var(--border-light);font-size:13px;vertical-align:middle}
.conf-table tr.div-row{background:var(--red-bg)}
.conf-table .conf-inp{width:64px;padding:5px 7px;text-align:right;border:1.5px solid var(--border);border-radius:6px;font-size:13px;font-weight:600}
.conf-table .conf-inp:focus{outline:none;border-color:var(--green)}
.conf-table .conf-inp.ok{border-color:var(--green);background:var(--green-bg);color:var(--green)}
.conf-table .conf-inp.diverge{border-color:var(--red);background:var(--red-bg);color:var(--red)}
</style>
</head>
<body>
<div id="tela-login">
  <div class="login-logo"><i class="ti ti-tire"></i></div>
  <div class="login-title">Tyre Eco</div>
  <div class="login-sub">Sistema Logístico — Osasco/SP</div>
  <div class="login-card">
    <div class="form-group">
      <label class="login-label">Usuário</label>
      <input class="login-input" id="inp-usuario" type="text" placeholder="seu.usuario" autocomplete="username" autocorrect="off" autocapitalize="none">
    </div>
    <div class="form-group">
      <label class="login-label">Senha</label>
      <input class="login-input" id="inp-senha" type="password" placeholder="••••••" autocomplete="current-password">
    </div>
    <button class="btn-login" id="btn-entrar">
      <i class="ti ti-login"></i> Entrar
    </button>
    <div class="login-erro" id="login-erro">Usuário ou senha incorretos.</div>
    <div class="login-hint">
      <p>Entrar como</p>
      <div class="hint-grid">
        <div class="hint-item" data-user="gestor" data-pass="tyre2024"><div class="hi-nome">Gestor</div><div class="hi-cargo">Logística</div></div>
        <div class="hint-item" data-user="motorista" data-pass="tyre2024"><div class="hi-nome">Motorista</div><div class="hi-cargo">Herlon Carrera</div></div>
        <div class="hint-item" data-user="conferente" data-pass="tyre2024"><div class="hi-nome">Conferente Op.</div><div class="hi-cargo">Descarga</div></div>
        <div class="hint-item" data-user="fiscal" data-pass="tyre2024"><div class="hi-nome">Conferente Fisc.</div><div class="hi-cargo">NF-e</div></div>
        <div class="hint-item" data-user="triagem" data-pass="tyre2024"><div class="hi-nome">Triagem</div><div class="hi-cargo">Pneus</div></div>
        <div class="hint-item" data-user="vendas" data-pass="tyre2024"><div class="hi-nome">Vendas</div><div class="hi-cargo">Comercial</div></div>
        <div class="hint-item" data-user="financeiro" data-pass="tyre2024"><div class="hi-nome">Financeiro</div><div class="hi-cargo">Relatórios</div></div>
        <div class="hint-item" data-user="nf" data-pass="tyre2024"><div class="hi-nome">Emissão NF</div><div class="hi-cargo">NFS-e</div></div>
      </div>
    </div>
  </div>
</div>
<div id="app">
  <div class="topbar">
    <div class="topbar-left">
      <div class="topbar-logo"><i class="ti ti-tire"></i></div>
      <div class="topbar-info">
        <h1 id="topbar-titulo">Tyre Eco</h1>
        <span id="topbar-sub">Carregando...</span>
      </div>
    </div>
    <div class="topbar-right">
      <button class="btn-logout" id="btn-logout"><i class="ti ti-logout"></i> Sair</button>
    </div>
  </div>
  <div class="content-area" id="content-area"></div>
</div>
<script>
const USUARIOS = {
  'gestor':     {senha:'tyre2024', nome:'Gestor Logística',    perfil:'gestor',     cor:'verde'},
  'motorista':  {senha:'tyre2024', nome:'Herlon Carrera',      perfil:'motorista',  cor:'azul'},
  'conferente': {senha:'tyre2024', nome:'Conferente Operacional', perfil:'conferente', cor:'laranja'},
  'fiscal':     {senha:'tyre2024', nome:'Conferente Fiscal',   perfil:'fiscal',     cor:'roxo'},
  'triagem':    {senha:'tyre2024', nome:'Triagem',              perfil:'triagem',    cor:'teal'},
  'vendas':     {senha:'tyre2024', nome:'Vendas',               perfil:'vendas',     cor:'amarelo'},
  'financeiro': {senha:'tyre2024', nome:'Financeiro (Relatórios)', perfil:'financeiro', cor:'vermelho'},
  'nf':         {senha:'tyre2024', nome:'Emissão de NF',           perfil:'emissao_nf', cor:'roxo'},
};

let usuarioAtual = null;
let telaAtual = 'dashboard';

const CAMINHOES_CONF = [
  {id:'c1',placa:'FPW-9J58',motorista:'Herlon Carrera',rota:'Rota Barretos/Batatais',chegada:'Hoje 14:30',totalPneus:459,status:'aguardando',km:566,
   lojas:[{nome:'DPASCHOAL BARRETOS',marca:'DP',pneus:317},{nome:'CAMPNEUS BARRETOS',marca:'CP',pneus:98},{nome:'DPASCHOAL BATATAIS',marca:'DP',pneus:44}]},
  {id:'c2',placa:'DEU-8A98',motorista:'Renan Marcondes',rota:'Rota Campinas',chegada:'Hoje 15:10',totalPneus:177,status:'aguardando',km:187,
   lojas:[{nome:'DPASCHOAL CAMPINAS',marca:'DP',pneus:57},{nome:'CAMPNEUS NORTE SUL',marca:'CP',pneus:82},{nome:'CAMPNEUS BARAO',marca:'CP',pneus:38}]},
  {id:'c3',placa:'GGA-0262',motorista:'Leonardo Vinicius',rota:'Rota Mogi',chegada:'Hoje 16:00',totalPneus:133,status:'conferido',km:156,
   lojas:[{nome:'DPASCHOAL MOGI GUACU',marca:'DP',pneus:133}]},
];
const CUSTO_POR_KM=2.50; // R$/km — usado para estimar custo logístico real das rotas

const ROTA_MOTORISTA = {
  nome:'Rota Barretos/Batatais', data:'11/06/2026',
  placa:'FPW-9J58', ajudante:'Kaike Santana', kmTotal:412,
  lojas:[
    {id:'l1',nome:'DPASCHOAL BARRETOS DP132',cidade:'Barretos/SP',marca:'DP',dist:210,checkin:null},
    {id:'l2',nome:'CAMPNEUS BARRETOS CP128',cidade:'Barretos/SP',marca:'CP',dist:3,checkin:null},
    {id:'l3',nome:'DPASCHOAL BATATAIS DP101',cidade:'Batatais/SP',marca:'DP',dist:48,checkin:null},
  ],distVolta:154
};

const CATS_TRIAGEM=[{id:'carcaca',nome:'Carcaça',cor:'var(--blue)'},{id:'risco',nome:'Risco',cor:'var(--green)'},{id:'meiavida',nome:'Meia Vida',cor:'var(--orange)'},{id:'cortados',nome:'Cortados',cor:'var(--red)'},{id:'lixo',nome:'Lixo',cor:'var(--text2)'}];
const AROS=['13','14','15','16','17','SUV','Cam.','Cam-hão'];
const AROS_FULL=['13','14','15','16','17','SUV','Camionete','Caminhão'];
const PAGS=[{id:'dinheiro',nome:'Dinheiro',icon:'ti-cash'},{id:'pix',nome:'PIX',icon:'ti-qrcode'},{id:'credito',nome:'Crédito',icon:'ti-credit-card'},{id:'debito',nome:'Débito',icon:'ti-credit-card'},{id:'boleto',nome:'Boleto',icon:'ti-file-invoice'},{id:'fiado',nome:'Fiado',icon:'ti-clock'},{id:'cheque',nome:'Cheque',icon:'ti-writing'}];

let motorState={viagemIniciada:false,checkins:{}};
let confState={camId:null,conferencias:{}};
let triagemState={camId:null,grade:{},salvas:{}};
let triagemGrade={};
let vendasState={tela:'cliente',cliSel:null,busca:'',qtds:{},foto:false,pagamento:null,valor:'',obs:'',historico:[]};
let fiscalState={tab:'entrada'};
let sigCtx=null,drawing=false,lx=0,ly=0;

let financeiroState={periodo:'mes'};
let finPedidoUI={}; // por id do pedido: {pagAberto, nfAberto}

const FIN_DATA={
  dia:{
    label:'Hoje · '+ (new Date()).toLocaleDateString('pt-BR'),
    receita:2198.00,custoLog:210.00,custoItens:640.00,
    chart:[{l:'08h',receita:120,custo:40},{l:'10h',receita:380,custo:70},{l:'12h',receita:290,custo:50},{l:'14h',receita:610,custo:90},{l:'16h',receita:498,custo:60},{l:'18h',receita:300,custo:40}],
    pagamentos:[{id:'pix',valor:890.00},{id:'dinheiro',valor:450.00},{id:'credito',valor:380.00},{id:'boleto',valor:280.00},{id:'fiado',valor:198.00}]
  },
  semana:{
    label:'Semana 30/06 – 06/07',
    receita:14320.00,custoLog:1840.00,custoItens:4120.00,
    chart:[{l:'Seg',receita:1980,custo:280},{l:'Ter',receita:2210,custo:310},{l:'Qua',receita:1890,custo:260},{l:'Qui',receita:2198,custo:210},{l:'Sex',receita:2640,custo:340},{l:'Sáb',receita:2402,custo:300},{l:'Dom',receita:1000,custo:140}],
    pagamentos:[{id:'pix',valor:5320},{id:'dinheiro',valor:2890},{id:'credito',valor:2410},{id:'debito',valor:1200},{id:'boleto',valor:1500},{id:'fiado',valor:1000}]
  },
  mes:{
    label:'Junho/2026',
    receita:38436.00,custoLog:12840.00,custoItens:9870.00,
    chart:[{l:'Sem 1',receita:8420,custo:2680},{l:'Sem 2',receita:9850,custo:3120},{l:'Sem 3',receita:10920,custo:3540},{l:'Sem 4',receita:9246,custo:3500}],
    pagamentos:[{id:'pix',valor:14200},{id:'dinheiro',valor:8340},{id:'credito',valor:6890},{id:'debito',valor:3200},{id:'boleto',valor:3806},{id:'fiado',valor:2000}]
  }
};

const CONTAS_RECEBER=[
  {cliente:'MESQUITAO COMERCIO DE PNEUS',valor:1240.00,vencimento:'28/06/2026',tipo:'Fiado',status:'vencido'},
  {cliente:'JATOBA PNEUS',valor:680.00,vencimento:'02/07/2026',tipo:'Boleto',status:'hoje'},
  {cliente:'TRUCKERS PNEUS',valor:920.00,vencimento:'03/07/2026',tipo:'Boleto',status:'amanha'},
  {cliente:'GI PNEUS E RODAS',valor:410.00,vencimento:'06/07/2026',tipo:'Fiado',status:'breve'},
  {cliente:'PRIME PNEUS COMERCIO E SERVICOS',valor:1580.00,vencimento:'12/07/2026',tipo:'Boleto',status:'ok'},
];

function ini(n){return n.split(' ').filter(Boolean).slice(0,2).map(w=>w[0]).join('').toUpperCase();}
function fmtM(v){return 'R$'+(+v).toLocaleString('pt-BR',{minimumFractionDigits:2,maximumFractionDigits:2});}
function now(){return new Date().toLocaleTimeString('pt-BR',{hour:'2-digit',minute:'2-digit'});}
function today(){return new Date().toLocaleDateString('pt-BR');}
function totalTriagem(){return Object.values(triagemGrade).reduce((s,v)=>s+(parseInt(v)||0),0);}
function totalQtdVendas(){return Object.values(vendasState.qtds).reduce((s,v)=>s+(parseInt(v)||0),0);}

// ── Financeiro: conexão com dados reais de vendas e rotas ─────────────────────
function addDias(base,n){const d=new Date(base);d.setDate(d.getDate()+n);return d;}
function fmtData(d){return d.toLocaleDateString('pt-BR');}
function statusVencimento(d){
  const hoje=new Date();hoje.setHours(0,0,0,0);
  const alvo=new Date(d);alvo.setHours(0,0,0,0);
  const diff=Math.round((alvo-hoje)/86400000);
  if(diff<0)return 'vencido';
  if(diff===0)return 'hoje';
  if(diff===1)return 'amanha';
  if(diff<=7)return 'breve';
  return 'ok';
}
function custoLogisticoRota(cam){return (cam.km||0)*CUSTO_POR_KM;}
function custoLogisticoTotalHoje(){return CAMINHOES_CONF.reduce((s,c)=>s+custoLogisticoRota(c),0);}
function valorTotalPedido(p){return parseFloat(p.valorTotal??p.valor)||0;}
function valorPagoPedido(p){return (p.pagamentos||[]).reduce((s,pg)=>s+(parseFloat(pg.valor)||0),0);}
function saldoPedido(p){return +(valorTotalPedido(p)-valorPagoPedido(p)).toFixed(2);}
function statusPedido(p){const saldo=saldoPedido(p),pago=valorPagoPedido(p);if(saldo<=0.009)return 'pago';if(pago>0)return 'parcial';return 'pendente';}
function receitaVendasHoje(){return vendasState.historico.reduce((s,v)=>s+valorTotalPedido(v),0);}
function pneusVendidosHoje(){return vendasState.historico.reduce((s,v)=>s+(parseInt(v.pneus)||0),0);}
function pagamentosVendasHoje(){
  const map={};
  vendasState.historico.forEach(p=>{
    (p.pagamentos||[]).forEach(pg=>{
      const meta=PAGS.find(x=>x.nome===pg.forma);
      const id=meta?meta.id:'outros';
      map[id]=(map[id]||0)+(parseFloat(pg.valor)||0);
    });
  });
  return Object.entries(map).map(([id,valor])=>({id,valor}));
}
function getFinanceiroDia(){
  const receita=receitaVendasHoje();
  const custoLog=custoLogisticoTotalHoje();
  const custoItens=+(receita*0.28).toFixed(2); // estimativa de custo de itens (28% da receita) — sem dado real disponível
  const pagamentosReais=pagamentosVendasHoje();
  const buckets={};
  vendasState.historico.forEach(v=>{
    const h=(v.hora||'00:00').split(':')[0]+'h';
    buckets[h]=(buckets[h]||0)+valorTotalPedido(v);
  });
  const horas=Object.keys(buckets).sort();
  const custoPorHora=horas.length?custoLog/horas.length:0;
  const chart=horas.length?horas.map(h=>({l:h,receita:buckets[h],custo:custoPorHora})):[{l:'Hoje',receita:0,custo:custoLog}];
  return{
    label:'Hoje · '+today()+' · dados reais',
    real:true,
    receita,custoLog,custoItens,chart,
    pagamentos:pagamentosReais.length?pagamentosReais:[{id:'dinheiro',valor:0}]
  };
}

document.getElementById('btn-entrar').addEventListener('click',fazerLogin);
document.getElementById('inp-senha').addEventListener('keydown',e=>{if(e.key==='Enter')fazerLogin();});
document.querySelectorAll('.hint-item').forEach(el=>{
  el.addEventListener('click',()=>{
    document.getElementById('inp-usuario').value=el.dataset.user;
    document.getElementById('inp-senha').value=el.dataset.pass;
    fazerLogin();
  });
});

function fazerLogin(){
  const u=document.getElementById('inp-usuario').value.trim().toLowerCase();
  const s=document.getElementById('inp-senha').value;
  const user=USUARIOS[u];
  if(!user||user.senha!==s){
    const err=document.getElementById('login-erro');
    err.style.display='block';
    setTimeout(()=>err.style.display='none',3000);
    return;
  }
  usuarioAtual={...user,login:u};
  document.getElementById('tela-login').style.display='none';
  document.getElementById('app').style.display='flex';
  document.getElementById('topbar-titulo').textContent='Tyre Eco';
  document.getElementById('topbar-sub').textContent=usuarioAtual.nome;
  renderDashboard();
}

document.getElementById('btn-logout').addEventListener('click',()=>{
  usuarioAtual=null;
  document.getElementById('tela-login').style.display='flex';
  document.getElementById('app').style.display='none';
  document.getElementById('inp-usuario').value='';
  document.getElementById('inp-senha').value='';
});

function renderDashboard(){
  telaAtual='dashboard';
  document.getElementById('topbar-titulo').textContent='Tyre Eco';
  document.getElementById('topbar-sub').textContent=usuarioAtual.nome;
  const perfil=usuarioAtual.perfil;
  const mods={
    gestor:[
      {id:'rota',icon:'ti-route-2',cor:'verde',nome:'Roterizador',desc:'Criar e gerenciar rotas'},
      {id:'frota',icon:'ti-truck',cor:'azul',nome:'Frota & Equipe',desc:'Veículos e motoristas'},
      {id:'financeiro',icon:'ti-report-money',cor:'laranja',nome:'Financeiro',desc:'Fechamento de rotas'},
      {id:'dashboard_gestor',icon:'ti-layout-dashboard',cor:'roxo',nome:'Dashboard',desc:'Visão geral do dia'},
    ],
    motorista:[
      {id:'motorista_rota',icon:'ti-map-pin',cor:'azul',nome:'Rota do dia',desc:'FPW-9J58 · Barretos'},
      {id:'motorista_checkin',icon:'ti-clipboard-check',cor:'verde',nome:'Check-in',desc:'Registrar coleta'},
      {id:'motorista_hist',icon:'ti-history',cor:'laranja',nome:'Histórico',desc:'Viagens anteriores'},
    ],
    conferente:[
      {id:'conf_lista',icon:'ti-truck',cor:'laranja',nome:'Caminhões',desc:'Selecionar para conferir',badge:CAMINHOES_CONF.filter(c=>c.status==='aguardando').length},
    ],
    fiscal:[
      {id:'fiscal_entrada',icon:'ti-arrow-bar-to-down',cor:'azul',nome:'NF Entrada',desc:'NFs das lojas'},
      {id:'fiscal_saida',icon:'ti-arrow-bar-up',cor:'verde',nome:'NF Saída',desc:'NFs para destino'},
    ],
    triagem:[
      {id:'triagem_lista',icon:'ti-filter',cor:'teal',nome:'Triagem',desc:'Pneus por categoria e aro'},
    ],
    vendas:[
      {id:'vendas_nova',icon:'ti-shopping-cart',cor:'amarelo',nome:'Nova venda',desc:'699 clientes cadastrados'},
      {id:'vendas_hist',icon:'ti-history',cor:'verde',nome:'Histórico',desc:'Vendas do dia'},
    ],
    financeiro:[
      {id:'financeiro_relatorios',icon:'ti-report-analytics',cor:'vermelho',nome:'Relatórios',desc:'Filtrar vendas, pagamentos e NFs'},
    ],
    emissao_nf:[
      {id:'nf_emitir',icon:'ti-file-invoice',cor:'roxo',nome:'Emitir NF',desc:'Gerar ficha da NFS-e'},
    ],
  };

  const items=mods[perfil]||[];
  const hora=new Date().getHours();

  document.getElementById('content-area').innerHTML=`
    <p class="dash-greeting">${hora<12?'Bom dia':hora<18?'Boa tarde':'Boa noite'}, ${usuarioAtual.nome.split(' ')[0]}!</p>
    <p class="dash-date">${today()} · ${now()}</p>
    <div class="modules-grid">
      ${items.map(m=>`<div class="mod-card ${m.cor}" id="mod-${m.id}">
        ${m.badge?`<div class="mod-badge">${m.badge}</div>`:''}
        <div class="mod-icon ${m.cor}"><i class="ti ${m.icon}"></i></div>
        <div class="mod-name">${m.nome}</div>
        <div class="mod-desc">${m.desc}</div>
      </div>`).join('')}
    </div>`;

  items.forEach(m=>{
    document.getElementById(`mod-${m.id}`)?.addEventListener('click',()=>abrirModulo(m.id));
  });
}

function abrirModulo(id){
  telaAtual=id;
  const mapa={
    'rota':renderRotaGestor,'frota':renderFrota,'financeiro':renderFinanceiro,
    'dashboard_gestor':renderDashboardGestor,
    'motorista_rota':renderMotoristaRota,'motorista_checkin':renderMotoristaCheckin,
    'motorista_hist':renderMotoristaHist,
    'conf_lista':renderConferenteLista,
    'fiscal_entrada':()=>renderFiscal('entrada'),'fiscal_saida':()=>renderFiscal('saida'),
    'triagem_lista':renderTriagemLista,
    'vendas_nova':()=>{vendasState.tela='cliente';renderVendas();},'vendas_hist':renderVendasHist,
    'financeiro_relatorios':renderRelatorioFinanceiro,
    'nf_emitir':renderEmitirNF,
  };
  mapa[id]?.();
}

function btnBack(label){
  return `<button class="btn btn-secondary btn-sm" id="btn-back-mod" style="margin-bottom:1rem"><i class="ti ti-arrow-left"></i> ${label||'Voltar'}</button>`;
}
function bindBack(){document.getElementById('btn-back-mod')?.addEventListener('click',renderDashboard);}

function renderRotaGestor(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header">
      <div class="mod-header-icon verde"><i class="ti ti-route-2"></i></div>
      <div><h2>Roteizador</h2><span>Multi-rota inteligente</span></div>
    </div>
    <div class="alert azul"><i class="ti ti-robot"></i><p>O roteizador multi-rota com K-Means geográfico está disponível no módulo completo. Aqui você vê as rotas ativas do dia.</p></div>
    <div class="section-title">Rotas ativas hoje</div>
    ${CAMINHOES_CONF.map(c=>`<div class="card">
      <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px">
        <strong style="font-size:14px">${c.placa}</strong>
        <span class="badge ${c.status==='conferido'?'verde':'laranja'}">${c.status==='conferido'?'Conferido':'Em andamento'}</span>
      </div>
      <div style="font-size:13px;color:var(--text2)">${c.motorista} · ${c.rota}</div>
      <div style="font-size:13px;color:var(--text2);margin-top:4px">${c.lojas.length} lojas · ${c.totalPneus} pneus · ${c.chegada}</div>
    </div>`).join('')}`;
  bindBack();
}

function renderFrota(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon azul"><i class="ti ti-truck"></i></div><div><h2>Frota & Equipe</h2><span>33 veículos · 33 funcionários</span></div></div>
    <div class="stat-grid">
      <div class="stat-box azul"><div class="sv">33</div><div class="sl">Veículos</div></div>
      <div class="stat-box verde"><div class="sv">33</div><div class="sl">Funcionários</div></div>
    </div>
    <div class="section-title">Veículos disponíveis hoje</div>
    ${['FPW-9J58 · VW 24.280','DEU-8A98 · VW 13180','GGA-0262 · Actros 2546','EEK-1A92 · Iveco Daily','TJX-4G17 · Actros 2651'].map((v,i)=>`<div class="card" style="display:flex;align-items:center;gap:10px;padding:.75rem 1rem">
      <div class="avatar azul"><i class="ti ti-truck" style="font-size:14px"></i></div>
      <div style="flex:1"><strong style="font-size:13px;display:block">${v.split('·')[0].trim()}</strong><span style="font-size:11px;color:var(--text2)">${v.split('·')[1].trim()}</span></div>
      <span class="badge verde">Disponível</span>
    </div>`).join('')}`;
  bindBack();
}

function svgChartFinanceiro(data){
  const w=340,h=150,padL=6,padR=6,padB=22,padT=10;
  const max=Math.max(1,...data.map(p=>Math.max(p.receita,p.custo)))*1.15;
  const bw=(w-padL-padR)/data.length;
  const barW=Math.min(20,bw*0.32);
  const usableH=h-padT-padB;
  let bars='';
  data.forEach((p,i)=>{
    const cx=padL+i*bw+bw/2;
    const hR=(p.receita/max)*usableH;
    const hC=(p.custo/max)*usableH;
    const xR=cx-barW-2, xC=cx+2;
    bars+=`<rect x="${xR}" y="${padT+usableH-hR}" width="${barW}" height="${hR}" rx="2" fill="#1D7A4F"/>`;
    bars+=`<rect x="${xC}" y="${padT+usableH-hC}" width="${barW}" height="${hC}" rx="2" fill="#B85C00"/>`;
    bars+=`<text x="${cx}" y="${h-6}" font-size="9" text-anchor="middle" fill="#6B6B65" font-family="-apple-system,sans-serif">${p.l}</text>`;
  });
  return `<svg viewBox="0 0 ${w} ${h}" style="width:100%;height:auto;display:block">
    <line x1="${padL}" y1="${padT+usableH}" x2="${w-padR}" y2="${padT+usableH}" stroke="#E5E4E0" stroke-width="1"/>
    ${bars}
  </svg>`;
}

function linhaPagamentoFin(p,total){
  const meta=PAGS.find(x=>x.id===p.id)||{nome:p.id,icon:'ti-cash'};
  const pct=total?Math.round(p.valor/total*100):0;
  return `<div style="margin-bottom:11px">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px">
      <span style="font-size:13px;color:var(--text);display:flex;align-items:center;gap:6px"><i class="ti ${meta.icon}" style="color:var(--text2);font-size:14px"></i>${meta.nome}</span>
      <span style="font-size:13px"><strong>${fmtM(p.valor)}</strong> <span style="color:var(--text2)">(${pct}%)</span></span>
    </div>
    <div class="prog-wrap" style="margin:0"><div class="prog-bar" style="width:${pct}%"></div></div>
  </div>`;
}

function linhaContaReceber(c){
  const labels={vencido:'Vencido',hoje:'Vence hoje',amanha:'Vence amanhã',breve:'Em breve',ok:'Em dia'};
  return `<div class="row">
    <div class="avatar cinza" style="width:32px;height:32px;font-size:11px">${ini(c.cliente)}</div>
    <div style="flex:1;min-width:0">
      <strong style="font-size:13px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${c.cliente.split(' ').slice(0,3).join(' ')}</strong>
      <span style="font-size:11px;color:var(--text2)">${c.tipo} · vence ${c.vencimento}</span>
    </div>
    <div style="text-align:right;flex-shrink:0">
      <div style="font-size:13px;font-weight:700">${fmtM(c.valor)}</div>
      <span class="badge vc-${c.status}" style="margin-top:3px">${labels[c.status]}</span>
    </div>
  </div>`;
}

function imprimirResumoFinanceiro(){
  const d=financeiroState.periodo==='dia'?getFinanceiroDia():FIN_DATA[financeiroState.periodo];
  const margem=d.receita-d.custoLog-d.custoItens;
  const totalPag=d.pagamentos.reduce((s,p)=>s+p.valor,0);
  const pedidosOrdenados=[...vendasState.historico].reverse();
  const totalOutras=CONTAS_RECEBER.reduce((s,c)=>s+c.valor,0);
  const win=window.open('','_blank');
  if(!win)return;
  win.document.write(`<!DOCTYPE html><html lang="pt-BR"><head><meta charset="UTF-8"><title>Resumo Financeiro — Tyre Eco</title>
    <style>
      body{font-family:-apple-system,Arial,sans-serif;padding:32px;color:#1A1A18;max-width:640px;margin:0 auto}
      h1{font-size:19px;margin-bottom:2px}
      h2{font-size:12px;color:#6B6B65;font-weight:400;margin-bottom:18px}
      h3{font-size:12px;text-transform:uppercase;letter-spacing:.04em;color:#6B6B65;margin:22px 0 8px}
      table{width:100%;border-collapse:collapse;margin-bottom:6px}
      td,th{padding:6px 4px;border-bottom:1px solid #E5E4E0;font-size:13px;text-align:left}
      th{text-align:right;color:#6B6B65;font-size:11px;text-transform:uppercase}
      th:first-child,td:first-child{text-align:left}
      td:not(:first-child),th:not(:first-child){text-align:right}
      .tot td{font-weight:700;border-top:2px solid #1A1A18;border-bottom:none}
      @media print{body{padding:12px}}
    </style></head><body>
    <h1>Resumo Financeiro — Tyre Eco</h1>
    <h2>${d.label} · Gerado em ${today()} ${now()}</h2>
    <h3>Resultado</h3>
    <table>
      <tr><td>Receita</td><td>${fmtM(d.receita)}</td></tr>
      <tr><td>Custo logístico${d.real?' (km real das rotas)':' (estimado)'}</td><td>-${fmtM(d.custoLog)}</td></tr>
      <tr><td>Custo de itens${d.real?' (estimado, 28% da receita)':''}</td><td>-${fmtM(d.custoItens)}</td></tr>
      <tr class="tot"><td>Margem líquida</td><td>${fmtM(margem)}</td></tr>
    </table>
    <h3>Por forma de pagamento (recebido)</h3>
    <table><tr><th style="text-align:left">Forma</th><th>Valor</th><th>%</th></tr>
      ${d.pagamentos.map(p=>{const meta=PAGS.find(x=>x.id===p.id)||{nome:p.id};const pct=totalPag?Math.round(p.valor/totalPag*100):0;return `<tr><td>${meta.nome}</td><td>${fmtM(p.valor)}</td><td>${pct}%</td></tr>`;}).join('')}
    </table>
    ${d.real?`<h3>Pedidos do dia</h3>
    <table><tr><th style="text-align:left">Cliente</th><th>Total</th><th>Pago</th><th>Saldo</th><th style="text-align:left">NFs</th></tr>
      ${pedidosOrdenados.map(p=>`<tr><td>${p.cliente}</td><td>${fmtM(valorTotalPedido(p))}</td><td>${fmtM(valorPagoPedido(p))}</td><td>${fmtM(Math.max(0,saldoPedido(p)))}</td><td style="text-align:left">${(p.notasFiscais||[]).map(nf=>nf.numero).join(', ')||'—'}</td></tr>`).join('')||`<tr><td colspan="5">Nenhum pedido hoje.</td></tr>`}
    </table>`:''}
    <h3>Outras contas a receber (total: ${fmtM(totalOutras)})</h3>
    <table><tr><th style="text-align:left">Cliente</th><th>Tipo</th><th>Vencimento</th><th>Valor</th></tr>
      ${CONTAS_RECEBER.map(c=>`<tr><td>${c.cliente}</td><td>${c.tipo}</td><td>${c.vencimento}</td><td>${fmtM(c.valor)}</td></tr>`).join('')}
    </table>
  </body></html>`);
  win.document.close();
  win.focus();
  setTimeout(()=>win.print(),200);
}

function renderPedidoFinanceiro(p){
  const ui=finPedidoUI[p.id]||{};
  const total=valorTotalPedido(p),pago=valorPagoPedido(p),saldo=saldoPedido(p);
  const status=statusPedido(p);
  const statusInfo={pago:{label:'Pago',cor:'verde'},parcial:{label:'Parcial',cor:'laranja'},pendente:{label:'Pendente',cor:'vermelho'}}[status];
  const nfs=p.notasFiscais||[];
  return `<div class="card">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:8px">
      <div style="min-width:0">
        <strong style="font-size:13px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;max-width:220px">${p.cliente.split(' ').slice(0,4).join(' ')}</strong>
        <span style="font-size:11px;color:var(--text2)">${p.hora} · ${p.pneus} pneus · ${p.pagamento}</span>
      </div>
      <span class="badge ${statusInfo.cor}" style="flex-shrink:0">${statusInfo.label}</span>
    </div>
    <div class="fin-row"><span class="fl">Valor total (a pagar)</span><span class="fv">${fmtM(total)}</span></div>
    <div class="fin-row"><span class="fl">Valor pago</span><span class="fv pos">${fmtM(pago)}</span></div>
    <div class="fin-row"><span class="fl">Saldo em aberto</span><span class="fv ${saldo>0.009?'neg':'pos'}">${fmtM(Math.max(0,saldo))}</span></div>

    <div style="margin-top:8px">
      <div style="font-size:10px;color:var(--text2);text-transform:uppercase;letter-spacing:.03em;margin-bottom:6px">Notas fiscais vinculadas</div>
      <div style="display:flex;flex-wrap:wrap;gap:6px">
        ${nfs.length?nfs.map((nf,i)=>`<span class="badge azul" style="gap:6px">NF ${nf.numero}${nf.valor?` · ${fmtM(nf.valor)}`:''} <i class="ti ti-x" data-rm-nf="${p.id}|${i}" style="cursor:pointer;font-size:11px;margin-left:2px"></i></span>`).join(''):'<span style="font-size:12px;color:var(--text3)">Nenhuma NF vinculada</span>'}
      </div>
    </div>

    <div style="display:flex;gap:8px;margin-top:10px">
      <button class="btn btn-secondary btn-sm" data-nf-toggle="${p.id}"><i class="ti ti-file-invoice"></i> Vincular NF</button>
      ${saldo>0.009?`<button class="btn btn-primary btn-sm" data-pag-toggle="${p.id}"><i class="ti ti-cash"></i> Registrar pagamento</button>`:''}
    </div>

    ${ui.nfAberto?`<div style="margin-top:10px;padding-top:10px;border-top:1px solid var(--border-light);display:flex;gap:6px;align-items:end">
      <div style="flex:1"><label style="font-size:10px;color:var(--text2);display:block;margin-bottom:3px">Número da NF</label><input type="text" id="nf-num-${p.id}" placeholder="Ex: 12345"></div>
      <div style="width:96px"><label style="font-size:10px;color:var(--text2);display:block;margin-bottom:3px">Valor</label><input type="number" step="0.01" min="0" id="nf-val-${p.id}" placeholder="0,00"></div>
      <button class="btn btn-primary btn-sm" data-nf-add="${p.id}"><i class="ti ti-plus"></i></button>
    </div>`:''}

    ${ui.pagAberto?`<div style="margin-top:10px;padding-top:10px;border-top:1px solid var(--border-light)">
      <div style="display:flex;gap:6px;align-items:end;margin-bottom:8px">
        <div style="flex:1"><label style="font-size:10px;color:var(--text2);display:block;margin-bottom:3px">Valor pago agora</label><input type="number" step="0.01" min="0" id="pag-val-${p.id}" placeholder="${saldo.toFixed(2)}"></div>
        <div style="width:110px"><label style="font-size:10px;color:var(--text2);display:block;margin-bottom:3px">Forma</label>
          <select id="pag-forma-${p.id}">${PAGS.map(pg=>`<option value="${pg.nome}">${pg.nome}</option>`).join('')}</select>
        </div>
        <button class="btn btn-primary btn-sm" data-pag-add="${p.id}"><i class="ti ti-check"></i></button>
      </div>
      ${p.pagamentos&&p.pagamentos.length?`<div style="font-size:11px;color:var(--text2)">Já pago: ${p.pagamentos.map(pg=>`${pg.forma} ${fmtM(pg.valor)} (${pg.hora})`).join(' · ')}</div>`:''}
    </div>`:''}
  </div>`;
}

function renderFinanceiro(){
  const d=financeiroState.periodo==='dia'?getFinanceiroDia():FIN_DATA[financeiroState.periodo];
  const margem=d.receita-d.custoLog-d.custoItens;
  const margemPct=d.receita?((margem/d.receita)*100).toFixed(1):'0.0';
  const totalPag=d.pagamentos.reduce((s,p)=>s+p.valor,0);
  const pedidosOrdenados=[...vendasState.historico].reverse();
  const totalPedidosValor=pedidosOrdenados.reduce((s,p)=>s+valorTotalPedido(p),0);
  const totalPedidosPago=pedidosOrdenados.reduce((s,p)=>s+valorPagoPedido(p),0);
  const totalPedidosSaldo=pedidosOrdenados.reduce((s,p)=>s+Math.max(0,saldoPedido(p)),0);
  const totalOutras=CONTAS_RECEBER.reduce((s,c)=>s+c.valor,0);
  const alertaCount=CONTAS_RECEBER.filter(c=>c.status==='vencido'||c.status==='hoje').length;
  const periodos=[{id:'dia',nome:'Dia'},{id:'semana',nome:'Semana'},{id:'mes',nome:'Mês'}];

  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header">
      <div class="mod-header-icon laranja"><i class="ti ti-report-money"></i></div>
      <div style="flex:1"><h2>Financeiro</h2><span>${d.label}</span></div>
      <button class="btn btn-secondary btn-sm" id="btn-imprimir-fin" title="Imprimir resumo"><i class="ti ti-printer"></i></button>
    </div>

    <div style="display:flex;gap:6px;margin-bottom:1rem;background:var(--bg);border-radius:var(--radius-sm);padding:4px">
      ${periodos.map(p=>`<button class="btn ${financeiroState.periodo===p.id?'btn-primary':'btn-secondary'} btn-sm" style="flex:1;justify-content:center" data-periodo="${p.id}">${p.nome}</button>`).join('')}
    </div>

    ${d.real?`<div class="alert verde"><i class="ti ti-plug-connected"></i><p><strong>Dados em tempo real</strong> — receita e forma de pagamento vêm das vendas registradas hoje; custo logístico vem do km cadastrado das rotas de hoje. Custo de itens é estimado (28% da receita) por falta de apontamento real.</p></div>`
    :`<div class="alert laranja"><i class="ti ti-info-circle"></i><p>Semana e mês ainda usam <strong>projeção histórica</strong> (sem dados diários acumulados). A aba "Dia" já reflete vendas e rotas reais do sistema.</p></div>`}

    <div class="stat-grid">
      <div class="stat-box verde"><div class="sv">${fmtM(d.receita)}</div><div class="sl">Receita</div></div>
      <div class="stat-box laranja"><div class="sv">${fmtM(d.custoLog)}</div><div class="sl">Custo logístico</div></div>
      <div class="stat-box vermelho"><div class="sv">${fmtM(d.custoItens)}</div><div class="sl">Custo de itens</div></div>
      <div class="stat-box ${margem>=0?'verde':'vermelho'}"><div class="sv">${fmtM(margem)}</div><div class="sl">Margem (${margemPct}%)</div></div>
    </div>

    ${d.real?`<div class="stat-grid-3">
      <div class="stat-box verde"><div class="sv">${fmtM(totalPedidosPago)}</div><div class="sl">Recebido</div></div>
      <div class="stat-box vermelho"><div class="sv">${fmtM(totalPedidosSaldo)}</div><div class="sl">A receber</div></div>
      <div class="stat-box"><div class="sv">${pedidosOrdenados.length}</div><div class="sl">Pedidos hoje</div></div>
    </div>`:''}

    <div class="section-title">Receita x Custo</div>
    <div class="card">
      <div style="display:flex;gap:14px;margin-bottom:8px;font-size:11px;color:var(--text2)">
        <span style="display:flex;align-items:center;gap:5px"><span style="width:9px;height:9px;border-radius:2px;background:var(--green);display:inline-block"></span>Receita</span>
        <span style="display:flex;align-items:center;gap:5px"><span style="width:9px;height:9px;border-radius:2px;background:var(--orange);display:inline-block"></span>Custo total</span>
      </div>
      ${svgChartFinanceiro(d.chart)}
    </div>

    <div class="section-title">Por forma de pagamento (recebido)</div>
    <div class="card">
      ${totalPag>0?d.pagamentos.map(p=>linhaPagamentoFin(p,totalPag)).join(''):`<p style="font-size:13px;color:var(--text2);text-align:center;padding:.5rem 0">Nenhum pagamento recebido ainda hoje.</p>`}
    </div>

    <div class="section-title" style="display:flex;justify-content:space-between;align-items:center">
      <span>Pedidos & recebimentos</span>
      <span style="font-weight:700;color:var(--text);text-transform:none;letter-spacing:0;font-size:12px">${fmtM(totalPedidosValor)} total</span>
    </div>
    ${pedidosOrdenados.length===0?`<div class="empty"><i class="ti ti-receipt-off"></i><p>Nenhum pedido registrado ainda hoje.</p></div>`:pedidosOrdenados.map(renderPedidoFinanceiro).join('')}

    <div class="section-title" style="display:flex;justify-content:space-between;align-items:center">
      <span>Outras contas a receber</span>
      <span style="font-weight:700;color:var(--text);text-transform:none;letter-spacing:0;font-size:12px">${fmtM(totalOutras)}</span>
    </div>
    ${alertaCount>0?`<div class="alert vermelho"><i class="ti ti-alert-triangle"></i><p><strong>${alertaCount}</strong> conta${alertaCount>1?'s':''} vencida${alertaCount>1?'s':''} ou vencendo hoje.</p></div>`:''}
    <div class="card" style="padding:.25rem 1rem">
      ${CONTAS_RECEBER.map(linhaContaReceber).join('')}
    </div>

    <div class="section-title">Rotas — status financeiro (km real)</div>
    ${CAMINHOES_CONF.map(c=>{
      const custo=custoLogisticoRota(c);
      const statusLabel=c.status==='conferido'?'Conferido':'Em andamento';
      const statusCor=c.status==='conferido'?'verde':'laranja';
      return `<div class="card">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
          <strong style="font-size:14px">${c.rota}</strong>
          <span class="badge ${statusCor}">${statusLabel}</span>
        </div>
        <div class="fin-row"><span class="fl">Distância</span><span class="fv">${c.km} km</span></div>
        <div class="fin-row"><span class="fl">Custo logístico (${fmtM(CUSTO_POR_KM)}/km)</span><span class="fv neg">${fmtM(custo)}</span></div>
        <div class="fin-row"><span class="fl">Pneus coletados</span><span class="fv">${c.totalPneus} un</span></div>
        <div class="fin-row"><span class="fl">Margem</span><span class="fv warn">Calculada após triagem e venda</span></div>
      </div>`;
    }).join('')}

    <button class="btn btn-secondary btn-block" id="btn-imprimir-fin-2" style="margin-top:4px"><i class="ti ti-printer"></i> Imprimir / exportar resumo</button>`;
  bindBack();
  document.querySelectorAll('[data-periodo]').forEach(btn=>{
    btn.addEventListener('click',()=>{financeiroState.periodo=btn.dataset.periodo;renderFinanceiro();});
  });
  document.getElementById('btn-imprimir-fin')?.addEventListener('click',imprimirResumoFinanceiro);
  document.getElementById('btn-imprimir-fin-2')?.addEventListener('click',imprimirResumoFinanceiro);

  document.querySelectorAll('[data-nf-toggle]').forEach(b=>{
    b.addEventListener('click',()=>{const id=b.dataset.nfToggle;finPedidoUI[id]=finPedidoUI[id]||{};finPedidoUI[id].nfAberto=!finPedidoUI[id].nfAberto;renderFinanceiro();});
  });
  document.querySelectorAll('[data-pag-toggle]').forEach(b=>{
    b.addEventListener('click',()=>{const id=b.dataset.pagToggle;finPedidoUI[id]=finPedidoUI[id]||{};finPedidoUI[id].pagAberto=!finPedidoUI[id].pagAberto;renderFinanceiro();});
  });
  document.querySelectorAll('[data-nf-add]').forEach(b=>{
    b.addEventListener('click',()=>{
      const id=b.dataset.nfAdd;
      const numero=document.getElementById(`nf-num-${id}`)?.value.trim();
      const valor=parseFloat(document.getElementById(`nf-val-${id}`)?.value)||0;
      if(!numero)return;
      const pedido=vendasState.historico.find(p=>p.id===id);
      if(pedido){pedido.notasFiscais=pedido.notasFiscais||[];pedido.notasFiscais.push({numero,valor});}
      if(finPedidoUI[id])finPedidoUI[id].nfAberto=false;
      renderFinanceiro();
    });
  });
  document.querySelectorAll('[data-rm-nf]').forEach(b=>{
    b.addEventListener('click',()=>{
      const [id,idx]=b.dataset.rmNf.split('|');
      const pedido=vendasState.historico.find(p=>p.id===id);
      if(pedido&&pedido.notasFiscais)pedido.notasFiscais.splice(parseInt(idx),1);
      renderFinanceiro();
    });
  });
  document.querySelectorAll('[data-pag-add]').forEach(b=>{
    b.addEventListener('click',()=>{
      const id=b.dataset.pagAdd;
      const valor=parseFloat(document.getElementById(`pag-val-${id}`)?.value);
      const forma=document.getElementById(`pag-forma-${id}`)?.value;
      if(!valor||valor<=0)return;
      const pedido=vendasState.historico.find(p=>p.id===id);
      if(pedido){pedido.pagamentos=pedido.pagamentos||[];pedido.pagamentos.push({valor,forma,hora:now()});}
      if(finPedidoUI[id])finPedidoUI[id].pagAberto=false;
      renderFinanceiro();
    });
  });
}

function renderDashboardGestor(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon roxo"><i class="ti ti-layout-dashboard"></i></div><div><h2>Dashboard</h2><span>Visão geral do dia</span></div></div>
    <div class="stat-grid">
      <div class="stat-box verde"><div class="sv">3</div><div class="sl">Rotas ativas</div></div>
      <div class="stat-box azul"><div class="sv">769</div><div class="sl">Pneus em trânsito</div></div>
    </div>
    <div class="stat-grid-3">
      <div class="stat-box"><div class="sv">2</div><div class="sl">Conferidos</div></div>
      <div class="stat-box laranja"><div class="sv">1</div><div class="sl">Triagem pend.</div></div>
      <div class="stat-box verde"><div class="sv">5</div><div class="sl">Vendas hoje</div></div>
    </div>
    <div class="alert verde"><i class="ti ti-circle-check"></i><p>Todas as rotas do dia foram criadas. Próxima coleta urgente: CAMPNEUS BARAO GERALDO (vence amanhã).</p></div>
    <div class="section-title">Status em tempo real</div>
    ${CAMINHOES_CONF.map(c=>`<div class="card" style="display:flex;align-items:center;gap:10px">
      <div class="avatar ${c.status==='conferido'?'verde':'azul'}"><i class="ti ti-truck" style="font-size:14px"></i></div>
      <div style="flex:1;min-width:0"><strong style="font-size:13px;display:block">${c.placa}</strong><span style="font-size:11px;color:var(--text2)">${c.motorista} · ${c.lojas.length} lojas</span></div>
      <span class="badge ${c.status==='conferido'?'verde':'laranja'}">${c.status==='conferido'?'Conferido':'Em rota'}</span>
    </div>`).join('')}`;
  bindBack();
}

function renderMotoristaRota(){
  const done=ROTA_MOTORISTA.lojas.filter(l=>motorState.checkins[l.id]?.done).length;
  const total=ROTA_MOTORISTA.lojas.length;
  const prox=ROTA_MOTORISTA.lojas.find(l=>!motorState.checkins[l.id]?.done);
  const pct=Math.round(done/total*100);
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon azul"><i class="ti ti-map-pin"></i></div><div><h2>${ROTA_MOTORISTA.nome}</h2><span>${ROTA_MOTORISTA.placa} · ${ROTA_MOTORISTA.ajudante}</span></div></div>
    ${motorState.viagemIniciada?`
    <div class="prog-wrap"><div class="prog-bar" style="width:${pct}%"></div></div>
    <p style="font-size:12px;color:var(--text2);margin-bottom:12px">${done} de ${total} coletas · ${pct}% concluído</p>
    ${prox?`<div class="alert azul"><i class="ti ti-map-pin"></i><p><strong>Próxima:</strong> ${prox.nome}</p></div>`:'<div class="alert verde"><i class="ti ti-circle-check"></i><p>Todas as coletas realizadas!</p></div>'}
    `:''}
    <div style="border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:12px">
      <div style="display:flex;gap:10px;padding:10px 12px;border-bottom:1px solid var(--border-light);background:var(--bg)">
        <div style="width:30px;height:30px;border-radius:50%;background:var(--blue);display:flex;align-items:center;justify-content:center;flex-shrink:0;color:#fff"><i class="ti ti-building-factory-2" style="font-size:13px"></i></div>
        <div style="padding-top:4px"><strong style="font-size:13px;display:block">Base — Osasco</strong><span style="font-size:11px;color:var(--text2)">CEP 06233-040 · Partida</span></div>
      </div>
      ${ROTA_MOTORISTA.lojas.map((l,i)=>{
        const ci=motorState.checkins[l.id];
        const done2=ci?.done;
        const isProx=motorState.viagemIniciada&&prox?.id===l.id;
        return `<div style="display:flex;gap:10px;padding:10px 12px;border-bottom:1px solid var(--border-light)">
          <div style="width:30px;height:30px;border-radius:50%;background:${done2?'var(--green)':isProx?'var(--blue-bg)':'var(--bg)'};border:${isProx?'2px solid var(--blue)':done2?'none':'1px solid var(--border)'};display:flex;align-items:center;justify-content:center;flex-shrink:0;color:${done2?'#fff':isProx?'var(--blue)':'var(--text2)'}">
            ${done2?`<i class="ti ti-check" style="font-size:12px"></i>`:i+1}
          </div>
          <div style="flex:1;padding-top:3px;min-width:0">
            <strong style="font-size:13px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${l.nome}</strong>
            <span style="font-size:11px;color:var(--text2)">${l.cidade}</span>
            ${done2?`<div style="font-size:11px;color:var(--green);margin-top:3px">✓ Coletado às ${ci.hora}</div>`:''}
            ${isProx&&motorState.viagemIniciada?`<button class="btn btn-primary btn-sm" id="btn-checkin-${l.id}" style="margin-top:6px"><i class="ti ti-clipboard-check"></i> Fazer check-in</button>`:''}
          </div>
          <span style="font-size:11px;padding:2px 7px;border-radius:20px;background:var(--bg);color:var(--text2);align-self:flex-start;flex-shrink:0;margin-top:4px">${l.dist} km</span>
        </div>`;
      }).join('')}
      <div style="display:flex;gap:10px;padding:10px 12px;background:var(--bg)">
        <div style="width:30px;height:30px;border-radius:50%;background:var(--blue);display:flex;align-items:center;justify-content:center;flex-shrink:0;color:#fff"><i class="ti ti-home" style="font-size:13px"></i></div>
        <div style="flex:1;padding-top:4px"><strong style="font-size:13px;display:block">Retorno — Base Osasco</strong></div>
        <span style="font-size:11px;padding:2px 7px;border-radius:20px;background:var(--orange-bg);color:var(--orange);align-self:flex-start;flex-shrink:0;margin-top:4px">${ROTA_MOTORISTA.distVolta} km</span>
      </div>
    </div>
    ${!motorState.viagemIniciada?`<button class="btn btn-primary btn-block" id="btn-iniciar-viagem"><i class="ti ti-player-play"></i> Iniciar viagem</button>`:''}
    ${motorState.viagemIniciada&&done===total?`<button class="btn btn-primary btn-block" id="btn-finalizar-viagem"><i class="ti ti-flag-check"></i> Finalizar viagem</button>`:''}`;
  bindBack();
  document.getElementById('btn-iniciar-viagem')?.addEventListener('click',()=>{motorState.viagemIniciada=true;renderMotoristaRota();});
  document.getElementById('btn-finalizar-viagem')?.addEventListener('click',()=>{motorState.viagemIniciada=false;motorState.checkins={};renderMotoristaRota();});
  ROTA_MOTORISTA.lojas.forEach(l=>{
    document.getElementById(`btn-checkin-${l.id}`)?.addEventListener('click',()=>renderCheckinModal(l.id));
  });
}

let ciLoja=null,ciEtapa=1,ciFotos={},ciItens={},ciNF=null,ciResp='',ciSigned=false;
const ITENS_CI=[{id:'pneus_passeio',nome:'Pneus passeio',un:'un'},{id:'pneus_estourado',nome:'Pneus estourado',un:'un'},{id:'amortecedor',nome:'Amortecedor',un:'un'},{id:'bandeja',nome:'Bandeja',un:'un'},{id:'disco',nome:'Disco',un:'un'},{id:'filtro_oleo',nome:'Filtro óleo',un:'kg'},{id:'frascos_oleo',nome:'Frascos óleo',un:'un'},{id:'mola',nome:'Mola',un:'un'},{id:'papelao',nome:'Papelão',un:'kg'},{id:'pastilha',nome:'Pastilha',un:'un'},{id:'plasticos',nome:'Plásticos',un:'kg'},{id:'roda',nome:'Roda',un:'un'},{id:'sucata',nome:'Sucata ferrosa',un:'kg'}];

function renderCheckinModal(lojaId){
  ciLoja=ROTA_MOTORISTA.lojas.find(l=>l.id===lojaId);
  ciEtapa=1;ciFotos={};ciItens={};ciNF=null;ciResp='';ciSigned=false;
  renderCI();
}

function renderCI(){
  const etapas=['Chegada','Fotos','Itens','Finalização'];
  const dots=etapas.map((_,i)=>`<div class="step-dot ${i+1<ciEtapa?'done':i+1===ciEtapa?'active':''}"></div>`).join('');
  let body='';
  if(ciEtapa===1) body=`
    <div class="card" style="margin-bottom:12px">
      <div class="fin-row"><span class="fl">Data</span><span class="fv">${today()}</span></div>
      <div class="fin-row"><span class="fl">Horário chegada</span><span class="fv">${now()}</span></div>
      <div class="fin-row"><span class="fl">Loja</span><span class="fv">${ciLoja.nome}</span></div>
    </div>
    <button class="btn btn-primary btn-block" id="ci-next">Próximo: fotos <i class="ti ti-arrow-right"></i></button>
    <button class="btn btn-danger btn-block" id="ci-ocorr" style="margin-top:6px"><i class="ti ti-alert-triangle"></i> Registrar ocorrência</button>`;
  else if(ciEtapa===2){
    const fotos=[{id:'pneus',l:'Foto dos pneus'},{id:'ferrosa1',l:'Tambor ferrosa 1'},{id:'ferrosa2',l:'Tambor ferrosa 2'},{id:'embals',l:'Embalagens'},{id:'filtro',l:'Tambor filtro óleo'}];
    body=`<div>${fotos.map(f=>`<div class="foto-slot${ciFotos[f.id]?' done':''}" data-foto="${f.id}"><input type="file" accept="image/*"><i class="ti ti-${ciFotos[f.id]?'circle-check':'camera'}"></i><p>${ciFotos[f.id]?'✓ '+f.l:f.l}</p></div>`).join('')}</div>
    <div style="display:flex;gap:8px;margin-top:8px"><button class="btn btn-secondary btn-sm" id="ci-prev"><i class="ti ti-arrow-left"></i></button><button class="btn btn-primary" style="flex:1;justify-content:center" id="ci-next">Itens <i class="ti ti-arrow-right"></i></button></div>`;
  }
  else if(ciEtapa===3) body=`
    <div style="max-height:360px;overflow-y:auto">
    ${ITENS_CI.map(it=>`<div style="display:flex;align-items:center;gap:8px;padding:7px 0;border-bottom:1px solid var(--border-light)">
      <span style="flex:1;font-size:13px">${it.nome}</span>
      <input class="ci-item-inp" type="number" inputmode="numeric" min="0" style="width:64px;padding:6px 8px;text-align:right;border:1.5px solid var(--border);border-radius:6px;font-size:14px;font-weight:500" placeholder="0" value="${ciItens[it.id]||''}" data-item="${it.id}">
      <span style="font-size:11px;color:var(--text2);width:20px">${it.un}</span>
    </div>`).join('')}
    </div>
    <div style="display:flex;gap:8px;margin-top:10px"><button class="btn btn-secondary btn-sm" id="ci-prev"><i class="ti ti-arrow-left"></i></button><button class="btn btn-primary" style="flex:1;justify-content:center" id="ci-next">Finalização <i class="ti ti-arrow-right"></i></button></div>`;
  else body=`
    <div style="margin-bottom:12px">
      <label style="font-size:12px;color:var(--text2);display:block;margin-bottom:5px">Nota fiscal</label>
      <div style="display:flex;gap:8px">
        <div class="pag-opt${ciNF===true?' sel':''}" style="flex:1" id="nf-sim"><i class="ti ti-file-invoice"></i><span>Tem NF</span></div>
        <div class="pag-opt${ciNF===false?' sel':''}" style="flex:1" id="nf-nao"><i class="ti ti-file-off"></i><span>Sem NF</span></div>
      </div>
    </div>
    <label style="font-size:12px;color:var(--text2);display:block;margin-bottom:5px">Responsável</label>
    <input id="ci-resp" type="text" placeholder="Nome do responsável" value="${ciResp}" style="margin-bottom:12px">
    <label style="font-size:12px;color:var(--text2);display:block;margin-bottom:5px">Assinatura digital</label>
    <canvas id="sig-canvas" class="sig-pad" width="360" height="100"></canvas>
    <div style="display:flex;gap:8px;margin-top:5px;margin-bottom:12px">
      <button class="btn btn-secondary btn-sm" id="sig-limpar"><i class="ti ti-eraser"></i> Limpar</button>
      ${ciSigned?'<span style="font-size:12px;color:var(--green);font-weight:500;padding:6px 0">✓ Assinatura capturada</span>':''}
    </div>
    <div style="display:flex;gap:8px"><button class="btn btn-secondary btn-sm" id="ci-prev"><i class="ti ti-arrow-left"></i></button><button class="btn btn-primary" style="flex:1;justify-content:center" id="ci-confirmar"><i class="ti ti-flag-check"></i> Confirmar saída</button></div>`;

  document.getElementById('content-area').innerHTML=`
    ${btnBack('Cancelar check-in')}
    <div class="mod-header"><div class="mod-header-icon azul"><i class="ti ti-clipboard-check"></i></div><div><h2>Check-in</h2><span>${ciLoja.nome}</span></div></div>
    <div class="steps-bar">${dots}</div>
    <p style="font-size:12px;color:var(--text2);margin-bottom:14px">Etapa ${ciEtapa} de 4 — ${etapas[ciEtapa-1]}</p>
    ${body}`;
  bindBack();
  document.getElementById('ci-next')?.addEventListener('click',()=>{ciEtapa++;renderCI();});
  document.getElementById('ci-prev')?.addEventListener('click',()=>{ciEtapa--;renderCI();});
  document.getElementById('ci-ocorr')?.addEventListener('click',()=>alert('Ocorrência registrada.'));
  document.querySelectorAll('.ci-item-inp').forEach(inp=>{inp.addEventListener('input',()=>{ciItens[inp.dataset.item]=inp.value;});});
  document.querySelectorAll('[data-foto]').forEach(el=>{el.addEventListener('click',()=>{ciFotos[el.dataset.foto]=true;renderCI();});});
  document.getElementById('nf-sim')?.addEventListener('click',()=>{ciNF=true;renderCI();});
  document.getElementById('nf-nao')?.addEventListener('click',()=>{ciNF=false;renderCI();});
  document.getElementById('ci-resp')?.addEventListener('input',e=>{ciResp=e.target.value;});
  document.getElementById('ci-confirmar')?.addEventListener('click',()=>{
    const resp=document.getElementById('ci-resp')?.value||ciResp;
    motorState.checkins[ciLoja.id]={done:true,hora:now(),itens:{...ciItens},nf:ciNF,responsavel:resp};
    renderMotoristaRota();
  });
  document.getElementById('sig-limpar')?.addEventListener('click',()=>{sigCtx?.clearRect(0,0,360,100);ciSigned=false;});
  attachSig();
}

function attachSig(){
  const c=document.getElementById('sig-canvas');if(!c||sigCtx)return;
  sigCtx=c.getContext('2d');sigCtx.strokeStyle='#1A5FA8';sigCtx.lineWidth=2.5;sigCtx.lineCap='round';
  const pos=(e)=>{const r=c.getBoundingClientRect();const s=e.touches?e.touches[0]:e;return{x:(s.clientX-r.left)*(c.width/r.width),y:(s.clientY-r.top)*(c.height/r.height)};};
  c.addEventListener('mousedown',e=>{drawing=true;const p=pos(e);lx=p.x;ly=p.y;});
  c.addEventListener('mousemove',e=>{if(!drawing)return;const p=pos(e);sigCtx.beginPath();sigCtx.moveTo(lx,ly);sigCtx.lineTo(p.x,p.y);sigCtx.stroke();lx=p.x;ly=p.y;ciSigned=true;});
  c.addEventListener('mouseup',()=>drawing=false);
  c.addEventListener('touchstart',e=>{e.preventDefault();drawing=true;const p=pos(e);lx=p.x;ly=p.y;},{passive:false});
  c.addEventListener('touchmove',e=>{e.preventDefault();if(!drawing)return;const p=pos(e);sigCtx.beginPath();sigCtx.moveTo(lx,ly);sigCtx.lineTo(p.x,p.y);sigCtx.stroke();lx=p.x;ly=p.y;ciSigned=true;},{passive:false});
  c.addEventListener('touchend',()=>drawing=false);
}

function renderMotoristaCheckin(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon verde"><i class="ti ti-clipboard-check"></i></div><div><h2>Check-in</h2><span>Lojas da rota de hoje</span></div></div>
    ${!motorState.viagemIniciada?`<div class="alert laranja"><i class="ti ti-lock"></i><p>Inicie a viagem na aba "Rota do dia" para liberar o check-in.</p></div>`:''}
    ${ROTA_MOTORISTA.lojas.map((l,i)=>{
      const ci=motorState.checkins[l.id];
      const done=ci?.done;
      const isProx=motorState.viagemIniciada&&!done&&ROTA_MOTORISTA.lojas.slice(0,i).every(ll=>motorState.checkins[ll.id]?.done);
      return `<div style="display:flex;align-items:center;gap:10px;padding:12px;border:1.5px solid ${done?'var(--green)':isProx?'var(--blue)':'var(--border)'};border-radius:var(--radius);margin-bottom:8px;background:${done?'var(--green-bg)':isProx?'var(--blue-bg)':'var(--surface)'};cursor:${isProx||done?'pointer':'not-allowed'}" ${isProx||done?`id="ci-open-${l.id}"`:''}">
        <div style="width:36px;height:36px;border-radius:50%;background:${done?'var(--green)':isProx?'var(--blue)':'var(--bg)'};display:flex;align-items:center;justify-content:center;font-size:${done?'16':'14'}px;color:${done?'#fff':isProx?'var(--blue)':'var(--text2)'}">
          ${done?'<i class="ti ti-check"></i>':isProx?'<i class="ti ti-map-pin"></i>':'<i class="ti ti-lock"></i>'}
        </div>
        <div style="flex:1;min-width:0">
          <strong style="font-size:13px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${l.nome}</strong>
          <span style="font-size:11px;color:var(--text2)">${l.cidade}</span>
          ${done?`<div style="font-size:11px;color:var(--green);margin-top:2px">✓ Registrado às ${ci.hora}</div>`:''}
        </div>
        <i class="ti ti-chevron-right" style="color:${done?'var(--green)':isProx?'var(--blue)':'var(--border)'};font-size:16px;flex-shrink:0"></i>
      </div>`;
    }).join('')}`;
  bindBack();
  ROTA_MOTORISTA.lojas.forEach(l=>{
    document.getElementById(`ci-open-${l.id}`)?.addEventListener('click',()=>renderCheckinModal(l.id));
  });
}

function renderMotoristaHist(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon laranja"><i class="ti ti-history"></i></div><div><h2>Histórico</h2><span>Viagens anteriores</span></div></div>
    <div class="stat-grid">
      <div class="stat-box azul"><div class="sv">48</div><div class="sl">Viagens (mês)</div></div>
      <div class="stat-box verde"><div class="sv">2.847</div><div class="sl">Pneus coletados</div></div>
    </div>
    ${[{nome:'Rota Campinas',data:'09/06',pneus:177,km:187},{nome:'Rota Osasco/Carap.',data:'06/06',pneus:150,km:89},{nome:'Rota Mogi/Limeira',data:'03/06',pneus:140,km:156}].map(h=>`<div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px">
        <strong style="font-size:14px">${h.nome}</strong>
        <span class="badge verde">Concluída</span>
      </div>
      <div style="font-size:13px;color:var(--text2)">${h.data} · ${h.pneus} pneus · ~${h.km} km</div>
    </div>`).join('')}`;
  bindBack();
}

function renderConferenteLista(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon laranja"><i class="ti ti-truck"></i></div><div><h2>Conferência de descarga</h2><span>Selecione o caminhão</span></div></div>
    <div class="section-title">Aguardando conferência (${CAMINHOES_CONF.filter(c=>c.status==='aguardando').length})</div>
    ${CAMINHOES_CONF.filter(c=>c.status==='aguardando').map(c=>`<div class="card" style="display:flex;align-items:center;gap:12px;cursor:pointer" id="cam-conf-${c.id}">
      <div class="mod-icon laranja"><i class="ti ti-truck"></i></div>
      <div style="flex:1">
        <strong style="font-size:15px;letter-spacing:.04em;display:block">${c.placa}</strong>
        <span style="font-size:12px;color:var(--text2)">${c.motorista} · ${c.rota}</span>
        <div style="font-size:12px;color:var(--text2);margin-top:3px">${c.lojas.length} lojas · ${c.totalPneus} pneus · ${c.chegada}</div>
      </div>
      <span class="badge laranja">Aguardando</span>
    </div>`).join('')}
    ${CAMINHOES_CONF.filter(c=>c.status==='conferido').length>0?`
    <div class="section-title">Já conferidos</div>
    ${CAMINHOES_CONF.filter(c=>c.status==='conferido').map(c=>`<div class="card" style="display:flex;align-items:center;gap:12px;opacity:.65">
      <div class="mod-icon verde"><i class="ti ti-circle-check"></i></div>
      <div style="flex:1"><strong style="font-size:15px;display:block">${c.placa}</strong><span style="font-size:12px;color:var(--text2)">${c.motorista}</span></div>
      <span class="badge verde">Conferido</span>
    </div>`).join('')}`:''}`;
  bindBack();
  CAMINHOES_CONF.filter(c=>c.status==='aguardando').forEach(c=>{
    document.getElementById(`cam-conf-${c.id}`)?.addEventListener('click',()=>renderConferenciaNotas(c.id));
  });
}

function renderConferenciaNotas(camId){
  const cam=CAMINHOES_CONF.find(c=>c.id===camId);
  if(!confState.conferencias[camId]){
    confState.conferencias[camId]={};
    cam.lojas.forEach(l=>{confState.conferencias[camId][l.nome]={fechada:false,itens:{},aberta:false};});
  }
  const conf=confState.conferencias[camId];
  const fechadas=Object.values(conf).filter(c=>c.fechada).length;
  const todas=fechadas===cam.lojas.length;
  document.getElementById('content-area').innerHTML=`
    <button class="btn btn-secondary btn-sm" id="btn-back-conf" style="margin-bottom:1rem"><i class="ti ti-arrow-left"></i> Caminhões</button>
    <div class="mod-header"><div class="mod-header-icon laranja"><i class="ti ti-clipboard-list"></i></div><div><h2>${cam.placa}</h2><span>${cam.motorista} · ${cam.rota}</span></div></div>
    <div class="prog-wrap"><div class="prog-bar" style="width:${Math.round(fechadas/cam.lojas.length*100)}%"></div></div>
    <p style="font-size:12px;color:var(--text2);margin-bottom:12px">${fechadas} de ${cam.lojas.length} notas conferidas</p>
    ${todas?`<div class="alert verde"><i class="ti ti-circle-check"></i><p>Todas as notas conferidas! Caminhão liberado para triagem.</p></div>`:''}
    ${cam.lojas.map(l=>{
      const lConf=conf[l.nome];
      const pneusMot=l.pneus;
      const isOpen=lConf.aberta;
      return `<div style="border:1.5px solid ${lConf.fechada?'var(--green)':'var(--border)'};border-radius:var(--radius);overflow:hidden;margin-bottom:8px">
        <div style="padding:12px 14px;display:flex;align-items:center;gap:10px;cursor:pointer;background:${lConf.fechada?'var(--green-bg)':'var(--bg)'}" id="nota-toggle-${l.nome.replace(/\s/g,'_')}">
          <div style="flex:1;min-width:0">
            <strong style="font-size:13px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${l.nome}</strong>
            <span style="font-size:11px;color:var(--text2)">${l.marca} · Motorista lançou: ${pneusMot} pneus</span>
            ${lConf.fechada?`<div style="font-size:11px;color:var(--green);margin-top:2px">✓ Conferido</div>`:''}
          </div>
          ${!lConf.fechada?`<button class="btn btn-primary btn-sm" id="btn-conferir-${l.nome.replace(/\s/g,'_')}">Conferir</button>`:''}
          <i class="ti ti-chevron-${isOpen?'up':'down'}" style="font-size:14px;color:var(--text2)"></i>
        </div>
        ${isOpen?`<div style="padding:14px;border-top:1px solid var(--border-light)">
          <table class="conf-table" style="width:100%">
            <thead><tr><th style="text-align:left">Item</th><th>Motorista</th><th>Conferido</th></tr></thead>
            <tbody>
              ${ITENS_CI.slice(0,5).map(it=>{
                const qMot=Math.floor(Math.random()*20)+1;
                const qConf=lConf.itens[it.id]||'';
                const diverge=qConf!==''&&parseInt(qConf)!==qMot;
                const ok=qConf!==''&&!diverge;
                return `<tr class="${diverge?'div-row':''}">
                  <td>${it.nome}</td>
                  <td style="text-align:right;font-weight:600">${qMot}</td>
                  <td style="text-align:right"><input class="conf-inp${diverge?' diverge':ok?' ok':''}" type="number" min="0" placeholder="${qMot}" value="${qConf}" data-loja="${l.nome}" data-item="${it.id}" style="width:60px"></td>
                </tr>`;
              }).join('')}
            </tbody>
          </table>
          <div style="display:flex;gap:8px;margin-top:12px">
            <button class="btn btn-secondary btn-sm" id="btn-igual-${l.nome.replace(/\s/g,'_')}">Tudo igual</button>
            <button class="btn btn-primary" style="flex:1;justify-content:center" id="btn-salvar-${l.nome.replace(/\s/g,'_')}"><i class="ti ti-device-floppy"></i> Salvar nota</button>
          </div>
        </div>`:``}
      </div>`;
    }).join('')}
    ${todas?`<button class="btn btn-primary btn-block" id="btn-finalizar-conf"><i class="ti ti-flag-check"></i> Finalizar conferência</button>`:''}`;

  document.getElementById('btn-back-conf')?.addEventListener('click',renderConferenteLista);
  cam.lojas.forEach(l=>{
    const key=l.nome.replace(/\s/g,'_');
    document.getElementById(`nota-toggle-${key}`)?.addEventListener('click',()=>{conf[l.nome].aberta=!conf[l.nome].aberta;renderConferenciaNotas(camId);});
    document.getElementById(`btn-conferir-${key}`)?.addEventListener('click',e=>{e.stopPropagation();conf[l.nome].aberta=true;renderConferenciaNotas(camId);});
    document.getElementById(`btn-igual-${key}`)?.addEventListener('click',()=>{conf[l.nome].fechada=true;conf[l.nome].aberta=false;renderConferenciaNotas(camId);});
    document.getElementById(`btn-salvar-${key}`)?.addEventListener('click',()=>{conf[l.nome].fechada=true;conf[l.nome].aberta=false;renderConferenciaNotas(camId);});
  });
  document.querySelectorAll('.conf-inp').forEach(inp=>{
    inp.addEventListener('input',()=>{
      const loja=inp.dataset.loja;
      if(!confState.conferencias[camId][loja]) confState.conferencias[camId][loja]={fechada:false,itens:{},aberta:true};
      confState.conferencias[camId][loja].itens[inp.dataset.item]=inp.value;
      const qMot=parseInt(inp.placeholder)||0;
      const qConf=parseInt(inp.value)||0;
      inp.className='conf-inp'+(qConf&&qConf!==qMot?' diverge':qConf?'ok':'');
    });
  });
  document.getElementById('btn-finalizar-conf')?.addEventListener('click',()=>{
    const idx=CAMINHOES_CONF.findIndex(c=>c.id===camId);
    if(idx>=0) CAMINHOES_CONF[idx].status='conferido';
    alert('✅ Conferência finalizada! Caminhão liberado para triagem.');
    renderConferenteLista();
  });
}

function renderFiscal(tipo){
  fiscalState.tab=tipo;
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon roxo"><i class="ti ti-robot"></i></div><div><h2>Conferente Fiscal IA</h2><span>Análise de NF-e</span></div></div>
    <div style="display:flex;gap:6px;margin-bottom:1rem;background:var(--bg);border-radius:var(--radius-sm);padding:4px">
      <button class="btn ${tipo==='entrada'?'btn-primary':'btn-secondary'} btn-sm" style="flex:1;justify-content:center" id="tab-entrada"><i class="ti ti-arrow-bar-to-down"></i> NF Entrada</button>
      <button class="btn ${tipo==='saida'?'btn-primary':'btn-secondary'} btn-sm" style="flex:1;justify-content:center" id="tab-saida"><i class="ti ti-arrow-bar-up"></i> NF Saída</button>
    </div>
    ${tipo==='entrada'?`
    <div class="alert azul"><i class="ti ti-info-circle"></i><p>NFs recebidas das lojas (Campneus/DPaschoal). A IA identifica a loja pelo CNPJ e cruza com o check-in.</p></div>
    <div style="border:2px dashed var(--border);border-radius:var(--radius);padding:2rem;text-align:center;margin-bottom:12px;cursor:pointer;position:relative">
      <input type="file" accept=".xml" multiple style="position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%">
      <i class="ti ti-file-code" style="font-size:32px;color:var(--text3);display:block;margin-bottom:8px"></i>
      <p style="font-size:14px;font-weight:600;color:var(--text2)">Arraste os XMLs aqui</p>
      <p style="font-size:12px;color:var(--text3)">Aceita múltiplos arquivos · NF-e 4.00</p>
    </div>
    <button class="btn btn-primary btn-block" id="btn-demo-fiscal"><i class="ti ti-sparkles"></i> Demonstrar com NFs reais</button>
    `:`
    <div class="alert verde"><i class="ti ti-info-circle"></i><p>NFs emitidas pela Tyre Eco para o destino final. A IA converte pneus em toneladas e confere o peso declarado.</p></div>
    <div class="card">
      <div class="fin-row"><span class="fl">NF nº 11381</span><span class="fv">TYRE ECO → SAG AMBIENTAL</span></div>
      <div class="fin-row"><span class="fl">Item</span><span class="fv">Sucata de pneus inservível</span></div>
      <div class="fin-row"><span class="fl">Quantidade NF</span><span class="fv" style="color:var(--purple)">5,000 TON</span></div>
      <div class="fin-row"><span class="fl">Pneus coletados (check-in)</span><span class="fv">459 un</span></div>
      <div class="fin-row"><span class="fl">Peso estimado (6,5kg×passeio)</span><span class="fv">≈ 2,109 TON</span></div>
      <div class="fin-row"><span class="fl">Diferença</span><span class="fv neg">+2,891 TON</span></div>
    </div>
    <div class="alert laranja"><i class="ti ti-alert-triangle"></i><p>Divergência detectada. Ajuste os pesos médios ou verifique se a NF inclui estoque anterior.</p></div>
    <div class="card">
      <p style="font-size:12px;color:var(--text2);margin-bottom:8px">Ajustar peso médio por pneu:</p>
      <div style="display:flex;gap:10px">
        <div style="flex:1"><label style="font-size:11px;color:var(--text2);display:block;margin-bottom:4px">Passeio (kg)</label><input type="number" value="6.5" style="text-align:center;font-size:15px;font-weight:600;color:var(--purple)"></div>
        <div style="flex:1"><label style="font-size:11px;color:var(--text2);display:block;margin-bottom:4px">Estourado (kg)</label><input type="number" value="3.0" style="text-align:center;font-size:15px;font-weight:600;color:var(--purple)"></div>
      </div>
    </div>`}`;
  bindBack();
  document.getElementById('tab-entrada')?.addEventListener('click',()=>renderFiscal('entrada'));
  document.getElementById('tab-saida')?.addEventListener('click',()=>renderFiscal('saida'));
  document.getElementById('btn-demo-fiscal')?.addEventListener('click',()=>{
    document.getElementById('content-area').innerHTML+=`
    <div class="alert verde" style="margin-top:10px"><i class="ti ti-circle-check"></i><p>6 NFs processadas · R$2.198,02 · 1 divergência encontrada (NF 719286: papelão 25kg vs 0kg lançado).</p></div>`;
  });
}

function renderTriagemLista(){
  const conf=CAMINHOES_CONF.filter(c=>c.status==='conferido');
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon teal"><i class="ti ti-filter"></i></div><div><h2>Triagem de pneus</h2><span>Por categoria e aro</span></div></div>
    ${conf.length===0?`<div class="empty"><i class="ti ti-truck-off"></i><p>Nenhum caminhão conferido disponível.</p></div>`:''}
    ${conf.map(c=>`<div class="card" style="display:flex;align-items:center;gap:12px;cursor:pointer" id="triagem-cam-${c.id}">
      <div class="mod-icon teal"><i class="ti ti-filter"></i></div>
      <div style="flex:1">
        <strong style="font-size:15px;letter-spacing:.04em;display:block">${c.placa}</strong>
        <span style="font-size:12px;color:var(--text2)">${c.motorista} · ${c.rota}</span>
        <div style="font-size:13px;font-weight:600;color:var(--teal);margin-top:4px">${c.totalPneus} pneus para triar</div>
      </div>
      <i class="ti ti-chevron-right" style="color:var(--text3);font-size:16px"></i>
    </div>`).join('')}`;
  bindBack();
  conf.forEach(c=>{
    document.getElementById(`triagem-cam-${c.id}`)?.addEventListener('click',()=>renderTriagemGrade(c.id));
  });
}

function renderTriagemGrade(camId){
  const cam=CAMINHOES_CONF.find(c=>c.id===camId);
  if(!triagemGrade[camId]) triagemGrade[camId]={};
  CATS_TRIAGEM.forEach(cat=>{
    if(!triagemGrade[camId][cat.id]) triagemGrade[camId][cat.id]={};
    AROS_FULL.forEach(a=>{if(!triagemGrade[camId][cat.id][a]) triagemGrade[camId][cat.id][a]=0;});
  });
  const tot=CATS_TRIAGEM.reduce((s,c)=>s+AROS_FULL.reduce((ss,a)=>ss+(parseInt(triagemGrade[camId][c.id][a])||0),0),0);
  const valido=tot===cam.totalPneus;
  const pct=Math.min(100,Math.round(tot/cam.totalPneus*100));

  document.getElementById('content-area').innerHTML=`
    <button class="btn btn-secondary btn-sm" id="btn-back-triagem" style="margin-bottom:1rem"><i class="ti ti-arrow-left"></i> Caminhões</button>
    <div class="mod-header"><div class="mod-header-icon teal"><i class="ti ti-filter"></i></div><div><h2>${cam.placa}</h2><span>${cam.totalPneus} pneus para triar</span></div></div>
    <div class="prog-wrap"><div class="prog-bar${tot>cam.totalPneus?' err':valido?'':' warn'}" style="width:${pct}%"></div></div>
    <div style="display:flex;justify-content:space-between;font-size:12px;color:var(--text2);margin-bottom:12px">
      <span>Lançado: <strong style="color:var(--text)">${tot}</strong> de <strong>${cam.totalPneus}</strong></span>
      <span style="font-weight:600;color:${tot>cam.totalPneus?'var(--red)':valido?'var(--green)':'var(--orange)'}">${tot>cam.totalPneus?`${tot-cam.totalPneus} a mais — corrija`:valido?'✓ Completo':`Faltam ${cam.totalPneus-tot}`}</span>
    </div>
    ${valido?`<div class="alert verde"><i class="ti ti-circle-check"></i><p>Total confere! Pronto para confirmar.</p></div>`:''}
    <div class="grade-scroll">
      <table class="grade" id="triagem-grade">
        <thead><tr>
          <th class="lbl">Categoria</th>
          ${AROS.map(a=>`<th>${a}</th>`).join('')}
          <th style="text-align:right;padding-right:6px">Total</th>
        </tr></thead>
        <tbody>
          ${CATS_TRIAGEM.map(cat=>{
            const catTot=AROS_FULL.reduce((s,a)=>s+(parseInt(triagemGrade[camId][cat.id][a])||0),0);
            return `<tr>
              <td class="cat-label" style="color:${cat.cor}">${cat.nome}</td>
              ${AROS_FULL.map(a=>{
                const v=parseInt(triagemGrade[camId][cat.id][a])||0;
                return `<td style="text-align:center;padding:2px"><input class="cell-inp${v>0?' tem':''}" type="number" inputmode="numeric" min="0" max="999" value="${v||''}" placeholder="·" data-cam="${camId}" data-cat="${cat.id}" data-aro="${a}"></td>`;
              }).join('')}
              <td class="tot-col${catTot>0?' tem':''}" id="tcat-${cat.id}">${catTot||'—'}</td>
            </tr>`;
          }).join('')}
          <tr class="total-row">
            <td style="text-align:left;padding-left:6px;font-size:10px;text-transform:uppercase;letter-spacing:.04em">Total aro</td>
            ${AROS_FULL.map(a=>{
              const t=CATS_TRIAGEM.reduce((s,c)=>s+(parseInt(triagemGrade[camId][c.id][a])||0),0);
              return `<td id="taro-${a}">${t||'—'}</td>`;
            }).join('')}
            <td class="geral${valido?' ok':''}" id="tgeral">${tot||'—'}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <button class="btn btn-primary btn-block${valido?'':' btn-dis'}" id="btn-confirmar-triagem" style="margin-top:12px;font-size:15px;padding:13px">
      <i class="ti ti-${valido?'device-floppy':'lock'}"></i> ${valido?'Confirmar triagem':`Preencha a grade — faltam ${cam.totalPneus-tot}`}
    </button>`;

  document.getElementById('btn-back-triagem')?.addEventListener('click',renderTriagemLista);
  document.querySelectorAll('.cell-inp[data-cam]').forEach(inp=>{
    inp.addEventListener('focus',()=>inp.select());
    inp.addEventListener('input',()=>{
      const {cam:cId,cat,aro}=inp.dataset;
      const val=Math.max(0,parseInt(inp.value)||0);
      triagemGrade[cId][cat][aro]=val;
      inp.value=val||'';
      inp.className='cell-inp'+(val>0?' tem':'');
      const catTot=AROS_FULL.reduce((s,a)=>s+(parseInt(triagemGrade[cId][cat][a])||0),0);
      const aroTot=CATS_TRIAGEM.reduce((s,c)=>s+(parseInt(triagemGrade[cId][c.id][aro])||0),0);
      const geral=CATS_TRIAGEM.reduce((s,c)=>s+AROS_FULL.reduce((ss,a)=>ss+(parseInt(triagemGrade[cId][c.id][a])||0),0),0);
      const camTot=CAMINHOES_CONF.find(c=>c.id===cId)?.totalPneus||0;
      const ok=geral===camTot;
      const elC=document.getElementById(`tcat-${cat}`);if(elC){elC.textContent=catTot||'—';elC.className='tot-col'+(catTot>0?' tem':'');}
      const elA=document.getElementById(`taro-${aro}`);if(elA)elA.textContent=aroTot||'—';
      const elG=document.getElementById('tgeral');if(elG){elG.textContent=geral||'—';elG.className='geral'+(ok?' ok':'');}
      const btn=document.getElementById('btn-confirmar-triagem');
      if(btn){if(ok){btn.innerHTML=`<i class="ti ti-device-floppy"></i> Confirmar triagem`;btn.classList.remove('btn-dis');}else{btn.innerHTML=`<i class="ti ti-lock"></i> Preencha a grade — faltam ${Math.max(0,camTot-geral)}`;btn.classList.add('btn-dis');}}
    });
  });
  document.getElementById('btn-confirmar-triagem')?.addEventListener('click',()=>{
    alert('✅ Triagem confirmada! Dados enviados para o gestor e projeção de receita atualizada.');
    renderTriagemLista();
  });
}

const CLIENTES_VND=[{"id":"1","nome":"BORRACHARIA PEREIRA LTDA"},{"id":"6","nome":"JATOBA PNEUS"},{"id":"7","nome":"WS DA SILVA COMERCIO DE PNEUS"},{"id":"8","nome":"RECAP PNEUS MARINGA"},{"id":"14","nome":"PRIME PNEUS COMERCIO E SERVICOS"},{"id":"17","nome":"SOSUKE CENTRO AUTOMOTIVO"},{"id":"23","nome":"ALEXANDRE DOS SANTOS"},{"id":"24","nome":"DANIEL PNEUS EIRELI ME"},{"id":"33","nome":"ATALAIA PNEUS E SERVICOS"},{"id":"43","nome":"PLATAFORMA CAR CENTER"},{"id":"63","nome":"MESQUITAO COMERCIO DE PNEUS"},{"id":"73","nome":"ROQUE WHEELS RODAS E PNEUS"},{"id":"82","nome":"TRUCKERS PNEUS"},{"id":"96","nome":"BORRACHARIA BR"},{"id":"99","nome":"CELIO CARRION"},{"id":"150","nome":"THINASS PNEUS ME"},{"id":"162","nome":"MULT COMERCIO DE PNEUS"},{"id":"263","nome":"GI PNEUS E RODAS"},{"id":"267","nome":"FR COMERCIO DE PNEUS"},{"id":"357","nome":"TCP ECOLOGY TYRE"},{"id":"363","nome":"SARADAO COMERCIO DE PNEUS"},{"id":"370","nome":"BENGEZEN COMERCIO DE PNEUS"},{"id":"371","nome":"JCM COMERCIO DE PNEUS"},{"id":"385","nome":"PNEUMAT COMERCIO DE PNEUS"},{"id":"399","nome":"AGILI DISTRIBUIDORA DE PNEUS"},{"id":"1000","nome":"KAUE PNEUS"},{"id":"1001","nome":"DANIEL JACOB LIMA"},{"id":"1009","nome":"EVANDRO DA SILVA ANDRADE"}];

const TCP_TAB={'13':[{m:'165/70R13',p:45},{m:'175/70R13',p:50},{m:'175/75R13',p:40}],'14':[{m:'175/65R14',p:45},{m:'175/70R14',p:55},{m:'185/65R14',p:50},{m:'185/70R14',p:50}],'15':[{m:'185/60R15',p:22},{m:'185/65R15',p:25},{m:'195/55R15',p:20},{m:'195/65R15',p:25},{m:'205/60R15',p:20},{m:'205/65R15',p:40}],'16':[{m:'205/55R16',p:10},{m:'205/60R16',p:15},{m:'215/65R16',p:30}],'17':[{m:'215/45R17',p:20},{m:'225/45R17',p:15},{m:'225/50R17',p:15}]};

let vndCad={'357':{categoria:'Carcaça',tipo:'medidas',tabela:TCP_TAB}};
let vndQtds={},vndFoto=false,vndPag=null,vndValor='',vndObs='';

function totalVnd(){return Object.values(vndQtds).reduce((s,v)=>s+(parseInt(v)||0),0);}
function valorVnd(){
  const cad=vndCad[vendasState.cliSel?.id];if(!cad)return 0;
  if(cad.tipo==='medidas'){
    let t=0;
    Object.entries(cad.tabela).forEach(([aro,meds])=>{meds.forEach((m,i)=>{t+=(parseInt(vndQtds[`${aro}|${i}`])||0)*m.p;});});
    return t;
  }
  return AROS_PADRAO.reduce((s,a)=>s+(parseInt(vndQtds[a])||0)*(parseFloat(cad.precos?.[a])||0),0);
}
const AROS_PADRAO=['13','14','15','16','17','SUV','Camionete','Caminhão'];

function renderVendas(){
  if(vendasState.tela==='cliente') renderVendasCliente();
  else if(vendasState.tela==='grade') renderVendasGrade();
  else if(vendasState.tela==='pagamento') renderVendasPagamento();
  else if(vendasState.tela==='confirmado') renderVendasConfirmado();
}

function renderVendasCliente(){
  const b=vendasState.busca.toLowerCase();
  const lista=CLIENTES_VND.filter(c=>!b||c.nome.toLowerCase().includes(b)||c.id.includes(b)).slice(0,40);
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon amarelo"><i class="ti ti-shopping-cart"></i></div><div><h2>Nova venda</h2><span>${CLIENTES_VND.length} clientes cadastrados</span></div></div>
    <div class="search-wrap"><i class="ti ti-search"></i><input id="busca-vnd" type="text" placeholder="Nome ou código..." value="${vendasState.busca}" autocomplete="off" autocorrect="off"></div>
    <div class="cli-list">
      ${lista.map(c=>{
        const sel=vendasState.cliSel?.id===c.id;
        const temC=!!vndCad[c.id];
        return `<div class="cli-row${sel?' sel':''}" data-vnd-cli="${c.id}">
          <div class="avatar ${sel?'verde':temC?'teal':'cinza'}">${temC?'<i class="ti ti-check" style="font-size:13px"></i>':ini(c.nome)}</div>
          <div style="flex:1;min-width:0">
            <strong style="font-size:14px;font-weight:500;display:block">${c.nome}</strong>
            <span style="font-size:11px;color:var(--text2)">Cód. ${c.id}${temC?` · <strong style="color:var(--teal)">${vndCad[c.id].categoria}</strong>`:' · 1ª venda'}</span>
          </div>
          ${sel?'<i class="ti ti-chevron-right" style="color:var(--green);font-size:16px;flex-shrink:0"></i>':''}
        </div>`;
      }).join('')}
    </div>
    <button class="btn btn-primary btn-block${vendasState.cliSel?'':' btn-dis'}" id="btn-vnd-avancar" style="margin-top:12px;font-size:15px;padding:13px">
      ${vendasState.cliSel?'Continuar ›':'Selecione um cliente'}
    </button>`;
  bindBack();
  document.getElementById('busca-vnd')?.addEventListener('input',e=>{vendasState.busca=e.target.value;renderVendasCliente();});
  document.querySelectorAll('[data-vnd-cli]').forEach(el=>{
    el.addEventListener('click',()=>{vendasState.cliSel=CLIENTES_VND.find(c=>c.id===el.dataset.vndCli);renderVendasCliente();});
  });
  document.getElementById('btn-vnd-avancar')?.addEventListener('click',()=>{
    if(!vendasState.cliSel)return;
    vndQtds={};vndFoto=false;vndPag=null;vndValor='';vndObs='';
    vendasState.tela='grade';renderVendasGrade();
  });
}

function renderVendasGrade(){
  const cli=vendasState.cliSel;
  const cad=vndCad[cli.id];
  const tot=totalVnd(),vt=valorVnd();
  if(!cad){
    document.getElementById('content-area').innerHTML=`
      ${btnBack()}
      <div class="mod-header"><div class="mod-header-icon amarelo"><i class="ti ti-user-check"></i></div><div><h2>${cli.nome.split(' ')[0]}</h2><span>Primeira venda — configurar</span></div></div>
      <div class="alert laranja"><i class="ti ti-sparkles"></i><p>Primeira venda para este cliente. No sistema completo, você configura a categoria e os preços por aro/medida aqui.</p></div>
      <p style="font-size:13px;color:var(--text2);margin-bottom:12px">Para o teste, vamos usar a tabela de demonstração.</p>
      <button class="btn btn-primary btn-block" id="btn-usar-demo"><i class="ti ti-arrow-right"></i> Usar tabela de demonstração</button>`;
    bindBack();
    document.getElementById('btn-usar-demo')?.addEventListener('click',()=>{
      vndCad[cli.id]={categoria:'Risco',tipo:'aros',precos:{'13':35,'14':35,'15':35,'16':35,'17':35,'SUV':35,'Camionete':35,'Caminhão':35}};
      renderVendasGrade();
    });
    return;
  }

  document.getElementById('content-area').innerHTML=`
    <button class="btn btn-secondary btn-sm" id="btn-back-grade" style="margin-bottom:1rem"><i class="ti ti-arrow-left"></i> Clientes</button>
    <div style="display:flex;align-items:center;gap:10px;margin-bottom:12px;padding-bottom:10px;border-bottom:1px solid var(--border-light)">
      <div class="avatar verde">${ini(cli.nome)}</div>
      <div style="flex:1;min-width:0"><strong style="font-size:14px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${cli.nome}</strong><span style="font-size:12px;font-weight:600;color:var(--teal)">${cad.categoria}</span></div>
    </div>
    ${cad.tipo==='medidas'?renderGradeVndMedidas(cad,cli.id):renderGradeVndAros(cad)}
    <div class="foto-slot${vndFoto?' done':''}" id="foto-vnd"><input type="file" accept="image/*" capture="environment" id="inp-foto-vnd"><i class="ti ti-${vndFoto?'circle-check':'camera'}"></i><p>${vndFoto?'Foto registrada':'Fotografar (opcional)'}</p></div>
    <div style="background:var(--bg);border-radius:var(--radius-sm);padding:10px 12px;margin-bottom:8px;display:flex;justify-content:space-between;align-items:center">
      <span style="font-size:13px;color:var(--text2)">Total: <strong style="color:var(--text)">${tot} pneu${tot!==1?'s':''}</strong></span>
      <span style="font-size:15px;font-weight:700;color:${tot>0?'var(--teal)':'var(--text2)'}">${vt>0?fmtM(vt):'—'}</span>
    </div>
    <button class="btn btn-primary btn-block${tot>0?'':' btn-dis'}" id="btn-vnd-pag" style="font-size:15px;padding:13px">
      ${tot>0?`Pagamento — ${tot} pneu${tot!==1?'s':''}${vt>0?' · '+fmtM(vt):''} ›`:'Preencha ao menos 1 pneu'}
    </button>`;

  document.getElementById('btn-back-grade')?.addEventListener('click',()=>{vendasState.tela='cliente';renderVendasCliente();});
  document.getElementById('inp-foto-vnd')?.addEventListener('change',e=>{if(e.target.files.length>0){vndFoto=true;renderVendasGrade();}});
  document.querySelectorAll('.cell-inp[data-vnd]').forEach(inp=>{
    inp.addEventListener('focus',()=>inp.select());
    inp.addEventListener('input',()=>{
      const val=Math.max(0,parseInt(inp.value)||0);
      vndQtds[inp.dataset.vnd]=val;
      inp.value=val||'';
      inp.className='cell-inp'+(val>0?' tem':'');
      atualizarTotaisVnd();
    });
  });
  document.getElementById('btn-vnd-pag')?.addEventListener('click',()=>{
    if(totalVnd()===0)return;
    const vt2=valorVnd();vndValor=vt2>0?vt2.toFixed(2):'';
    vendasState.tela='pagamento';renderVendasPagamento();
  });
}

function renderGradeVndMedidas(cad,cliId){
  return Object.keys(cad.tabela).map(aro=>{
    const meds=cad.tabela[aro];
    const subAro=meds.reduce((s,m,i)=>s+(parseInt(vndQtds[`${aro}|${i}`])||0)*m.p,0);
    const qtdAro=meds.reduce((s,m,i)=>s+(parseInt(vndQtds[`${aro}|${i}`])||0),0);
    return `<div style="margin-bottom:10px">
      <div style="background:var(--bg);border-radius:var(--radius-sm) var(--radius-sm) 0 0;border:1px solid var(--border);border-bottom:none;padding:8px 10px;display:flex;justify-content:space-between;align-items:center">
        <strong style="font-size:13px">Aro ${aro}</strong>
        ${qtdAro>0?`<span style="font-size:12px;font-weight:600;color:var(--teal)">${qtdAro}un · ${fmtM(subAro)}</span>`:''}
      </div>
      <table style="width:100%;border-collapse:collapse;border:1px solid var(--border);border-top:none;border-radius:0 0 var(--radius-sm) var(--radius-sm);overflow:hidden">
        <thead><tr style="background:var(--bg)"><th style="font-size:10px;font-weight:600;color:var(--text2);padding:5px 8px;border-bottom:1px solid var(--border);text-align:left">Medida</th><th style="font-size:10px;padding:5px 4px;border-bottom:1px solid var(--border);text-align:center">R$/un</th><th style="font-size:10px;padding:5px 4px;border-bottom:1px solid var(--border);text-align:center">Qtd</th><th style="font-size:10px;padding:5px 8px;border-bottom:1px solid var(--border);text-align:right">Sub</th></tr></thead>
        <tbody>${meds.map((m,i)=>{const k=`${aro}|${i}`;const q=parseInt(vndQtds[k])||0;const sub=q*m.p;return `<tr><td style="font-size:13px;font-weight:500;padding:6px 8px">${m.m}</td><td style="text-align:center;font-size:12px;color:var(--teal);padding:4px">${fmtM(m.p)}</td><td style="text-align:center;padding:3px"><input class="cell-inp${q>0?' tem':''}" type="number" inputmode="numeric" min="0" value="${q||''}" placeholder="·" data-vnd="${k}" style="width:48px;height:44px"></td><td style="text-align:right;font-size:12px;font-weight:500;padding:4px 8px;color:${sub>0?'var(--teal)':'var(--text3)'}">${sub>0?fmtM(sub):'—'}</td></tr>`;}).join('')}</tbody>
      </table>
    </div>`;
  }).join('');
}

function renderGradeVndAros(cad){
  const precos=cad.precos||{};
  return `<table style="width:100%;border-collapse:collapse;border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;margin-bottom:10px">
    <thead><tr style="background:var(--bg)"><th style="padding:8px 12px;text-align:left;font-size:11px;font-weight:600;color:var(--text2);border-bottom:1px solid var(--border)">Aro</th><th style="padding:8px;text-align:center;font-size:11px;font-weight:600;color:var(--text2);border-bottom:1px solid var(--border)">Preço</th><th style="padding:8px;text-align:center;font-size:11px;font-weight:600;color:var(--text2);border-bottom:1px solid var(--border)">Qtd</th><th style="padding:8px 12px;text-align:right;font-size:11px;font-weight:600;color:var(--text2);border-bottom:1px solid var(--border)">Sub</th></tr></thead>
    <tbody>${AROS_PADRAO.map(a=>{const p=parseFloat(precos[a])||0;const q=parseInt(vndQtds[a])||0;const sub=q*p;return `<tr><td style="font-size:14px;font-weight:500;padding:8px 12px">Aro ${a}</td><td style="text-align:center;font-size:13px;color:${p>0?'var(--teal)':'var(--text3)'};">${p>0?fmtM(p):'—'}</td><td style="text-align:center;padding:4px"><input class="cell-inp${q>0?' tem':''}" type="number" inputmode="numeric" min="0" value="${q||''}" placeholder="${p>0?'·':'—'}" ${p===0?'style="opacity:.3;pointer-events:none"':''} data-vnd="${a}" style="width:48px;height:44px"></td><td style="text-align:right;padding:8px 12px;font-size:13px;font-weight:500;color:${sub>0?'var(--teal)':'var(--text3)'}">${sub>0?fmtM(sub):'—'}</td></tr>`;}).join('')}</tbody>
  </table>`;
}

function atualizarTotaisVnd(){
  const tot=totalVnd(),vt=valorVnd();
  const btn=document.getElementById('btn-vnd-pag');
  if(btn){if(tot>0){btn.innerHTML=`Pagamento — ${tot} pneu${tot!==1?'s':''}${vt>0?' · '+fmtM(vt):''} ›`;btn.classList.remove('btn-dis');}else{btn.textContent='Preencha ao menos 1 pneu';btn.classList.add('btn-dis');}}
  const resumo=document.querySelector('.vnd-resumo');
  if(resumo){resumo.querySelector('.vr-tot').textContent=`${tot} pneus`;resumo.querySelector('.vr-val').textContent=vt>0?fmtM(vt):'—';}
}

function renderVendasPagamento(){
  const cli=vendasState.cliSel,tot=totalVnd(),vt=valorVnd();
  if(!vndValor&&vt>0)vndValor=vt.toFixed(2);
  document.getElementById('content-area').innerHTML=`
    <button class="btn btn-secondary btn-sm" id="btn-back-pag" style="margin-bottom:1rem"><i class="ti ti-arrow-left"></i> Editar pedido</button>
    <div style="background:var(--teal-bg);border:1px solid var(--teal-light);border-radius:var(--radius);padding:12px 14px;margin-bottom:14px;display:flex;justify-content:space-between;align-items:center">
      <div><strong style="font-size:14px;color:var(--teal)">${cli.nome.split(' ')[0]}</strong><div style="font-size:12px;color:var(--teal);margin-top:2px">${tot} pneu${tot!==1?'s':''} · ${fmtM(vt)}</div></div>
    </div>
    <p class="section-title">Forma de pagamento</p>
    <div class="pag-grid">
      ${PAGS.map(p=>`<div class="pag-opt${vndPag===p.id?' sel':''}" data-pag="${p.id}"><i class="ti ${p.icon}"></i><span>${p.nome}</span></div>`).join('')}
    </div>
    <p class="section-title">Valor total</p>
    <input id="inp-vnd-valor" type="number" inputmode="decimal" step="0.01" min="0" value="${vndValor}" placeholder="0,00" style="font-size:22px;font-weight:700;color:var(--teal);border-color:var(--teal);text-align:center;padding:12px;margin-bottom:6px">
    ${vt>0?`<p style="font-size:11px;color:var(--text2);text-align:center;margin-bottom:10px">Tabelado: ${fmtM(vt)}</p>`:''}
    <div class="form-group"><label>Observação (opcional)</label><input id="inp-vnd-obs" type="text" placeholder="Entrega, desconto, parcelado..." value="${vndObs}"></div>
    <button class="btn btn-primary btn-block${vndPag?'':' btn-dis'}" id="btn-confirmar-venda" style="font-size:15px;padding:13px"><i class="ti ti-check"></i> Confirmar venda</button>`;

  document.getElementById('btn-back-pag')?.addEventListener('click',()=>{vendasState.tela='grade';renderVendasGrade();});
  document.querySelectorAll('.pag-opt[data-pag]').forEach(el=>{
    el.addEventListener('click',()=>{vndPag=el.dataset.pag;document.querySelectorAll('.pag-opt').forEach(e=>e.classList.remove('sel'));el.classList.add('sel');document.getElementById('btn-confirmar-venda')?.classList.remove('btn-dis');});
  });
  document.getElementById('inp-vnd-valor')?.addEventListener('input',e=>{vndValor=e.target.value;});
  document.getElementById('inp-vnd-obs')?.addEventListener('input',e=>{vndObs=e.target.value;});
  document.getElementById('btn-confirmar-venda')?.addEventListener('click',()=>{
    const v=document.getElementById('inp-vnd-valor')?.value||vndValor;
    const o=document.getElementById('inp-vnd-obs')?.value||vndObs;
    if(!vndPag||!v)return;
    const formaNome=PAGS.find(p=>p.id===vndPag)?.nome||'';
    const pagoAVista=['dinheiro','pix','credito','debito','cheque'].includes(vndPag);
    const valorNum=parseFloat(v)||0;
    vendasState.historico.push({
      id:'ped_'+Date.now()+'_'+Math.floor(Math.random()*1000),
      cliente:vendasState.cliSel.nome,pneus:tot,pagamento:formaNome,valor:v,valorTotal:valorNum,obs:o,hora:now(),
      data:today(),dataISO:new Date().toISOString().slice(0,10),
      pagamentos:pagoAVista?[{valor:valorNum,forma:formaNome,hora:now()}]:[],
      notasFiscais:[]
    });
    vendasState.tela='confirmado';renderVendasConfirmado();
  });
}

function renderVendasConfirmado(){
  const v=vendasState.historico[vendasState.historico.length-1];if(!v)return;
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div style="text-align:center;padding:.5rem 0 1.5rem">
      <div style="width:72px;height:72px;border-radius:50%;background:var(--teal-bg);display:flex;align-items:center;justify-content:center;margin:0 auto 12px"><i class="ti ti-circle-check" style="font-size:36px;color:var(--teal)"></i></div>
      <p style="font-size:20px;font-weight:700;color:var(--teal)">Venda registrada!</p>
      <p style="font-size:13px;color:var(--text2);margin-top:4px">${v.hora}</p>
    </div>
    <div class="card">
      <div class="fin-row"><span class="fl">Cliente</span><span class="fv">${v.cliente}</span></div>
      <div class="fin-row"><span class="fl">Pneus</span><span class="fv">${v.pneus} un</span></div>
      <div class="fin-row"><span class="fl">Pagamento</span><span class="fv">${v.pagamento}</span></div>
      <div class="fin-row" style="font-size:16px"><span class="fl">Valor</span><span class="fv" style="color:var(--teal)">${fmtM(v.valor)}</span></div>
      ${v.obs?`<div class="fin-row"><span class="fl">Obs.</span><span class="fv">${v.obs}</span></div>`:''}
    </div>
    <button class="btn btn-primary btn-block" id="btn-nova-vnd" style="font-size:15px;padding:13px"><i class="ti ti-plus"></i> Nova venda</button>`;
  document.getElementById('btn-back-mod')?.addEventListener('click',renderDashboard);
  document.getElementById('btn-nova-vnd')?.addEventListener('click',()=>{vendasState.cliSel=null;vendasState.busca='';vndQtds={};vndFoto=false;vndPag=null;vndValor='';vndObs='';vendasState.tela='cliente';renderVendas();});
}

function renderVendasHist(){
  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon verde"><i class="ti ti-history"></i></div><div><h2>Histórico de vendas</h2><span>Hoje</span></div></div>
    ${vendasState.historico.length===0?`<div class="empty"><i class="ti ti-shopping-cart-off"></i><p>Nenhuma venda registrada ainda.</p></div>`:`
    <div class="stat-grid"><div class="stat-box teal"><div class="sv">${vendasState.historico.length}</div><div class="sl">Vendas</div></div><div class="stat-box verde"><div class="sv">${fmtM(vendasState.historico.reduce((s,v)=>s+parseFloat(v.valor||0),0))}</div><div class="sl">Total</div></div></div>
    ${[...vendasState.historico].reverse().map(v=>`<div class="card"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px"><strong style="font-size:14px">${v.cliente.split(' ').slice(0,2).join(' ')}</strong><span style="font-size:16px;font-weight:700;color:var(--teal)">${fmtM(v.valor)}</span></div><div style="font-size:13px;color:var(--text2)">${v.hora} · ${v.pneus} un · ${v.pagamento}</div>${v.obs?`<div style="font-size:12px;color:var(--text2);margin-top:4px">${v.obs}</div>`:''}</div>`).join('')}`}`;
  bindBack();
}

// ── FINANCEIRO (RELATÓRIOS) ───────────────────────────────────────────────────
let relatorioState={cliente:'',data:'',pagamento:'',nf:''};

function pedidosFiltrados(){
  return vendasState.historico.filter(p=>{
    if(relatorioState.cliente && !p.cliente.toLowerCase().includes(relatorioState.cliente.toLowerCase()))return false;
    if(relatorioState.data && p.dataISO!==relatorioState.data)return false;
    if(relatorioState.pagamento && p.pagamento!==relatorioState.pagamento)return false;
    if(relatorioState.nf){
      const achou=(p.notasFiscais||[]).some(nf=>nf.numero.toLowerCase().includes(relatorioState.nf.toLowerCase()));
      if(!achou)return false;
    }
    return true;
  }).slice().reverse();
}

function imprimirRelatorioFiltrado(lista){
  const totalValor=lista.reduce((s,p)=>s+valorTotalPedido(p),0);
  const totalPago=lista.reduce((s,p)=>s+valorPagoPedido(p),0);
  const totalSaldo=lista.reduce((s,p)=>s+Math.max(0,saldoPedido(p)),0);
  const win=window.open('','_blank');
  if(!win)return;
  win.document.write(`<!DOCTYPE html><html lang="pt-BR"><head><meta charset="UTF-8"><title>Relatório Financeiro — Tyre Eco</title>
    <style>
      body{font-family:-apple-system,Arial,sans-serif;padding:32px;color:#1A1A18;max-width:760px;margin:0 auto}
      h1{font-size:19px;margin-bottom:2px}
      h2{font-size:12px;color:#6B6B65;font-weight:400;margin-bottom:18px}
      table{width:100%;border-collapse:collapse;margin-bottom:6px}
      td,th{padding:6px 4px;border-bottom:1px solid #E5E4E0;font-size:12px;text-align:left}
      th{color:#6B6B65;font-size:10px;text-transform:uppercase}
      td:not(:first-child),th:not(:first-child){text-align:right}
      .tot td{font-weight:700;border-top:2px solid #1A1A18;border-bottom:none}
      @media print{body{padding:12px}}
    </style></head><body>
    <h1>Relatório Financeiro — Tyre Eco</h1>
    <h2>Filtros: cliente="${relatorioState.cliente||'todos'}" · data="${relatorioState.data||'todas'}" · pagamento="${relatorioState.pagamento||'todas'}" · NF="${relatorioState.nf||'todas'}" · Gerado em ${today()} ${now()}</h2>
    <table><tr><th>Cliente</th><th>Data</th><th>Pagamento</th><th>Total</th><th>Pago</th><th>Saldo</th><th>NFs</th></tr>
      ${lista.map(p=>`<tr><td>${p.cliente}</td><td>${p.data||'—'}</td><td>${p.pagamento}</td><td>${fmtM(valorTotalPedido(p))}</td><td>${fmtM(valorPagoPedido(p))}</td><td>${fmtM(Math.max(0,saldoPedido(p)))}</td><td>${(p.notasFiscais||[]).map(nf=>nf.numero).join(', ')||'—'}</td></tr>`).join('')||'<tr><td colspan="7">Nenhum pedido encontrado com esses filtros.</td></tr>'}
      <tr class="tot"><td colspan="3">Total (${lista.length} pedido${lista.length!==1?'s':''})</td><td>${fmtM(totalValor)}</td><td>${fmtM(totalPago)}</td><td>${fmtM(totalSaldo)}</td><td></td></tr>
    </table>
  </body></html>`);
  win.document.close();
  win.focus();
  setTimeout(()=>win.print(),200);
}

function renderRelatorioFinanceiro(){
  const lista=pedidosFiltrados();
  const totalValor=lista.reduce((s,p)=>s+valorTotalPedido(p),0);
  const totalPago=lista.reduce((s,p)=>s+valorPagoPedido(p),0);
  const totalSaldo=lista.reduce((s,p)=>s+Math.max(0,saldoPedido(p)),0);
  const temFiltro=relatorioState.cliente||relatorioState.data||relatorioState.pagamento||relatorioState.nf;

  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header">
      <div class="mod-header-icon vermelho"><i class="ti ti-report-analytics"></i></div>
      <div style="flex:1"><h2>Relatórios Financeiros</h2><span>Filtrar vendas, pagamentos e NFs</span></div>
      <button class="btn btn-secondary btn-sm" id="btn-imprimir-rel" title="Exportar/imprimir"><i class="ti ti-printer"></i></button>
    </div>

    <div class="card">
      <div class="form-group" style="margin-bottom:10px">
        <label>Cliente</label>
        <input type="text" id="rel-cliente" placeholder="Buscar por nome do cliente..." value="${relatorioState.cliente}">
      </div>
      <div style="display:flex;gap:8px;margin-bottom:10px">
        <div class="form-group" style="flex:1;margin-bottom:0">
          <label>Data da venda</label>
          <input type="date" id="rel-data" value="${relatorioState.data}">
        </div>
        <div class="form-group" style="flex:1;margin-bottom:0">
          <label>Pagamento</label>
          <select id="rel-pagamento">
            <option value="">Todas</option>
            ${PAGS.map(p=>`<option value="${p.nome}" ${relatorioState.pagamento===p.nome?'selected':''}>${p.nome}</option>`).join('')}
          </select>
        </div>
      </div>
      <div class="form-group" style="margin-bottom:10px">
        <label>Nº da NF emitida</label>
        <input type="text" id="rel-nf" placeholder="Buscar por número de NF..." value="${relatorioState.nf}">
      </div>
      <div style="display:flex;gap:8px">
        <button class="btn btn-primary" style="flex:1;justify-content:center" id="btn-rel-filtrar"><i class="ti ti-filter"></i> Filtrar</button>
        ${temFiltro?`<button class="btn btn-secondary" id="btn-rel-limpar"><i class="ti ti-x"></i> Limpar</button>`:''}
      </div>
    </div>

    <div class="stat-grid-3">
      <div class="stat-box"><div class="sv">${lista.length}</div><div class="sl">Pedidos</div></div>
      <div class="stat-box verde"><div class="sv">${fmtM(totalPago)}</div><div class="sl">Pago</div></div>
      <div class="stat-box vermelho"><div class="sv">${fmtM(totalSaldo)}</div><div class="sl">Saldo</div></div>
    </div>

    ${lista.length===0?`<div class="empty"><i class="ti ti-file-search"></i><p>Nenhum pedido encontrado com esses filtros.</p></div>`:`
    <div class="grade-scroll">
      <table class="conf-table" style="min-width:640px">
        <thead><tr>
          <th style="text-align:left">Cliente</th>
          <th style="text-align:left">Data</th>
          <th style="text-align:left">Pagamento</th>
          <th>Total</th>
          <th>Pago</th>
          <th>Saldo</th>
          <th style="text-align:left">NFs emitidas</th>
        </tr></thead>
        <tbody>
          ${lista.map(p=>{
            const saldo=Math.max(0,saldoPedido(p));
            return `<tr class="${saldo>0.009?'div-row':''}">
              <td style="font-weight:600">${p.cliente.split(' ').slice(0,3).join(' ')}</td>
              <td>${p.data||'—'}${p.hora?` · ${p.hora}`:''}</td>
              <td>${p.pagamento}</td>
              <td style="text-align:right">${fmtM(valorTotalPedido(p))}</td>
              <td style="text-align:right;color:var(--green)">${fmtM(valorPagoPedido(p))}</td>
              <td style="text-align:right;font-weight:600;color:${saldo>0.009?'var(--red)':'var(--green)'}">${fmtM(saldo)}</td>
              <td>${(p.notasFiscais||[]).length?(p.notasFiscais||[]).map(nf=>`<span class="badge azul" style="margin:1px">NF ${nf.numero}</span>`).join(''):'<span style="color:var(--text3)">—</span>'}</td>
            </tr>`;
          }).join('')}
        </tbody>
      </table>
    </div>
    <div class="fin-row" style="margin-top:8px;font-size:14px"><span class="fl">Total do filtro</span><span class="fv">${fmtM(totalValor)}</span></div>
    `}`;
  bindBack();
  document.getElementById('btn-rel-filtrar')?.addEventListener('click',()=>{
    relatorioState.cliente=document.getElementById('rel-cliente')?.value||'';
    relatorioState.data=document.getElementById('rel-data')?.value||'';
    relatorioState.pagamento=document.getElementById('rel-pagamento')?.value||'';
    relatorioState.nf=document.getElementById('rel-nf')?.value||'';
    renderRelatorioFinanceiro();
  });
  document.getElementById('btn-rel-limpar')?.addEventListener('click',()=>{
    relatorioState={cliente:'',data:'',pagamento:'',nf:''};
    renderRelatorioFinanceiro();
  });
  document.getElementById('btn-imprimir-rel')?.addEventListener('click',()=>imprimirRelatorioFiltrado(lista));
}

// ── EMISSÃO DE NF (NFS-e) — gera a ficha de conferência (Passos 1 a 3) ────────
// Dados do prestador (sua empresa) — edite com os dados reais da Tyre Eco.
let prestadorNF={razaoSocial:'TYRE ECO RECICLAGEM DE PNEUS LTDA',cnpj:'00.000.000/0001-00',ccm:'0.000.000-0'};
let rpsSeq=1;
let fichasNF=[]; // fichas confirmadas nesta sessão
let nfForm={
  cliente:'',cnpjTomador:'',endereco:'',email:'',
  parcela:'1',valor:'',vencimento:'',
  servicoCodigo:'2680',servicoDesc:'Coleta, transporte e destinação de pneus inservíveis',
  dataAssinatura:'',serieRps:'A'
};

function fmtDataBr(iso){if(!iso)return'';const[y,m,d]=iso.split('-');return`${d}/${m}/${y}`;}

function montarFichaNF(f,rps){
  const hoje=today();
  const vencBr=fmtDataBr(f.vencimento);
  const assinBr=fmtDataBr(f.dataAssinatura);
  const discriminacao=`${f.servicoDesc}${assinBr?` — ${f.parcela}ª parcela referente ao contrato firmado em ${assinBr}`:` — ${f.parcela}ª parcela`}`;
  return`━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  FICHA DA NFS-e
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PRESTADOR:    ${prestadorNF.razaoSocial||'—'}
CNPJ:         ${prestadorNF.cnpj||'—'}
CCM:          ${prestadorNF.ccm||'—'}

TOMADOR:      ${f.cliente||'—'}
CNPJ:         ${f.cnpjTomador||'—'}
E-MAIL NF:    ${f.email||'—'}

PARCELA:      ${f.parcela||'—'}ª — R$ ${f.valor?parseFloat(f.valor).toLocaleString('pt-BR',{minimumFractionDigits:2}):'—'}
VENCIMENTO:   ${vencBr||'—'}

SERVIÇO:      ${f.servicoCodigo||'—'} — ${f.servicoDesc||'—'}
DISCRIMINAÇÃO:${discriminacao}

RPS:          Nº ${rps} — Série ${f.serieRps||'A'}
DATA EMISSÃO: ${hoje}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━`;
}

function copiarTexto(txt){
  if(navigator.clipboard&&navigator.clipboard.writeText){navigator.clipboard.writeText(txt);}
}

function renderEmitirNF(){
  const fichaTexto=montarFichaNF(nfForm,rpsSeq);
  const clientesSugeridos=nfForm.cliente?CLIENTES_VND.filter(c=>c.nome.toLowerCase().includes(nfForm.cliente.toLowerCase())).slice(0,5):[];
  const camposOk=nfForm.cliente&&nfForm.cnpjTomador&&nfForm.valor&&nfForm.vencimento;

  document.getElementById('content-area').innerHTML=`
    ${btnBack()}
    <div class="mod-header"><div class="mod-header-icon roxo"><i class="ti ti-file-invoice"></i></div><div><h2>Emitir NF</h2><span>Ficha da NFS-e — próximo RPS: ${rpsSeq}</span></div></div>

    <div class="alert laranja"><i class="ti ti-alert-triangle"></i><p>Esta tela monta e confere a <strong>ficha da NFS-e</strong> (dados do tomador, parcela e serviço). A emissão real no portal <strong>nfe.prefeitura.sp.gov.br</strong> exige login com certificado digital e-CNPJ/e-CPF e precisa ser feita manualmente ou numa sessão separada com Claude in Chrome — não é possível automatizar o portal dentro deste arquivo.</p></div>

    <div class="section-title">Prestador (sua empresa)</div>
    <div class="card">
      <div class="form-group"><label>Razão social</label><input type="text" id="nf-prest-razao" value="${prestadorNF.razaoSocial}"></div>
      <div style="display:flex;gap:8px">
        <div class="form-group" style="flex:1"><label>CNPJ</label><input type="text" id="nf-prest-cnpj" value="${prestadorNF.cnpj}"></div>
        <div class="form-group" style="flex:1"><label>CCM</label><input type="text" id="nf-prest-ccm" value="${prestadorNF.ccm}"></div>
      </div>
    </div>

    <div class="section-title">Tomador (cliente)</div>
    <div class="card">
      <div class="form-group" style="margin-bottom:${clientesSugeridos.length?'2px':'12px'}">
        <label>Razão social / nome</label>
        <input type="text" id="nf-cliente" placeholder="Buscar ou digitar..." value="${nfForm.cliente}" autocomplete="off">
      </div>
      ${clientesSugeridos.length?`<div class="cli-list" style="margin-bottom:12px">${clientesSugeridos.map(c=>`<div class="cli-row" data-nf-sug="${c.nome.replace(/"/g,'&quot;')}"><div class="avatar teal">${ini(c.nome)}</div><div style="flex:1;font-size:13px">${c.nome}</div></div>`).join('')}</div>`:''}
      <div class="form-group"><label>CNPJ do tomador</label><input type="text" id="nf-cnpj" placeholder="XX.XXX.XXX/XXXX-XX" value="${nfForm.cnpjTomador}"></div>
      <div class="form-group"><label>Endereço</label><input type="text" id="nf-endereco" placeholder="Endereço completo" value="${nfForm.endereco}"></div>
      <div class="form-group"><label>E-mail para envio da NF</label><input type="email" id="nf-email" placeholder="financeiro@cliente.com" value="${nfForm.email}"></div>
    </div>

    <div class="section-title">Parcela e serviço</div>
    <div class="card">
      <div style="display:flex;gap:8px">
        <div class="form-group" style="flex:1"><label>Parcela (Nº)</label><input type="number" min="1" id="nf-parcela" value="${nfForm.parcela}"></div>
        <div class="form-group" style="flex:1"><label>Valor (R$)</label><input type="number" step="0.01" min="0" id="nf-valor" value="${nfForm.valor}"></div>
        <div class="form-group" style="flex:1"><label>Vencimento</label><input type="date" id="nf-vencimento" value="${nfForm.vencimento}"></div>
      </div>
      <div style="display:flex;gap:8px">
        <div class="form-group" style="flex:1"><label>Código do serviço</label><input type="text" id="nf-servico-cod" value="${nfForm.servicoCodigo}"></div>
        <div class="form-group" style="flex:2"><label>Descrição do serviço</label><input type="text" id="nf-servico-desc" value="${nfForm.servicoDesc}"></div>
      </div>
      <div style="display:flex;gap:8px">
        <div class="form-group" style="flex:1"><label>Data de assinatura do contrato</label><input type="date" id="nf-data-assin" value="${nfForm.dataAssinatura}"></div>
        <div class="form-group" style="width:90px"><label>Série RPS</label><input type="text" maxlength="2" id="nf-serie" value="${nfForm.serieRps}"></div>
      </div>
    </div>

    <div class="section-title">Ficha gerada (Nº RPS ${rpsSeq})</div>
    <div class="card" style="background:var(--bg)">
      <pre style="font-family:'SF Mono',Consolas,monospace;font-size:11.5px;line-height:1.5;white-space:pre-wrap;word-break:break-word;color:var(--text);margin:0">${fichaTexto}</pre>
    </div>

    <div style="display:flex;gap:8px;margin-bottom:1rem">
      <button class="btn btn-secondary" style="flex:1;justify-content:center" id="btn-nf-copiar"><i class="ti ti-copy"></i> Copiar ficha</button>
      <button class="btn btn-primary${camposOk?'':' btn-dis'}" style="flex:1;justify-content:center" id="btn-nf-confirmar"><i class="ti ti-check"></i> Confirmar ficha</button>
    </div>

    ${fichasNF.length?`<div class="section-title">Fichas confirmadas nesta sessão (${fichasNF.length})</div>
    ${fichasNF.slice().reverse().map(f=>`<div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px">
        <strong style="font-size:13px">${f.cliente}</strong>
        <span class="badge roxo">RPS ${f.rps}</span>
      </div>
      <div style="font-size:12px;color:var(--text2)">Parcela ${f.parcela}ª · ${fmtM(f.valor)} · venc. ${fmtDataBr(f.vencimento)} · gerada ${f.horaGeracao}</div>
    </div>`).join('')}`:''}`;

  bindBack();
  document.getElementById('nf-prest-razao')?.addEventListener('input',e=>{prestadorNF.razaoSocial=e.target.value;renderEmitirNF();});
  document.getElementById('nf-prest-cnpj')?.addEventListener('input',e=>{prestadorNF.cnpj=e.target.value;renderEmitirNF();});
  document.getElementById('nf-prest-ccm')?.addEventListener('input',e=>{prestadorNF.ccm=e.target.value;renderEmitirNF();});
  document.getElementById('nf-cliente')?.addEventListener('input',e=>{nfForm.cliente=e.target.value;renderEmitirNF();});
  document.querySelectorAll('[data-nf-sug]').forEach(el=>{
    el.addEventListener('click',()=>{nfForm.cliente=el.dataset.nfSug;renderEmitirNF();});
  });
  document.getElementById('nf-cnpj')?.addEventListener('input',e=>{nfForm.cnpjTomador=e.target.value;renderEmitirNF();});
  document.getElementById('nf-endereco')?.addEventListener('input',e=>{nfForm.endereco=e.target.value;renderEmitirNF();});
  document.getElementById('nf-email')?.addEventListener('input',e=>{nfForm.email=e.target.value;renderEmitirNF();});
  document.getElementById('nf-parcela')?.addEventListener('input',e=>{nfForm.parcela=e.target.value;renderEmitirNF();});
  document.getElementById('nf-valor')?.addEventListener('input',e=>{nfForm.valor=e.target.value;renderEmitirNF();});
  document.getElementById('nf-vencimento')?.addEventListener('input',e=>{nfForm.vencimento=e.target.value;renderEmitirNF();});
  document.getElementById('nf-servico-cod')?.addEventListener('input',e=>{nfForm.servicoCodigo=e.target.value;renderEmitirNF();});
  document.getElementById('nf-servico-desc')?.addEventListener('input',e=>{nfForm.servicoDesc=e.target.value;renderEmitirNF();});
  document.getElementById('nf-data-assin')?.addEventListener('input',e=>{nfForm.dataAssinatura=e.target.value;renderEmitirNF();});
  document.getElementById('nf-serie')?.addEventListener('input',e=>{nfForm.serieRps=e.target.value;renderEmitirNF();});
  document.getElementById('btn-nf-copiar')?.addEventListener('click',()=>copiarTexto(fichaTexto));
  document.getElementById('btn-nf-confirmar')?.addEventListener('click',()=>{
    if(!camposOk)return;
    fichasNF.push({rps:rpsSeq,cliente:nfForm.cliente,parcela:nfForm.parcela,valor:parseFloat(nfForm.valor)||0,vencimento:nfForm.vencimento,horaGeracao:now(),ficha:fichaTexto});
    rpsSeq++;
    nfForm={...nfForm,cliente:'',cnpjTomador:'',endereco:'',email:'',valor:'',vencimento:''};
    renderEmitirNF();
  });
}

</script>
</body>
</html>
