# SSO Manager — Gestão de Segurança Ocupacional

Sistema web completo para gestão de segurança do trabalho em empresas com mão de obra terceirizada. Controla documentos, treinamentos, auditorias comportamentais e reportes de segurança em um único lugar.

---

## Funcionalidades

### Empresas e Colaboradores
- Cadastro de empresas terceirizadas com CNPJ, tipo de contrato e dados de contato
- Cadastro de colaboradores com CPF, cargo, foto e documentos obrigatórios
- Status de conformidade calculado automaticamente com base nos documentos do colaborador (Ativo / Pendente / Reprovado)
- Controle de documentos por empresa (contratos, alvarás, certificações)

### Documentos
- Upload e gerenciamento de documentos de colaboradores: ASO, NR-10, NR-20, NR-35, EPI e outros
- Aprovação/reprovação de documentos com auditoria de cada alteração
- Cálculo automático de vencimento e status (Aprovado / Vencido / Pendente / Reprovado)

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

### Safety Reports
- Formulário de reporte de segurança (público ou autenticado) com foto, classificação de risco e ação imediata
- Workflow de encerramento com histórico completo de alterações
- Ações corretivas vinculadas ao reporte com prazo e responsável
- Dashboard com KPIs: total por status, ações vencidas, tempo médio de resolução, top setores

### Auditoria Comportamental
- Registro de observações de comportamento seguro/inseguro por categoria (EPI, postura, ferramentas, movimentação de materiais, etc.)
- Dashboard com tendências mensais, distribuição por local e análise por categoria comportamental
- Histórico completo de alterações com dados antes/depois

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
- `admin` — acesso total ao sistema

---

