
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="AAEGM Cours de Vacances - Amicale des Anciens Élèves de Gallo Malick">
<title>AAEGM Cours de Vacances</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{box-sizing:border-box;margin:0;padding:0}

:root{
  --blue:#0757a0;
  --blue2:#0b76d1;
  --dark:#073763;
  --light:#f4f8fc;
  --white:#fff;
  --green:#198754;
  --red:#dc3545;
  --orange:#f59f00;
  --gray:#6c757d;
  --border:#dce5ef;
  --shadow:0 8px 25px rgba(0,0,0,.08);
}

body{
  font-family:Arial,Helvetica,sans-serif;
  background:var(--light);
  color:#17212b;
  line-height:1.5;
}

button,input,select,textarea{font:inherit}

button{
  cursor:pointer;
  border:0;
}

a{
  text-decoration:none;
  color:inherit;
}

.hidden{display:none!important}

/* HEADER */
header{
  background:linear-gradient(135deg,var(--dark),var(--blue2));
  color:white;
  position:sticky;
  top:0;
  z-index:100;
  box-shadow:0 3px 15px rgba(0,0,0,.15);
}

.navbar{
  max-width:1200px;
  margin:auto;
  min-height:70px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:12px 20px;
  gap:20px;
}

.logo-area{
  display:flex;
  align-items:center;
  gap:12px;
}

.logo{
  width:48px;
  height:48px;
  border-radius:50%;
  background:white;
  color:var(--blue);
  display:flex;
  align-items:center;
  justify-content:center;
  font-weight:900;
  font-size:14px;
}

.logo-text strong{
  display:block;
  font-size:18px;
}

.logo-text small{
  opacity:.85;
}

.nav-actions{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
}

/* BUTTONS */
.btn{
  padding:11px 18px;
  border-radius:8px;
  font-weight:700;
  transition:.2s;
}

.btn:hover{
  transform:translateY(-1px);
  opacity:.94;
}

.btn-primary{
  background:var(--blue2);
  color:white;
}

.btn-white{
  background:white;
  color:var(--blue);
}

.btn-outline{
  background:transparent;
  color:white;
  border:1px solid rgba(255,255,255,.6);
}

.btn-danger{
  background:var(--red);
  color:white;
}

.btn-success{
  background:var(--green);
  color:white;
}

.btn-gray{
  background:#e9ecef;
  color:#333;
}

.btn-small{
  padding:8px 12px;
  font-size:14px;
}

/* HERO */
.hero{
  background:
    linear-gradient(135deg,rgba(3,39,75,.95),rgba(7,87,160,.9)),
    radial-gradient(circle at top right,#35a7ff,transparent 35%);
  color:white;
  padding:85px 20px;
}

.hero-inner{
  max-width:1100px;
  margin:auto;
  text-align:center;
}

.hero h1{
  font-size:clamp(34px,6vw,64px);
  margin-bottom:15px;
}

.hero p{
  max-width:760px;
  margin:0 auto 30px;
  font-size:19px;
  opacity:.95;
}

.hero-buttons{
  display:flex;
  justify-content:center;
  flex-wrap:wrap;
  gap:12px;
}

/* SECTIONS */
.section{
  max-width:1100px;
  margin:auto;
  padding:60px 20px;
}

.section-title{
  text-align:center;
  color:var(--dark);
  font-size:32px;
  margin-bottom:35px;
}

.cards{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:20px;
}

.card{
  background:white;
  border-radius:14px;
  padding:25px;
  box-shadow:var(--shadow);
  border:1px solid var(--border);
}

.card h3{
  color:var(--blue);
  margin-bottom:10px;
}

.icon{
  font-size:38px;
  margin-bottom:12px;
}

/* MODALS */
.modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.65);
  display:flex;
  justify-content:center;
  align-items:center;
  padding:15px;
  z-index:1000;
}

.modal-box{
  background:white;
  width:100%;
  max-width:550px;
  max-height:92vh;
  overflow:auto;
  border-radius:15px;
  box-shadow:0 20px 60px rgba(0,0,0,.3);
}

.modal-header{
  background:var(--blue);
  color:white;
  padding:18px 22px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.modal-header h2{
  font-size:20px;
}

.close{
  background:transparent;
  color:white;
  font-size:28px;
}

.modal-body{
  padding:22px;
}

/* FORMS */
.form-group{
  margin-bottom:15px;
}

.form-group label{
  display:block;
  font-weight:700;
  margin-bottom:6px;
}

.form-group input,
.form-group select,
.form-group textarea{
  width:100%;
  padding:11px 12px;
  border:1px solid #ccd6e0;
  border-radius:8px;
  outline:none;
  background:white;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus{
  border-color:var(--blue2);
  box-shadow:0 0 0 3px rgba(11,118,209,.1);
}

.form-row{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:12px;
}

.form-actions{
  display:flex;
  gap:10px;
  justify-content:flex-end;
  margin-top:20px;
  flex-wrap:wrap;
}

.role-choice{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
  margin-bottom:20px;
}

.role-choice button{
  border:2px solid var(--border);
  background:white;
  padding:15px;
  border-radius:10px;
  font-weight:700;
}

.role-choice button.active{
  border-color:var(--blue2);
  background:#eef7ff;
  color:var(--blue);
}

/* APP */
#app{
  min-height:100vh;
}

.app-layout{
  display:flex;
  min-height:calc(100vh - 70px);
}

.sidebar{
  width:250px;
  background:#082f55;
  color:white;
  padding:18px 12px;
  flex-shrink:0;
}

.sidebar-user{
  padding:12px;
  border-bottom:1px solid rgba(255,255,255,.15);
  margin-bottom:10px;
}

.sidebar-user strong{
  display:block;
}

.sidebar-user small{
  opacity:.7;
}

.sidebar button{
  width:100%;
  text-align:left;
  background:transparent;
  color:white;
  padding:12px;
  border-radius:8px;
  margin:2px 0;
}

.sidebar button:hover,
.sidebar button.active{
  background:rgba(255,255,255,.13);
}

.main-content{
  flex:1;
  padding:25px;
  overflow:auto;
}

.page-title{
  margin-bottom:20px;
}

.page-title h1{
  color:var(--dark);
}

/* STATS */
.stats{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:15px;
  margin-bottom:25px;
}

.stat{
  background:white;
  border:1px solid var(--border);
  box-shadow:var(--shadow);
  border-radius:12px;
  padding:20px;
}

.stat-number{
  font-size:32px;
  font-weight:900;
  color:var(--blue);
}

.stat-label{
  color:var(--gray);
}

/* TABLE */
.table-container{
  background:white;
  border-radius:12px;
  box-shadow:var(--shadow);
  overflow:auto;
  border:1px solid var(--border);
}

table{
  width:100%;
  border-collapse:collapse;
  min-width:650px;
}

th,td{
  padding:12px 14px;
  border-bottom:1px solid var(--border);
  text-align:left;
}

th{
  background:#eef5fb;
  color:var(--dark);
}

.badge{
  display:inline-block;
  padding:4px 9px;
  border-radius:20px;
  font-size:12px;
  font-weight:bold;
  background:#e9ecef;
}

.badge-blue{
  background:#dceeff;
  color:#0757a0;
}

.badge-green{
  background:#dff5e8;
  color:#146c43;
}

.badge-orange{
  background:#fff0d5;
  color:#996300;
}

/* NOTICES */
.notice{
  padding:13px 15px;
  border-radius:8px;
  margin-bottom:12px;
  background:#eef7ff;
  border-left:4px solid var(--blue2);
}

.notice.success{
  background:#eaf8ef;
  border-color:var(--green);
}

.notice.error{
  background:#fff0f0;
  border-color:var(--red);
}

/* FOOTER */
footer{
  background:#062c4e;
  color:white;
  text-align:center;
  padding:30px 20px;
}

/* MOBILE */
@media(max-width:800px){
  .navbar{
    align-items:flex-start;
  }

  .nav-actions{
    justify-content:flex-end;
  }

  .sidebar{
    width:100%;
    position:relative;
  }

  .app-layout{
    flex-direction:column;
  }

  .form-row{
    grid-template-columns:1fr;
  }

  .hero{
    padding:60px 20px;
  }
}
</style>
</head>

<body>

<!-- ================= PUBLIC SITE ================= -->

<div id="publicSite">

<header>
  <div class="navbar">
    <div class="logo-area">
      <div class="logo">AAEGM</div>
      <div class="logo-text">
        <strong>AAEGM Cours de Vacances</strong>
        <small>Amicale des Anciens Élèves de Gallo Malick</small>
      </div>
    </div>

    <div class="nav-actions">
      <button class="btn btn-outline btn-small" onclick="openLogin()">Connexion</button>
      <button class="btn btn-white btn-small" onclick="openRegister()">Inscription</button>
    </div>
  </div>
</header>

<section class="hero">
  <div class="hero-inner">
    <h1>AAEGM Cours de Vacances</h1>
    <p>
      Un espace éducatif pour organiser les cours de vacances,
      accompagner les apprenants et suivre leur progression.
    </p>

    <div class="hero-buttons">
      <button class="btn btn-white" onclick="openRegister('student')">
        Inscription élève
      </button>

      <button class="btn btn-primary" onclick="openRegister('teacher')">
        Inscription encadreur
      </button>

      <button class="btn btn-outline" onclick="openLogin()">
        Se connecter
      </button>
    </div>
  </div>
</section>

<section class="section">
  <h2 class="section-title">Nos fonctionnalités</h2>

  <div class="cards">
    <div class="card">
      <div class="icon">📚</div>
      <h3>Cours</h3>
      <p>Les élèves peuvent consulter les matières et les cours qui leur sont destinés.</p>
    </div>

    <div class="card">
      <div class="icon">📝</div>
      <h3>Notes</h3>
      <p>Les résultats peuvent être enregistrés et consultés depuis l'espace personnel.</p>
    </div>

    <div class="card">
      <div class="icon">👨‍🏫</div>
      <h3>Encadreurs</h3>
      <p>Les encadreurs disposent d'un espace pour suivre leurs cours et leurs apprenants.</p>
    </div>

    <div class="card">
      <div class="icon">📅</div>
      <h3>Planning</h3>
      <p>Le planning des cours permet de suivre les jours et horaires programmés.</p>
    </div>
  </div>
</section>

<section class="section">
  <h2 class="section-title">Niveaux concernés</h2>

  <div class="cards">
    <div class="card">
      <h3>Élémentaire</h3>
      <p>CI • CP • C1 • C2 • CM1 • CM2</p>
    </div>

    <div class="card">
      <h3>Collège</h3>
      <p>6e • 5e • 4e • 3e</p>
    </div>

    <div class="card">
      <h3>Lycée</h3>
      <p>Seconde • Première • Terminale</p>
    </div>
  </div>
</section>

<footer>
  <strong>AAEGM Cours de Vacances</strong>
  <p>Amicale des Anciens Élèves de Gallo Malick</p>
  <p>© 2026 — Tous droits réservés</p>
</footer>

</div>


<!-- ================= LOGIN MODAL ================= -->

<div id="loginModal" class="modal hidden">
  <div class="modal-box">

    <div class="modal-header">
      <h2>Connexion</h2>
      <button class="close" onclick="closeModal('loginModal')">×</button>
    </div>

    <div class="modal-body">

      <div id="loginMessage"></div>

      <form onsubmit="login(event)">

        <div class="form-group">
          <label>Email</label>
          <input id="loginEmail" type="email" required autocomplete="email">
        </div>

        <div class="form-group">
          <label>Mot de passe</label>
          <input id="loginPassword" type="password" required autocomplete="current-password">
        </div>

        <div class="form-actions">
          <button type="button" class="btn btn-gray" onclick="closeModal('loginModal')">
            Annuler
          </button>

          <button type="submit" class="btn btn-primary">
            Se connecter
          </button>
        </div>

      </form>

      <p style="margin-top:18px;text-align:center">
        Pas encore de compte ?
        <button onclick="closeModal('loginModal');openRegister()" style="color:#0757a0;background:none;font-weight:bold">
          S'inscrire
        </button>
      </p>

    </div>
  </div>
</div>


<!-- ================= REGISTER MODAL ================= -->

<div id="registerModal" class="modal hidden">
  <div class="modal-box">

    <div class="modal-header">
      <h2>Créer un compte</h2>
      <button class="close" onclick="closeModal('registerModal')">×</button>
    </div>

    <div class="modal-body">

      <div id="registerMessage"></div>

      <div class="role-choice">
        <button id="studentRoleBtn" type="button" onclick="setRegisterRole('student')">
          👨‍🎓 Élève
        </button>

        <button id="teacherRoleBtn" type="button" onclick="setRegisterRole('teacher')">
          👨‍🏫 Encadreur
        </button>
      </div>

      <form onsubmit="register(event)">

        <div class="form-group">
          <label>Nom complet</label>
          <input id="registerName" type="text" required>
        </div>

        <div class="form-row">

          <div class="form-group">
            <label>Email</label>
            <input id="registerEmail" type="email" required autocomplete="email">
          </div>

          <div class="form-group">
            <label>Téléphone</label>
            <input id="registerPhone" type="tel">
          </div>

        </div>

        <div class="form-group">
          <label>Mot de passe</label>
          <input id="registerPassword" type="password" minlength="6" required autocomplete="new-password">
          <small>Minimum 6 caractères.</small>
        </div>

        <div id="studentFields">

          <div class="form-row">

            <div class="form-group">
              <label>Niveau</label>

              <select id="registerLevel" onchange="updateStudentFields()">
                <option value="">Choisir</option>
                <option>CI</option>
                <option>CP</option>
                <option>C1</option>
                <option>C2</option>
                <option>CM1</option>
                <option>CM2</option>
                <option>6e</option>
                <option>5e</option>
                <option>4e</option>
                <option>3e</option>
                <option>Seconde</option>
                <option>Première</option>
                <option>Terminale</option>
              </select>
            </div>

            <div class="form-group">
              <label>Série / filière</label>

              <select id="registerStream">
                <option value="">Aucune</option>
                <option>Scientifique</option>
                <option>Littéraire</option>
              </select>
            </div>

          </div>

          <div class="form-group">
            <label>Contact parent</label>
            <input id="registerParent" type="tel">
          </div>

        </div>


        <div id="teacherFields" class="hidden">

          <div class="form-group">
            <label>Matière enseignée</label>

            <select id="registerSubject">
              <option value="">Choisir</option>
              <option>Français</option>
              <option>Mathématiques</option>
              <option>SVT</option>
              <option>Science physique</option>
              <option>Anglais</option>
              <option>Arabe</option>
              <option>Histoire</option>
              <option>Géographie</option>
            </select>
          </div>

          <div class="form-group">
            <label>Disponibilités</label>
            <textarea id="registerAvailability" rows="3"
              placeholder="Exemple : lundi matin, mercredi après-midi..."></textarea>
          </div>

        </div>


        <div class="form-actions">

          <button type="button" class="btn btn-gray"
            onclick="closeModal('registerModal')">
            Annuler
          </button>

          <button id="registerSubmit" type="submit" class="btn btn-primary">
            Créer mon compte
          </button>

        </div>

      </form>

    </div>
  </div>
</div>


<!-- ================= APPLICATION ================= -->

<div id="app" class="hidden"></div>


<script>
/* =========================================================
   SUPABASE
========================================================= */

const SUPABASE_URL =
  "https://zvzzumryonnqvqrpxgwb.supabase.co";

const SUPABASE_PUBLISHABLE_KEY =
  "sb_publishable__lCtQAyv8xBE_w8kwqgAAQ_iIfc3rdi";

let aaegmSupabase = null;
let currentUser = null;
let currentProfile = null;
let registerRole = "student";


/* =========================================================
   INITIALISATION SUPABASE
========================================================= */

function initSupabase(){

  try{

    if(!window.supabase){
      console.error("La bibliothèque Supabase n'est pas chargée.");
      return false;
    }

    aaegmSupabase = window.supabase.createClient(
      SUPABASE_URL,
      SUPABASE_PUBLISHABLE_KEY
    );

    console.log("Supabase connecté.");

    return true;

  }catch(error){

    console.error("Erreur Supabase :",error);

    return false;
  }
}


/* =========================================================
   UTILITAIRES
========================================================= */

function esc(value){

  if(value === null || value === undefined) return "";

  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");
}


function message(target,text,type=""){

  const el=document.getElementById(target);

  if(!el)return;

  el.innerHTML =
    `<div class="notice ${type}">${esc(text)}</div>`;
}


function closeModal(id){

  document.getElementById(id)?.classList.add("hidden");
}


function openLogin(){

  closeModal("registerModal");

  document.getElementById("loginModal").classList.remove("hidden");

  document.getElementById("loginMessage").innerHTML="";
}


function openRegister(role="student"){

  closeModal("loginModal");

  document.getElementById("registerModal").classList.remove("hidden");

  setRegisterRole(role);

  document.getElementById("registerMessage").innerHTML="";
}


function setRegisterRole(role){

  registerRole=role;

  const studentBtn=document.getElementById("studentRoleBtn");
  const teacherBtn=document.getElementById("teacherRoleBtn");

  studentBtn.classList.toggle("active",role==="student");
  teacherBtn.classList.toggle("active",role==="teacher");

  document
    .getElementById("studentFields")
    .classList.toggle("hidden",role!=="student");

  document
    .getElementById("teacherFields")
    .classList.toggle("hidden",role!=="teacher");

  document.getElementById("registerLevel").required =
    role==="student";

  document.getElementById("registerSubject").required =
    role==="teacher";
}


function updateStudentFields(){

  const level=document.getElementById("registerLevel").value;

  const stream=document.getElementById("registerStream");

  if(["Seconde","Première","Terminale"].includes(level)){
    stream.disabled=false;
  }else{
    stream.value="";
    stream.disabled=true;
  }
}


/* =========================================================
   INSCRIPTION
========================================================= */

async function register(event){

  event.preventDefault();

  if(!aaegmSupabase){
    message(
      "registerMessage",
      "La connexion à Supabase n'est pas disponible.",
      "error"
    );
    return;
  }

  const button=document.getElementById("registerSubmit");

  button.disabled=true;
  button.textContent="Création du compte...";

  try{

    const name=document.getElementById("registerName").value.trim();
    const email=document.getElementById("registerEmail").value.trim();
    const password=document.getElementById("registerPassword").value;

    const phone=document.getElementById("registerPhone").value.trim();

    const level=document.getElementById("registerLevel").value;
    const stream=document.getElementById("registerStream").value;
    const parent=document.getElementById("registerParent").value.trim();

    const subject=document.getElementById("registerSubject").value;
    const availability=
      document.getElementById("registerAvailability").value.trim();


    const metadata={
      full_name:name,
      role:registerRole,
      phone:phone,
      level:registerRole==="student"?level:null,
      stream:registerRole==="student"?stream:null,
      subject:registerRole==="teacher"?subject:null,
      availability:registerRole==="teacher"?availability:null,
      parent_contact:registerRole==="student"?parent:null
    };


    const {data,error}=await aaegmSupabase.auth.signUp({

      email,
      password,

      options:{
        data:metadata
      }

    });


    if(error) throw error;

    if(!data.user){
      throw new Error("Supabase n'a pas créé l'utilisateur.");
    }


    /*
      Si la confirmation email est désactivée,
      une session est immédiatement disponible.
    */

    if(data.session){

      await createOrUpdateProfile(
        data.user,
        metadata
      );

      currentUser=data.user;

      await loadCurrentProfile();

      closeModal("registerModal");

      showApp();

      return;
    }


    /*
      Si Supabase demande une confirmation email,
      le compte Auth est créé mais la session n'est pas encore ouverte.
    */

    message(
      "registerMessage",
      "Compte créé. Vérifie ton adresse email puis connecte-toi avec ton email et ton mot de passe.",
      "success"
    );

  }catch(error){

    console.error("Erreur inscription :",error);

    message(
      "registerMessage",
      translateSupabaseError(error),
      "error"
    );

  }finally{

    button.disabled=false;
    button.textContent="Créer mon compte";
  }
}


/* =========================================================
   PROFIL
========================================================= */

async function createOrUpdateProfile(user,metadata){

  if(!aaegmSupabase || !user)return null;

  const profile={

    id:user.id,

    full_name:
      metadata.full_name ||
      user.user_metadata?.full_name ||
      "",

    email:user.email,

    role:
      metadata.role ||
      user.user_metadata?.role ||
      "student",

    phone:metadata.phone || null,

    level:metadata.level || null,

    stream:metadata.stream || null,

    subject:metadata.subject || null,

    availability:metadata.availability || null,

    parent_contact:metadata.parent_contact || null
  };


  const {data,error}=await aaegmSupabase
    .from("profiles")
    .upsert(profile,{onConflict:"id"})
    .select()
    .single();


  if(error){

    console.warn("Profil non enregistré :",error);

    return null;
  }

  return data;
}


/* =========================================================
   CONNEXION
========================================================= */

async function login(event){

  event.preventDefault();

  if(!aaegmSupabase){

    message(
      "loginMessage",
      "Supabase n'est pas initialisé.",
      "error"
    );

    return;
  }

  const email=document.getElementById("loginEmail").value.trim();
  const password=document.getElementById("loginPassword").value;

  const button=event.submitter;

  if(button){
    button.disabled=true;
    button.textContent="Connexion...";
  }

  try{

    const {data,error}=
      await aaegmSupabase.auth.signInWithPassword({
        email,
        password
      });

    if(error)throw error;

    currentUser=data.user;

    await loadCurrentProfile();

    closeModal("loginModal");

    showApp();

  }catch(error){

    console.error(error);

    message(
      "loginMessage",
      translateSupabaseError(error),
      "error"
    );

  }finally{

    if(button){

      button.disabled=false;
      button.textContent="Se connecter";
    }
  }
}


/* =========================================================
   CHARGER PROFIL
========================================================= */

async function loadCurrentProfile(){

  if(!aaegmSupabase || !currentUser)return null;

  try{

    let {data,error}=await aaegmSupabase
      .from("profiles")
      .select("*")
      .eq("id",currentUser.id)
      .maybeSingle();


    /*
      Si le profil n'existe pas encore,
      on utilise les métadonnées enregistrées lors de l'inscription.
    */

    if(!data){

      const metadata=currentUser.user_metadata || {};

      data=await createOrUpdateProfile(
        currentUser,
        {
          full_name:metadata.full_name,
          role:metadata.role || "student",
          phone:metadata.phone,
          level:metadata.level,
          stream:metadata.stream,
          subject:metadata.subject,
          availability:metadata.availability,
          parent_contact:metadata.parent_contact
        }
      );

    }

    if(!data){

      currentProfile={
        id:currentUser.id,
        email:currentUser.email,
        full_name:currentUser.user_metadata?.full_name || currentUser.email,
        role:currentUser.user_metadata?.role || "student"
      };

    }else{

      currentProfile=data;
    }

    return currentProfile;

  }catch(error){

    console.error("Profil :",error);

    currentProfile={
      id:currentUser.id,
      email:currentUser.email,
      full_name:currentUser.email,
      role:currentUser.user_metadata?.role || "student"
    };

    return currentProfile;
  }
}


/* =========================================================
   AFFICHAGE APPLICATION
========================================================= */

function showApp(){

  document.getElementById("publicSite").classList.add("hidden");

  const app=document.getElementById("app");

  app.classList.remove("hidden");

  buildApplication();

  showPanel("dashboard");
}


/* =========================================================
   STRUCTURE APP
========================================================= */

function buildApplication(){

  const role=currentProfile?.role || "student";

  let menu="";

  menu+=`
    <button onclick="showPanel('dashboard')" data-panel="dashboard">
      🏠 Tableau de bord
    </button>
  `;


  if(role==="admin"){

    menu+=`
      <button onclick="showPanel('teachers')" data-panel="teachers">
        👨‍🏫 Encadreurs
      </button>

      <button onclick="showPanel('students')" data-panel="students">
        👨‍🎓 Élèves
      </button>

      <button onclick="showPanel('courses')" data-panel="courses">
        📅 Cours & planning
      </button>

      <button onclick="showPanel('grades')" data-panel="grades">
        📝 Notes
      </button>

      <button onclick="showPanel('notifications')" data-panel="notifications">
        🔔 Notifications
      </button>
    `;

  }else if(role==="teacher"){

    menu+=`
      <button onclick="showPanel('profile')" data-panel="profile">
        👤 Mon profil
      </button>

      <button onclick="showPanel('courses')" data-panel="courses">
        📅 Mes cours
      </button>

      <button onclick="showPanel('grades')" data-panel="grades">
        📝 Mes notes
      </button>

      <button onclick="showPanel('notifications')" data-panel="notifications">
        🔔 Notifications
      </button>
    `;

  }else{

    menu+=`
      <button onclick="showPanel('profile')" data-panel="profile">
        👤 Mon profil
      </button>

      <button onclick="showPanel('courses')" data-panel="courses">
        📚 Mes cours
      </button>

      <button onclick="showPanel('grades')" data-panel="grades">
        📝 Mes notes
      </button>

      <button onclick="showPanel('notifications')" data-panel="notifications">
        🔔 Notifications
      </button>
    `;
  }


  document.getElementById("app").innerHTML=`

    <div class="app-layout">

      <aside class="sidebar">

        <div class="sidebar-user">

          <strong>${esc(currentProfile?.full_name || currentUser?.email)}</strong>

          <small>
            ${esc(roleLabel(role))}
          </small>

        </div>

        ${menu}

        <button onclick="logout()">
          🚪 Déconnexion
        </button>

      </aside>


      <main class="main-content">

        <div id="panel"></div>

      </main>

    </div>
  `;
}


function roleLabel(role){

  if(role==="admin")return"Administrateur";
  if(role==="teacher")return"Encadreur";
  return"Élève";
}


/* =========================================================
   PANELS
========================================================= */

async function showPanel(panel){

  document
    .querySelectorAll(".sidebar button[data-panel]")
    .forEach(btn=>{
      btn.classList.toggle(
        "active",
        btn.dataset.panel===panel
      );
    });


  const container=document.getElementById("panel");

  if(!container)return;

  container.innerHTML=
    `<div class="card"><p>Chargement...</p></div>`;


  try{

    if(panel==="dashboard")
      await dashboardPanel();

    else if(panel==="profile")
      await profilePanel();

    else if(panel==="teachers")
      await teachersPanel();

    else if(panel==="students")
      await studentsPanel();

    else if(panel==="courses")
      await coursesPanel();

    else if(panel==="grades")
      await gradesPanel();

    else if(panel==="notifications")
      await notificationsPanel();

  }catch(error){

    console.error(error);

    container.innerHTML=`
      <div class="notice error">
        Une erreur est survenue lors du chargement.
      </div>
    `;
  }
}


/* =========================================================
   DASHBOARD
========================================================= */

async function dashboardPanel(){

  const role=currentProfile?.role;

  if(role==="admin"){

    const profiles=await safeSelect("profiles","id,role");

    const students=
      profiles.filter(x=>x.role==="student").length;

    const teachers=
      profiles.filter(x=>x.role==="teacher").length;

    const admins=
      profiles.filter(x=>x.role==="admin").length;


    const courses=await safeSelect("courses","id");

    const grades=await safeSelect("grades","id");


    document.getElementById("panel").innerHTML=`

      <div class="page-title">
        <h1>Tableau de bord administrateur</h1>
        <p>Bienvenue ${esc(currentProfile.full_name)}.</p>
      </div>

      <div class="stats">

        <div class="stat">
          <div class="stat-number">${students}</div>
          <div class="stat-label">Élèves</div>
        </div>

        <div class="stat">
          <div class="stat-number">${teachers}</div>
          <div class="stat-label">Encadreurs</div>
        </div>

        <div class="stat">
          <div class="stat-number">${courses.length}</div>
          <div class="stat-label">Cours programmés</div>
        </div>

        <div class="stat">
          <div class="stat-number">${grades.length}</div>
          <div class="stat-label">Notes enregistrées</div>
        </div>

      </div>

      <div class="card">

        <h3>Administration AAEGM</h3>

        <p style="margin-top:10px">
          Utilise le menu à gauche pour gérer les élèves,
          les encadreurs, les cours, les notes et les notifications.
        </p>

      </div>
    `;

    return;
  }


  if(role==="teacher"){

    const courses=await safeSelect(
      "courses",
      "*",
      q=>q.eq("teacher_id",currentUser.id)
    );

    const grades=await safeSelect(
      "grades",
      "*",
      q=>q.eq("teacher_id",currentUser.id)
    );


    document.getElementById("panel").innerHTML=`

      <div class="page-title">
        <h1>Bonjour ${esc(currentProfile.full_name)}</h1>
        <p>Espace encadreur</p>
      </div>

      <div class="stats">

        <div class="stat">
          <div class="stat-number">${courses.length}</div>
          <div class="stat-label">Mes cours</div>
        </div>

        <div class="stat">
          <div class="stat-number">${grades.length}</div>
          <div class="stat-label">Notes saisies</div>
        </div>

      </div>

      <div class="card">
        <h3>Votre espace encadreur</h3>
        <p style="margin-top:10px">
          Consultez votre planning et gérez les notes de vos élèves.
        </p>
      </div>
    `;

    return;
  }


  const courses=await safeSelect(
    "courses",
    "*",
    q=>q.eq("level",currentProfile?.level || "")
  );

  const grades=await safeSelect(
    "grades",
    "*",
    q=>q.eq("student_id",currentUser.id)
  );


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Bonjour ${esc(currentProfile.full_name)}</h1>
      <p>Votre espace élève</p>
    </div>

    <div class="stats">

      <div class="stat">
        <div class="stat-number">${courses.length}</div>
        <div class="stat-label">Cours disponibles</div>
      </div>

      <div class="stat">
        <div class="stat-number">${grades.length}</div>
        <div class="stat-label">Notes</div>
      </div>

    </div>

    <div class="card">
      <h3>Mon niveau</h3>
      <p style="margin-top:8px">
        ${esc(currentProfile.level || "Non renseigné")}
        ${currentProfile.stream ? " — "+esc(currentProfile.stream) : ""}
      </p>
    </div>
  `;
}


/* =========================================================
   PROFIL
========================================================= */

async function profilePanel(){

  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Mon profil</h1>
    </div>

    <div class="card">

      <div id="profileMessage"></div>

      <form onsubmit="saveProfile(event)">

        <div class="form-group">
          <label>Nom complet</label>
          <input id="profileName"
            value="${esc(currentProfile.full_name || "")}"
            required>
        </div>

        <div class="form-group">
          <label>Email</label>
          <input value="${esc(currentProfile.email || currentUser.email)}"
            disabled>
        </div>

        <div class="form-group">
          <label>Téléphone</label>
          <input id="profilePhone"
            value="${esc(currentProfile.phone || "")}">
        </div>

        ${
          currentProfile.role==="student"
          ?
          `
          <div class="form-row">

            <div class="form-group">
              <label>Niveau</label>

              <select id="profileLevel">
                ${levelOptions(currentProfile.level)}
              </select>
            </div>

            <div class="form-group">
              <label>Série / filière</label>

              <select id="profileStream">
                <option value="">Aucune</option>
                <option ${currentProfile.stream==="Scientifique"?"selected":""}>
                  Scientifique
                </option>
                <option ${currentProfile.stream==="Littéraire"?"selected":""}>
                  Littéraire
                </option>
              </select>
            </div>

          </div>

          <div class="form-group">
            <label>Contact parent</label>
            <input id="profileParent"
              value="${esc(currentProfile.parent_contact || "")}">
          </div>
          `
          :
          `
          <div class="form-group">
            <label>Matière</label>
            <input id="profileSubject"
              value="${esc(currentProfile.subject || "")}">
          </div>

          <div class="form-group">
            <label>Disponibilités</label>
            <textarea id="profileAvailability">${esc(currentProfile.availability || "")}</textarea>
          </div>
          `
        }

        <button class="btn btn-primary">
          Enregistrer
        </button>

      </form>

    </div>
  `;
}


function levelOptions(selected){

  const levels=[
    "CI","CP","C1","C2","CM1","CM2",
    "6e","5e","4e","3e",
    "Seconde","Première","Terminale"
  ];

  return `<option value="">Choisir</option>`+
    levels.map(level=>
      `<option ${selected===level?"selected":""}>${level}</option>`
    ).join("");
}


async function saveProfile(event){

  event.preventDefault();

  const profile={
    full_name:document.getElementById("profileName").value.trim(),
    phone:document.getElementById("profilePhone").value.trim()
  };


  if(currentProfile.role==="student"){

    profile.level=
      document.getElementById("profileLevel").value;

    profile.stream=
      document.getElementById("profileStream").value;

    profile.parent_contact=
      document.getElementById("profileParent").value.trim();

  }else{

    profile.subject=
      document.getElementById("profileSubject").value.trim();

    profile.availability=
      document.getElementById("profileAvailability").value.trim();
  }


  const {data,error}=await aaegmSupabase
    .from("profiles")
    .update(profile)
    .eq("id",currentUser.id)
    .select()
    .single();


  if(error){

    message(
      "profileMessage",
      "Impossible d'enregistrer le profil : "+error.message,
      "error"
    );

    return;
  }


  currentProfile=data;

  message(
    "profileMessage",
    "Profil enregistré avec succès.",
    "success"
  );

  buildApplication();
  showPanel("profile");
}


/* =========================================================
   ENCADREURS
========================================================= */

async function teachersPanel(){

  const teachers=await safeSelect(
    "profiles",
    "*",
    q=>q.eq("role","teacher")
  );


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Encadreurs</h1>
      <p>Liste des encadreurs inscrits.</p>
    </div>

    <div class="table-container">

      <table>

        <thead>
          <tr>
            <th>Nom</th>
            <th>Email</th>
            <th>Téléphone</th>
            <th>Matière</th>
            <th>Disponibilités</th>
          </tr>
        </thead>

        <tbody>

          ${
            teachers.length
            ?
            teachers.map(t=>`

              <tr>
                <td>${esc(t.full_name)}</td>
                <td>${esc(t.email)}</td>
                <td>${esc(t.phone || "-")}</td>
                <td>
                  <span class="badge badge-blue">
                    ${esc(t.subject || "-")}
                  </span>
                </td>
                <td>${esc(t.availability || "-")}</td>
              </tr>

            `).join("")
            :
            `<tr><td colspan="5">Aucun encadreur.</td></tr>`
          }

        </tbody>

      </table>

    </div>
  `;
}


/* =========================================================
   ELEVES
========================================================= */

async function studentsPanel(){

  const students=await safeSelect(
    "profiles",
    "*",
    q=>q.eq("role","student")
  );


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Élèves</h1>
      <p>Liste des élèves inscrits.</p>
    </div>

    <div class="table-container">

      <table>

        <thead>
          <tr>
            <th>Nom</th>
            <th>Email</th>
            <th>Niveau</th>
            <th>Série</th>
            <th>Téléphone</th>
            <th>Parent</th>
          </tr>
        </thead>

        <tbody>

          ${
            students.length
            ?
            students.map(s=>`

              <tr>
                <td>${esc(s.full_name)}</td>
                <td>${esc(s.email)}</td>
                <td>
                  <span class="badge badge-blue">
                    ${esc(s.level || "-")}
                  </span>
                </td>
                <td>${esc(s.stream || "-")}</td>
                <td>${esc(s.phone || "-")}</td>
                <td>${esc(s.parent_contact || "-")}</td>
              </tr>

            `).join("")
            :
            `<tr><td colspan="6">Aucun élève.</td></tr>`
          }

        </tbody>

      </table>

    </div>
  `;
}


/* =========================================================
   COURS
========================================================= */

async function coursesPanel(){

  let courses=[];


  if(currentProfile.role==="admin"){

    courses=await safeSelect("courses","*");

  }else if(currentProfile.role==="teacher"){

    courses=await safeSelect(
      "courses",
      "*",
      q=>q.eq("teacher_id",currentUser.id)
    );

  }else{

    courses=await safeSelect(
      "courses",
      "*",
      q=>q.eq("level",currentProfile.level || "")
    );

    if(currentProfile.stream){

      courses=courses.filter(c=>
        !c.stream ||
        c.stream===currentProfile.stream
      );
    }
  }


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>
        ${currentProfile.role==="admin"?"Cours & planning":"Mes cours"}
      </h1>
    </div>

    ${
      currentProfile.role==="admin"
      ?
      `
      <div class="card" style="margin-bottom:20px">

        <h3>Programmer un cours</h3>

        <form onsubmit="saveCourse(event)" style="margin-top:15px">

          <div class="form-row">

            <div class="form-group">
              <label>Encadreur</label>
              <select id="courseTeacher" required>
                <option value="">Choisir</option>
                ${await teacherOptions()}
              </select>
            </div>

            <div class="form-group">
              <label>Niveau</label>
              <select id="courseLevel" required>
                ${levelOptions("")}
              </select>
            </div>

          </div>

          <div class="form-row">

            <div class="form-group">
              <label>Série / filière</label>
              <select id="courseStream">
                <option value="">Aucune</option>
                <option>Scientifique</option>
                <option>Littéraire</option>
              </select>
            </div>

            <div class="form-group">
              <label>Matière</label>

              <select id="courseSubject" required>
                <option value="">Choisir</option>
                <option>Français</option>
                <option>Mathématiques</option>
                <option>SVT</option>
                <option>Science physique</option>
                <option>Anglais</option>
                <option>Arabe</option>
                <option>Histoire</option>
                <option>Géographie</option>
              </select>

            </div>

          </div>

          <div class="form-row">

            <div class="form-group">
              <label>Jour</label>
              <select id="courseDay" required>
                <option>Lundi</option>
                <option>Mardi</option>
                <option>Mercredi</option>
                <option>Jeudi</option>
                <option>Vendredi</option>
                <option>Samedi</option>
                <option>Dimanche</option>
              </select>
            </div>

            <div class="form-group">
              <label>Date</label>
              <input id="courseDate" type="date">
            </div>

          </div>

          <div class="form-row">

            <div class="form-group">
              <label>Heure début</label>
              <input id="courseStart" type="time" required>
            </div>

            <div class="form-group">
              <label>Heure fin</label>
              <input id="courseEnd" type="time" required>
            </div>

          </div>

          <div class="form-row">

            <div class="form-group">
              <label>Salle</label>
              <input id="courseRoom">
            </div>

            <div class="form-group">
              <label>Description</label>
              <input id="courseDescription">
            </div>

          </div>

          <button class="btn btn-primary">
            Programmer le cours
          </button>

        </form>

        <div id="courseMessage" style="margin-top:15px"></div>

      </div>
      `
      :
      ""
    }


    <div class="table-container">

      <table>

        <thead>
          <tr>
            <th>Niveau</th>
            <th>Série</th>
            <th>Matière</th>
            <th>Jour</th>
            <th>Horaire</th>
            <th>Date</th>
            <th>Salle</th>
          </tr>
        </thead>

        <tbody>

          ${
            courses.length
            ?
            courses.map(c=>`

              <tr>

                <td>${esc(c.level)}</td>

                <td>${esc(c.stream || "-")}</td>

                <td>
                  <span class="badge badge-blue">
                    ${esc(c.subject)}
                  </span>
                </td>

                <td>${esc(c.day)}</td>

                <td>
                  ${esc(c.start_time || "")}
                  -
                  ${esc(c.end_time || "")}
                </td>

                <td>${esc(c.course_date || "-")}</td>

                <td>${esc(c.room || "-")}</td>

              </tr>

            `).join("")
            :
            `<tr><td colspan="7">Aucun cours programmé.</td></tr>`
          }

        </tbody>

      </table>

    </div>
  `;
}


async function teacherOptions(){

  const teachers=await safeSelect(
    "profiles",
    "id,full_name,subject",
    q=>q.eq("role","teacher")
  );

  return teachers.map(t=>
    `<option value="${esc(t.id)}">
      ${esc(t.full_name)}${t.subject?" — "+esc(t.subject):""}
    </option>`
  ).join("");
}


async function saveCourse(event){

  event.preventDefault();

  const course={

    teacher_id:document.getElementById("courseTeacher").value,

    level:document.getElementById("courseLevel").value,

    stream:document.getElementById("courseStream").value || null,

    subject:document.getElementById("courseSubject").value,

    day:document.getElementById("courseDay").value,

    start_time:document.getElementById("courseStart").value,

    end_time:document.getElementById("courseEnd").value,

    room:document.getElementById("courseRoom").value.trim() || null,

    course_date:document.getElementById("courseDate").value || null,

    description:
      document.getElementById("courseDescription").value.trim() || null
  };


  const {data,error}=await aaegmSupabase
    .from("courses")
    .insert(course)
    .select()
    .single();


  if(error){

    message(
      "courseMessage",
      "Erreur : "+error.message,
      "error"
    );

    return;
  }


  message(
    "courseMessage",
    "Cours programmé avec succès.",
    "success"
  );


  await sendNotification(
    course.teacher_id,
    "Nouveau cours programmé",
    `Votre cours de ${course.subject} est programmé ${course.day} de ${course.start_time} à ${course.end_time}.`,
    "course"
  );


  setTimeout(()=>{
    showPanel("courses");
  },700);
}


/* =========================================================
   NOTES
========================================================= */

async function gradesPanel(){

  let grades=[];


  if(currentProfile.role==="student"){

    grades=await safeSelect(
      "grades",
      "*",
      q=>q.eq("student_id",currentUser.id)
    );

  }else if(currentProfile.role==="teacher"){

    grades=await safeSelect(
      "grades",
      "*",
      q=>q.eq("teacher_id",currentUser.id)
    );

  }else{

    grades=await safeSelect("grades","*");
  }


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Notes</h1>
    </div>

    ${
      currentProfile.role==="teacher" ||
      currentProfile.role==="admin"
      ?
      `
      <div class="card" style="margin-bottom:20px">

        <h3>Ajouter une note</h3>

        <form onsubmit="saveGrade(event)" style="margin-top:15px">

          <div class="form-row">

            <div class="form-group">
              <label>Élève</label>

              <select id="gradeStudent" required>
                <option value="">Choisir</option>
                ${await studentOptions()}
              </select>

            </div>

            <div class="form-group">
              <label>Matière</label>

              <select id="gradeSubject" required>
                <option>Français</option>
                <option>Mathématiques</option>
                <option>SVT</option>
                <option>Science physique</option>
                <option>Anglais</option>
                <option>Arabe</option>
                <option>Histoire</option>
                <option>Géographie</option>
              </select>

            </div>

          </div>

          <div class="form-row">

            <div class="form-group">
              <label>Évaluation</label>
              <input id="gradeTitle" required
                placeholder="Ex : Devoir 1">
            </div>

            <div class="form-group">
              <label>Note /20</label>
              <input id="gradeScore"
                type="number"
                min="0"
                max="20"
                step="0.01"
                required>
            </div>

          </div>

          <div class="form-group">
            <label>Coefficient</label>
            <input id="gradeCoefficient"
              type="number"
              min="0.1"
              step="0.1"
              value="1">
          </div>

          <div id="gradeMessage"></div>

          <button class="btn btn-primary">
            Enregistrer la note
          </button>

        </form>

      </div>
      `
      :
      ""
    }


    <div class="table-container">

      <table>

        <thead>
          <tr>
            <th>Élève</th>
            <th>Matière</th>
            <th>Évaluation</th>
            <th>Note</th>
            <th>Coefficient</th>
          </tr>
        </thead>

        <tbody>

          ${
            grades.length
            ?
            grades.map(g=>`

              <tr>
                <td>${esc(g.student_id)}</td>
                <td>${esc(g.subject)}</td>
                <td>${esc(g.title)}</td>
                <td>
                  <strong>${esc(g.score)}/20</strong>
                </td>
                <td>${esc(g.coefficient || 1)}</td>
              </tr>

            `).join("")
            :
            `<tr><td colspan="5">Aucune note.</td></tr>`
          }

        </tbody>

      </table>

    </div>
  `;
}


async function studentOptions(){

  const students=await safeSelect(
    "profiles",
    "id,full_name,level",
    q=>q.eq("role","student")
  );

  return students.map(s=>
    `<option value="${esc(s.id)}">
      ${esc(s.full_name)}${s.level?" — "+esc(s.level):""}
    </option>`
  ).join("");
}


async function saveGrade(event){

  event.preventDefault();


  const teacherId=
    currentProfile.role==="teacher"
      ? currentUser.id
      : null;


  const grade={

    student_id:
      document.getElementById("gradeStudent").value,

    teacher_id:teacherId,

    subject:
      document.getElementById("gradeSubject").value,

    title:
      document.getElementById("gradeTitle").value.trim(),

    score:
      Number(document.getElementById("gradeScore").value),

    coefficient:
      Number(document.getElementById("gradeCoefficient").value) || 1
  };


  const {error}=await aaegmSupabase
    .from("grades")
    .insert(grade);


  if(error){

    message(
      "gradeMessage",
      "Erreur : "+error.message,
      "error"
    );

    return;
  }


  message(
    "gradeMessage",
    "Note enregistrée avec succès.",
    "success"
  );


  await sendNotification(
    grade.student_id,
    "Nouvelle note",
    `Une note de ${grade.score}/20 en ${grade.subject} a été enregistrée.`,
    "grade"
  );


  setTimeout(()=>{
    showPanel("grades");
  },700);
}


/* =========================================================
   NOTIFICATIONS
========================================================= */

async function notificationsPanel(){

  const notifications=await safeSelect(
    "notifications",
    "*",
    q=>q.eq("user_id",currentUser.id)
  );


  document.getElementById("panel").innerHTML=`

    <div class="page-title">
      <h1>Notifications</h1>
    </div>

    <div>

      ${
        notifications.length
        ?
        notifications
          .sort((a,b)=>
            new Date(b.created_at || 0) -
            new Date(a.created_at || 0)
          )
          .map(n=>`

            <div class="notice ${n.read?"":"success"}">

              <strong>${esc(n.title)}</strong>

              <p>${esc(n.message)}</p>

              <small>
                ${esc(n.created_at || "")}
              </small>

            </div>

          `).join("")
        :
        `
        <div class="card">
          <p>Aucune notification.</p>
        </div>
        `
      }

    </div>
  `;


  await markNotificationsRead();
}


async function sendNotification(userId,title,msg,type="info"){

  if(!userId)return;

  try{

    await aaegmSupabase
      .from("notifications")
      .insert({

        user_id:userId,
        title:title,
        message:msg,
        type:type,
        read:false
      });

  }catch(error){

    console.warn(
      "Notification non envoyée :",
      error
    );
  }
}


async function markNotificationsRead(){

  try{

    await aaegmSupabase
      .from("notifications")
      .update({read:true})
      .eq("user_id",currentUser.id)
      .eq("read",false);

  }catch(error){

    console.warn(error);
  }
}


/* =========================================================
   OUTILS SUPABASE
========================================================= */

async function safeSelect(table,columns="*",modifier=null){

  try{

    let query=aaegmSupabase
      .from(table)
      .select(columns);

    if(modifier){
      query=modifier(query);
    }

    const {data,error}=await query;

    if(error){

      console.warn(
        `Table ${table} :`,
        error.message
      );

      return [];
    }

    return data || [];

  }catch(error){

    console.error(error);

    return [];
  }
}


/* =========================================================
   DECONNEXION
========================================================= */

async function logout(){

  try{

    await aaegmSupabase.auth.signOut();

  }catch(error){

    console.warn(error);

  }finally{

    currentUser=null;
    currentProfile=null;

    document.getElementById("app").classList.add("hidden");

    document.getElementById("publicSite").classList.remove("hidden");
  }
}


/* =========================================================
   ERREURS SUPABASE
========================================================= */

function translateSupabaseError(error){

  const text=(error?.message || "").toLowerCase();

  if(text.includes("invalid login credentials")){
    return "Email ou mot de passe incorrect.";
  }

  if(text.includes("email not confirmed")){
    return "Ton adresse email n'est pas encore confirmée.";
  }

  if(text.includes("user already registered")){
    return "Cette adresse email possède déjà un compte.";
  }

  if(text.includes("password")){
    return "Le mot de passe doit contenir au moins 6 caractères.";
  }

  if(text.includes("rate limit")){
    return "Trop de tentatives. Réessaie plus tard.";
  }

  return error?.message ||
    "Une erreur est survenue.";
}


/* =========================================================
   INITIALISATION
========================================================= */

async function startApplication(){

  if(!initSupabase()){

    console.error(
      "Impossible d'initialiser Supabase."
    );

    return;
  }


  try{

    const {
      data:{
        session
      }
    }=await aaegmSupabase.auth.getSession();


    if(session?.user){

      currentUser=session.user;

      await loadCurrentProfile();

      showApp();

    }

  }catch(error){

    console.error(
      "Erreur restauration session :",
      error
    );
  }


  aaegmSupabase.auth.onAuthStateChange(
    async (event,session)=>{

      if(session?.user){

        currentUser=session.user;

        /*
          On ne reconstruit pas inutilement l'interface
          pendant les événements internes de Supabase.
        */

        if(event==="SIGNED_IN"){

          await loadCurrentProfile();

          showApp();
        }

      }else if(event==="SIGNED_OUT"){

        currentUser=null;
        currentProfile=null;

        document.getElementById("app").classList.add("hidden");

        document
          .getElementById("publicSite")
          .classList.remove("hidden");
      }
    }
  );
}


document.addEventListener(
  "DOMContentLoaded",
  startApplication
);


/* Fermer les fenêtres en cliquant à l'extérieur */

document.addEventListener("click",function(event){

  if(event.target.classList.contains("modal")){

    event.target.classList.add("hidden");
  }
});
</script>

</body>
</html>
