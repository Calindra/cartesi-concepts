# Lambada e/ou Co-Processors

É uma iniciativa do Carsten.

[Lambada](https://governance.cartesi.io/t/cartesi-lambada-a-worse-is-better-initiative/328)

[Tarefas](https://docs.google.com/document/d/1NFGr5Yig0jbZ1s9vI4GjUUHVGpdJlcuQSD2OL7Vlbfc/edit)

[Git Repo](https://github.com/zippiehq/cartesi-lambada-coprocessor)

O co-processor vai utilizar o consenso do EigenLayer.
[See YouTube explanation](https://youtu.be/-V-fG4J1N_M?si=7l9RC8S_W-GdO50K&t=2141)

Aqui o Co-founder do EigenLayer critica o merged mining do bitcoin
[Video](https://www.youtube.com/watch?v=HcEGXoC57Rw&t=1062s)

[EigenLayer Docs](https://docs.eigenlayer.xyz/)

[AVS Docs](https://docs.eigenlayer.xyz/eigenlayer/avs-guides/incredible-squaring#incredible-squaring-avs-lifecycle-flow)

[AVS Video](https://www.loom.com/share/50314b3ec0f34e2ba386d45724602d76?sid=9d68d8cb-d2d5-4123-bd06-776de2076de0)

[Vitalik Don't overload Ethereum's consensus](./vitalik/dont_overload.md)


## Cheat Sheet

[Original](https://gist.githubusercontent.com/stskeeps/983640ac4e2e072553347c859ba7712f/raw/76b7639ce2a04b0e939827f1581370f58fe4f5d6/gistfile1.txt)

```bash
mkdir -p ~/coprocessor-demo
cd coprocessor-demo
git clone https://github.com/Calindra/cartesi-application-templates -b lambada lambada-templates
cd lambada-templates/typescript
cartesi build



# open new terminal
cd ~/coprocessor-demo
git clone https://github.com/Calindra/cartesi-lambada-coprocessor coprocessor
cd coprocessor
git submodule update --init --recursive
cd contracts
# install forge before this , to get JSON 
forge build
cd ../demo
npm install
npm install ethers@5
cd ..
docker compose build
docker compose up
# wait until it says subscribed to TaskManager events or likes, then switch back to original terminal

# this uploads the built dapp to the coprocessors
curl -X POST -F file=@.cartesi/image/sample.car http://127.0.0.1:5001/api/v0/dag/import
curl -X POST -F file=@.cartesi/image/machine.car http://127.0.0.1:5001/api/v0/dag/import

curl -X POST -F file=@.cartesi/image/sample.car http://127.0.0.1:5002/api/v0/dag/import
curl -X POST -F file=@.cartesi/image/machine.car http://127.0.0.1:5002/api/v0/dag/import

curl -X POST -F file=@.cartesi/image/sample.car http://127.0.0.1:5003/api/v0/dag/import
curl -X POST -F file=@.cartesi/image/machine.car http://127.0.0.1:5003/api/v0/dag/import


PROGRAM_CID=`cat .cartesi/image/sample.car.cid` PROGRAM_INPUT="hello world" node ~/coprocessor-demo/coprocessor/demo/demo.mjs

# see resulting output hash + output + CID
```

The output should be something like:

```bash
taskInputHash: 0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad
Next Batch Index: 0
TaskBatchRegistered: 0 19 0xc6bad35add9f93184fd415062916deababef0e5f9bbcb0f95bff0471635b6c38
[
  '0x01701220196f55462c7009708dac87e44b677b5d07fc586d118a1fbc2d2fcacf68b9ea7e',
  '0xb94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9',
  resultCID: '0x01701220196f55462c7009708dac87e44b677b5d07fc586d118a1fbc2d2fcacf68b9ea7e',
  outputHash: '0xb94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9'
]
Task Responded: {
  batchIndex: 0,
  outputHash: '0xb94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9',
  resultCID: '0x01701220196f55462c7009708dac87e44b677b5d07fc586d118a1fbc2d2fcacf68b9ea7e'
}
Ethereum Block Number: 19
Ethereum Block Hash: 0xc6bad35add9f93184fd415062916deababef0e5f9bbcb0f95bff0471635b6c38
{
  metadata: {
    'ja62BU8gb23hXMVivcJog65z9/7tTcS2YxLgtQy5TTo=': 'pFjb5KvjYDW0RbBGsMwOAnhz1G7fEiD675bd0AOVDa8=',
    '8WDSbTPNI+IOj4tkz9WNQt7Ya4l1EIwIIIeGFEMoXj4=': 'AAAAAAAAABM=',
    'nA22OtVjDhZqtMnr7KwhbIiOXh14fhCBkCm8p6bxPyA=': 'xrrTWt2fkxhP1BUGKRbeq6vvDl+bvLD5W/8EcWNbbDg='
  },
  payload: 'aGVsbG8gd29ybGQ='
}
{ cid: 'bafybeiazn5kumldqbfyi3leh4rfwo625a76fq3irrip3yljpzlhwropkpy' }
Local compute job matches output of co-processor, result CID bafybeiazn5kumldqbfyi3leh4rfwo625a76fq3irrip3yljpzlhwropkpy output file hash: b94d27b9934d3e08a52e52d7da7dabfac484efe37a5380ee9088f7ace2efcde9
output file contents: hello world
```