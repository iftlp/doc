@startuml
[*] --> App : Lancement de l'application

state "Application" as App {
  [*] --> Attente : Initialisation terminée

  Attente --> Identification : Cliquer "Identifier une chanson"
  Attente <-- Identification : Cliquer "Accueil"
  
  note bottom of Identification : Suite de la partie identification dans un autre diagramme\n

  Attente --> Historique : Cliquer "Historique"
  Attente <-- Historique : Cliquer "Accueil"

  note bottom of Historique : Suite de la partie historique dans un autre diagramme\n
  
  Attente --> ModeDeGestion : Mode administrateur activé
  ModeDeGestion --> Attente : Mode administrateur désactivé
  
  note bottom of ModeDeGestion : Suite de la partie gestion dans un autre diagramme\n
}

App --> [*] : Fermeture de l'application
@enduml
