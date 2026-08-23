/**
 * PharmaLink — création automatique des deux formulaires d'enquête.
 *
 * MODE D'EMPLOI
 *  1. Va sur https://script.google.com → Nouveau projet.
 *  2. Efface le contenu par défaut, colle TOUT ce fichier.
 *  3. En haut, choisis la fonction "creerLesDeuxFormulaires" puis clique Exécuter.
 *  4. Google demande une autorisation la première fois :
 *     "Avancé" → "Accéder à <ton projet> (non sécurisé)" → Autoriser.
 *     (C'est ton propre script sur ton propre compte, rien ne sort de ton Drive.)
 *  5. Le journal d'exécution affiche, en bas :
 *       - les liens des deux formulaires (édition + diffusion)
 *       - le bloc de configuration à coller dans index.html
 *
 * Les deux formulaires sont créés dans la racine de ton Google Drive.
 */

function creerLesDeuxFormulaires() {
  var patients    = creerFormulairePatients();
  var pharmaciens = creerFormulairePharmaciens();

  var bloc = [
    '',
    '════════════════════════════════════════════════════════════',
    '  À COLLER DANS index.html — remplace la constante FORMS',
    '════════════════════════════════════════════════════════════',
    '',
    '  var FORMS = {',
    '    patient: {',
    '      url: "' + patients.url + '",',
    '      entrySource: "' + patients.entry + '"',
    '    },',
    '    pharmacien: {',
    '      url: "' + pharmaciens.url + '",',
    '      entrySource: "' + pharmaciens.entry + '"',
    '    }',
    '  };',
    '',
    '  Et dans les deux balises <a data-profil="…"> plus haut dans la page,',
    '  remplace le href par la même url (sans paramètre).',
    '',
    '════════════════════════════════════════════════════════════',
    '  LIENS D\'ÉDITION (pour relire et retoucher)',
    '════════════════════════════════════════════════════════════',
    '',
    '  Patients    : ' + patients.edit,
    '  Officines   : ' + pharmaciens.edit,
    ''
  ].join('\n');

  Logger.log(bloc);
  return bloc;
}

/* ══════════════════════════════════════════════════════════════
   FORMULAIRE PATIENTS
   ══════════════════════════════════════════════════════════════ */

function creerFormulairePatients() {
  var f = FormApp.create('Trouver un médicament à Dakar — votre expérience');

  f.setDescription(
    'Nous préparons un service d\'information sur la disponibilité des ' +
    'médicaments en officine. Vos réponses nous aident à savoir quoi ' +
    'construire en premier.\n\n' +
    'C\'est anonyme et ça prend 2 minutes. Nous ne demandons aucune ' +
    'information sur votre santé et nous ne mettons en avant aucune pharmacie.'
  );
  f.setProgressBar(true);
  f.setCollectEmail(false);
  f.setAllowResponseEdits(false);
  f.setConfirmationMessage(
    'Merci, vos réponses sont enregistrées.\n\n' +
    'Si vous connaissez quelqu\'un que ça concerne, transférez-lui le lien : ' +
    'pharmalink.sn/enquete'
  );

  /* ---- Section : vous ---- */

  f.addMultipleChoiceItem()
    .setTitle('Dans quelle ville habitez-vous ?')
    .setChoiceValues([
      'Dakar',
      'Pikine / Guédiawaye',
      'Rufisque / Bargny',
      'Thiès',
      'Mbour / Saly',
      'Saint-Louis',
      'Touba / Mbacké',
      'Ziguinchor',
      'Kaolack'
    ])
    .showOtherOption(true)
    .setRequired(true);

  f.addTextItem()
    .setTitle('Votre quartier ou commune')
    .setHelpText('Facultatif. Ça nous aide à savoir où lancer en premier.');

  f.addMultipleChoiceItem()
    .setTitle('Votre tranche d\'âge')
    .setChoiceValues([
      'Moins de 25 ans',
      '25 – 34 ans',
      '35 – 49 ans',
      '50 – 64 ans',
      '65 ans et plus'
    ]);

  f.addCheckboxItem()
    .setTitle('En général, vous achetez des médicaments pour…')
    .setChoiceValues([
      'Vous-même',
      'Votre enfant',
      'Un parent âgé',
      'Une autre personne de la famille',
      'Vous n\'en achetez presque jamais'
    ]);

  /* ---- Section : la dernière fois ---- */

  f.addPageBreakItem()
    .setTitle('La dernière fois')
    .setHelpText(
      'Les questions suivantes portent sur la dernière fois que vous êtes allé ' +
      'chercher un médicament en pharmacie. Pas en général — cette fois-là ' +
      'précisément.'
    );

  f.addMultipleChoiceItem()
    .setTitle('C\'était quand ?')
    .setChoiceValues([
      'Cette semaine',
      'Ce mois-ci',
      'Il y a 2 à 6 mois',
      'Il y a plus de 6 mois',
      'Je ne suis jamais allé chercher un médicament moi-même'
    ])
    .setRequired(true);

  f.addMultipleChoiceItem()
    .setTitle('Vous l\'avez trouvé dans la première pharmacie ?')
    .setChoiceValues([
      'Oui, du premier coup',
      'Non, il a fallu 2 pharmacies',
      'Non, il a fallu 3 pharmacies ou plus',
      'Je ne l\'ai pas trouvé du tout ce jour-là',
      'Je ne me souviens plus'
    ])
    .setRequired(true);

  f.addMultipleChoiceItem()
    .setTitle('Au total, combien de temps ça vous a pris ?')
    .setChoiceValues([
      'Moins de 15 minutes',
      'Entre 15 et 30 minutes',
      'Entre 30 minutes et 1 heure',
      'Plus d\'une heure',
      'Plusieurs jours / plusieurs déplacements'
    ]);

  f.addMultipleChoiceItem()
    .setTitle('Il s\'agissait d\'un médicament…')
    .setChoiceValues([
      'Sur ordonnance',
      'En vente libre (sans ordonnance)',
      'Les deux',
      'Je ne sais pas'
    ]);

  f.addCheckboxItem()
    .setTitle('Si vous ne l\'avez pas trouvé tout de suite, qu\'avez-vous fait ?')
    .setChoiceValues([
      'J\'ai fait le tour d\'autres pharmacies à pied ou en voiture',
      'J\'ai appelé une ou plusieurs pharmacies',
      'J\'ai demandé à un proche de chercher de son côté',
      'Le pharmacien m\'a orienté vers une autre officine',
      'J\'ai demandé dans un groupe WhatsApp / sur Facebook',
      'J\'ai pris un autre médicament équivalent',
      'J\'ai laissé tomber',
      'Ça ne s\'est pas produit, j\'ai trouvé du premier coup'
    ]);

  f.addParagraphTextItem()
    .setTitle('En repensant à ce moment, qu\'est-ce qui a été le plus pénible ?')
    .setHelpText('Une phrase suffit.');

  /* ---- Section : en général ---- */

  f.addPageBreakItem().setTitle('En général');

  f.addMultipleChoiceItem()
    .setTitle('Ces 3 derniers mois, combien de fois avez-vous eu du mal à trouver un médicament ?')
    .setChoiceValues([
      'Jamais',
      'Une fois',
      'Deux ou trois fois',
      'Plus de trois fois'
    ])
    .setRequired(true);

  f.addMultipleChoiceItem()
    .setTitle('Vous est-il déjà arrivé de chercher une pharmacie de garde la nuit ou un jour férié ?')
    .setChoiceValues([
      'Oui, et j\'ai trouvé l\'information facilement',
      'Oui, mais l\'information était difficile à trouver ou fausse',
      'Oui, et je n\'ai pas trouvé du tout',
      'Non, jamais'
    ]);

  /* ---- Section : le service ---- */

  f.addPageBreakItem()
    .setTitle('Le service')
    .setHelpText(
      'Imaginez un service où vous tapez le nom d\'un médicament et vous voyez ' +
      'les pharmacies proches qui l\'ont en stock, avec les pharmacies de garde ' +
      'du jour. L\'information vient des pharmacies elles-mêmes.'
    );

  f.addMultipleChoiceItem()
    .setTitle('La dernière fois dont vous avez parlé plus haut, ça vous aurait aidé ?')
    .setChoiceValues([
      'Ça m\'aurait beaucoup aidé',
      'Ça m\'aurait un peu aidé',
      'Ça n\'aurait rien changé',
      'Je ne sais pas'
    ])
    .setRequired(true);

  f.addCheckboxItem()
    .setTitle('Qu\'est-ce qui vous ferait hésiter à l\'utiliser ?')
    .setChoiceValues([
      'La peur que l\'information ne soit pas à jour',
      'Je préfère appeler ou passer directement',
      'Ça consomme de la connexion / des données',
      'Je ne suis pas à l\'aise avec ce genre d\'outil',
      'Rien, je l\'utiliserais'
    ])
    .showOtherOption(true);

  f.addMultipleChoiceItem()
    .setTitle('Sous quelle forme l\'utiliseriez-vous le plus volontiers ?')
    .setChoiceValues([
      'Sur WhatsApp',
      'Un site web à ouvrir dans le navigateur',
      'Une application à installer',
      'Par SMS',
      'En appelant un numéro'
    ]);

  /* ---- Section : contact ---- */

  f.addPageBreakItem().setTitle('Rester en contact');

  f.addTextItem()
    .setTitle('Souhaitez-vous être prévenu au lancement ?')
    .setHelpText(
      'Facultatif. Laissez un numéro WhatsApp ou un e-mail. Il ne servira ' +
      'qu\'à ça et ne sera transmis à personne.'
    );

  var source = f.addTextItem()
    .setTitle('Source')
    .setHelpText('Champ technique, rempli automatiquement. Merci de ne rien écrire ici.');

  return infosFormulaire(f, source);
}

/* ══════════════════════════════════════════════════════════════
   FORMULAIRE OFFICINES
   ══════════════════════════════════════════════════════════════ */

function creerFormulairePharmaciens() {
  var f = FormApp.create('Gestion du stock en officine — 12 questions');

  f.setDescription(
    'Nous concevons un outil de suivi de stock pour les officines, couplé à ' +
    'un service d\'information sur la disponibilité des médicaments et les gardes.\n\n' +
    'Avant d\'écrire une ligne de code, nous voulons comprendre comment vous ' +
    'travaillez réellement. 2 minutes, et vos réponses restent confidentielles : ' +
    'aucune officine n\'est nommée ni comparée dans nos résultats.'
  );
  f.setProgressBar(true);
  f.setCollectEmail(false);
  f.setAllowResponseEdits(false);
  f.setConfirmationMessage(
    'Merci pour votre temps. Nous revenons vers vous si vous avez accepté un échange.'
  );

  /* ---- Section : l'officine ---- */

  f.addMultipleChoiceItem()
    .setTitle('Votre fonction')
    .setChoiceValues([
      'Pharmacien titulaire',
      'Pharmacien assistant',
      'Préparateur / assistant en pharmacie',
      'Gérant / responsable administratif'
    ])
    .showOtherOption(true)
    .setRequired(true);

  f.addTextItem()
    .setTitle('Commune ou quartier de l\'officine')
    .setRequired(true);

  f.addMultipleChoiceItem()
    .setTitle('Combien de personnes travaillent à l\'officine ?')
    .setChoiceValues(['1 à 2', '3 à 5', '6 à 10', 'Plus de 10']);

  f.addMultipleChoiceItem()
    .setTitle('L\'officine assure-t-elle des gardes ?')
    .setChoiceValues(['Oui, régulièrement', 'Oui, occasionnellement', 'Non']);

  /* ---- Section : le stock aujourd'hui ---- */

  f.addPageBreakItem().setTitle('Le stock aujourd\'hui');

  f.addCheckboxItem()
    .setTitle('Comment suivez-vous votre stock actuellement ?')
    .setChoiceValues([
      'Un logiciel de gestion d\'officine',
      'Un tableur (Excel, Google Sheets)',
      'Un cahier ou des fiches papier',
      'De mémoire, en regardant les rayons'
    ])
    .showOtherOption(true)
    .setRequired(true);

  f.addTextItem()
    .setTitle('Si vous utilisez un logiciel, lequel ?');

  f.addMultipleChoiceItem()
    .setTitle('Ce que vous avez dans le logiciel correspond-il à ce qu\'il y a réellement dans les rayons ?')
    .setChoiceValues([
      'Oui, c\'est fiable au jour le jour',
      'À peu près, avec quelques écarts',
      'Souvent décalé, il faut vérifier en rayon',
      'Nous n\'avons pas de stock informatisé'
    ])
    .setRequired(true);

  f.addParagraphTextItem()
    .setTitle('Qui met le stock à jour, et à quel moment ?')
    .setHelpText(
      'Par exemple : « le préparateur, à la réception de la commande », ou ' +
      '« personne systématiquement ».'
    );

  /* ---- Section : le quotidien ---- */

  f.addPageBreakItem().setTitle('Le quotidien');

  f.addMultipleChoiceItem()
    .setTitle('Dans une journée type, combien de fois un client demande-t-il un produit que vous n\'avez pas en stock ?')
    .setChoiceValues([
      'Rarement, moins de 5 fois',
      '5 à 15 fois',
      '15 à 30 fois',
      'Plus de 30 fois'
    ])
    .setRequired(true);

  f.addMultipleChoiceItem()
    .setTitle('Combien d\'appels téléphoniques recevez-vous par jour pour demander si un produit est disponible ?')
    .setChoiceValues([
      'Presque aucun',
      'Moins de 10',
      '10 à 30',
      'Plus de 30'
    ]);

  f.addCheckboxItem()
    .setTitle('Quand vous n\'avez pas le produit, que faites-vous le plus souvent ?')
    .setChoiceValues([
      'Je propose un équivalent',
      'J\'appelle un confrère pour vérifier',
      'J\'oriente le client vers une autre officine, sans certitude',
      'Je commande chez le grossiste pour le lendemain',
      'Je note la demande pour la prochaine commande'
    ])
    .showOtherOption(true);

  /* ---- Section : l'outil ---- */

  f.addPageBreakItem()
    .setTitle('L\'outil')
    .setHelpText(
      'L\'outil que nous concevons a deux faces : côté officine, un suivi de ' +
      'stock simplifié ; côté public, une information sur la disponibilité et ' +
      'les gardes, alimentée par les officines elles-mêmes. Le classement ' +
      'affiché au public est strictement objectif — distance, disponibilité, ' +
      'garde — sans mise en avant possible.'
    );

  f.addMultipleChoiceItem()
    .setTitle('Combien de temps par jour seriez-vous prêt à consacrer à la mise à jour du stock ?')
    .setChoiceValues([
      'Rien de plus : il faudrait que ça se fasse depuis notre logiciel existant',
      'Moins de 5 minutes',
      '5 à 15 minutes',
      'Plus de 15 minutes si le gain est réel'
    ])
    .setRequired(true);

  f.addCheckboxItem()
    .setTitle('Qu\'est-ce qui vous ferait hésiter ?')
    .setChoiceValues([
      'Le temps de saisie quotidien',
      'La crainte d\'afficher un stock faux au public',
      'Le fait de rendre visible ce que nous avons ou n\'avons pas',
      'Le coût de l\'abonnement',
      'Nous avons déjà un outil qui fait cela',
      'La formation de l\'équipe',
      'Rien de particulier'
    ])
    .showOtherOption(true);

  /* ---- Section : la suite ---- */

  f.addPageBreakItem().setTitle('La suite');

  f.addMultipleChoiceItem()
    .setTitle('Accepteriez-vous un échange de 20 minutes, à l\'officine ou par téléphone ?')
    .setChoiceValues([
      'Oui, avec plaisir',
      'Oui, mais plutôt par téléphone',
      'Peut-être plus tard',
      'Non merci'
    ])
    .setRequired(true);

  f.addTextItem()
    .setTitle('Vos coordonnées')
    .setHelpText(
      'Nom de l\'officine, numéro ou e-mail. Utilisés uniquement pour vous ' +
      'recontacter, jamais diffusés.'
    );

  var source = f.addTextItem()
    .setTitle('Source')
    .setHelpText('Champ technique, rempli automatiquement. Merci de ne rien écrire ici.');

  return infosFormulaire(f, source);
}

/* ══════════════════════════════════════════════════════════════
   OUTIL — récupère l'URL publique et l'identifiant entry.XXXX
   du champ Source, en fabriquant une réponse préremplie de test.
   ══════════════════════════════════════════════════════════════ */

function infosFormulaire(form, sourceItem) {
  var reponse = form.createResponse()
    .withItemResponse(sourceItem.asTextItem().createResponse('__test__'));

  var urlPreremplie = reponse.toPrefilledUrl();
  var trouve = urlPreremplie.match(/(entry\.\d+)=__test__/);

  return {
    titre: form.getTitle(),
    url:   form.getPublishedUrl(),
    edit:  form.getEditUrl(),
    entry: trouve ? trouve[1] : 'INTROUVABLE'
  };
}
