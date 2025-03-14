@startuml
entity "Artiste" {
    * id : UUID
    nom : String
    genre : String
    nationalite : String
}

entity "Album" {
    * id : UUID
    titre : String
    dateSortie : Date
    genre : String
}

entity "Musique" {
    * id : UUID
    titre : String
    duree : Time
    genre : String
    numeroPiste : Integer
}

entity "User" {
    * id : UUID
    username : String
    email : String
    dateInscription : Date
}

entity "Participation" {
    role : String
}

entity "Historique" {
    dateEcoute : DateTime
}

' Relations
Artiste ||--o{ Participation : "participe à"
Participation }o--|| Album : "lié à"
Album ||--o{ Musique : "contient"
User ||--o{ Historique : "a un"
Historique }o--|| Musique : "contient"
@enduml