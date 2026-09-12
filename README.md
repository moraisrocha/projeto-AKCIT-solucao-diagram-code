# Atividade Produção de soluções com diagrams as code

O objetivo da atividade consistiu em aplicar a abordagem de Diagrams as Code e a utilização de Inteligência Artificial Generativa para apoiar a fase de discovery e modelagem arquitetural do Sistema para Cálculo de T-Shirt Sizing para engenharia de dados.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                                   FLUXO DA ATIVIDADE                                   │
│                                                                                        │
│  [Prompt-1-forum-unidade-3] ──► Generação via IA ──► [Resposta-prompt-1]               │
│               │                                              │                         │
│               ▼                                              ▼                         │
│  [Prompt-2-unidade-3]       ──► Refinamento/Sequência ──► [Resposta-prompt-2]          │
│                                                                                        │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

1. Mapeamento dos Requisitos Iniciais e Identificação de Lacunas
 * Ação: A partir da descrição geral do negócio no documento Prompt-1-forum-unidade-3, a IA assumiu a persona de Arquiteto de Software Sênior.
 * Execução: Foi solicitada uma análise prévia contendo de 6 a 10 lacunas arquiteturais e de 5 a 8 perguntas de esclarecimento para refinar o escopo antes da geração do código do diagrama.
2. Redação do Roteiro Revisado e Modelagem de Containers em PlantUML
 * Ação: Com base nas lacunas identificadas, foi elaborado um roteiro técnico definindo os limites da aplicação.
 * Execução: A IA gerou o documento Resposta-prompt-1, entregando a análise de lacunas, o roteiro reescrito, o diagrama de Containers no nível C4 em PlantUML e um checklist de revisão em Pull Request com 9 itens.
3. Refinamento de Restrições e Modelagem Comportamental (Diagrama de Sequência)
 * Ação: Para tornar o projeto mais conciso e aderente a um cenário real, as diretrizes foram refinadas no documento Prompt-2-unidade-3.
 * Execução: O modelo de LLM foi especificado como hospedado em infraestrutura privada, a ferramenta de controle de projetos foi definida como JIRA e foi solicitada a criação de um diagrama comportamental de sequência em Mermaid.
4. Emissão da Resposta Ajustada e Consolidação para o Fórum
 * Ação: A IA processou as novas restrições e produziu a Resposta-prompt-2.
 * Execução: Foram entregues o diagrama de Containers atualizado (com JIRA e LLM privada) em PlantUML e o diagrama de sequência cobrindo as 4 etapas do ciclo de vida em Mermaid. Os resultados subsidiaram a reflexão final publicada no fórum da disciplina.

## Significado e Análise Técnica das Respostas

### 1. Significado da Resposta-prompt-1
 * Análise das Lacunas e Perguntas: A IA identificou pontos críticos que não estavam especificados no briefing inicial, como a indefinição da ferramenta de projetos, a incerteza sobre como processar gravações pesadas de áudio/vídeo e os riscos de segurança ao enviar dados de contratos de fornecedores para LLMs públicas.
 * Roteiro Revisado: Delimitou claramente o que o sistema faz (gestão de estimativas, acionamento de IA, cálculo financeiro) e o que ele não faz (deploy e execução dos pipelines de dados).
 * Diagrama de Containers C4 (PlantUML): Apresenta uma arquitetura baseada em microserviços e processamento assíncrono:
   * Aplicação Web Frontend e API Gateway para interação e controle de entrada.
   * Serviço de Gestão de Estimativas, Serviço de Ingestão e Processamento e Orquestrador de IA Generativa dividindo as responsabilidades de negócio.
   * Barramento de Eventos / Filas (RabbitMQ/Kafka) para garantir a resiliência em chamadas assíncronas.
   * Marcação das integrações externas com <<external>> (Provedor de IA, Serviço de Transcrição e Ferramenta de Projetos) sem expor endpoints HTTP internos.
 * Checklist de PR: Estabeleceu critérios objetivos para validar se o código do diagrama segue as boas práticas do C4 Model e não vaza detalhes de implementação.

### 2. Significado da Resposta-prompt-2
 * Ajuste no Diagrama de Containers: Incorporou a substituição da ferramenta genérica de projetos pelo JIRA (Atlassian) e atualizou a LLM para um Provedor LLM (Infra Privada), reforçando a conformidade com a privacidade de dados contratuais.
 * Diagrama de Sequência Comportamental (Mermaid): Mapeou com clareza o fluxo assíncrono entre os componentes divididos nas 4 fases da demanda:
   * Etapa 1 (Abertura e Inclusão): O Engenheiro faz o upload; os arquivos vão para o S3; as mídias são transcritas via STT e um evento é disparado via Message Broker.
   * Etapa 2 (Processamento via LLM): O Orquestrador busca os contratos no PostgreSQL, envia o prompt anonimizado para a LLM Privada e calcula o T-shirt sizing.
   * Etapa 3 (Aprovação Humana): O Engenheiro revisa os custos/jornadas na interface web e aprova a estimativa.
   * Etapa 4 (Integração JIRA): O Serviço de Integração cria automaticamente o ticket no JIRA (ex: DATA-1234) e conclui o fluxo.

### 3. Síntese e Conclusão
Como registrado na postagem do fórum, a utilização da abordagem Diagrams as Code com IA Generativa demonstrou grande valor ao levantar lacunas de discovery com rapidez. Contudo, identificou-se que, para permitir a implementação autônoma por um agente de IA de codificação, é indispensável resolver as lacunas restantes (especificação dos contratos de API e schemas dos bancos de dados), além de buscar um fluxo de containers leve e objetivo.
