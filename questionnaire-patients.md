# Enquête PharmaLink — Formulaire patients

**Cible :** grand public, diffusion WhatsApp / Facebook / Telegram
**Durée visée :** 2 minutes — 14 questions, dont 11 à cocher
**Objectif :** mesurer la fréquence et le coût réel de la recherche de médicaments,
avant de parler du produit.

> Convention : `[unique]` = choix multiple à une réponse · `[cases]` = plusieurs réponses
> possibles · `[texte]` = réponse courte · **(obligatoire)** = question requise.
> Les questions non marquées restent facultatives.

---

## Section 1 — Introduction (pas de question)

**Titre du formulaire :** Trouver un médicament à Dakar — votre expérience

**Description :**

> Nous préparons un service d'information sur la disponibilité des médicaments
> en officine. Vos réponses nous aident à savoir quoi construire en premier.
>
> C'est anonyme, ça prend 2 minutes. Nous ne demandons aucune information
> sur votre santé et nous ne mettons en avant aucune pharmacie.

*Ajouter ici la question technique « Source » (texte court), remplie automatiquement
par la page-porte. La rendre facultative et la placer en dernier si tu ne veux pas
qu'elle apparaisse en tête.*

---

## Section 2 — Vous

**1. Dans quelle ville habitez-vous ?** `[unique]` **(obligatoire)**

- Dakar
- Pikine / Guédiawaye
- Rufisque / Bargny
- Thiès
- Mbour / Saly
- Saint-Louis
- Touba / Mbacké
- Ziguinchor
- Kaolack
- Autre : ______

**2. Votre quartier ou commune** `[texte]`

> *Facultatif. Ça nous aide à savoir où lancer en premier.*

**3. Votre tranche d'âge** `[unique]`

- Moins de 25 ans
- 25 – 34 ans
- 35 – 49 ans
- 50 – 64 ans
- 65 ans et plus

**4. En général, vous achetez des médicaments pour…** `[cases]`

- Vous-même
- Votre enfant
- Un parent âgé
- Une autre personne de la famille
- Vous n'en achetez presque jamais

---

## Section 3 — La dernière fois

> **Texte d'introduction de section :**
> Les questions suivantes portent sur **la dernière fois** que vous êtes allé
> chercher un médicament en pharmacie. Pas en général — cette fois-là précisément.

**5. C'était quand ?** `[unique]` **(obligatoire)**

- Cette semaine
- Ce mois-ci
- Il y a 2 à 6 mois
- Il y a plus de 6 mois
- Je ne suis jamais allé chercher un médicament moi-même

**6. Vous l'avez trouvé dans la première pharmacie ?** `[unique]` **(obligatoire)**

- Oui, du premier coup
- Non, il a fallu 2 pharmacies
- Non, il a fallu 3 pharmacies ou plus
- Je ne l'ai pas trouvé du tout ce jour-là
- Je ne me souviens plus

**7. Au total, combien de temps ça vous a pris ?** `[unique]`

- Moins de 15 minutes
- Entre 15 et 30 minutes
- Entre 30 minutes et 1 heure
- Plus d'une heure
- Plusieurs jours / plusieurs déplacements

**8. Il s'agissait d'un médicament…** `[unique]`

- Sur ordonnance
- En vente libre (sans ordonnance)
- Les deux
- Je ne sais pas

**9. Si vous ne l'avez pas trouvé tout de suite, qu'avez-vous fait ?** `[cases]`

- J'ai fait le tour d'autres pharmacies à pied ou en voiture
- J'ai appelé une ou plusieurs pharmacies
- J'ai demandé à un proche de chercher de son côté
- Le pharmacien m'a orienté vers une autre officine
- J'ai demandé dans un groupe WhatsApp / sur Facebook
- J'ai pris un autre médicament équivalent
- J'ai laissé tomber
- Ça ne s'est pas produit, j'ai trouvé du premier coup

**10. En repensant à ce moment, qu'est-ce qui a été le plus pénible ?** `[texte]`

> *Une phrase suffit.*

---

## Section 4 — En général

**11. Ces 3 derniers mois, combien de fois avez-vous eu du mal à trouver un
médicament ?** `[unique]` **(obligatoire)**

- Jamais
- Une fois
- Deux ou trois fois
- Plus de trois fois

**12. Vous est-il déjà arrivé de chercher une pharmacie de garde la nuit ou un
jour férié ?** `[unique]`

- Oui, et j'ai trouvé l'information facilement
- Oui, mais l'information était difficile à trouver ou fausse
- Oui, et je n'ai pas trouvé du tout
- Non, jamais

---

## Section 5 — Le service

> **Texte d'introduction de section :**
> Imaginez un service où vous tapez le nom d'un médicament et vous voyez
> les pharmacies proches qui l'ont en stock, avec les pharmacies de garde du jour.
> L'information vient des pharmacies elles-mêmes.

**13. La dernière fois dont vous avez parlé plus haut, ça vous aurait aidé ?**
`[unique]` **(obligatoire)**

- Ça m'aurait beaucoup aidé
- Ça m'aurait un peu aidé
- Ça n'aurait rien changé
- Je ne sais pas

**14. Qu'est-ce qui vous ferait hésiter à l'utiliser ?** `[cases]`

- La peur que l'information ne soit pas à jour
- Je préfère appeler ou passer directement
- Ça consomme de la connexion / des données
- Je ne suis pas à l'aise avec ce genre d'outil
- Rien, je l'utiliserais
- Autre : ______

**15. Sous quelle forme l'utiliseriez-vous le plus volontiers ?** `[unique]`

- Sur WhatsApp
- Un site web à ouvrir dans le navigateur
- Une application à installer
- Par SMS
- En appelant un numéro

---

## Section 6 — Rester en contact

**16. Souhaitez-vous être prévenu au lancement ?** `[texte]`

> *Facultatif. Laissez un numéro WhatsApp ou un e-mail. Il ne servira qu'à ça
> et ne sera transmis à personne.*

**Message de fin :**

> Merci. Vos réponses sont enregistrées.
> Si vous connaissez quelqu'un que ça concerne, transférez-lui le lien :
> pharmalink.sn/enquete

---

# Notes de conception

**La question 6 est ta question centrale.** Le pourcentage de gens qui répondent
« 3 pharmacies ou plus » ou « pas trouvé » est le chiffre unique qui justifie ou
tue le projet. Tout le reste est du contexte autour d'elle.

**Section 3 avant section 5.** Les questions sur le vécu passent toutes avant la
présentation du service : une fois que le répondant a lu le concept, il devient
gentil et surestime rétroactivement sa douleur. L'ordre protège la fiabilité de
tes données.

**« La dernière fois » plutôt que « en général ».** Une question générale
(« avez-vous souvent du mal ? ») récolte une opinion sur soi-même, pas un fait.
Un souvenir daté récolte un fait. La question 11 pose quand même la fréquence,
mais après le souvenir précis, quand le répondant a une référence concrète en tête.

**Question 13 formulée au conditionnel passé**, pas « utiliseriez-vous ce
service ? ». Les gens répondent oui à tout ce qui est gratuit et futur : cette
question-là ne mesure rien. La rattacher à un épisode réel donne une réponse
qu'on peut prendre au sérieux.

**Question 14 cherche le refus, pas l'adhésion.** Les objections que tu récoltes
là sont ta feuille de route produit — et la première option (« l'information ne
sera pas à jour ») est précisément le risque numéro un de PharmaLink. Si elle
sort en tête, ton problème n'est pas technique, il est dans la fraîcheur des
données côté officines.

**Question 15 pilote une décision technique coûteuse.** Si WhatsApp domine
largement, un bot coûte moins cher à construire et à faire adopter qu'une app,
et t'évite le mur de l'installation.

**Aucune donnée de santé.** Pas de nom de médicament, pas de pathologie. La
question 8 (ordonnance / vente libre) donne l'information utile sans toucher au
sensible — et te permet d'annoncer honnêtement « aucune information sur votre
santé » en tête de formulaire, ce qui augmente le taux de réponse.

**Rien qui compare ou classe les officines.** Aucune question ne demande de
nommer, noter ou préférer une pharmacie : l'enquête reste dans le registre du
service d'information, cohérente avec le positionnement du produit.

## Ce que tu regarderas à l'analyse

| Croisement | Ce qu'il t'apprend |
|---|---|
| Q6 × Q1 (ville) | Où la douleur est la plus forte → où lancer |
| Q6 × Q11 | Épisode isolé ou problème chronique |
| Q7 (temps perdu) | La valeur que ton service fait économiser |
| Q9 | Les solutions de contournement actuelles = tes vrais concurrents |
| Q14 | Les objections à traiter dans l'UI dès la v1 |
| Q15 × Q3 (âge) | Le canal à construire en premier, et pour qui |

**Seuil de lecture :** en dessous de ~100 réponses, lis les tendances, pas les
pourcentages. À partir de 200–300 réponses réparties sur plusieurs quartiers,
les croisements ci-dessus deviennent exploitables.
