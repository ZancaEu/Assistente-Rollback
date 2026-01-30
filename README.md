# Como e por que o projeto foi desenvolvido.

## Este projeto foi desenvolvido durante um evento interno de desenvolvimento utilizando plataformas de vibe coding (Lovable).

## O projeto serviu como um experimento para familiarização com a plataforma e com o conceito de vibe code.

## Este projeto não foi realizado com o intuito de ser utilizado ou propriamente desenvolvido. O projeto foi realizado apenas como uma oportunidade de aprendizado e utiliza dados fictícios.


# Definição do Projeto


### Ele consiste de uma plataforma que monitora deploys em ambientes como production, staging e development, com integração com a ferramenta de CI Jenkins utilizada para os deploys no cluster.

### A aplicação cruza informações de deploys no jenkins com aplicações em estados problemáticos (Error, Terminated, Failed, CrashLoopBackOFF, ImagePullBackOFF, etc...) em um cluster kubernetes e 
### toma uma ação de rollback conforme uma regra definida na aplicação, podendo ser um rollback automático ou que necessita de aprovação. A aplicação também armazena e analisa logs da aplicação 
### para fornecer insights em qual pode ter sido o problema que estava afetando a aplicação, os logs ficam armazenados para análise futura dos responsáveis.


# Funcionalidades

## Dashboards e Incidentes


### A aplicação fornece dashboards simples que apresentam dados como Total de pods no sistema, Pods saudáveis e Pods problemáticos e Rollbacks de hoje. Além de um dashboard de Saúde de Cluster com a porcentagem de Pods saudáveis e Pods problemáticos.
### A seção de incidentes apresenta um histórico dos rollbacks efetuados e dados sobre a aplicação antes do rollback, como Nome, Ambiente, Status, Logs, Revision e uma análise rápida do sistema.


## Usuários e Times


### A aplicação conta um sistema de roles para usuários, com permissões específicas e restritas para certos usuários, como criação e edição de regras, aprovação ou reprovação de rollbacks e gerenciamento geral do sistema.
### Além do controle de permissões por usuário também é possível definir times, se um usuário estiver incluso em um time suas permissões se aplicarão apenas a aplicações, regras, rollbacks e outras funcionalidades do seu respectivo time.


## Regras de Rollback


### As regras de rollback podem ser definidas a vários níveis de atuação, sendo elas regras de Cluster (Afetam todo o ambiente, disponível apenas para admins e gerentes), Namespace, Grupo ou Aplicação individual.
### Usuários com as permissões suficientes podem agrupar aplicações em grupos, podendo selecionar apenas aplicações do seu respectivo time, estes grupos podem ser utilizados para aplicar regras de rollback a várias aplicações.

### As regras consistem de configurações como seleção de escopo (Cluster, Namespace, Grupo, Aplicação), Ambiente para Cluster, Ambiente e Namespace para Namespace, Ambiente e Grupo para Grupo Ambiente, Namespace e Aplicação para Aplicação.
### Modo de Rollback (Automático ou Requer Aprovação), Tempo de espera até acionar a regra e minímo de pods em estado problemático para acionar a regra.
### Também é possível definir condições especiais para acionamento da regra como um número de restarts maior ou igual a um certo valor. 
### Tags podem ser definidas em uma regra para melhor definição.
