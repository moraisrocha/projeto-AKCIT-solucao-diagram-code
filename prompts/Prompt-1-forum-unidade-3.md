# Prompt-1-forum-unidade-3
Persona: Você é um arquiteto de software sênior que produzirá um diagrama estrutural e revisável (diagrams as code).

Descrição:

Sistema Para Cálculo de T-shirt

O sistema deverá auxiliar o time de engenharia de dados para calcular, em alto nível, isto é realizar uma t-shirt, do esforço e do valor para o desenvolvimento de fluxos de dados. O sistema deverá ser capaz de receber requisitos técnicos em formato textual, áudio e/ou visual (capturas de tela de reunião, desenhos de solução).

O sistema deverá ser capaz de acionar um modelo LLM de IA Generativa para calcular a quantidade de jornadas, informar o perfil dos profissionais, o valor financeiro, os requisitos funcionais, não funcionais, premissas e riscos.

O sistema deverá integrar com a ferramenta de controle de projetos para após a aprovação do usuário lançar a estimativa formalmente na ferramenta de controle.

O sistema também deverá conter o fluxo das etapas da estimativa, desde a abertura, passando pela execução e espera de respostas até a conclusão.

Objetivo do diagrama:
- Tipo: estrutural
- Nível (C4): Containers
- Escopo: fluxo de criação de estimativa, upload de arquivos, integração com IA generativa e com sistema de controle de projeto.

Restrições:
- Marcar integrações externas como <<external>>
- Não listar endpoints; mostrar apenas dependências relevantes.
- Não misturar níveis do C4
- Mostrar apenas dependências relevantes

Entregue nesta ordem:
1) Lacunas e perguntas: liste 6–10 lacunas e faça 5–8 perguntas curtas para esclarecer o cenário.
2) Roteiro revisado: reescreva a descrição em 8–12 linhas, explicitando Escopo, Nível, Limites e Responsabilidades, Integrações Externas, Restrições e Lacunas.
3) Criar no formato mermaid a visão de containers inspirado em C4.
4) Checklist: 8–12 itens para revisão do diagrama em pull request (limites, dependências, vazamentos, consistência com restrições).

Regras: se faltar contexto, explicite suposições antes do fluxo estrutural. Não assuma fatos como certezas.

Formato: Markdown.
