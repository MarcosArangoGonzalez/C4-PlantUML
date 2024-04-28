@startuml RippleArchitecture
!include <C4/C4_Container>

' Personas
Person_Ext(usuario, "Usuario", "Persona que utiliza la red Ripple")

System_Boundary(sistema_ripple, "Sistema Ripple") {
    Person(admin, "Administrador", "Persona responsable de administrar y mantener el sistema Ripple")
  
    System(alias_sistema_ripple, "Sistema Ripple", "Plataforma para facilitar transferencias de dinero y pagos globales")
}

System_Ext(oraculo, "Oráculo", "Proporciona soluciones a problemas no resueltos")

Rel(usuario, alias_sistema_ripple, "Transfiere fondos", "Red Ripple P2P")
Rel(alias_sistema_ripple, usuario, "Facilita transacciones", "Red Ripple P2P")
Rel(oraculo, alias_sistema_ripple, "Proporciona soluciones", "Red Ripple P2P")
Rel(admin, alias_sistema_ripple, "Administra y mantiene", "Red Ripple P2P")

' Componentes internos del sistema Ripple
System_Boundary(sistema_interno, "Componentes Internos del Sistema Ripple") {
    Component(xCurrent, "xCurrent", "Facilita la interoperabilidad entre diferentes libros de contabilidad y redes de pagos")
    Component(xRapid, "xRapid", "Fuente de liquidez para la red, facilita el intercambio rápido con una tasa estable")
    Component(xVia, "xVia", "Interfaz de pago para enviar pagos entre usuarios")
  
    Rel(alias_sistema_ripple, xCurrent, "Utiliza", "Interfaz de usuario")
    Rel(alias_sistema_ripple, xRapid, "Utiliza", "Interfaz de usuario")
    Rel(alias_sistema_ripple, xVia, "Utiliza", "Interfaz de usuario")
}

' Información adicional
note left of usuario
    Peer-to-Peer (P2P) technology is based on the decentralization concept, which lets network participants conduct transactions without needing any middle-man, intermediaries or central server. Peer-to-peer technology is how Bitcoin operates; no administrator is required to maintain track of user transactions on the network. Instead, the peers in the network cooperate to handle deals and manage the BTC.
end note

note right of oraculo
    The security of the underlying consensus algorithms and the privacy of transactions are all closely tied to its implementation, making the P2P network a crucial component of blockchains. However, no common P2P protocol for blockchains has been suggested. Instead, different cryptocurrencies have developed and adapted their own peer-to-peer protocols.
end note

note bottom of sistema_interno
    RippleNet is the digital payments network running on Ripple’s XRP Ledger. RippleNet uses blockchain and modern APIs to enable financial institutions on the network to send money to any corner of the globe instantly and at a fraction of the cost that regular transfers would take.
end note

@enduml
