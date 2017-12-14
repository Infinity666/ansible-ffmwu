# Ansible role network-fastd

Diese Ansible role konfiguriert Netzwerk Interfaces für die definierten fastd Instanzen.

Es wird zwischen node- und intragate-Instanzen unterschieden.

## Interface-Benamung
Node-Interfaces: $mesh.id + vpn + '-' + $mesh.fastd.nodes.instances.xx.mtu, z.B. "mzvpn-1312"
Intragate-Interfaces: $mesh.id + 'ig' + vpn + '-' + $mesh.fastd.intragate.instances.xx.mtu, z.B. "mzigvpn-1312"

## Benötigte Variablen

- Dictionary `meshes`
´´´
meshes:
  - id: xx
...
    ipv4_network:
...
    fastd:
      nodes:
        instances:
          - id: 0 # integer
            mtu: # integer
          ...
      intragate:
        instances:
          - id: 0 # integer
            mtu: # integer
          ...

´´´
- Host Variable `magic`

## MAC-Adressen

Die MAC-Adressen der Interfaces werden aus dem IPv4-Subnetz sowie der `magic`-Nummer des Hosts berechnet.

xxvpn-$mtu prefix: `02:2x` # x = ID der fastd-Instanz
xxigvpn-$mtu prefix: `02:3x` # x = ID der fastd-Instanz