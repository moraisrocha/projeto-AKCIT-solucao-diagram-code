# Prompt-2-forum-unidade-3

Persona: Você é um arquiteto de software sênior que revisará uma solução proposta

Descrição Técnica do Sistema: O Sistema para Cálculo de T-Shirt é uma solução voltada ao time de engenharia de dados para estimar esforço, custo e premissas técnicas na construção de fluxos de dados.

Escopo: Upload de documentos e mídias, processamento do contexto via LLM, cálculo de custos com base na jornada por perfil, gestão do ciclo de vida da estimativa (abertura, execução, espera e conclusão) e integração final com a ferramenta JIRA de projetos após aprovação humana.

Nível (C4): Containers.

Limites e Responsabilidades: O sistema orquestra as etapas de estimativa, persiste dados de apoio e integra com serviços terceiros. Não é responsável pela execução ou deploy dos pipelines de dados em si.

Integrações Externas: Serviço de IA Generativa (LLM) com modelo hospedado em infraestrutura privada, Serviço de Transcrição de Mídia (Speech-to-Text) e Ferramenta de Controle de Projetos.

Restrições: Diagrama estrutural sem exposição de URIs/endpoints; sistemas externos identificados rigorosamente com o estereótipo <<external>>.

Lacunas Assumidas: O processamento de arquivos é assíncrono via mensageria; a transcrição de mídias é delegada a um serviço externo especializado; a LLM recebe prompts anonimizados com os dados dos contratos mantidos em banco interno.

Objetivo do diagrama:
- Tipo: estrutural
- Nível (C4): Containers
- Escopo: fluxo de criação de estimativa, upload de arquivos, integração com IA generativa e com sistema JIRA de controle de projeto.

- Tipo: comportamental
- Nivel: diagrama de sequência 
- Escopo: abertura da estimativa, inclusão de documentos, aprovação estimativa e integração com o JIRA.

Respostas:
Criar no formato mermaid o diagrama de sequencia.
Revisar e ajustar o diagrama de Containers

Formato: markdown
