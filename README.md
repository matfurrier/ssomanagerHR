# SSO Manager — Gestão de Segurança Ocupacional

Sistema web completo para gestão de segurança do trabalho em empresas com mão de obra terceirizada. Controla documentos, permissões de trabalho, treinamentos, ocorrências, planos de ação, indicadores proativos, auditorias comportamentais e reportes de segurança em um único lugar.

---

## Funcionalidades

### Empresas e Colaboradores
- Cadastro de empresas terceirizadas com CNPJ, tipo de contrato e dados de contato
- Cadastro de colaboradores com CPF, cargo, foto e documentos obrigatórios
- Status de conformidade calculado automaticamente com base nos documentos do colaborador (Ativo / Pendente / Reprovado)
- Controle de documentos por empresa (contratos, alvarás, certificações, PCMSO/PGR-LTCAT)

### Documentos
- Upload e gerenciamento de documentos de colaboradores: ASO, NR-10, NR-20, NR-35, EPI e outros
- Aprovação/reprovação de documentos com auditoria de cada alteração
- Cálculo automático de vencimento e status (Aprovado / Vencido / Pendente / Reprovado)

### Permissões de Trabalho (PTC)
- Emissão de Permissão de Trabalho para tipos críticos: eletricidade (NR-10), trabalho a quente, produtos químicos, içamento/movimentação de cargas, espaço confinado (formulário dedicado) e outros
- Checklists dinâmicos por tipo crítico, com blocos condicionais, campos numéricos com unidade e alertas de plano de içamento
- Controle de EPI (lista completa) e EPC exigidos por permissão, com origem sempre auditável
- Autocomplete unificado de trabalhadores (internos e terceiros), com validação automática de treinamentos obrigatórios por NR
- Workflow de aprovação, revalidação e encerramento com assinatura e carimbo de data/hora
- Geração de PDF da permissão com todos os checklists, EPI/EPC e assinaturas

### Treinamentos
- Cadastro de tipos de treinamento com carga horária, validade e objetivos
- Agendamento de sessões (internas e externas) com instrutor, local e setor
- Gestão de participantes internos (usuários corporativos) e externos (terceiros)
- Registro de aprovação, nota, habilidades adquiridas (skills matrix) e emissão de certificado
- Upload de lista de presença e arquivos de prova por participante
- Alertas automáticos de vencimento por e-mail, configuráveis por tipo de treinamento

### Avaliação de Treinamentos
- **Satisfação:** formulário público de 14 perguntas enviado por e-mail aos participantes após a sessão — avalia conteúdo, instrutor, metodologia, instalações e eficácia percebida
- **Eficácia:** formulário público de 40 perguntas enviado ao gestor/supervisor 30-60 dias após o treinamento — mede transferência de conhecimento, mudança comportamental e impacto no desempenho
- Relatórios consolidados com médias, distribuição de respostas e exportação em PDF e CSV

### Matriz de Treinamentos por NR
- Matriz de exigências de NR por colaborador (NR-06, NR-10, NR-11, NR-13, NR-17, NR-18, NR-20, NR-23, NR-26, NR-33, NR-34, NR-35 e outras), com catálogo de códigos e sub-variantes
- Cálculo de conformidade por NR (válido / a vencer / vencido / nunca fez), respeitando o certificado real emitido no treinamento
- Bloqueio de exigência com propagação por grupo de NRs relacionadas, e vínculo manual (individual ou em lote por setor)
- Tela de divergências para revisão dirigida dos casos pendentes de regularização

### Safety Reports
- Formulário de reporte de segurança (público ou autenticado) com foto, classificação de risco e ação imediata
- Workflow de encerramento com histórico completo de alterações
- Ações corretivas vinculadas ao reporte com prazo e responsável
- Dashboard com KPIs: total por status, ações vencidas, tempo médio de resolução, top setores

### Ocorrências SST
- Registro de acidentes e incidentes com tabelas de apoio: tipo de acidente, parte do corpo, fonte geradora, agente causador, tipo de energia e evento SIF
- Dashboard de Taxa de Frequência e Gravidade por período e setor
- Filtro por ano fiscal configurável (setembro–agosto)

### Planos de Ação
- Motor de ações corretivas/preventivas compartilhado entre Safety Reports, Auditoria Comportamental, Brigada de Incêndio e PTC
- Dashboard com KPIs, distribuição por tipo e prioridade, responsável, diretoria e setor, e linha do tempo mensal de criação/conclusão
- Anexos armazenados em bucket próprio, vinculados à ação e à origem que a gerou

### Auditoria Comportamental
- Registro de observações de comportamento seguro/inseguro por categoria (EPI, postura, ferramentas, movimentação de materiais, etc.)
- Dashboard com tendências mensais, distribuição por local e análise por categoria comportamental
- Histórico completo de alterações com dados antes/depois

### Painel de Indicadores Proativos (Mural)
- Visão consolidada dos indicadores recorrentes de SST, com semáforo de conformidade (em dia / a vencer / vencido) por indicador
- **Extintores:** controle de vencimento de recarga e de teste hidrostático por ativo
- **DSS (Diálogo de Segurança):** aderência por setor contra meta configurável de encontros/mês
- **Ginástica Laboral:** importação do relatório mensal de frequência da empresa terceirizada
- **Brigada de Incêndio:** checklist de inspeção por área/gestor, gestão de responsabilidades (entrada/saída de time ajusta a meta automaticamente) e aderência histórica
- **Trabalhos Críticos (PTC) e Matriz NR:** cards reaproveitando os indicadores já calculados nos módulos correspondentes
- Filtro de período por ano fiscal (setembro–agosto) em todos os indicadores

### Módulo de Limpeza
- Catálogo de atividades de limpeza por área, frequência (diária/semanal/quinzenal/mensal) e tempo estimado
- Execução mobile-first: colaboradora seleciona a atividade, inicia e finaliza (com observações opcionais), horário registrado automaticamente
- Dashboard com métricas, filtros por período/colaboradora/área e exportação de relatórios

### Guarita — Controle de Acesso de Terceiros
- Consulta de liberação de colaborador terceiro na portaria, combinando status cadastral, documentos aprovados/vencidos e documentos da empresa (PCMSO/PGR-LTCAT)
- Aviso visual (não bloqueante) para NRs vencidas, mantendo a decisão final com o operador da guarita
- Dashboard de acompanhamento das liberações

### Relatórios
- Relatório de treinamentos por usuário com filtros, paginação e ordenação
- Relatório de avaliações de satisfação por sessão
- Relatório de eficácia com exportação PDF individual e consolidado por sessão

---

## Stack

| Camada | Tecnologias |
|--------|-------------|
| **Backend** | Node.js, Express, Sequelize ORM |
| **Frontend** | React 18, React Router v6, TailwindCSS, Material UI |
| **Banco de dados** | PostgreSQL (dois bancos lógicos: `security` e `sso_manager`) |
| **Autenticação** | JWT + Argon2, base de usuários corporativa |
| **E-mail** | Nodemailer + templates Handlebars |
| **Jobs** | node-cron (alertas de vencimento diários) |
| **Deploy** | Docker + Docker Compose + Nginx |

---

## Arquitetura

O sistema usa **dois bancos PostgreSQL**:

- `security` — usuários corporativos, departamentos e controle de acesso às aplicações SSO
- `sso_manager` — todos os dados da aplicação (empresas, colaboradores, treinamentos, safety reports, auditorias)

A autenticação é feita contra o banco `security`. O acesso ao SSO Manager é controlado pela associação do usuário com a aplicação `SSO` nessa base.

**Perfis de acesso:**
- `sso_manager` — acesso completo (CRUD)
- `sso_auditor` — acesso de leitura e relatórios
- `sso_limpeza` — acesso restrito ao módulo de Limpeza
- `sso_guarita` — acesso restrito à consulta de liberação na portaria
- `admin` — acesso total ao sistema

---

