# PLANEJAMENTO DO ENTREGÁVEL 1

## DURAÇÃO DO PROJETO
* **Período:** 04/05/2026 a 14/06/2026
* **Duração total:** 1,5 meses
* **Quantidade de Sprints:** 3
* **Time box por Sprint:** 14 dias

---

## OBJETIVO DO PROJETO
Desenvolver um ecossistema digital com padrão Premium para centralizar a gestão de treinamentos dos lojistas do **Flamboyant JP Mall**. A plataforma automatizará a entrada de dados (via importação inteligente de planilhas), calculará KPIs de engajamento em tempo real (Radar de Risco) e permitirá a exportação de dossiês gerenciais (PDF/Excel) para prestação de contas e tomada de decisão.

---

## PRODUTOS DO ENTREGÁVEL 1
- [ ] **Banco de dados relacional** estruturado na nuvem (Supabase) com 3 tabelas centrais (Lojas, Treinamentos, Presenças).
- [ ] **Módulo de registro de treinamentos** (registro completo do treinamento e tudo relacionado a ele)
- [ ] **Módulo completo de registro de presenças** (Inserção manual e Importação de Planilhas Excel).
- [ ] **Funcionalidade de Importação Inteligente** de Planilhas (Drag-and-drop).
- [ ] **Dashboard Executivo simplificado** com Gráficos interativos (Drill-down para Calendário), Radar de Risco (Lojas Omissas) e Top 5 Lojas Engajadas.
- [ ] **Histórico de participação** integrado ao perfil da loja e cálculo de porcentagem de engajamento.
- [ ] **Motor de geração e exportação** de relatórios em PDF (Dossiê da Loja) e Excel (.xls) com formatação da marca.

---

## CADÊNCIAS DO PROJETO

* **Planning / Review / Retro:**
  * Frequência: Quinzenal (Início e fim da Sprint)
  * Horário: Quintas-Feiras, 18h50 - 20h20.

* **Status semanal:**
  * Frequência: Semanal
  * Horário: Quintas-feiras, 20h40 - 22h00

* **Report ao cliente:**
  * Frequência: Final de cada Sprint

* **Entrega formal:**
  * Data: 22/06/2026

---

## TIMES / ÁREAS ENVOLVIDAS
* Backend
* Frontend
* QA / Testes

---

## RISCOS INICIAIS
- [ ] **Risco 1:** Sobrecarga técnica na Sprint 1 devido à complexidade de estruturar o banco e o motor de upload simultaneamente.
- [ ] **Risco 2:** Dificuldade na sanitização de dados caso as planilhas importadas fujam muito do template padrão.
- [ ] **Risco 3:** Complexidade no roteamento de estados (Drill-down do Gráfico de Barras para a View de Calendário).
- [ ] **Risco 4:** Limitações de renderização visual ao converter componentes HTML para PDF no Frontend.

---

## DEPENDÊNCIAS
- [ ] **Entre grupos:** O motor de cálculo do Dashboard (Sprint 2) depende do sucesso da importação de dados da Sprint 1.
- [ ] **Tecnológicas:** Bibliotecas de parser de planilhas (`papaparse` ou `xlsx`) e de geração de PDF (`html2pdf`).
- [ ] **Dados / APIs:** Definição clara do `.env` e chaves de segurança do Supabase.

---

## SPRINT 1 (SPT 01) - Fundação e Gestão de Presenças
**Período:** 04/05 a 17/05

### OBJETIVO DA SPRINT
Estruturar a base de dados do sistema, permitir a criação de treinamentos e entregar a funcionalidade central de apontamento de presenças de forma manual.

### ENTREGÁVEIS DA SPRINT
- [ ] **Entregável 1:** Banco de Dados configurado e criação de treinamentos funcional.
- [ ] **Entregável 2:** Inserção manual e exclusão de presenças dentro de um Treinamento.
- [ ] **Entregável 3:** Importação Inteligente de Planilhas (CSV/Excel) com sanitização de dados e download de modelo.
- [ ] **Entregável 4:** Criar o sistema de lista e adição de treinamentos.  
- [ ] **Entregável 5:** Layout Base do CRM (Sidebar, Headers, Padrão de Cores e Zero Emojis).

### REQUISITOS (Conforme Documentação)
- [ ] **RF-01:** Registro de treinamento com campos para Tema, Data, Conteúdo.
- [ ] **RF-02:** Upload de arquivos de planilha para registro de presenças.
- [ ] **RF-03:** Leitura de planilha e vínculo automático de representantes via código LUC.
- [ ] **RF-05:** Alerta de erro para códigos LUC inexistentes na base.
- [ ] **RF-06:** Exclusão manual de registro de presença.
- [ ] **RF-07:** Botão para download de planilha modelo/template.
- [ ] **RF-10:** Exibição da lista de lojas e representantes participantes de um treinamento.
- [ ] **RF-11:** Registro de observações associadas ao treinamento.

### TAREFAS TÉCNICAS
**Backend:**
- [ ] Modelagem do banco de dados (Lojas, Treinamentos, Presenças).
- [ ] Endpoint de criação e listagem de Treinamentos.
- [ ] Endpoint de Inserção/Exclusão manual de presenças.
- [ ] Endpoint de Bulk Insert (Processamento em lote) com validação de LUC.

**Frontend:**
- [ ] Desenvolvimento do Layout base.
- [ ] Telas de cadastro e listagem de treinamentos.
- [ ] Componente Dropzone para upload e download de template.
- [ ] Tabela interativa de lista de presença.

---

## SPRINT 2 (SPT 02) - Histórico, Métricas e Buscas
**Período:** 18/05 a 31/05

### OBJETIVO DA SPRINT
Dar vida ao sistema. Interligar as lojas aos treinamentos através da tabela de presenças, desenvolver a visualização de Calendário e conectar a matemática de KPIs ao Dashboard Estratégico.

### ENTREGÁVEIS DA SPRINT
- [ ] **Entregável 1:** Aba de perfil da loja contendo seu histórico de participação.
- [ ] **Entregável 2:** Dashboard com o cálculo da porcentagem de engajamento do lojista.
- [ ] **Entregável 3:** Barra de pesquisa multifuncional para a listagem de treinamentos.
- [ ] **Entregável 4:** Dashboard Executivo gerando dados reais (Radar de Risco e Top 5).
- [ ] **Entregável 5:** Visão de Calendário interativa e navegação Drill-down.

### REQUISITOS (Conforme Documentação)
- [ ] **RF-04:** Histórico de treinamentos da loja dentro do perfil da loja.
- [ ] **RF-08:** Barra de pesquisa para filtrar eventos por Tema, Conteúdo ou Data.
- [ ] **RF-12:** Cálculo automático da porcentagem de participação (Presenças / Total de Eventos).

### TAREFAS TÉCNICAS
**Backend:**
- [ ] Queries de histórico filtradas por LUC.
- [ ] Rota analítica para cálculo de engajamento.
- [ ] Implementação de query strings para busca de eventos.
- [ ] Rastreamento de KPIs (Taxa de presença, Lojas Impactadas, Média de Colaboradores, Total Participantes).

**Frontend:**
- [ ] Componente "Store Explorer" (Perfil da Loja).
- [ ] Painel de indicadores de engajamento (UI limpa).
- [ ] Implementação de filtros e busca em tempo real.

**QA / TESTES:**
- [ ] Validação do cálculo percentual (prevenção de erro de divisão por zero).

---

## SPRINT 3 (SPT 03) - Relatórios e Exportações
**Período:** 01/06 a 14/06

### OBJETIVO DA SPRINT
Finalizar o produto implementando as funcionalidades de exportação que permitem a análise e prestação de contas externas do engajamento dos lojistas.

### ENTREGÁVEIS DA SPRINT
- [ ] **Entregável 1:** Exportação do Dossiê de Loja em formato PDF.
- [ ] **Entregável 2:** Planilha Dinâmica Inteligente (Excel .xls formatado).
- [ ] **Entregável 3:** Ajustes finais de UI/UX e correção de bugs (Homologação Final).

### REQUISITOS (Conforme Documentação)
- [ ] **RF-09:** Exportação de relatórios de participação nos formatos PDF e Excel.

### TAREFAS TÉCNICAS
**Frontend:**
- [ ] Biblioteca para captura de componentes e geração de PDF A4.
- [ ] Script de estruturação de tabelas HTML para exportação nativa `.xls`.
- [ ] Testes de layout para garantir fidelidade visual e formatação condicional.

**QA / TESTES:**
- [ ] Testes de quebra de página no PDF.
- [ ] Validação de integridade de colunas no Excel.
