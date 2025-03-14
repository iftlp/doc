@startuml
[*] --> App : Cliquer "Historique"

state "Application" as App {
  [*] --> Historique : Initialisation terminée

  Historique --> [*] : Cliquer "Retour à l'accueil"
  Historique : do/afficherHistorique()

  Historique --> InfoChanson : Cliquer "Détail de la chanson"
  InfoChanson : do/afficherInfosChanson()
  InfoChanson --> Historique : Cliquer "Retour"

  InfoChanson --> InfoArtiste : Cliquer "Détail de l'artiste"
  InfoArtiste --> InfoChanson : Cliquer "Retour"
  InfoArtiste : do/afficherInfosArtiste()
}

App --> [*] : Cliquer "Retour à l'accueil"
@enduml
