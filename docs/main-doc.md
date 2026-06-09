# Documento de Especificação de Requisitos e Modelagem (DERM) do software NutriRim
Projeto: NOME Versão: 0.2.0-alpha Data: 5 de Junho de 2026  
Alunos: Francisco Felipe Sampaio Neto, Raimundo José de Sousa Neto, Carlos Eduardo, José Victor de Moura Rufino

---
### 1. Histórico de Revisões

Versão | Data | Descrição | Autor
-| - | - | -
0.1.0-alpha | 05/06/2026 | Inicio da documentação | Francisco Felipe
0.1.1-alpha | 06/06/2026 | Requisitos funcionais adicionados | Francisco Felipe
0.1.2-alpha | 06/06/2026 | Atualização nos requisitos funcionais e adicionado regras de negócio | Francisco Felipe
0.1.3-alpha | 06/06/2026 | Atualização nos IDs dos requisitos funcionais e regras de negócio. Adicionado requisitos não funcionais | Raimundo Neto
0.1.4-alpha | 07/06/2026 | Criação dos diagramas de seqência | Francisco Felipe
0.1.5-alpha | 07/06/2026 | Criação do diagrama de implantação | Francisco Felipe
0.1.6-alpha	| 07/06/2026 | Criação do diagrama de caso de uso	Raimundo Neto
0.1.7-alpha	| 07/06/2026 | Criação do diagrama de classes	Raimundo Neto
0.1.8-alpha	| 07/06/2026 | Criação do diagrama de atividades	Raimundo Neto
0.1.9-alpha	| 07/06/2026 | Criação dos protótipos	Francisco Felipe
0.2.0-alpha	| 08/06/2026 | Atualização dos requisitos funcionas, não funcionais e regras de negócio	Francisco Felipe
0.2.1-alpha	| 08/06/2026 | Atualização no diagrama de sequência	Francisco Felipe
0.2.2-alpha	| 08/06/2026 | Atualização no diagrama de implantação	Francisco Felipe
0.2.3-alpha	| 08/06/2026 | Atualização no protótipos de tela	Francisco Felipe
0.2.4-alpha | 08/06/2026 | Atualização no diagrama de caso de uso	Raimundo Neto


### 2. Introdução
#### 2.1. Objetivo  
Este documento descreve os requisitos funcionais e não funcionais, bem como a modelagem UML para o sistema para controle alimento e de água de pacientes com problemas renais de acordo com o perfil do usuário

#### 2.2. Escopo  
O sistema irá auxiliar a nutrição de pacientes com problemas renais, com controle de água, alimentos e nutrientes consumidos. Ele irá atuar mapeando o perfil do usuário, realizando checklists diários, sugerindo receitas que encaixem na dieta e contará com um chatbot para dúvidas e suporte.


### 3. Levantamento de requisitos
#### 3.1. Requisitos funcionais  
ID | Nome | Descrição | Prioridade  
-|-|-|-   
RF001 | Mapear perfil | O sistema vai pegar informações do paciente e armazenar o perfil dele | Alta
RF002 | Registrar alimento consumido | O sistema deve permitir o cadastro de um alimento consumido pelo usuário | Alta
RF003 | Calcular nutrientes consumidos | O sistema deve calcular a quantidade de nutrientes consumido a partir do alimento cadastrado | Alta
RF004 | Registrar água consumida | O sistema deve permitir o cadastro de água consumida pelo usuário | Média
RF005 | Realizar checklist | O sistema deve realizar um checklist todo dia... | Media
RF006 | Sugerir receitas | O sistema deve sugerir receitas culinárias que encaixem na dieta do usuáio | Alta
RF007 | Emitir alertas | O sistema deve emitir alertas para o usuário em condições críticas | Alta
RF008 | Perguntar para chatbot | O sistema deve permitir que o usuário tire dúvidas ou peça ajuda ao chatbot | Media
RF009 | Visualizar dashboard do paciente | O sistema deve disponibilizar um dashboard para o nutricionista acompanhar o progresso e os registros do paciente | Alta
RF010 | Cadastrar dieta | O sistema deve permitir que o nutricionista cadastre e atualize a dieta do paciente | Alta

#### 3.2. Requisitos não Funcionais  
ID | Categoria | Nome | Descrição | Prioridade  
-|-|-|-|-
RNF001 | Desempenho | Tempo de resposta do cálculo de nutrientes | O sistema deve calcular e exibir os nutrientes consumidos em até 2 segundos após o registro do alimento | Alta
RNF002 | Segurança | Proteção de dados do paciente | Os dados de perfil e histórico alimentar devem ser armazenados de forma criptografada, em conformidade com a LGPD | Alta
RNF003 | Usabilidade | Facilidade no registro de alimentos | O cadastro de um alimento consumido deve ser concluído em no máximo 3 interações do usuário com a interface | Alta
RNF004 | Diponibilidade | Disponibilidade dos alertas | O sistema de alertas deve ter disponibilidade mínima de 99,5%, garantindo que notificações críticas não sejam perdidas | Alta
RNF005 | Escalabilidade | Capacidade do banco de alimentos | O sistema deve suportar uma base de pelo menos 10.000 alimentos cadastrados sem degradação de performance na busca | Alta
RNF006 | Acessibilidade | Legibilidade e visualização | A interface deve seguir diretrizes de acessibilidade (como contraste adequado e textos legíveis), considerando o uso por pacientes idosos ou com limitações visuais. | Média 
RNF007 | Desempenho | Integração com o chatbot | O chatbot deve responder às perguntas do usuário em até 5 segundos em condições normais de rede | Baixa
RNF008 | Segurança | Controle de acesso do nutricionista | O acesso ao dashboard e criação de dietas deve ser restrito a usuários com perfil de nutricionista devidamente autenticados | Alta
RNF009 | Usabilidade | Visualização de métricas | O dashboard do nutricionista deve apresentar os dados do paciente de forma clara, priorizando gráficos e indicadores de adesão à dieta | Média


#### 3.3. Regras de Negócio
ID | Nome | Descrição | RF  
-|-|-|-  
RN001 | Dependência de Perfil para Dietas | O sistema não deve permitir o cálculo de nutrientes consumidos ou a sugestão de receitas sem que o perfil do paciente (RF001) esteja completamente preenchido. | RF003, RF006
RN002 | Base de Dados Nutricional Oficial | O cálculo de nutrientes deve ser baseado em tabelas nutricionais oficiais e multiplicado estritamente pela porção informada. | RF002, RF003 
RN003 | Alerta de Limite Diário | O sistema deve emitir um alerta visual imediato ao usuário quando o consumo de água ou de algum nutriente restrito atingir 90% do limite diário estabelecido no perfil. | RF002, RF004, RF007
RN004 | Filtro de Receitas por Perfil | As receitas sugeridas pelo sistema devem conter apenas ingredientes e quantidades de nutrientes que estejam estritamente dentro dos limites permitidos pelo perfil do paciente. | RF001, RF006 
RN005 | Reset do Checklist Diário | O checklist diário de consumo deve ser resetado automaticamente pelo sistema à meia-noite (00:00) do horário local configurado no perfil do usuário. | RF005 
RN006 | Limitação de Escopo do Chatbot | O chatbot deve ser instruído a responder exclusivamente sobre dúvidas de alimentação e uso do aplicativo, emitindo um aviso padrão para que o usuário consulte seu médico ou nutricionista em caso de sintomas clínicos. | RF008 
RN007 | Exclusividade de Prescrição | Apenas usuários com perfil de nutricionista podem cadastrar ou alterar os limites da dieta dos pacientes. | RF010
RN008 | Atualização Sincronizada | Quando o nutricionista cadastrar uma dieta, os limites de nutrientes e alertas do paciente devem ser automaticamente ajustados no sistema. | RF010, RF001, RF007

### 4. Modelagem UML
#### 4.1 Diagrama de Caso de Uso

Detalhamento de Caso de Uso Principal   

Atores: Paciente, Nutricionista, IA, Chatbot e Notificador

Pré-condição: Cadastro e login do paciente

Fluxo Principal: 
1. Mapear perfil 
2. Registrar alimento consumido
3. Registrar água consumida
4. Calcular nutrientes consumidos

![diagrama de caso de uso](/src/Diagrama%20de%20classe%20de%20uso.jpg)

#### 4.2 Diagrama de Classes

![diagrama de classes](/src/Diagrama%20de%20Classe%20Ideathon.jpg)

#### 4.3 Diagrama de Atividade

![diagrama de atividade](/src/Diagrama%20de%20Atividades.jpg)

#### 4.4 Diagrama de Sequencia
![diagrama de sequencia](/src/diagrama-sequencia.png)

#### 4.5 Diagrama de Implantação
![diagrama de implantação](/src/diagrama-implantacao.png)


### 5. Dicionário de Dados
Classe | Atributo | Descrição  
-|-|-  


### 6. Prototipação de Telas
Nesta seção, são apresentados os esboços da interface do usuário. O objetivo é validar o fluxo
de navegação e a disposição dos elementos antes da fase de desenvolvimento.
#### 6.1 Guia de Estilo (UI Kit)
Cores Principais: `#2563eb`, `#10b981`, `#f59e0b`, `#757681`  
Tipografia: Open Sans  
Ferramenta utilizada: Stitch
#### 6.2 Protótipos de Média Fidelidade
#### Tela principal  
![tela inicial](/src/prototipos/dashboard.png)

#### Dashboard nutricionista  
![Dashboard nutricionista](/src/prototipos/dashboard-nutricionista.png)

#### Cadastro de alimento  
![Cadastro de alimento](/src/prototipos/foto-scan.png)

#### Relatório do alimento  
![Relatório do alimento](/src/prototipos/report-alimento.png)

#### Receitas geradas  
![Receitas geradas](/src/prototipos/receitas-geradas.png)

#### Receita  
![Receita](/src/prototipos/receita.png)

#### Chatbot
![chatbot](/src/prototipos/chatbot-novo.png)