# Atividade Produção de soluções com diagrams as code

O objetivo da atividade consistiu em aplicar a abordagem de Diagrams as Code e a utilização de Inteligência Artificial Generativa para apoiar a fase de discovery e modelagem arquitetural do Sistema de Estimativa de Jornada com IA Generativa.

```
┌────────────────────────────────────────────────────────────────────────────────┐
│                                   FLUXO DA ATIVIDADE                           │
│                                                                                │
│  [prompts/Prompt-1-forum-unidade-3.md] ──► Generação via IA ──► [respostas/Resposta-Prompt-1.md]         │
│               │                                              │                 │
│               ▼                                              ▼                 │
│  [prompts/Prompt-2-forum-unidade-3.md] ──► Refinamento/Sequência ──► [respostas/Resposta-Prompt-2.md]    │
│                                                                                │
└────────────────────────────────────────────────────────────────────────────────┘
```

## Estrutura do Repositório

- **prompts/** - Contém os prompts utilizados para gerar as respostas
  - `Prompt-1-forum-unidade-3.md` - Primeiro prompt com descrição geral do negócio
  - `Prompt-2-forum-unidade-3.md` - Segundo prompt com refinamento de restrições
- **respostas/** - Contém as respostas geradas pela IA
  - `Resposta-Prompt-1.md` - Análise de lacunas, roteiro revisado e diagrama de Containers em PlantUML
  - `Resposta-Prompt-2.md` - Diagrama de Containers atualizado e diagrama de sequência em Mermaid
- **imagens/** - Contém as imagens dos diagramas
  - `plantUML.png` - Diagrama PlantUML do Prompt-1
  - `plantUML-prompt-2.png` - Diagrama PlantUML atualizado do Prompt-2

## Etapas da Atividade

### 1. Mapeamento dos Requisitos Iniciais e Identificação de Lacunas
* **Ação**: A partir da descrição geral do negócio no documento `prompts/Prompt-1-forum-unidade-3.md`, a IA assumiu a persona de Arquiteto de Software Sênior.
* **Execução**: Foi solicitada uma análise prévia contendo de 6 a 10 lacunas arquiteturais e de 5 a 8 perguntas de esclarecimento para refinar o escopo antes da geração do código do diagrama.

### 2. Redação do Roteiro Revisado e Modelagem de Containers em PlantUML
* **Ação**: Com base nas lacunas identificadas, foi elaborado um roteiro técnico definindo os limites da aplicação.
* **Execução**: A IA gerou o documento `respostas/Resposta-Prompt-1.md`, entregando a análise de lacunas, o roteiro reescrito, o diagrama de Containers no nível C4 em PlantUML (visualizado em `imagens/plantUML.png`) e um checklist de revisão para Pull Requests.

### 3. Refinamento de Restrições e Modelagem Comportamental (Diagrama de Sequência)
* **Ação**: Para tornar o projeto mais conciso e aderente a um cenário real, as diretrizes foram refinadas no documento `prompts/Prompt-2-forum-unidade-3.md`.
* **Execução**: O modelo de LLM foi especificado como hospedado em infraestrutura privada, a ferramenta de controle de projetos foi definida como JIRA e foi solicitada a criação de um diagrama comportamental em Mermaid.

### 4. Emissão da Resposta Ajustada e Consolidação para o Fórum
* **Ação**: A IA processou as novas restrições e produziu a `respostas/Resposta-Prompt-2.md`.
* **Execução**: Foram entregues o diagrama de Containers atualizado (com JIRA e LLM privada) em PlantUML (visualizado em `imagens/plantUML-prompt-2.png`) e o diagrama de sequência cobrindo as 4 etapas do ciclo de vida em Mermaid.

## Significado e Análise Técnica das Respostas

### 1. Significado da Resposta-Prompt-1
Arquivo: `respostas/Resposta-Prompt-1.md`

* **Análise das Lacunas e Perguntas**: A IA identificou pontos críticos que não estavam especificados no briefing inicial, como a indefinição da ferramenta de projetos e a incerteza sobre como processar os arquivos de mídia.
* **Roteiro Revisado**: Delimitou claramente o que o sistema faz (gestão de estimativas, acionamento de IA, cálculo financeiro) e o que ele não faz (deploy e execução dos pipelines de dados).
* **Diagrama de Containers C4 (PlantUML)**: Apresenta uma arquitetura baseada em microserviços e processamento assíncrono:
  - Aplicação Web Frontend e API Gateway para interação e controle de entrada.
  - Serviço de Gestão de Estimativas, Serviço de Ingestão e Processamento e Orquestrador de IA Generativa dividindo as responsabilidades de negócio.
  - Barramento de Eventos / Filas (RabbitMQ/Kafka) para garantir a resiliência em chamadas assíncronas.
  - Marcação das integrações externas com `<<external>>` (Provedor de IA, Serviço de Transcrição e Ferramenta de Projetos) sem expor endpoints HTTP internos.
* **Checklist de PR**: Estabeleceu critérios objetivos para validar se o código do diagrama segue as boas práticas do C4 Model e não vaza detalhes de implementação.

### 2. Significado da Resposta-Prompt-2
Arquivo: `respostas/Resposta-Prompt-2.md`

* **Ajuste no Diagrama de Containers**: Incorporou a substituição da ferramenta genérica de projetos pelo JIRA (Atlassian) e atualizou a LLM para um Provedor LLM (Infra Privada), reforçando a conformidade com restrições específicas.
* **Diagrama de Sequência Comportamental (Mermaid)**: Mapeou com clareza o fluxo assíncrono entre os componentes divididos nas 4 fases da demanda:
  - **Etapa 1 (Abertura e Inclusão)**: O Engenheiro faz o upload; os arquivos vão para o S3; as mídias são transcritas via STT e um evento é disparado via Message Broker.
  - **Etapa 2 (Processamento via LLM)**: O Orquestrador busca os contratos no PostgreSQL, envia o prompt anonimizado para a LLM Privada e calcula o T-shirt sizing.
  - **Etapa 3 (Aprovação Humana)**: O Engenheiro revisa os custos/jornadas na interface web e aprova a estimativa.
  - **Etapa 4 (Integração JIRA)**: O Serviço de Integração cria automaticamente o ticket no JIRA (ex: DATA-1234) e conclui o fluxo.

### 3. Síntese e Conclusão
A utilização da abordagem Diagrams as Code com IA Generativa demonstrou grande valor ao levantar lacunas de discovery com rapidez. Contudo, identificou-se a importância de refinamentos iterativos para garantir aderência ao contexto real da organização, validando pressupostos e restrições junto aos stakeholders.
