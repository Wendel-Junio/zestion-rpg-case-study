# Casos de Teste — Zestion

[English](../en/test-cases.md) | [Português](casos-de-teste.md)

## Escopo

Autenticação, acesso protegido, gerenciamento de personagens, regras da ficha, progressão, árvores de habilidades, upload de retratos, rolador de dados, responsividade, acessibilidade e controles de segurança.

## Status

- **Confirmado:** comportamento informado como funcional no MVP publicado; evidências formais ainda estão sendo organizadas.
- **Cobertura automatizada:** o repositório privado possui teste automatizado para o controle.
- **Execução formal pendente:** necessita de execução documentada, ambiente e evidência.
- **Não implementado:** funcionalidade do roadmap, sem representar defeito do MVP atual.

## Pré-condições

- URL de produção disponível;
- Acesso a e-mail de teste para confirmação e recuperação;
- Pelo menos dois usuários de teste para cenários de isolamento;
- Nenhum dado real de jogador deve ser utilizado.

## Casos de teste

| ID | Requisito | Cenário | Passos principais | Resultado esperado | Status |
|---|---|---|---|---|---|
| ZES-AUTH-001 | RF-001 | Cadastrar com dados válidos | Abrir cadastro, preencher dados válidos e enviar | Conta é criada e o fluxo configurado de confirmação é iniciado | Confirmado |
| ZES-AUTH-002 | RF-002 | Entrar com credenciais válidas | Informar credenciais confirmadas e enviar | Dashboard protegido é aberto | Confirmado |
| ZES-AUTH-003 | RF-002 | Rejeitar credenciais inválidas | Enviar combinação inválida de e-mail e senha | Acesso é negado e mensagem segura é apresentada | Execução formal pendente |
| ZES-AUTH-004 | RF-004 | Bloquear dashboard sem autenticação | Abrir URL protegida sem sessão | Usuário é redirecionado para autenticação | Confirmado |
| ZES-AUTH-005 | RF-005 | Encerrar sessão | Selecionar logout em página autenticada | Sessão termina e conteúdo protegido deixa de estar disponível | Confirmado |
| ZES-AUTH-006 | RF-003 | Recuperar senha | Solicitar recuperação, abrir link e definir nova senha | Nova senha é aceita e permite autenticação | Confirmado |
| ZES-AUTH-007 | RF-001 | Cadastrar e-mail existente | Enviar e-mail já cadastrado | Duplicidade é evitada sem expor informação sensível | Execução formal pendente |
| ZES-CHAR-001 | RF-007 | Criar personagem | Selecionar criar personagem | Nova ficha abre e aparece na lista do jogador | Confirmado |
| ZES-CHAR-002 | RF-007 | Criar múltiplos personagens | Criar mais de um personagem | Todos aparecem de forma independente | Confirmado |
| ZES-CHAR-003 | RF-008 | Salvar alterações válidas | Editar campos válidos e salvar | Feedback de sucesso aparece e dados são armazenados | Confirmado |
| ZES-CHAR-004 | RF-008 | Preservar alterações após atualizar | Salvar e recarregar a página | Valores permanecem inalterados | Confirmado |
| ZES-CHAR-005 | RF-009 | Excluir personagem | Selecionar exclusão e confirmar ação explícita | Personagem correto é removido | Confirmado |
| ZES-CHAR-006 | RF-006 / RNF-001 | Isolar personagens entre usuários | Comparar duas contas e tentar acesso direto | Cada conta acessa somente os próprios personagens | Execução formal pendente |
| ZES-CHAR-007 | RF-010 | Enviar retrato válido | Enviar imagem suportada dentro do limite | Retrato é armazenado de forma privada e exibido | Confirmado |
| ZES-CHAR-008 | RNF-002 | Rejeitar conteúdo inválido no retrato | Tentar arquivo inválido ou falsificado | Upload é rejeitado com segurança | Cobertura automatizada |
| ZES-SHEET-001 | RF-011 | Manter classe bloqueada no nível 1 | Definir personagem no nível 1 | Classe permanece indisponível ou é removida | Confirmado |
| ZES-SHEET-002 | RF-012 | Liberar classe no nível 2 | Alterar nível de 1 para 2 | Seleção de classe fica disponível | Confirmado |
| ZES-SHEET-003 | RF-013 | Validar limite de atributos | Tentar ultrapassar pontos disponíveis | Salvamento é bloqueado com feedback compreensível | Confirmado |
| ZES-SHEET-004 | RF-013 | Validar limite e custo de perícias | Tentar distribuição inválida | Salvamento é bloqueado com feedback compreensível | Confirmado |
| ZES-SHEET-005 | RF-014 | Calcular valores derivados | Alterar atributos relacionados | PV, Sanidade, Defesa, Iniciativa ou Carga atualizam conforme as regras | Confirmado |
| ZES-SHEET-006 | RF-015 | Aplicar bônus de espécie | Selecionar espécie com bônus | Bônus corretos aparecem sem consumir pontos distribuídos | Confirmado |
| ZES-SHEET-007 | RF-015 | Aplicar bônus de classe e passivas | Selecionar combinação válida | Totais correspondentes atualizam conforme as regras | Confirmado |
| ZES-SHEET-008 | RF-018 | Salvar inventário e anotações | Preencher inventário, equipamentos e informações e salvar | Conteúdo permanece vinculado ao personagem | Confirmado |
| ZES-SKILL-001 | RF-016 | Acessar árvore da classe | Usar personagem nível 2+ com classe | Árvore correta é aberta | Confirmado |
| ZES-SKILL-002 | RF-016 | Validar bloqueio de tiers | Tentar selecionar nó de tier bloqueado | Seleção é impedida e requisitos permanecem visíveis | Confirmado |
| ZES-SKILL-003 | RF-016 | Validar requisitos e custos | Tentar combinação inválida | Seleção inválida é rejeitada | Confirmado |
| ZES-SKILL-004 | RF-017 | Persistir escolhas válidas | Selecionar nós, voltar à ficha e reabrir árvore | Escolhas permanecem no personagem correto | Confirmado |
| ZES-SKILL-005 | RF-015 | Refletir passiva na ficha | Selecionar passiva que altera total | Ficha apresenta valor correto atualizado | Confirmado |
| ZES-DICE-001 | RF-019 | Rolar todos os dados suportados | Rolar D4, D6, D8, D10, D12, D20 e D100 | Cada resultado fica dentro do intervalo do dado | Confirmado |
| ZES-DICE-002 | RF-019 | Rolar múltiplos dados | Escolher quantidade maior que um e rolar | Resultados individuais e soma correta são apresentados | Confirmado |
| ZES-DICE-003 | RF-019 | Validar limite de quantidade | Tentar quantidade abaixo de 1 ou acima de 20 | Controle mantém o intervalo permitido | Confirmado |
| ZES-UX-001 | RNF-004 | Usar fluxos críticos no mobile | Executar autenticação, personagens, ficha, árvore e dados no mobile | Nenhum controle crítico fica cortado, sobreposto ou inacessível | Execução formal pendente |
| ZES-UX-002 | RNF-005 | Navegar controles pelo teclado | Usar Tab, Shift+Tab, Enter e Espaço | Foco fica visível e ordem é lógica | Execução formal pendente |
| ZES-UX-003 | RNF-006 | Exibir feedback seguro de erro | Provocar falhas de autenticação, salvamento e upload | Mensagem clara aparece sem detalhes técnicos ou sensíveis | Execução formal pendente |
| ZES-SEC-001 | RNF-002 | Rejeitar origem não confiável | Enviar upload com origem ausente ou não confiável | Requisição é rejeitada | Cobertura automatizada |
| ZES-SEC-002 | RNF-002 | Validar assinatura real da imagem | Declarar MIME enganoso ou conteúdo inseguro | Somente assinaturas JPEG, PNG ou WebP são aceitas | Cobertura automatizada |
| ZES-SEC-003 | RNF-002 | Rejeitar corpo acima do limite | Enviar corpo acima do limite configurado | Requisição é rejeitada mesmo sem `Content-Length` | Cobertura automatizada |
| ZES-SEC-004 | RNF-003 | Proteger cookies de autenticação | Criar sessão Supabase | Cookies usam `HttpOnly`, `SameSite=Lax` e `Secure` em produção | Cobertura automatizada |
| ZES-GM-001 | GM-001–GM-003 | Acessar área do Mestre | Selecionar a opção Mestre | Funcionalidade permanece identificada como em desenvolvimento | Não implementado |
| ZES-SO-001 | SO-001–SO-007 | Criar e entrar em sessão online | Tentar fluxo planejado | Funcionalidade não está disponível no MVP atual | Não implementado |

## Registro inicial

| Data | Versão | Ambiente | Resultado |
|---|---|---|---|
| 01/10/2026 | MVP em produção | URL publicada; navegador e dispositivo ainda não registrados formalmente | Fluxos implementados informados como funcionais; ciclo formal de evidências pendente |

## Modelo de evidência

Em cada execução formal, registrar:

- Data e versão da aplicação;
- Navegador, versão, sistema e dispositivo;
- ID do caso;
- Resultado esperado e encontrado;
- Status;
- Captura ou gravação sem dados pessoais;
- ID do defeito, quando aplicável.
