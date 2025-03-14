@startuml
[*] --> App : Appuyer sur "Identifier une chanson"

state "Application" as App {
  [*] --> Identification : Initialisation terminée  

  Erreur : do/afficherErreur()
  
  Identification : do/enregistrerAudio()
  Identification --> Analyse : Enregistrement terminé
  Identification --> Erreur : Problème pendant l'enregistrement

  Analyse : do/analyserAudio()
  Analyse --> Recherche : Analyse terminée
  Analyse --> Erreur : Échec de l'analyse

  Recherche : do/rechercherCorrespondance()
  Recherche --> RésultatTrouvé : Correspondance trouvée
  Recherche --> Erreur : Problème pendant la recherche

  RésultatTrouvé : do/ajouterHistorique()
  RésultatTrouvé : do/afficherTitre()
  RésultatNonTrouvé : do/afficherMessage()

  RésultatTrouvé --> InfoChanson : Cliquer "Détail de la chanson"
  InfoChanson : do/afficherInfosChanson()

  InfoChanson --> InfoArtiste : Cliquer "Détail de l'artiste"
  InfoArtiste --> InfoChanson : Cliquer "Retour"
  InfoArtiste : do/afficherInfosArtiste()
  
  Recherche --> RésultatNonTrouvé : Aucune correspondance

}

App --> [*] : Cliquer "Retour"
@enduml
