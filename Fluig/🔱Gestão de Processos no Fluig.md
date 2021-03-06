## Gestão de Processos - BPM/ECM Essentials, Intermediate and Advanced

### 1. Sobre Processos de negócio

O que é BPM?

BPM (Business Process Management ou Gerenciamento de Processos de Negócio) é um modelo que abrange a modelagem, automação, execução, controle e melhoria contínua de processos de negócio.

O que é ECM?

ECM(Enterprise Content Management ou Gestão de Conteúdo Empresarial) é uma combinação dinâmica de estratégias, métodos e ferramentas que são utilizados para capturar, gerenciar, armazenar, preservar e oferecer informações de apoio aos processos organizacionais durante seu ciclo de vida.

### O que é processo ?

* Uma sequência continuada de fatos ou operações 
* Um processo sempre tem o intuito de alcançar algum resultado
* Para que este resultado seja alcançado é necessário que sejam executadas tarefas (atividades)
* Essas atividades devem ter um fluxo como o workflow

##### Workflow: Em resumo, é o passo a passo mais eficiente e prático para a execução de um trabalho.
É o método usado para organizar o fluxo de trabalho em uma empresa. Ele consiste na disposição e realização das atividades em sequência lógica, preferencialmente de forma automatizada.

### Conhecendo as propriedades do processo com modelagem:

##### BPMN (Business Process Model and Notation ou Modelo de Processo de Negócios e Notação) é uma notação para modelagem de processos de negócio. Em outras palavras, o BPMN estabelece um padrão para representar os processos graficamente, por meio de diagramas. 

##### OBS: Nos processo é possivel configurar papéis de quem efetuará o processo, grupo ou qualquer pessoa pode movimentar esse processo

🟩- Início
-Indica o início do processo

-Usuários que tiverem a permissão poderão iniciar o mesmo através da tela de inicialização de solicitações do fluig

-As permissões são definidas através do mecanismo de atribuição desta atividade

-O fluig aceitará apenas uma única instância de objeto de Início comum por diagrama

-Controle de Tempo de expiração da tarefa, notificação de gestor ou solicitante, tempo de tolerência de atraso ou mesmo tempo de expediente da sua empresa para não aceitar dar continuidade no fim de semana por exemplo onde ninguém trabalha(no nosso exemplo)

🟥- Fim
-Indica o fim do processo

-Esta tarefa não é atribuída a nenhum usuário

-Não ocorrem processamentos após o final da solicitação(exceto via desenvolvimento)

-É possível ter um ou mais Finais comuns

-Neste componente podemos alterar o nome e marcar quais os usuários que serão notificados ao chegar nesta atividade.

⬜- Atividade comum
-É a unidade básica da separação de um processo em atividades
-Deverá ser executado por um usuário para dar andamento a solicitação

🟨- Automático (Gateway Exclusivo)
Irá decidir o destino de um processo através de programação que
será utilizada para mover o processo para a atividade relacionada
Apenas um caminho poderá ser percorrido utilizado este tipo de gateway.
 Além de alterar o nome de exibição, neste componente podemos definir quais as condições a serem validadas bem como as atividades de destino.
-EX:
Expressão de escolha no Automático: hAPI.getCardValue("id_campo_desejado exemplo: tipo_hardware_software")==Resposta desejada.

3. Exemplo campo qual o tipo de problema? 1(Hardware) ou 2(Software)

R:1

na programação da atividade automática em Expressão:

hAPI.getCardValue("tipo_hardware_software")==1 = Hardware

hAPI.getCardValue("tipo_hardware_software")==2 = Software

dependendo da resposta ela terá caminhos diferentes, passando para outros processos.

🟩- Fluxo Comum
-Padrão para movimentação de atividades
-Permite que uma atividade seja movimentada sem a possibilidade de retorno
-Ex:

Movimentei o processo de tipo de problemas e nenhum se encaixou, coloco uma resposta diferente ou opção "outros" para movimentar em outro processo que pode ser para ser analisado por um membro do departamento de TI

🟥- Fluxo de Retorno
-Permite retorno para a atividade de origem
-Ex:

Não entendi o problema. Detalhe melhor os detalhes.

e quando enviar, terá a opção de retorno ao solicitante.

🟨- Fluxo Automático 
-Se o prazo da atividade for concluído sem que ela tenha sido movimentada, será movido automaticamente

-Obrigatório que a atividade de origem tenha um prazo definido e que uma tarefa agendada seja configurada (Fluxo automático)

-Ex:

Movimentei para a analista de RH, ela no tempo definido não viu( por quê estava de licença sem sabermos) logo com o fluxo automático ele manda por exemplo para o gestor do RH e ele da continuidade ao processo.

🟦- Swinlane:
-Componente é utilizado para definir o escopo de cada processo  e possibilita identificar os papéis responsáveis pela execução 

📒- Documento
 -Permite anexar ao diagrama um documento previamente publicado no fluig a fim de que o mesmo possa ser consultado durante a fase de execução de um processo

📝- Anotação
 -Permite adicionar notas explicativas para facilitar o entendimento do processo por todos os envolvidos

🎗- Fork & Join:
 -Fork e Join indicam, respectivamente, o início e o fim das atividades paralelas
-Caso existam atividades paralelas pendentes, o processo fica posicionado no Join, até que todas as atividades sejam concluídas

⬜- Subprocesso:
-Alterar as características do componente e selecionar qual subprocesso será inicializado ao chegar nesta atividade.

⬛- Subprocesso Ad Hoc
-Criar lista de tarefas, definir o que será feito o responsável em executar a tarefa e qual o prazo. 

##### OBS: Em propriedades do Processo, temos variadas funções como a aba de versão adicionar nova versão com um descrição com as opções de atualizar a versão dentro dos anexos dos processos e também confirmação de senha para fazerem os processos, na aba de segurança de anexos podemos privar acesso dos usuários sobre a publicação, editamento e removeção anexos dele ou de outros usuários.

### O que são mecanismos de atribuição ? 

* Os Mecanismos de Atribuição permitem restringir as opções de usuários que podem receber ou assumir uma determinada atividade do processo

* Cada mecanismo permite que apenas determinado usuário ou usuários estabelecidos pela lógica interna do mecanismo tenham controle sobre a respectiva atividade

Atribuições: 

* Para um Papel (Pool) = Qualquer um dos usuários no papel escolhido pode assumir as tarefas para completá-las

* Para um Grupo (Pool) = Qualquer um dos usuários no grupo escolhido pode assumir as tarefas para completá-las

* Por Associação = Permite compor lógicas complexas de atribuição através da associação de vários mecanismos

* Por Campo de Formulário = Permite atribuir tarefas ao usuário informado em um campo do formulário do processo

### Regras nos campos de formulário:

Podemos adicionar regras nos campos do formulário para definir o comportamento dos campos em todas as atividades do processo.

### Exportação dica: Podendo ser exportado o processo criados, já feitos e baixá-los em formato aberto no Excel, para dar uma organizada rápida selecio as colunas na setinha esquerda do lado do A1 e depois de selecionar todos os campos clique na linha entre os campos para organizá-los e CTRL+SHIFT+L = Filtro Rápido

### Campo de Painel de Controle:

* Expediente, dias e horas que a empresa trabalha podendo ser sujeitos a mudança

* Feriados programados e únicos, como por exemplo um aniversário da empresa de 15 anos

* Valor hora-usuário onde programamos por usuários seu cálculo de salário por horas trabalhadas, para cumprir sua jornada por exemplo de 8 horas por dia nos 5 dias da semana.

* Temas de Formulários onde se personaliza as cores e modelos de um formulário e pode ser escolhido na sua criação

* Gerador de Imagem de Processo, imagem do fluxograma de um processo, que pode ser usado como modelo ou apresentação

### Extra: Approval Fluig

* Aplicativo destinado a pessoas com papéis de finalizar ou dar continuidade para o processo pela sua decisão, podendo ser visualizada nesse app

