# Zestion RPG — Estudo de Caso de QA e Produto

[English](README.md) | [Português](README.pt-BR.md)

Estudo de caso bilíngue de QA e produto sobre o **Zestion**, um MVP web funcional para criação, gerenciamento e evolução de fichas do sistema autoral de RPG **Ruptura**.

Este repositório público contém somente documentação e evidências de testes. O código-fonte da aplicação permanece em um repositório privado.

## Aplicação publicada

[https://zestion-rpg.com.br/](https://zestion-rpg.com.br/)

## Visão geral

O Zestion reúne autenticação, dados privados por usuário, gerenciamento de personagens, regras de progressão, árvores de habilidades, upload de retratos e rolador de dados 3D. O projeto está em evolução contínua: as funcionalidades atuais de jogador estão operacionais, enquanto a área do Mestre e as sessões online fazem parte do roadmap.

## Escopo implementado

- Cadastro, login, confirmação de e-mail, recuperação de senha e logout;
- Dashboard protegido do jogador;
- Criação, edição, salvamento e exclusão de múltiplos personagens;
- Fichas e retratos privados, isolados por usuário;
- Atributos, perícias, PV, Sanidade, Defesa, Iniciativa e Carga;
- Regras de espécie, classe, progressão e bônus automáticos;
- Árvores de habilidades por classe, com tiers, requisitos, custos e efeitos passivos;
- Inventário, equipamentos, anotações e informações do personagem;
- Rolador de dados 3D com D4, D6, D8, D10, D12, D20 e D100;
- Conteúdo de Regras Gerais / Como Jogar;
- Interface web responsiva.

## Documentação de QA

- [Requirements and acceptance criteria](docs/en/requirements.md)
- [Test cases](docs/en/test-cases.md)
- [QA report](docs/en/qa-report.md)
- [Requisitos e critérios de aceite](docs/pt-BR/requisitos.md)
- [Casos de teste](docs/pt-BR/casos-de-teste.md)
- [Relatório de QA](docs/pt-BR/relatorio-qa.md)
- [Guia de evidências](evidence/screenshots/README.md)

## Abordagem de testes

O estudo de caso combina:

- Validação funcional manual do MVP publicado;
- Testes de regras de negócio para cálculos, progressão e árvores de habilidades;
- Testes automatizados de segurança presentes no repositório privado;
- Execução formal planejada para responsividade, acessibilidade, compatibilidade e cenários negativos;
- Rastreabilidade entre requisitos, critérios de aceite e casos de teste.

Os status dos CTs diferenciam comportamentos confirmados pelo responsável pelo produto, coberturas automatizadas e cenários que ainda aguardam um ciclo formal documentado.

## Cobertura automatizada de segurança

O repositório privado da aplicação possui cinco testes automatizados:

1. Validação de origem confiável para uploads de retratos;
2. Verificação do conteúdo real da imagem, independentemente do MIME declarado;
3. Processamento limitado de uploads multipart válidos;
4. Rejeição de corpo acima do limite, inclusive sem `Content-Length`;
5. Cookies de sessão Supabase com `HttpOnly`, `SameSite=Lax` e `Secure` em produção.

## Roadmap

### Área do Mestre

- Espaço exclusivo para Mestres;
- Gerenciamento de documentos de campanha;
- Anotações privadas;
- Centralização de informações de mundos, aventuras e sessões.

### Sessões online

- Criação de sessões e convites para jogadores;
- Entrada dos jogadores por convite;
- Seleção de um personagem existente ao entrar;
- Acesso do Mestre às fichas selecionadas pelos participantes;
- Regras de participação e permissão;
- Acompanhamento dos personagens durante a sessão.

### Evolução da qualidade

- Ciclos formais em diferentes navegadores e dispositivos;
- Verificações de acessibilidade com teclado e tecnologia assistiva;
- Testes de integração para autenticação e persistência;
- Regressão automatizada dos principais fluxos do jogador;
- Coleta de evidências em cada ciclo formal.

## Tecnologias utilizadas pelo produto

- React 19;
- TypeScript;
- Next.js 16 e Vinext;
- Tailwind CSS;
- Three.js;
- Supabase Auth, Database e Storage;
- Cloudflare Workers;
- Git e GitHub.

## Competências demonstradas

- Análise de requisitos e critérios de aceite;
- Planejamento e execução de testes manuais;
- Testes de regras de negócio e cenários negativos;
- Análise de riscos de segurança;
- Separação entre defeitos, riscos e melhorias;
- Planejamento de roadmap de produto;
- Documentação técnica bilíngue;
- Comunicação entre necessidade do usuário e comportamento implementado;
- Uso responsável de ferramentas de IA, com revisão e validação humana.

## Evidências

Capturas e registros de execução serão adicionados progressivamente sem expor dados de jogadores, credenciais, fichas privadas ou o código-fonte da aplicação.

---

O Zestion é um projeto autoral desenvolvido para aprendizado, portfólio e suporte às sessões do sistema Ruptura.
