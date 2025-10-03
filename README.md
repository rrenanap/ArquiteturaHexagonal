# ArquiteturaHexagonal

Nosso projeto x Arquitetura hexagonal

Analise nosso microsserviço de autenticação disponível no github, e identifique os seguintes pontos:

  *Portas de entrada
  *Portas de saida
  *Adaptadores
  *Domínios
  
Nosso projeto não está seguinto o modelo hexagonal a risca, o que falta para ele estar 100% aderente?
Sugira classes, pacotes e como eles podem ser aplicados em nosso projeto construido durante as aulas

Questões extras:

1. O objetivo central da Arquitetura Hexagonal é:
A) Padronizar camadas de repositório com JPA
B) Centralizar decisões no banco de dados
C) Manter o domínio independente de infraestrutura
D) Reduzir o número de testes de integração

C) Manter o domínio independente de infraestrutura
A arquitetura hexagonal (Ports & Adapters) visa isolar o domínio das dependências técnicas, como bancos de dados e frameworks, garantindo que o núcleo da aplicação (domínio) seja independente.
 

2. Em “Ports & Adapters”, Input Ports representam:
A) Interfaces para recursos externos (DB, mensageria)
B) Interfaces que expõem casos de uso do aplicativo
C) Controllers REST
D) Repositórios de banco de dados

B) Interfaces que expõem casos de uso do aplicativo
Input Ports são interfaces pelas quais o domínio recebe comandos, ou seja, expõem os casos de uso da aplicação.

3. Output Ports são:
A) Interfaces usadas pelo domínio/aplicação para falar com o “mundo externo”
B) Controllers que recebem requisições
C) Entidades JPA
D) Serviços de domínio com regras de negócio

A) Interfaces usadas pelo domínio/aplicação para falar com o “mundo externo”
Output Ports são as interfaces que o domínio usa para se comunicar com recursos externos, como banco de dados, mensageria, etc.

4. Onde não devem aparecer anotações de framework (ex.: @Entity, @RestController)?
A) Adaptadores
B) Domínio
C) Camada Web
D) Persistência

B) Domínio
O domínio deve ser puro, sem dependências de frameworks para garantir independência e testabilidade. 

5. Trocar REST por gRPC sem tocar na regra de negócio é possível porque:
A) As entidades do domínio expõem ResponseEntity
B) Controllers chamam diretamente repositórios
C) A UI é um adaptador de entrada plugado em uma porta de entrada
D) O domínio conhece o protocolo gRPC

C) A UI é um adaptador de entrada plugado em uma porta de entrada
A interface (UI) é um adaptador que usa as portas para interagir com o domínio, permitindo trocar protocolos sem alterar o núcleo da aplicação.

6. Qual é um anti-padrão em Hexagonal?
A) Portas com linguagem do negócio
B) Domínio anêmico e serviços de aplicação gordos com toda a regra
C) Adaptadores restritos a I/O e mapeamento
D) Separar Input e Output Ports

B) Domínio anêmico e serviços de aplicação gordos com toda a regra
 Domínio anêmico (sem lógica, só dados) é um anti-padrão, pois a lógica deve estar no domínio para manter a arquitetura limpa.

7. Qual benefício direto da Hexagonal?
A) Menos código cerimonial
B) Substituir infraestrutura com menor impacto no domínio
C) Reduzir número de interfaces
D) Eliminar testes E2E

B) Substituir infraestrutura com menor impacto no domínio
A arquitetura permite trocar componentes de infraestrutura sem alterar o núcleo do domínio. 

8. Marque os itens como verdadeiro ou falso, justificando brevemente sua resposta:

[ f ] Domínio pode depender de JPA desde que use apenas @Entity.

[ v ] Input Ports expõem casos de uso; Output Ports modelam dependências externas.

[ f ] Adaptadores conhecem detalhes do domínio e podem validar regras complexas.

[ v ] Controllers devem falar com o caso de uso (input port), não diretamente com repositórios.

[ f ] Trocar o banco (JPA → JDBC) deve exigir mudanças extensas no domínio.

 
9. Explique a diferença entre Port e Adapter

Port:
É uma interface que define um ponto de comunicação entre o domínio e o mundo externo. Pode ser uma porta de entrada (Input Port), que o domínio expõe para receber comandos, ou uma porta de saída (Output Port), que o domínio usa para acessar serviços externos.

Adapter:
É a implementação concreta de uma porta. Ele adapta a interface da porta para o protocolo, tecnologia ou framework específico (ex: REST controller, repositório JPA, cliente gRPC).
