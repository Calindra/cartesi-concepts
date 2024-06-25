# cartesi-concepts

## [Home](https://github.com/Calindra/cartesi-concepts/wiki)
 ### [O que é a Cartesi?](https://github.com/Calindra/cartesi-concepts/wiki#o-que-%C3%A9-a-cartesi)
 A Cartesi pode ser definida como uma solução de segunda camada(layer 2 solution), uma tecnologia que opera sobre a blockchain principal, nesse caso a Ethereum, com o objetivo de melhorar sua eficiência. A blockchain principal é chamada de camada um(layer 1), e qualquer tecnologia adicional que funcione sobre ela é chamada de camada dois.

 Esta solução funciona da seguinte forma:
 - Realiza as operações custosas fora da blockchain Ethereum. Esse processo é chamado de off-chain

 - É possível garantir resultados corretos e confiáveis, mesmo que as operações sejam realizadas off-chain. Pois, essas operações são feitas de uma forma que possam ser verificadas e comprovadas.

 - Após realizar as operações de forma off-chain, a Cartesi reporta os resultados de volta na blockchain. Dessa forma é possível que todos possam verificar o que foi feito, além de manter a integriade dos dados.
 ## [Principais Conceitos](https://github.com/Calindra/cartesi-concepts/wiki#principais-conceitos)
 ### [Cartesi Rollup](https://github.com/Calindra/cartesi-concepts/wiki#cartesi-rollup)
 É uma solução de escalabilidade de blockchain que faz com que transações complexas sejam executadas em um ambiente separado fora da camada base, neste caso, a Ethereum.

 Ao utilizar rollups, a blockchain recebe e registra transações. Casos de ataque ativo ou participação de agentes maliciosos são raros, mas caso ocorram e haja discordância sobre os resultados de alguma computação, a blockchain resolverá a disputa. No entanto, é importante observar que tais discordâncias não são esperadas em circunstâncias normais.

 Usuários interagem com rollup através de transações na camada base. Eles enviam mensagens (entradas) para os contratos inteligentes on-chain do rollup para definir uma computação a ser processada e, assim, avançar o estado do ambiente de computação na camada de execução. Partes interessadas executam o componente off-chain que monitora a blockchain em busca de entradas, compreendendo e executando as atualizações do estado.

 Periodicamente o estado atual do sistema é gravado na blockchain principal. Esse registro é considerado finalizado e imutável, o que permite que qualquer econtrato inteligente na camada base utilize esses dados de forma confiável para suas operações e lógica de negócios.

 É essencial garantir que esta operação seja segura, por isso que o nó da camada de execução deve de alguma forma provar o novo estado para a camada base. E essa prova pode ser feita de duas formas:
 
 1 - Zero-knowledge Rollups (ZK Rollups), que utilizam provas de validade.

 2 - Optimistic Rollups (ORs), que utilizam provas de fraude.

 ### [Máquina Cartesi](https://github.com/Calindra/cartesi-concepts/wiki#maquina-cartesi)
 A Máquina Cartesi é uma máquina virtual que executa um sistema operacional Linux completo, no qual o backend de um dApp é executado. Ela é baseada na ISA RISC-V, um conjunto de instruções para processadores. Opera de forma isolada, o que significa que funciona de maneira independente e é reproduzível.

Considerada peça central nos Cartesi Rollups, a Máquina Cartesi foi projetada para realizar cálculos off-chain para aplicações blockchain. Quando examinada em um nível elevado de 
abstração, a Máquina Cartesi apresenta as seguintes características:

- Execução de código: O código é executado com base em entradas específicas para realizar cálculos, processar dados ou executar lógica personalizada, dependendo dos requisitos da tarefa em questão.

- Abstração da infraestrutura: A infraestrutura subjacente é abstraída, permitindo que você se concentre na escrita de código sem se preocupar com a gestão de servidores, hardware ou recursos de rede.

- Flexibilidade em linguagens de programação e bibliotecas: Você tem flexibilidade na escolha de linguagens de programação e todas as bibliotecas open-source disponíveis no Linux.

A Máquina Cartesi é uma máquina de estados que permanece ociosa até surgir uma nova solicitação. O conceito de estado, neste caso, está vinculado tanto às solicitações de entrada que a Máquina Cartesi recebe quanto à execução das instruções RISC-V que a máquina segue no processamento dessas solicitações. A Máquina Cartesi lida com:

- Estados discretos: As instruções RISC-V são executadas passo a passo, transitando de um estado para outro.

- Transições de estado: As transições de estado ocorrem de forma determinística à medida que o emulador processa essas instruções RISC-V, alterando o estado do sistema para um novo estado discreto.

- Determinismo: Dado o mesmo estado inicial e entrada, a Máquina Cartesi sempre produzirá a mesma saída e estado final para garantir que os cálculos off-chain possam ser verificados e concordados.

- A Máquina Cartesi é autocontida e não pode fazer uma solicitação externa. Para alcançar a reprodução, ela opera isoladamente de qualquer influência externa sobre o cálculo.

### [Arquitetura](https://github.com/Calindra/cartesi-concepts/wiki#arquitetura)
Podemos afirmar que as duas partes fundamentais que compõe o framework Cartesi Rollups são os componentes da camada base e a camada de execução.

Os componentes que compõe um dApp o qual é executado na Cartesi são:

- Cartes Rollup

- Cartesi Machine

- Backend: Pode ser encarado como o estado da aplicação e a lógica verificável. O backend é executado dentro da Máquina Cartesi como uma aplicação Linux.

- Frontend: A interface voltada para o usuário da aplicação.


### Componentes On-chain

A parte on-chain dos Cartesi Rollups envolve contratos inteligentes implantados na camada base, cada um com papéis distintos para seu dApp. Cada dApp Cartesi utiliza a funcionalidade que esses contratos fornecem.

- InputBox: Este contrato recebe entradas de usuários que desejam interagir com a camada off-chain. Todas as entradas para seu dApp passam por este contrato.

- CartesiDApp: Este contrato CartesiDApp é instanciado para cada dApp (ou seja, cada dApp tem seu endereço de aplicação). Com este endereço, uma aplicação pode manter a propriedade sobre ativos digitais na camada base, como Ether, tokens ERC-20 e NFTs.

- CartesiDAppFactory: O contrato CartesiDAppFactory permite que qualquer pessoa implante contratos CartesiDApp com uma simples chamada de função. Ele oferece maior conveniência ao implantador e segurança aos usuários e validadores, pois eles sabem que o bytecode não poderia ter sido alterado maliciosamente.

- Portals: Estes são um conjunto de contratos usados para teletransportar com segurança ativos da camada base para o ambiente de execução do seu dApp. Atualmente, existem contratos Portal para os seguintes tipos de ativos: Ether (ETH), ERC-20 (tokens fungíveis), ERC-721 (tokens não fungíveis), transferências únicas ERC-1155 e transferências em lote de tokens ERC-1155.


### Camada Off-chain

A camada de execução é off-chain e consiste no Cartesi Node, que lida com o processamento de entradas para mudar o estado do dApp.

Ele pode atuar como um validador e inspecionar o estado do dApp.

Aqui está uma visão geral de alto nível das principais funcionalidades do Cartesi Node:

- Processa entradas da blockchain para mudar o estado das aplicações descentralizadas.
- Permite que o nó funcione como um validador, gerando reivindicações no final dos epochs.
- Captura e analisa solicitações para inspecionar o estado dos dApps.
- Gerencia um servidor GraphQL para que as saídas sejam consultadas pelo cliente.

Conforme explicado, a Máquina Cartesi fornece aos desenvolvedores de dApps um ambiente onde eles podem realizar grandes cálculos verificáveis. Essas máquinas são integradas com os contratos inteligentes on-chain por um middleware que gerencia e controla sua comunicação. Assim, este middleware é responsável por primeiro ler dados do contrato inteligente InputBox da L1, depois enviá-los para a máquina para serem processados e, finalmente, publicar os resultados na blockchain.

O Cartesi Node é o componente L2 que combina a Máquina Cartesi e este middleware. Qualquer pessoa interessada no estado do rollup pode usá-lo.

Simplificando, os Cartesi Nodes desempenham um papel semelhante ao do Geth no ecossistema Ethereum: eles executam e recuperam informações.

Na prática, dois tipos distintos de agentes executam Cartesi Nodes: usuários e validadores. Cada um interage com os rollups on-chain de maneiras diferentes e, portanto, executa diferentes tipos de Cartesi Nodes:

**Nó de Usuário ou Leitor:** estão envolvidos apenas em avançar o estado da máquina off-chain e tornar esse estado publicamente disponível. Eles consomem informações da blockchain, mas não se preocupam em impor atualizações de estado, confiando que os validadores garantirão a validade de todas as atualizações de estado on-chain.

**Nó de Validador:**  têm mais responsabilidade: eles não apenas observam a blockchain, mas também combatem validadores desonestos para garantir a prevalência de reivindicações honestas para atualizações de estado. Por outro lado, se houver Nodos de Leitor disponíveis, os validadores não precisam expor endpoints para recuperar o estado da aplicação. Portanto, eles podem operar em ambientes mais seguros e permanecer inacessíveis a clientes e usuários externos.
