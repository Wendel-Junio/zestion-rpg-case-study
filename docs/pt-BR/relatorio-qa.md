# Relatório de QA — Zestion

[English](../en/qa-report.md) | [Português](relatorio-qa.md)

## 1. Resumo executivo

O Zestion é um MVP web funcional com fluxo amplo para jogadores e regras de negócio complexas. A documentação atual identifica o escopo implementado, define critérios de aceite e estabelece uma base rastreável de testes sem expor código privado nem dados de jogadores.

O principal valor do projeto para QA está na combinação de autenticação, dados privados, operações de personagens, cálculos baseados em regras, restrições de progressão, árvores de habilidades, upload de arquivos e comportamento 3D interativo.

## 2. Avaliação atual

### Pontos fortes confirmados

- Autenticação e dashboard protegidos;
- Múltiplos personagens por conta;
- Persistência das fichas;
- Cálculos e bônus automáticos;
- Restrições de nível, pontos, tiers e requisitos;
- Fluxo privado de retratos;
- Rolagem de dados 3D;
- Roadmap explícito para a área do Mestre;
- Testes automatizados de segurança no repositório privado;
- Separação clara entre funcionalidades atuais e planejadas.

### Maturidade das evidências

As funcionalidades principais foram informadas como operacionais em produção. Ainda é necessário um ciclo formal para registrar versões de navegadores, dispositivos, capturas e resultados encontrados em cada caso. Até essa execução, os status confirmados não representam certificação independente nem cobertura completa de regressão.

## 3. Estratégia de testes

| Nível | Objetivo |
|---|---|
| Funcional | Verificar autenticação e gerenciamento de personagens |
| Regras de negócio | Validar cálculos, limites, progressão, bônus, tiers e requisitos |
| Negativo | Validar credenciais, valores e operações inválidas |
| Segurança | Verificar upload, cookies, isolamento de dados e erros seguros |
| Responsivo | Verificar fluxos críticos em diferentes telas e por toque |
| Acessibilidade | Verificar rótulos, foco, teclado e anúncios de status |
| Regressão | Reexecutar fluxos críticos após alterações de regras ou funcionalidades |

## 4. Principais riscos

| ID | Área | Prioridade | Risco | Recomendação |
|---|---|---:|---|---|
| QA-001 | Controle de acesso | Crítica | Jogador pode acessar ficha de outra conta se consultas ou RLS estiverem incorretas | Executar teste com duas contas e manter verificação das políticas RLS |
| QA-002 | Regras de negócio | Alta | Alterações podem quebrar cálculos ou invalidar fichas salvas | Criar testes unitários para valores derivados e restrições |
| QA-003 | Autenticação | Alta | Confirmação ou recuperação pode variar entre provedores e ambientes | Executar testes de ponta a ponta repetíveis |
| QA-004 | Upload | Alta | Retratos inválidos ou grandes podem afetar segurança e armazenamento | Manter controles automatizados e adicionar integração com storage |
| QA-005 | Regressão | Alta | Novas classes, espécies e skills podem quebrar personagens existentes | Criar pacote versionado com personagens representativos |
| QA-006 | Acessibilidade | Média | Fichas e árvores complexas podem ser difíceis por teclado ou tecnologia assistiva | Testar foco, semântica, teclado e leitor de tela |
| QA-007 | UX mobile | Média | Formulários densos e nós podem ficar difíceis em telas pequenas | Executar testes em dispositivos e registrar capturas |
| QA-008 | Compatibilidade | Média | Three.js pode variar entre navegadores e GPUs | Testar Chrome, Firefox, Edge, Safari/mobile e movimento reduzido |
| QA-009 | Evidências | Média | Afirmações do portfólio podem não ter ambiente reproduzível | Registrar versão, dispositivo, navegador e evidência |
| QA-010 | Sessões online | Alta futura | Convites e compartilhamento introduzirão novos riscos de permissão | Definir autorização e ameaças antes da implementação |

## 5. Classificação

- **Defeito:** comportamento implementado diverge de requisito definido.
- **Melhoria:** comportamento funciona, mas pode oferecer experiência melhor.
- **Risco:** condição que pode causar impacto ou falha futura.
- **Funcionalidade planejada:** está fora do MVP atual e não representa defeito.

## 6. Ciclo formal sugerido

1. Criar duas contas isoladas de teste;
2. Registrar ambiente e versão publicada;
3. Executar autenticação e recuperação de senha;
4. Criar personagens representativos de nível 1 e nível 2+;
5. Conferir valores derivados por cálculo independente;
6. Testar caminhos válidos e inválidos da árvore;
7. Verificar autorização entre usuários;
8. Executar casos negativos de retrato em ambiente controlado;
9. Testar teclado e layouts mobile;
10. Anexar evidências sanitizadas e abrir defeitos;
11. Reexecutar casos críticos após correções.

## 7. Critérios de qualidade para o roadmap

Antes de publicar área do Mestre e sessões online:

- Definir atores, permissões, ciclo dos convites e estados da sessão;
- Definir se o acesso do Mestre às fichas será somente leitura ou edição;
- Definir quando o jogador pode ter o acesso revogado;
- Impedir entrada sem convite válido;
- Limitar consultas por usuário autenticado e participação na sessão;
- Manter registros rastreáveis de convites e personagens selecionados;
- Testar atualizações concorrentes e participantes desconectados;
- Definir privacidade para anotações, documentos e fichas.

## Conclusão

O Zestion já oferece um case forte para QA, análise de produto, comportamento front-end, autenticação e testes de regras de negócio. O próximo marco de qualidade é criar um ciclo formal repetível, com evidências sanitizadas e regressão automatizada para as regras mais críticas.
