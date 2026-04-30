# Pacote 3 – Critérios de Aceite

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



