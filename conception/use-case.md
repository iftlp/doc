@startuml
left to right direction

actor Utilisateur
actor "Admin"

rectangle "Application" {
    Utilisateur -- (Identifier une chanson)
    Utilisateur -- (Consulter l'historique)

    Admin -- (Gérer la base de données)
    (Gérer la base de données) <.. (Ajouter une chanson) : <<extend>>
    (Gérer la base de données) <.. (Modifier une chanson) : <<extend>>
    (Gérer la base de données) <.. (Supprimer une chanson) : <<extend>>

    (Identifier une chanson) <.. (Consulter l'historique) : <<extend>>
}

Admin --|> Utilisateur

@enduml
