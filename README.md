# cartesi-concepts

## [Home](https://github.com/Calindra/cartesi-concepts/wiki)
 ### [O que é a Cartesi?](https://github.com/Calindra/cartesi-concepts/wiki#o-que-%C3%A9-a-cartesi)
 A Cartesi pode ser definida como uma solução de segunda camada(layer 2 solution), uma tecnologia que opera sobre a blockchain principal, nesse caso a Ethereum, com o objetivo de melhorar sua eficiência. A blockchain principal é chamada de camada um(layer 1), e qualquer tecnologia adicional que funcione sobre ela é chamada de camada dois.

 Esta solução funciona da seguinte forma:
 - Realiza as operações custosas fora da blockchain Ethereum. Esse processo é chamado de off-chain

 - É possível garantir resultados corretos e confiáveis, mesmo que as operações sejam realizadas off-chain. Pois, essas operações são feitas de uma forma que possam ser verificadas e comprovadas.

 - Após realizar as operações de forma off-chain, a Cartesi reporta os resultados de volta na blockchain. Dessa forma é possível que todos possam verificar o que foi feito, além de manter a integriade dos dados.
 ## [Principais Conceitos](https://github.com/Calindra/cartesi-concepts/wiki#principais-conceitos)
 ### [Rollup](https://github.com/Calindra/cartesi-concepts/wiki#rollup)
 É uma solução de escalabilidade de blockchain que faz com que transações complexas sejam executadas em um ambiente separado fora da camada base, neste caso, a Ethereum.

 Ao utilizar rollups, a blockchain recebe e registra transações. Casos de ataque ativo ou participação de agentes maliciosos são raros, mas caso ocorram e haja discordância sobre os resultados de alguma computação, a blockchain resolverá a disputa. No entanto, é importante observar que tais discordâncias não são esperadas em circunstâncias normais.

 Usuários interagem com rollup através de transações na camada base. Eles enviam mensagens (entradas) para os contratos inteligentes on-chain do rollup para definir uma computação a ser processada e, assim, avançar o estado do ambiente de computação na camada de execução. Partes interessadas executam o componente off-chain que monitora a blockchain em busca de entradas, compreendendo e executando as atualizações do estado.

 Periodicamente o estado atual do sistema é gravado na blockchain principal. Esse registro é considerado finalizado e imutável, o que permite que qualquer econtrato inteligente na camada base utilize esses dados de forma confiável para suas operações e lógica de negócios.

 É essencial garantir que esta operação seja segura, por isso que o nó da camada de execução deve de alguma forma provar o novo estado para a camada base. E essa prova pode ser feita de duas formas:
 
 1 - Zero-knowledge Rollups (ZK Rollups), que utilizam provas de validade.

 2 - Optimistic Rollups (ORs), que utilizam provas de fraude.

 ### [Máquina Cartesi](https://github.com/Calindra/cartesi-concepts/wiki#maquina-cartesi)
 A Máquina Cartesi é uma máquina virtual que executa um sistema operacional Linux completo, no qual o backend de um dApp é executado. Ela é baseada na ISA RISC-V, um conjunto de instruções para processadores. Opera de forma isolada, o que significa que funciona de maneira independente e é reproduzível.

Central nos Cartesi Rollups está a Cartesi Machine, uma máquina virtual projetada para realizar cálculos off-chain para aplicações blockchain. Quando examinada em um nível elevado de 
abstração, a Cartesi Machine apresenta as seguintes características:

- Execução de código: O código é executado com base em entradas específicas para realizar cálculos, processar dados ou executar lógica personalizada, dependendo dos requisitos da tarefa em questão.

- Abstração da infraestrutura: A infraestrutura subjacente é abstraída, permitindo que você se concentre na escrita de código sem se preocupar com a gestão de servidores, hardware ou recursos de rede.

- Flexibilidade em linguagens de programação e bibliotecas: Você tem flexibilidade na escolha de linguagens de programação e todas as bibliotecas open-source disponíveis no Linux.

A Máquina Cartesi é uma máquina de estados que permanece ociosa até surgir uma nova solicitação. O conceito de estado, neste caso, está vinculado tanto às solicitações de entrada que a Máquina Cartesi recebe quanto à execução das instruções RISC-V que a máquina segue no processamento dessas solicitações. A Máquina Cartesi lida com:

- Estados discretos: As instruções RISC-V são executadas passo a passo, transitando de um estado para outro.

- Transições de estado: As transições de estado ocorrem de forma determinística à medida que o emulador processa essas instruções RISC-V, alterando o estado do sistema para um novo estado discreto.

- Determinismo: Dado o mesmo estado inicial e entrada, a Máquina Cartesi sempre produzirá a mesma saída e estado final para garantir que os cálculos off-chain possam ser verificados e concordados.

- A Máquina Cartesi é autocontida e não pode fazer uma solicitação externa. Para alcançar a reprodução, ela opera isoladamente de qualquer influência externa sobre o cálculo.

## [Arquitetura](https://github.com/Calindra/cartesi-concepts/wiki/Arquitetura)
