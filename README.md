<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AEPPCS – Formulaire d’adhésion</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f9f9f9;
      color: #333;
      line-height: 1.6;
    }

    header {
      background: #00695c;
      color: white;
      text-align: center;
      padding: 1.5rem;
    }

    header h1 {
      margin: 0;
      font-size: 1.8rem;
    }

    section {
      padding: 2rem 1rem;
      max-width: 900px;
      margin: auto;
    }

    h2 {
      color: #00695c;
      margin-bottom: 1rem;
      border-bottom: 2px solid #00695c;
      display: inline-block;
      padding-bottom: 0.3rem;
    }

    h3 {
      margin-top: 1.5rem;
      color: #444;
    }

    .form-group {
      margin-bottom: 1rem;
    }

    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: bold;
    }

    input, textarea {
      width: 100%;
      padding: 0.7rem;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 1rem;
      box-sizing: border-box;
    }

    input:focus, textarea:focus {
      border-color: #00695c;
      outline: none;
      box-shadow: 0 0 5px rgba(0, 105, 92, 0.4);
    }

    .radio-group {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
    }

    button {
      background: #00695c;
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 25px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background: #004d40;
    }

    #message-succes {
      display: none;
      background: #d4edda;
      color: #155724;
      padding: 1rem;
      border: 1px solid #c3e6cb;
      border-radius: 6px;
      margin-bottom: 1rem;
    }

    ul {
      list-style: none;
      padding-left: 0;
    }

    ul li::before {
      content: "✔ ";
      color: #00695c;
    }

    footer {
      background: #004d40;
      color: white;
      text-align: center;
      padding: 1rem;
      margin-top: 2rem;
    }

    /* Responsive */
    @media (max-width: 600px) {
      header h1 {
        font-size: 1.4rem;
      }
      section {
        padding: 1rem;
      }
      button {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>AEPPCS – Formulaire d’adhésion</h1>
  </header>

  <section id="adhesion">
    <h2>Adhésion à l’AEPPCS</h2>
    <p>Bienvenue ! Merci de remplir soigneusement ce formulaire d’adhésion.</p>

    <h3>Formulaire d’adhésion</h3>
    <div id="message-succes">
      🎉 Merci ! Votre demande a bien été envoyée. Nous vous contacterons très bientôt.
    </div>

    <form id="form-adhesion" action="https://formspree.io/f/xdklaawq" method="POST">
      <!-- Informations personnelles -->
      <h3>1. Informations personnelles</h3>
      <div class="form-group">
        <label for="prenoms">Prénoms</label>
        <input type="text" id="prenoms" name="prenoms" required>
      </div>
      <div class="form-group">
        <label for="nom">Nom</label>
        <input type="text" id="nom" name="nom" required>
      </div>
      <div class="form-group">
        <label>Sexe</label>
        <div class="radio-group">
          <label><input type="radio" name="sexe" value="Masculin" required> Masculin</label>
          <label><input type="radio" name="sexe" value="Féminin" required> Féminin</label>
        </div>
      </div>

      <!-- ... (tous les autres champs que tu avais déjà, inchangés) ... -->

      <div class="form-group">
        <button type="submit">Envoyer ma demande</button>
      </div>
    </form>

    <script>
      const form = document.getElementById("form-adhesion");
      const message = document.getElementById("message-succes");

      form.addEventListener("submit", async function (e) {
        e.preventDefault();
        const formData = new FormData(form);
        const response = await fetch(form.action, {
          method: form.method,
          body: formData,
          headers: { 'Accept': 'application/json' }
        });
        if (response.ok) {
          form.reset();
          message.style.display = "block";
          window.scrollTo(0, 0);
        } else {
          alert("Erreur lors de l'envoi. Merci de réessayer.");
        }
      });
    </script>
  </section>

  <section id="contribution">
    <h2>Contribution & Soutien</h2>
    <ul>
      <li>Montant mensuel : 500 FCFA pour les membres actifs</li>
      <li>Dons & Soutiens : via compte Wave de Fatou (trésorière) – <strong>0153121825</strong></li>
    </ul>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p><strong>Président :</strong> Kouamé Evrard</p>
    <p><strong>Téléphone :</strong> 01 42 31 36 50</p>
    <p><strong>Siège :</strong> Université de Bondoukou</p>
    <p><strong>Facebook :</strong> 
      <a href="https://www.facebook.com/profile.php?id=61571152195740" target="_blank">Aeppcs. Officiel</a>
    </p>
    <p><strong>WhatsApp :</strong> 
      <a href="https://whatsapp.com/channel/0029VawNHPJ6WaKpJc2vDP0M" target="_blank">AEPPCS. Infos</a>
    </p>
  </section>

  <footer>
    <p>© 2025 AEPPCS – Tous droits réservés</p>
  </footer>
</body>
</html>
