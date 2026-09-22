# Registro de Auditoria de Responsividade

Tabela de problemas de responsividade identificados no web app, categorizados por severidade e status de resolução.

| # | Página | Breakpoint | Problema | Arquivo:linha | Severidade (alta/média/baixa) | Status |
|---|---|---|---|---|---|---|
| 1 | Geral / Treino | 320px, 375px | Overflow horizontal crítico (scrollWidth 534px) causado por inputs da tabela de séries (`.hevy-cell-input`) com `min-width: auto` padrão (size ~20ch/195px), impedindo encolhimento flex e expandindo as linhas para 495px | `styles.css:898` | alta | ✅ corrigido |
| 2 | Geral / Treino | 320px | Overflow horizontal da barra de dias da semana (`.hevy-week-strip`). A grid com `repeat(7, 1fr)` não permite encolhimento (`min-content` ~45px por coluna), esticando a barra para 347px em viewport com 288px disponíveis | `styles.css:298` | alta | ✅ corrigido |
| 3 | Geral / Treino (Mobile) | 320px, 375px, 768px | Botão de conclusão de série (`.hevy-check-btn`) com área de toque de apenas 26x26px, inferior ao mínimo de 44x44px recomendado para uso mobile | `styles.css:929` | alta | ✅ corrigido |
| 4 | Geral / Treino (Mobile) | 320px, 375px, 768px | Botão "Finalizar Treino" (`.hevy-btn-finish`) possui altura de 30px (padding 7px 16px), abaixo do mínimo de toque acessível de 44px | `styles.css:229` | alta | ✅ corrigido |
| 5 | Anotações / Treino (Mobile) | 320px, 375px, 768px | Campo `textarea#dayNotes` possui `font-size: 14px`, provocando disparo de zoom automático indesejado no iOS / Safari Mobile (mínimo 16px para inputs) | `styles.css:1011` | alta | ✅ corrigido |
| 6 | Geral / Treino (Mobile) | 320px, 375px, 768px | Botões de utilitários e ações secundárias (`#themeToggle`, `#resetDayButton`, `.hevy-card-more`, `.badge-cadence`) com área de toque inferior a 44x44px | `styles.css:209, 589, 764, 1323` | média | ✅ corrigido |
| 7 | Timer / Descanso (Mobile) | 320px, 375px, 768px | Botões de controle de descanso no pill principal e sticky (`.hevy-pill-btn-small`, `.hevy-pill-btn`) com altura reduzida (24-28px), inferior a 44px de área de toque | `styles.css:431, 539` | média | ✅ corrigido |
| 8 | Modal Treinador de Execução | 320px, 375px | SVG do treinador (`.coach-svg`) e palco de animação com dimensões rígidas acumuladas com paddings de modal, arriscando overflow em 320px | `styles.css:1572, 1590` | média | ✅ corrigido |
| 9 | Modal de Cadência | 320px | Grid da fórmula didática de cadência (`.cadence-formula-grid`) com 4 colunas rígidas e padding que comprime excessivamente números e rótulos em 320px | `styles.css:1398` | média | ✅ corrigido |
| 10 | Navegação Principal (Desktop) | 1024px, 1440px, 1920px | Barra de navegação inferior (`.hevy-tab-bar`) estica em 100% da tela (1920px), dispersando os ícones nos cantos extremos e desalinhando da casca central do app (`max-width: 620px`) | `styles.css:1216` | média | ✅ corrigido |
| 11 | Modais (Desktop) | 1024px, 1440px, 1920px | Modais (`.hevy-modal-sheet`) renderizam presos como bottom sheet no rodapé em telas grandes, sem elevação centralizada como diálogo de desktop | `styles.css:1091, 1113` | baixa | ✅ corrigido |
| 12 | Faixa de Métricas (Mobile Pequeno) | 320px | Espaçamento rígido na barra de 3 métricas (`.hevy-metrics-strip`, gap 16px e padding 14px) aperta excessivamente os valores em 320px | `styles.css:247` | baixa | ✅ corrigido |
