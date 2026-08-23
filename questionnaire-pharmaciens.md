# Enquête PharmaLink — Formulaire officines

**Cible :** pharmaciens titulaires, assistants, préparateurs, gérants
**Durée visée :** moins de 2 minutes — 12 questions
**Objectif réel :** décrocher un entretien de 20 minutes. Le formulaire n'est pas
la fin, c'est la porte d'entrée.

> Convention : `[unique]` = une réponse · `[cases]` = plusieurs réponses ·
> `[texte]` = réponse courte · **(obligatoire)** = question requise.

---

## Section 1 — Introduction (pas de question)

**Titre du formulaire :** Gestion du stock en officine — 12 questions

**Description :**

> Nous concevons un outil de suivi de stock pour les officines, couplé à un
> service d'information sur la disponibilité des médicaments et les gardes.
>
> Avant d'écrire une ligne de code, nous voulons comprendre comment vous
> travaillez réellement. 2 minutes, et vos réponses restent confidentielles :
> aucune officine n'est nommée ni comparée dans nos résultats.

---

## Section 2 — L'officine

**1. Votre fonction** `[unique]` **(obligatoire)**

- Pharmacien titulaire
- Pharmacien assistant
- Préparateur / assistant en pharmacie
- Gérant / responsable administratif
- Autre : ______

**2. Commune ou quartier de l'officine** `[texte]` **(obligatoire)**

**3. Combien de personnes travaillent à l'officine ?** `[unique]`

- 1 à 2
- 3 à 5
- 6 à 10
- Plus de 10

**4. L'officine assure-t-elle des gardes ?** `[unique]`

- Oui, régulièrement
- Oui, occasionnellement
- Non

---

## Section 3 — Le stock aujourd'hui

**5. Comment suivez-vous votre stock actuellement ?** `[cases]` **(obligatoire)**

- Un logiciel de gestion d'officine
- Un tableur (Excel, Google Sheets)
- Un cahier ou des fiches papier
- De mémoire, en regardant les rayons
- Autre : ______

**6. Si vous utilisez un logiciel, lequel ?** `[texte]`

**7. Ce que vous avez dans le logiciel correspond-il à ce qu'il y a réellement
dans les rayons ?** `[unique]` **(obligatoire)**

- Oui, c'est fiable au jour le jour
- À peu près, avec quelques écarts
- Souvent décalé, il faut vérifier en rayon
- Nous n'avons pas de stock informatisé

**8. Qui met le stock à jour, et à quel moment ?** `[texte]`

> *Par exemple : « le préparateur, à la réception de la commande », ou
> « personne systématiquement ».*

---

## Section 4 — Le quotidien

**9. Dans une journée type, combien de fois un client demande-t-il un produit que
vous n'avez pas en stock ?** `[unique]` **(obligatoire)**

- Rarement, moins de 5 fois
- 5 à 15 fois
- 15 à 30 fois
- Plus de 30 fois

**10. Combien d'appels téléphoniques recevez-vous par jour pour demander si un
produit est disponible ?** `[unique]`

- Presque aucun
- Moins de 10
- 10 à 30
- Plus de 30

**11. Quand vous n'avez pas le produit, que faites-vous le plus souvent ?**
`[cases]`

- Je propose un équivalent
- J'appelle un confrère pour vérifier
- J'oriente le client vers une autre officine, sans certitude
- Je commande chez le grossiste pour le lendemain
- Je note la demande pour la prochaine commande
- Autre : ______

---

## Section 5 — L'outil

> **Texte d'introduction de section :**
> L'outil que nous concevons a deux faces : côté officine, un suivi de stock
> simplifié ; côté public, une information sur la disponibilité et les gardes,
> alimentée par les officines elles-mêmes. Le classement affiché au public est
> strictement objectif — distance, disponibilité, garde — sans mise en avant
> possible.

**12. Combien de temps par jour seriez-vous prêt à consacrer à la mise à jour du
stock ?** `[unique]` **(obligatoire)**

- Rien de plus : il faudrait que ça se fasse depuis notre logiciel existant
- Moins de 5 minutes
- 5 à 15 minutes
- Plus de 15 minutes si le gain est réel

**13. Qu'est-ce qui vous ferait hésiter ?** `[cases]`

- Le temps de saisie quotidien
- La crainte d'afficher un stock faux au public
- Le fait de rendre visible ce que nous avons ou n'avons pas
- Le coût de l'abonnement
- Nous avons déjà un outil qui fait cela
- La formation de l'équipe
- Rien de particulier
- Autre : ______

---

## Section 6 — La suite

**14. Accepteriez-vous un échange de 20 minutes, à l'officine ou par téléphone ?**
`[unique]` **(obligatoire)**

- Oui, avec plaisir
- Oui, mais plutôt par téléphone
- Peut-être plus tard
- Non merci

**15. Vos coordonnées** `[texte]`

> *Nom de l'officine, numéro ou e-mail. Utilisés uniquement pour vous
> recontacter, jamais diffusés.*

**Message de fin :**

> Merci pour votre temps. Nous revenons vers vous si vous avez accepté un échange.

---

# Notes de conception

**Le formulaire ne sert pas à mesurer, il sert à qualifier.** Tu n'auras jamais
de volume statistique côté officines — et tu n'en as pas besoin. Les questions 5,
7 et 12 suffisent à trier : celles qui ont un logiciel fiable et celles qui
tiennent le stock de mémoire ne sont pas le même produit. La question 14 est la
seule dont dépend la suite.

**La question 7 est celle qui décide de ta faisabilité technique.** Si la majorité
répond « souvent décalé », ta promesse au public — « ce médicament est disponible
ici » — s'effondre à la source, et ton produit devient d'abord un outil qui fiabilise
le stock, l'affichage public venant après. C'est une réponse qui peut changer
l'ordre de ton roadmap entier.

**La question 10 chiffre ta valeur de leur côté.** Trente appels par jour à traiter
au comptoir, c'est du temps volé à la dispensation. C'est ton argument le plus
solide auprès d'un titulaire, et il est mesurable — contrairement à tout ce qui
touche à la clientèle, que tu ne peux ni promettre ni évoquer.

**L'option « rendre visible ce que nous avons ou n'avons pas » en question 13**
n'est pas là par symétrie. C'est probablement l'objection réelle, celle qu'un
pharmacien n'exprimera pas spontanément par politesse. La voir cochée te prépare
à la traiter en entretien.

**Vocabulaire tenu du début à la fin.** « Outil de gestion », « service
d'information », « classement objectif ». Jamais de visibilité, de clientèle ni
de mise en avant : un pharmacien titulaire lit ce vocabulaire comme du démarchage
et se ferme immédiatement, et le positionnement du produit ne le permet de toute
façon pas.

**Aucune question de prix.** Un chiffre donné dans un formulaire anonyme ne vaut
rien et t'enferme sur un ancrage. Le prix se discute en entretien, après avoir
entendu le problème.

---

# Message d'approche

**En visite, au comptoir** — demander le titulaire, ou son horaire de présence :

> Bonjour, je m'appelle Muslim, je développe un outil de suivi de stock pour les
> officines. Je ne vends rien aujourd'hui — j'essaie de comprendre comment vous
> gérez votre stock, pour ne pas construire quelque chose d'inutile.
> Est-ce que je peux vous poser deux ou trois questions, ou revenir à un moment
> plus calme ?

**Par WhatsApp, avec le lien direct qui saute la page-porte :**

> Bonjour Docteur, je développe un outil de gestion de stock pour les officines
> à Dakar. Avant de le construire, je recueille l'avis des pharmaciens sur leur
> façon de travailler. 12 questions, moins de 2 minutes :
> pharmalink.sn/enquete?profil=pharmacien&src=whatsapp-direct
> Merci d'avance pour votre temps.

Les deux disent la même chose : **je ne vends rien, j'apprends**. C'est ce qui
fait la différence entre un pharmacien qui répond et un pharmacien qui classe le
message parmi les sollicitations.

---

# Guide d'entretien — 20 minutes

À utiliser une fois le rendez-vous obtenu. Prends des notes, ne remplis pas le
formulaire à sa place.

1. Racontez-moi votre matinée d'hier, du moment où vous avez ouvert.
2. Combien de fois hier avez-vous dû dire « je ne l'ai pas » ?
3. La dernière fois que c'est arrivé, qu'est-ce que vous avez fait exactement ?
4. Comment savez-vous ce qu'il vous reste d'un produit ? *(le faire montrer,
   pas raconter)*
5. Qu'est-ce qui vous fait perdre le plus de temps dans une journée ?
6. Vous avez déjà essayé un outil pour ça ? Qu'est-ce qui n'a pas marché ?
7. *(après avoir présenté le concept)* Qu'est-ce qui ne marcherait pas chez vous ?
8. Qui décide d'un achat comme celui-là dans l'officine ?

**La question 4 est celle qui vaut le déplacement.** Demande à voir l'écran ou le
cahier. Ce que les gens décrivent de leur méthode et ce qu'ils font réellement
diffèrent presque toujours — et c'est dans cet écart que se trouve ton produit.

**La question 7 est formulée en négatif exprès.** « Qu'est-ce que vous en pensez ? »
récolte de la politesse. « Qu'est-ce qui ne marcherait pas chez vous ? » autorise
la critique et récolte de l'information.
