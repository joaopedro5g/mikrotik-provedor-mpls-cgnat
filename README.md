# Projeto Mikrotik - Rede com Edge, PPPoE e MPLS

Este repositório contém a configuração de uma rede Mikrotik simulada no Pnetlab. A rede foi projetada com dois cenários principais, um B2C (Business-to-Consumer) para usuários domésticos e um B2B (Business-to-Business) para clientes empresariais. A configuração inclui o uso de roteadores Edge e PPPoE, além de autenticação centralizada via Mikrotik User Manager, CGNAT e MPLS para comunicação entre filiais.

## Estrutura da Rede

A rede é composta pelos seguintes elementos principais:

1. **Roteador Edge**:
   - Configurado com **CGNAT** para fornecer endereçamento de rede e compartilhamento de IPs públicos para múltiplos clientes.
   - **Mikrotik User Manager** configurado para gerenciar autenticações PPPoE de forma centralizada.
   
2. **Concentradores PPPoE**:
   - Dois roteadores configurados para autenticação e distribuição de PPPoE.
   - O roteador Edge atua como ponto central de autenticação e gerenciamento.

3. **Cenário B2C (Business-to-Consumer)**:
   - Clientes domésticos (usuários finais) se conectam ao concentrador PPPoE, onde recebem uma conexão de internet via CGNAT e autenticação centralizada.

4. **Cenário B2B (Business-to-Business)**:
   - **Filial SP**: Configurada com PPPoE em cima de uma VLAN 402. Um servidor DHCP fornece endereços IP para os clientes locais.
   - **Filial RJ**: A comunicação com a filial SP é feita através de um túnel **MPLS** para garantir a conectividade entre as duas filiais.
   - O servidor DHCP em SP envia configurações de rede para a filial RJ, garantindo que os clientes na filial RJ obtenham seus IPs dinamicamente.

## Componentes e Tecnologias

- **Mikrotik RouterOS**: Sistema operacional utilizado nos roteadores Edge e concentradores PPPoE.
- **PPPoE**: Protocolo Point-to-Point Protocol over Ethernet, utilizado para autenticar e fornecer IPs aos clientes.
- **User Manager**: Ferramenta do Mikrotik usada para gerenciar autenticação de usuários PPPoE.
- **CGNAT**: Carrier-Grade NAT, utilizado no roteador Edge para gerenciar múltiplos clientes com IPs privados.
- **MPLS**: Multiprotocol Label Switching, utilizado para criar túneis de comunicação entre as filiais SP e RJ.
- **VLAN 402**: Configuração de VLAN usada para a comunicação na filial SP.

<img src="https://raw.githubusercontent.com/joaopedro5g/mikrotik-provedor-mpls-cgnat/refs/heads/main/topologia.PNG" />
