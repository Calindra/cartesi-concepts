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


## [Arquitetura](https://github.com/Calindra/cartesi-concepts/wiki/Arquitetura)
