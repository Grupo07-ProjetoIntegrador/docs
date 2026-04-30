# Pacote 1 – Estudo de Caso

## Área de Requisitos de Software

---

## 1. Identificação do Projeto

* **Nome do Projeto:** Sistema JP Mall (Módulo de Treinamentos)
* **Equipe / Grupo:** Grupo 7 - Treinamentos
* **Data:** 02/04/2026
* **Stakeholders principais:** Jéssica Pedrosa

---

## 2. Necessidades

### 2.1 Descrição das Necessidades

* **N01** - O shopping necessita documentar as ações de capacitação (palestras e treinamentos) em um repositório único, eliminando a fragmentação de registros em pastas físicas ou arquivos isolados.
* **N02** - O controle de participação dos lojistas é manual, sendo necessário registrar as presenças de forma estruturada para armazenamento de dados.
* **N03** - Não há controle estruturado da participação dos lojistas em eventos e treinamentos, sendo necessário registrar e acompanhar essas participações.
* **N04** - A área de relacionamento precisa metrificar a porcentagem de participação de cada loja em treinamentos e palestras.

### 2.2 Problemas Identificados

  A atual falta de centralização e automação faz com que o registro de presenças se perca em listas de papel ou ficheiros isolados. Isso impossibilita a administração de cruzar o nível de engajamento das lojas com a sua performance real de vendas.

### 2.3 Objetivos do Sistema

  Automatizar a importação de listas de presença através de upload de planilhas e criar um histórico visual no perfil de cada loja, metrificando o engajamento do lojista em treinamentos e palestras. Além disso, criar uma aba de treinamentos que armazena todo o histórico de treinamentos/palestras.


---

## 3. Fontes de Requisitos

| Tipo de Fonte       | Descrição                                                                 | Método de Coleta                                                                                                   |
| ------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Stakeholders        | Jéssica Pedrosa                                                           | Entrevista presencial de levantamento de requisitos na UFG.                                                        |
| Documentos          | Projeto Integrador - Escopo                                               | Análise dos documentos do escopo do projeto.                                                                     |
| Sistemas existentes | Mallcomm                                                                  | Análise Documental: Estudo dos white papers e manuais de produto do fornecedor.                                    |
| Observação          | Planilha de controle de presenças                                         | Análise do fluxo manual de listas de presença. (A entender via e-mail o template da planilha).                     |

---

## 4. Escopo do Produto

### 4.1 Dentro do Escopo

Registro de treinamentos e palestras (com Tema, Data e Conteúdo) em uma aba chamada “Treinamento”. Controle de participação vinculando o representante à loja correspondente. Upload de planilhas de listas (em Excel). Apresentação do histórico de participação no perfil da loja.

### 4.2 Fora do Escopo

Não contemplará a inscrição de participantes diretamente no sistema, nem o envio automático de convites, notificações ou confirmações. Sua atuação será restrita ao cadastro dos treinamentos e ao registo e acompanhamento das presenças importadas por planilha.

### 4.3 Descrição Geral do Produto

Um submódulo focado na inteligência de relacionamento, que transforma as planilhas de presença num histórico associado ao LUC (Loja de Uso Comercial), permitindo avaliar o grau de parceria da loja.

---

### 5. Histórias de Usuário (Com Critérios de Aceitação)

#### Funcionalidade #01:
**COMO:** Analista de relacionamento.  
**QUERO:** Fazer o upload de uma planilha com a lista de presenças.  
**PARA:** Registar de forma massiva e rápida quais os funcionários que compareceram.  

**Critérios de Aceitação:**
* **Cenário 1: Upload bem-sucedido**
  * **DADO** que o analista está na tela do treinamento e seleciona um arquivo Excel válido (menor que 5MB) com os códigos LUC preenchidos,
  * **QUANDO** ele clica em "Importar Lista",
  * **ENTÃO** o sistema processa o arquivo em menos de 10 segundos (RNF01), vincula os representantes às lojas (RF03) e exibe uma mensagem de sucesso.
* **Cenário 2: Arquivo excede o tamanho limite**
  * **DADO** que o analista tenta importar um arquivo maior que 5MB (RN01),
  * **QUANDO** ele anexa o arquivo e tenta prosseguir,
  * **ENTÃO** o sistema bloqueia a importação e exibe um erro informando o limite máximo permitido.
* **Cenário 3: Validação de LUC Inexistente**
  * **DADO** que a planilha possui linhas com códigos LUC que não existem no banco de dados,
  * **QUANDO** o sistema realiza o processamento da leitura,
  * **ENTÃO** o sistema emite um alerta de erro apontando quais linhas/LUCs falharam (RF05) e não processa essas linhas específicas.
* **Cenário 4: Prevenção de duplicidade**
  * **DADO** que o analista realiza o upload de uma planilha que contém presenças já cadastradas para o mesmo treinamento,
  * **QUANDO** o sistema processa os dados,
  * **ENTÃO** o sistema ignora os registros duplicados (RN04) e adiciona apenas as novas presenças.

---

#### Funcionalidade #02:
**COMO:** Gestor de treinamento do shopping.  
**QUERO:** Registar um novo evento definindo o Tema, Data e Conteúdo.  
**PARA:** Criar uma base de dados organizada das ações de treinamento/palestras oferecidas no ano.  

**Critérios de Aceitação:**
* **Cenário 1: Cadastro válido**
  * **DADO** que o gestor acessa a aba "Treinamentos" e clica em cadastrar,
  * **QUANDO** ele preenche todos os campos obrigatórios (Tema, Data, Conteúdo) (RF01) e clica em "Salvar",
  * **ENTÃO** o sistema registra o evento e atualiza a lista de treinamentos disponíveis.

---

#### Funcionalidade #03:
**COMO:** Gerente de Relacionamento.  
**QUERO:** Visualizar o histórico completo de participação em treinamentos no perfil de uma loja.  
**PARA:** Entender o nível de engajamento do lojista.  

**Critérios de Aceitação:**
* **Cenário 1: Loja ativa e com histórico**
  * **DADO** que o gerente acessa a página de perfil de uma loja com contrato "Ativo" (RN02),
  * **QUANDO** ele navega até a aba interna de treinamentos,
  * **ENTÃO** o sistema exibe a lista cronológica de todos os eventos em que aquela loja registrou presença (RF04).

---

#### Funcionalidade #04:
**COMO:** Gestor de treinamento.  
**QUERO:** Visualizar os detalhes de um treinamento.  
**PARA:** Verificar quais lojas e representantes participaram.  

**Critérios de Aceitação:**
* **Cenário 1: Exibição de detalhes do evento**
  * **DADO** que o gestor está na lista geral de treinamentos,
  * **QUANDO** ele clica no nome de um treinamento específico,
  * **ENTÃO** o sistema abre uma tela contendo o Tema, Data, Conteúdo, observações registradas (RF11) e uma tabela com os nomes das lojas (LUC) e seus respectivos representantes presentes (RF10).

---

#### Funcionalidade #05:
**COMO:** Analista de relacionamento.  
**QUERO:** Filtrar treinamentos por tema ou data.  
**PARA:** Localizar eventos rapidamente.  

**Critérios de Aceitação:**
* **Cenário 1: Filtro com resultados**
  * **DADO** que o analista está visualizando o catálogo na aba "Treinamentos",
  * **QUANDO** ele utiliza a barra de pesquisa digitando um "Tema" específico ou seleciona uma "Data" e clica em buscar (RF08),
  * **ENTÃO** o sistema filtra e exibe apenas os treinamentos que correspondem aos parâmetros informados.

---

#### Funcionalidade #06:
**COMO:** Gestor de treinamento.  
**QUERO:** Exportar relatório de participação.  
**PARA:** Analisar o engajamento dos lojistas.  

**Critérios de Aceitação:**
* **Cenário 1: Exportação de dados**
  * **DADO** que o gestor aplicou filtros ou está na visão geral de um treinamento,
  * **QUANDO** ele aciona a opção "Exportar",
  * **ENTÃO** o sistema disponibiliza opções para baixar o documento em formato PDF ou Excel (RF09) contendo os dados visualizados na tela.

---

#### Funcionalidade #07:
**COMO:** Analista de relacionamento.  
**QUERO:** Baixar o modelo de planilha.  
**PARA:** Garantir que o upload siga o formato correto.  

**Critérios de Aceitação:**
* **Cenário 1: Download do Template**
  * **DADO** que o analista está na tela de upload para importar presenças,
  * **QUANDO** ele clica no botão/link "Baixar Modelo Padrão" (RF07/RNF03),
  * **ENTÃO** o sistema realiza o download automático de um arquivo Excel contendo as colunas obrigatórias vazias (ex: LUC, Nome do Representante).

---

#### Funcionalidade #08:
**COMO:** Analista de relacionamento.  
**QUERO:** Visualizar um indicador percentual de presença da loja em relação ao total de treinamentos do período.  
**PARA:** Classificar o nível de engajamento do lojista antes de uma reunião de negociação.  

**Critérios de Aceitação:**
* **Cenário 1: Exibição da métrica de engajamento**
  * **DADO** que o analista acessa o perfil de uma loja na plataforma,
  * **QUANDO** a aba/seção de engajamento carrega,
  * **ENTÃO** o sistema exibe automaticamente um percentual, resultante da divisão do número de treinamentos que a loja compareceu pelo total de treinamentos ativos no período (RF12).

---

## 6. Requisitos Funcionais

| ID    | Descrição |
| ----- | --------- |
| RF01 | O sistema deve permitir o registro de um treinamento com campos para Tema, Data, Conteúdo. |
| RF02 | O sistema deve permitir o upload de arquivos de planilha para registro de presenças em treinamentos. |
| RF03 | O sistema deve ler a planilha e vincular automaticamente os representantes presentes às suas respectivas lojas, baseando-se no código LUC. |
| RF04 | O sistema deve conter o histórico de treinamentos em que a loja participou dentro do perfil da loja. |
| RF05 | O sistema deve emitir um alerta de erro caso a planilha contenha códigos LUC inexistentes na base de dados. |
| RF06 | O sistema deve permitir a exclusão manual de um registo de presença vinculado a uma loja. |
| RF07 | O sistema deve possuir um botão para o download da planilha modelo em branco com os cabeçalhos exatos exigidos para a importação de presenças. |
| RF08 | O sistema deve disponibilizar uma barra de pesquisa para filtrar eventos pelo "Tema", "Conteúdo" ou “Data”. |
| RF09 | O sistema deve permitir a exportação de relatórios de participação em treinamentos nos formatos PDF e Excel. |
| RF10 | O sistema deve exibir a lista de lojas e representantes participantes de um treinamento. |
| RF11 | O sistema deve permitir o registro de observações sobre o treinamento, associado ao cadastro do treinamento. |
| RF12 | O sistema deve calcular automaticamente a porcentagem de participação da loja, dividindo o número de presenças confirmadas pelo número total de treinamentos cadastrados no intervalo de tempo selecionado. |

---

## 7. Requisitos Não Funcionais

| ID     | Categoria       | Descrição |
| ------ | --------------- | --------- |
| RNF01 | Desempenho      | O processamento e importação dos dados de uma planilha com até 300 linhas não deve exceder 10 segundos. |
| RNF02 | Segurança       | O upload de listas de presença só pode ser realizado por utilizadores com permissões para cadastro. |
| RNF03 | Usabilidade     | O sistema deve apresentar o modelo padrão (template de Excel) para descarregamento na seção de upload, garantindo que o utilizador saiba o formato correto. |
| RNF04 | Disponibilidade | O histórico de treinamentos geral deve carregar ao abrir a aba de ‘‘Treinamentos’’. |
| RNF05 | Auditoria       | O sistema deve registrar a data, a hora e o usuário responsável por importar uma lista de presenças. |

---

## 8. Regras de Negócio

| ID    | Regra |
| ----- | ----- |
| RN01 | O sistema deve aceitar apenas arquivos de planilha com tamanho máximo de 5MB. |
| RN02 | Somente lojas com status de contrato “Ativo” podem ter presenças registradas em treinamentos. |
| RN03 | O código LUC é obrigatório para identificação da loja no processamento da planilha de presença. |
| RN04 | Caso uma planilha seja reenviada para o mesmo treinamento, o sistema deve evitar duplicação de registros já existentes. |

---

## 9. Fluxos de Estados (Faremos depois)

### 9.1 Descrição do Fluxo
* -

### 9.2 Estados Identificados
* -

### 9.3 Transições
* -

---

## 10. Rastreabilidade

| Necessidade | História de Usuário | RF | RNF | RN |
| ----------- | ------------------- | -- | --- | -- |
| N01 | HU-02, HU-05 | RF-01, RF-08, RF-11 | RNF-04 | RN-01 |
| N02 | HU-01, HU-07 | RF-02, RF-03, RF-05, RF-07 | RNF-01, RNF-02, RNF-03, RNF-05 | RN-03, RN-04 |
| N03 | HU-03, HU-04 | RF-04, RF-06, RF-10 | RNF-04 | RN-02 |
| N04 | HU-03, HU-06, HU-08 | RF-04, RF-12 | RNF-01, RNF-04 | RN-02 |

---

## 11. Observações Gerais

* O Módulo de Treinamento é responsável por construir um sistema robusto de upload de arquivos Excel, além de construir uma base de dados completa de cada treinamento/palestra sendo registrado temas, datas e lojas participantes com o intuito de armazenar essas informações como estratégia de negociações para contratos com os lojistas.
