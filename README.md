# SRE Platform Challenge

Bem vindo(a), e obrigado pelo seu interesse na Stone! Esse desafio será importante para te avaliarmos e para você entender melhor como é o nosso dia a dia. Por isso, pensamos em um desafio bem próximo a nossa realidade.

É importante ressaltar que nenhum código produzido por você nesse desafio será utilizado na Stone, tudo que for feito será utilizado apenas para te avaliar nesse desafio.

Essa base de código é a que utilizaremos para nosso livecoding. É importante que você se sinta confortável com ele e entenda os conceitos, além disso que esteja apto a modificar esse código durante o LiveCoding.

## Resumo do Desafio

O produto do nosso time é uma plataforma interna para desenvolvedores. A plataforma é capaz de provisionar recursos para aplicações, como repositórios, pipelines de CI/CD e databases.

A plataforma é construída extendendo a API do Kubernetes usando o padrão `Operator`, assim ela pode ser consumida com uma abordagem de IaC (Infra as Code) ou integrada como uma API HTTP.

Você deverá implementar algumas funcionalidades em um operator que deve ser capaz de gerenciar o ciclo de vida de um Repositório do GitHub.

Um exemplo do manifesto Kubernetes que representa o CRD (_Custom Resource Definition_) é:

```yaml
apiVersion: repositories.platform.buy4.io/v1alpha1
kind: Repository
metadata:
  name: example
spec:
  name: golang-best-practices
  owner: stone-payments
  type: OpenSource # or ClosedSource
  credentialsRef:
    name: github-credentials
    key: token
```

Os possíveis campos no spec do CRD são:

- `name` (obrigatório): nome do repositório no GitHub.
- `owner` (obrigatório): nome do owner do repositório no GitHub.
- `type` (obrigatório): tipo do repositório a ser criado.
- `credentialsRef` (obrigatório): referência para uma chave de um `Secret` que conterá um PAT (_Personal Access Token_) para se autenticar com a API do GitHub.
- `description` (opcional): a descrição do repositório.

## Como será o LiveCoding

O código neste repositório já apresenta uma implementação inicial incompleta. Você deve implementar as tarefas descritas nos entregáveis que os avaliadores te indicarem durante o LiveCoding.

Dentro deste repositório, existem duas principais pastas: `client` e `controllers`.

A pasta `client` contém todo código responsável por se comunicar com a API do GitHub.

A pasta `controllers` contém a implementação do operator `Repository`, que utiliza o pacote `client`.
> É importante ressaltar que você deve utilizar o client que está neste repositório e não um sdk externo. A utilização, melhoria e implementação dele também fazem parte do desafio.

Testes também são importantes e vão ser levados em consideração no desafio.

## Setup de desenvolvimento local

Durante o ciclo de desenvolvimento, recomendamos que utilize um cluster local. Isso evita faturas em cloud providers e torna o ciclo de desenvolvimento mais simples. Para isso, recomendamos que utilize qualquer uma das ferramentas abaixo:
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Kind](https://kind.sigs.k8s.io/)
- [K3D](https://k3d.io/)

Depois dessa instalação, siga o [Quick Start do Kubebuilder](https://kubebuilder.io/quick-start.html#test-it-out) para entender como utilizar o Makefile do repositório para auxiliar no seu processo de desenvolvimento.

## Referências

Para ajudá-lo no processo de estudos sobre os assuntos, separamos alguns materiais de estudos:

### Go

- [A Tour of Go](https://go.dev/tour/)
- [Aprenda Go com Testes](https://larien.gitbook.io/aprenda-go-com-testes/)
- [Effective Go](https://go.dev/doc/effective_go)

### Kubernetes
- [Secrets](https://kubernetes.io/pt-br/docs/concepts/configuration/secret/)
- [Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)

### Kubernetes Operator/Kubebuilder

- [Kubernetes Operator simply explained in 10 mins](https://youtu.be/ha3LjlD6g7g)
- [The Kubebuilder Book](https://kubebuilder.io/)
- [Tutorial: Deep Dive into the Operator Framework for... Melvin Hillsman, Michael Hrivnak, & Matt Dorn](https://youtu.be/8_DaCcRMp5I) - (até os 37 minutos)
- [Writing a Kubernetes Operator from Scratch Using Kubebuilder - Dinesh Majrekar](https://youtu.be/LLVoyXjYlYM)

### Testes
- [Testing framework Ginkgo](https://onsi.github.io/ginkgo/)
- [Testing Kubernetes CRDs - Christie Wilson, Google](https://youtu.be/T4EB0KB1-fc)
