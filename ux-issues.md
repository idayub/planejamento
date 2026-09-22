# Registro de Auditoria e Correção de UX (Hevy Edition)

Tabela de problemas de experiência do usuário, usabilidade e acessibilidade identificados no web app, categorizados por heurística de Nielsen, critérios WCAG 2.1 AA, severidade e status de resolução.

| # | Fluxo/Página | Heurística violada | Problema | Impacto no usuário | Arquivo:linha | Severidade (alta/média/baixa) | Status |
|---|---|---|---|---|---|---|---|
| 1 | Modais e Diálogos | Controle e liberdade (H3) / WCAG 2.1.2 | Modais (`#workoutSummaryModal`, `#cadenceModal`, `#executionModal`) não fecham com a tecla `Escape` e não aprisionam o foco do teclado | Usuário de teclado fica preso ou o foco vaza para elementos de fundo fora do modal aberto | `app.js:1740, 2638` | alta | ✅ corrigido |
| 2 | Cards de Exercício | Flexibilidade e eficiência (H7) / Feedback (H1) | Botão `⋯` (`.hevy-card-more`) não possuía clique nem funcionalidade e faltava o botão "+ Adicionar Série" previsto no design system original (`docs/DESIGN.md:396`) | Usuário clica no botão sem qualquer resposta e fica impedido de adicionar séries adicionais ao seu treino | `app.js:765, 1306, 1407, 1837; index.html:503` | alta | ✅ corrigido |
| 3 | Finalizar Treino / Resumo | Visibilidade de estado (H1) | Ao clicar em "Concluir & Salvar" no resumo, o cronômetro do treino não era congelado e continuava rodando em segundo plano | A duração da sessão finalizada era distorcida e continuava aumentando indefinidamente | `app.js:871, 1920, 1947` | alta | ✅ corrigido |
| 4 | Dias de Descanso (OFF) | Prevenção de erros (H5) / Realidade (H2) | Botões "Finalizar" e "Redefinir" permaneciam ativos no cabeçalho nos dias de descanso (Sábado/Domingo) | Usuário podia disparar resumo comemorativo sem exercícios (0 séries, 0 kg) ou receber prompt de redefinir descanso | `app.js:1156, 1934, 2606; styles.css:101` | alta | ✅ corrigido |
| 5 | Geral / Interações | WCAG 2.4.7 (Focus Visible) | Ausência de anel de foco de alto contraste (`:focus-visible`) nos botões, abas, inputs e modais | Usuários que navegam por teclado não conseguiam identificar visualmente qual elemento estava focado | `styles.css:105` | média | ✅ corrigido |
| 6 | Tabela de Séries | Visibilidade de estado (H1) / WCAG 4.1.2 | Botões de conclusão (`.hevy-check-btn`) não alteravam `aria-label` nem possuíam `aria-pressed` / `aria-checked` ao concluir a série | Leitores de tela continuavam anunciando "Concluir série X" sem indicar se a série estava feita ou pendente | `app.js:1374, 1415` | média | ✅ corrigido |
| 7 | Tabela de Séries | Reconhecimento e memória (H6) / WCAG 1.3.1 | Inputs de KG e Repetições possuíam `aria-label` genérico ("Carga em kg da série 1") sem citar o exercício correspondente | Navegação de campos por tecnologias assistivas não permitia saber a qual exercício o campo pertencia | `app.js:1363, 1370` | média | ✅ corrigido |
| 8 | Modais e Diálogos | Controle e liberdade (H3) | Modais não possuíam botão de fechar visível ("✕") nos cabeçalhos | Usuário mobile precisava rolar longos conteúdos até o rodapé ou descobrir que o scrim/puxador fecha a tela | `index.html:329, 369, 397, 514; styles.css:1302` | média | ✅ corrigido |
| 9 | Redefinir Treino | Prevenção de erros (H5) / Clareza | Confirmação de redefinição usava texto vago sem detalhar as consequências da ação destrutiva | Usuário podia redefinir sem saber que as séries seriam desmarcadas e as cargas salvas como histórico | `app.js:2611` | média | ✅ corrigido |
| 10 | Preferências | Visibilidade de estado (H1) | Botão de notificações exibia texto estático "Permitir" mesmo quando a permissão já havia sido concedida ou bloqueada | Falta de feedback sobre se as notificações estavam efetivamente ativas ou bloqueadas no navegador | `app.js:1802, 2927` | média | ✅ corrigido |
| 11 | Cabeçalho / Tema | Visibilidade de estado (H1) / WCAG 4.1.2 | Botão de alternar tema possuía `aria-label` genérico e não indicava a ação resultante | Usuário de tecnologia assistiva não sabia se a ação ativaria o tema escuro ou claro | `app.js:2687` | baixa | ✅ corrigido |
| 12 | Treinador de Execução | Feedback (H1) / WCAG 4.1.2 | Botão de som (`#coachSoundToggle`) não atualizava seu `aria-label` nem `aria-pressed` ao alternar mudo/ativo | Usuário não tinha confirmação semântica do estado do áudio da animação | `app.js:2391` | baixa | ✅ corrigido |
| 13 | Anotações do Dia | Visibilidade de estado (H1) | Área de texto salvava automaticamente sem nenhum indicativo visual de salvamento | Usuário ficava inseguro se o texto digitado havia sido persistido com sucesso | `app.js:2885; index.html:263; styles.css:1146` | baixa | ✅ corrigido |
| 14 | Navegação Principal | Consistência e padrões (H4) / Correspondência (H2) | As 5 abas inferiores possuem rótulos do app nativo ("Início", "Perfil", "Treino", "Histórico", "Exercícios"), mas fazem scroll para blocos locais de função diferente | Causa confusão: usuário clica em "Perfil" e cai em anotações; clica em "Histórico" e cai na barra muscular; clica em "Exercícios" e cai em preferências | `index.html:507; app.js:2560` | média | ⚠️ recomendação |
| 15 | Identidade Visual / Cores | WCAG 1.4.3 (Contraste Mínimo) | Cor de texto terciária (`--text-tertiary: #5E6675`) possui taxa de contraste ~3.3:1 em relação ao card escuro (`#161B22`) | Dificulta a leitura da coluna "ANTERIOR" e dicas em ambientes de academia sob forte iluminação | `styles.css:23` | média | ⚠️ recomendação |

---

## Propostas Detalhadas para Itens ⚠️ RECOMENDAÇÃO (Decisões de Design Subjetivas)

### Proposta para Item #14 (Navegação Inferior - Bottom Tab Bar)
**Contexto**: O web app atual é um *single-page workout tracker*. As 5 abas foram estilizadas com base no aplicativo nativo iOS do Hevy (`Home`, `Profile`, `Workout`, `History`, `Exercises`), porém apenas a tela de `Workout` foi implementada.
**Proposta**: 
1. **Opção Recomendada (A)**: Atualizar os rótulos e ícones para refletir navegação real das seções da página:
   - "Semana" (`#dayTabs`)
   - "Músculos" (`#structureSection`)
   - "Treino" (`#workoutList`)
   - "Notas" (`#notesCard`)
   - "Ajustes" (`#settingsCard`)
2. **Opção Alternativa (B)**: Desenvolver modais dedicados de "Histórico" (exibindo registros de treinos anteriores salvos no localStorage) e "Exercícios" (biblioteca de exercícios do Arnold Split com filtros de grupo muscular).

### Proposta para Item #15 (Contraste da Identidade Visual)
**Contexto**: A variável `--text-tertiary: #5E6675` foi definida no design system original como cor de suporte para placeholders e hints (`docs/DESIGN.md:23`). No entanto, ao ser utilizada nos números da coluna `ANTERIOR` (13pt), sua taxa de contraste fica em 3.28:1, abaixo da recomendação WCAG AA de 4.5:1.
**Proposta**: Ajustar a cor `--text-tertiary` no tema escuro para `#8B95A5` (ou utilizar `--text-secondary: #9BA3B0` especificamente na classe `.hevy-col-prev`). Isso eleva a taxa de contraste para 5.4:1 sem descaracterizar a atmosfera Gym-Floor escura do aplicativo.
