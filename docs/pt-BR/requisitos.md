# Requisitos e Critérios de Aceite — Zestion

[English](../en/requirements.md) | [Português](requisitos.md)

## Objetivo do produto

Oferecer aos jogadores um espaço web seguro e acessível para criar, manter e utilizar fichas do RPG Ruptura, aplicando de forma consistente as regras de cálculo e progressão do sistema.

## Atores

- **Visitante:** pode cadastrar-se, entrar, confirmar o e-mail e recuperar a senha.
- **Jogador:** pode gerenciar somente seus personagens, fichas, retratos, habilidades e ferramentas de jogo.
- **Mestre:** ator planejado que administrará conteúdo de campanha e sessões online.

## Requisitos funcionais atuais

| ID | Requisito | Critério de aceite |
|---|---|---|
| RF-001 | Cadastrar uma conta | O visitante envia dados válidos e recebe o fluxo de confirmação configurado |
| RF-002 | Autenticar usuário | Credenciais válidas permitem acesso ao dashboard protegido |
| RF-003 | Recuperar senha | Um usuário cadastrado solicita a recuperação e define uma nova senha |
| RF-004 | Proteger rotas privadas | Acesso sem autenticação ao dashboard redireciona para a autenticação |
| RF-005 | Encerrar sessão | O logout encerra a sessão ativa e retorna à autenticação |
| RF-006 | Listar personagens | O jogador visualiza somente personagens associados à própria conta |
| RF-007 | Criar personagens | O jogador pode criar mais de um personagem |
| RF-008 | Editar e salvar ficha | Alterações válidas persistem após atualizar a página |
| RF-009 | Excluir personagem | O personagem selecionado é removido somente após ação explícita |
| RF-010 | Gerenciar retratos | O jogador envia um retrato privado em formato suportado |
| RF-011 | Aplicar restrições do nível 1 | Um personagem de nível 1 não pode selecionar classe |
| RF-012 | Liberar classes | A seleção de classe fica disponível a partir do nível 2 |
| RF-013 | Validar limites de pontos | Atributos, perícias e progressão não ultrapassam os pontos disponíveis |
| RF-014 | Calcular valores derivados | PV, Sanidade, Defesa, Iniciativa e Carga seguem as regras atuais |
| RF-015 | Aplicar bônus | Bônus de espécie, classe e passivas atualizam os valores correspondentes |
| RF-016 | Gerenciar árvore de habilidades | O jogador seleciona somente habilidades permitidas por nível, tier, requisitos e pontos |
| RF-017 | Persistir habilidades | Seleções válidas permanecem vinculadas ao personagem correto |
| RF-018 | Gerenciar inventário e anotações | O jogador salva inventário, equipamentos e informações do personagem |
| RF-019 | Rolar dados | O jogador rola dados suportados e visualiza resultados individuais e o total |
| RF-020 | Consultar regras | O jogador acessa o conteúdo atual de Regras Gerais / Como Jogar |

## Requisitos não funcionais atuais

| ID | Requisito | Critério de aceite |
|---|---|---|
| RNF-001 | Isolamento de dados | Leituras e alterações são limitadas ao usuário autenticado e reforçadas por RLS |
| RNF-002 | Segurança de upload | Retratos possuem validação de origem, tamanho e conteúdo real do arquivo |
| RNF-003 | Proteção da sessão | Cookies de autenticação utilizam atributos de segurança adequados |
| RNF-004 | Responsividade | Fluxos principais permanecem utilizáveis em layouts desktop e mobile |
| RNF-005 | Acessibilidade | Controles principais possuem rótulos, acesso por teclado e feedback de status quando aplicável |
| RNF-006 | Tratamento de erros | Falhas esperadas exibem mensagens compreensíveis sem detalhes sensíveis |
| RNF-007 | Privacidade | Documentação e evidências públicas não contêm credenciais nem dados de jogadores |

## Requisitos planejados

| ID | Requisito planejado |
|---|---|
| GM-001 | Disponibilizar espaço exclusivo para o Mestre |
| GM-002 | Permitir gerenciamento de documentos de campanha |
| GM-003 | Permitir anotações privadas organizadas por campanha ou sessão |
| SO-001 | Permitir que o Mestre crie uma sessão online |
| SO-002 | Gerar convites para jogadores |
| SO-003 | Permitir entrada de jogadores convidados |
| SO-004 | Exigir que cada jogador selecione um personagem existente |
| SO-005 | Permitir acesso do Mestre às fichas escolhidas naquela sessão |
| SO-006 | Proteger participantes, permissões e informações privadas |
| SO-007 | Manter atualizadas as informações dos participantes e personagens selecionados |

## Fora do escopo do MVP atual

- Compartilhamento público de fichas privadas;
- Funcionalidades de gerenciamento do Mestre;
- Salas de sessão online;
- Automação de combate em tempo real;
- Pagamentos ou assinaturas.
