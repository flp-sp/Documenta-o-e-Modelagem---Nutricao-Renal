# Documento de Especificação de Requisitos e Modelagem (DERM)
Projeto: NOME Versão: 0.1.1-alpha Data: 5 de Junho de 2026  
Alunos: Francisco Felipe Sampaio Neto, Raimundo José de Sousa Neto, Carlos Eduardo, José Victor de Moura Rufino

---
### 1. Histórico de Revisões

Versão | Data | Descrição | Autor
-| - | - | -
0.1.0-alpha | 05/06/2026 | Inicio da documentação | Francisco Felipe
0.1.1-alpha | 06/06/2026 | Requisitos funcionais adicionados | Francisco Felipe
0.1.2-alpha | 06/06/2026 | Atualização nos requisitos funcionais e adicinado regras de negócio | Francisco Felipe



### 2. Introdução
#### 2.1. Objetivo  
Este documento descreve os requisitos funcionais e não funcionais, bem como a modelagem UML para o sistema para controle alimento e de água de pacientes com problemas renais de acordo com o perfil do usuário

#### 2.2. Escopo  
O sistema irá auxiliar a nutrição de pacientes com problemas renais, com controle de água, alimentos e nutrientes consumidos. Ele irá atuar mapeando o perfil do usuário, realizando checklists diários, sugerindo receitas que encaixem na dieta e contará com um chatbot para dúvidas e suporte.


### 3. Levantamento de requisitos
#### 3.1. Requisitos funcionais  
ID | Nome | Descrição | Prioridade  
-|-|-|-   
RF01 | Mapear perfil | O sistema vai pegar informações do paciente e armazenar o perfil dele | Alta
RF02 | Registrar alimento consumido | O sistema deve permitir o cadastro de um alimento consumido pelo usuário | Alta
RF03 | Calcular nutrientes consumidos | O sistema deve calcular a quantidade de nutrientes consumido a partir do alimento cadastrado | Alta
RF04 | Registrar água consumida | O sistema deve permitir o cadastro de água consumida pelo usuário | Média
RF05 | Realizar checklist | O sistema deve realizar um checklist todo dia... | Media
RF06 | Sugerir receitas | O sistema deve sugerir receitas culinárias que encaixem na dieta do usuáio | Alta
RF07 | Emitir alertas | O sistema deve emitir alertas para o usuário em condições críticas | Alta
RF08 | Perguntar para chatbot | O sistema deve permitir que o usuário tire dúvidas ou peça ajuda ao chatbot | Media

#### 3.2. Requisitos não Funcionais  
ID | Nome | Descrição | Prioridade  
-|-|-|-  

#### 3.3. Regras de Negócio
ID | Nome | Descrição | RF  
-|-|-|-  
RN01 | Dependência de Perfil para Dietas | O sistema não deve permitir o cálculo de nutrientes consumidos ou a sugestão de receitas sem que o perfil do paciente (RF01) esteja completamente preenchido. | RF03, RF06
RN02 | Base de Dados Nutricional Oficial | O cálculo de nutrientes deve ser baseado em tabelas nutricionais oficiais e multiplicado estritamente pela porção informada. | RF02, RF03 
RN03 | Alerta de Limite Diário | O sistema deve emitir um alerta visual imediato ao usuário quando o consumo de água ou de algum nutriente restrito atingir 90% do limite diário estabelecido no perfil. | RF02, RF04, RF07
RN04 | Filtro de Receitas por Perfil | As receitas sugeridas pelo sistema devem conter apenas ingredientes e quantidades de nutrientes que estejam estritamente dentro dos limites permitidos pelo perfil do paciente. | RF01, RF06 
RN05 | Reset do Checklist Diário | O checklist diário de consumo deve ser resetado automaticamente pelo sistema à meia-noite (00:00) do horário local configurado no perfil do usuário. | RF05 
RN06 | Limitação de Escopo do Chatbot | O chatbot deve ser instruído a responder exclusivamente sobre dúvidas de alimentação e uso do aplicativo, emitindo um aviso padrão para que o usuário consulte seu médico ou nutricionista em caso de sintomas clínicos. | RF08 

### 4. Modelagem UML
#### 4.1 Diagrama de Caso de Uso

Detalhamento de Caso de Uso Principal   
Atores:   
Pré-condição:  
Fluxo Principal:
1. 
2. 
3. 
4. 

Pós-condição: 

#### 4.2 Diagrama de Classes

#### 4.2 Diagrama de Atividade

#### 4.3 Diagrama de Sequencia

#### 4.5 Diagrama de Implantação


### 5. Dicionário de Dados
Classe | Atributo | Descrição  
-|-|-  


### 6. Prototipação de Telas
Nesta seção, são apresentados os esboços da interface do usuário. O objetivo é validar o fluxo
de navegação e a disposição dos elementos antes da fase de desenvolvimento.
#### 6.1 Guia de Estilo (UI Kit)
Cores Principais:  
Tipografia:  
Ferramenta utilizada:  
#### 6.2 Protótipos de Média Fidelidade

### 7. Conclusão e Justificativa Técnica