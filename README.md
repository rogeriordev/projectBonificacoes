# 💰 Sistema de Gestão de Bonificações

[![PHP Version](https://img.shields.io/badge/PHP-8.x-blue.svg)](https://www.php.net/)
[![CodeIgniter](https://img.shields.io/badge/CodeIgniter-4.x-red.svg)](https://codeigniter.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-orange.svg)](https://www.mysql.com/)

> Aplicação web robusta para gerenciar bonificações de colaboradores baseada em métricas e atingimentos mensais, com fluxo de aprovação e controle financeiro completo.

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura do Sistema](#-arquitetura-do-sistema)
- [Requisitos](#-requisitos)
- [Instalação](#-instalação)
- [Estrutura de Diretórios](#-estrutura-de-diretórios)
- [Módulos do Sistema](#-módulos-do-sistema)
- [Fluxo de Trabalho](#-fluxo-de-trabalho)
- [Segurança](#-segurança)
- [Roadmap](#-roadmap)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

## 🎯 Sobre o Projeto

O **Sistema de Gestão de Bonificações** é uma solução completa desenvolvida em PHP com CodeIgniter 4 para automatizar e gerenciar todo o processo de bonificações de colaboradores baseado em indicadores de desempenho (KPIs).

### 🎪 Problema Resolvido

Empresas com múltiplos setores e colaboradores enfrentam desafios para:
- Calcular bonificações de forma justa e transparente
- Gerenciar diferentes tipos de metas (fixas, mensais, trimestrais, anuais)
- Controlar aprovações e validações financeiras
- Manter histórico e auditoria completa
- Gerar relatórios precisos para pagamento

### ✨ Solução Oferecida

Sistema flexível que permite:
- **Configuração dinâmica** de indicadores e regras de bonificação
- **Múltiplos tipos de cálculo** (fixo, proporcional, escalonado, faixas, etc.)
- **Fluxo de aprovação** completo (cálculo → validação → conclusão)
- **Controle de acesso** granular por perfil e contexto
- **Auditoria completa** de todas as operações
- **Interface intuitiva** e responsiva

## 🚀 Funcionalidades Principais

### 📊 Dashboard Inteligente
- Visualização de bonificações por período, setor, colaborador
- Gráficos interativos de desempenho
- Estatísticas em tempo real
- Filtros dinâmicos por contexto do usuário

### 🎯 Gestão de Indicadores (KPIs)
- Criação de indicadores customizados
- Suporte a múltiplos tipos: monetário, percentual, quantidade, texto, boolean
- Definição de metas: mensal, trimestral, semestral, anual ou fixa
- Indicadores por empresa, setor ou colaborador específico

### 💰 Regras de Bonificação Flexíveis
- **8 tipos de cálculo disponíveis:**
  - Fixo (valor predefinido)
  - Proporcional (% sobre atingimento)
  - Escalonado (faixas progressivas)
  - Por nível de colaborador
  - Combinado (múltiplos indicadores)
  - Quantidade (por unidade)
  - Percentual sobre valor
- Configuração de pisos e tetos
- Simulador de bonificações

### 📈 Registro de Atingimentos
- Inserção manual de valores
- Importação via planilhas (CSV, Excel)
- Validação automática de dados
- Histórico completo de alterações
- Atingimentos por mês/ano

### ✅ Fluxo de Aprovação
1. **Cálculo**: Sistema ou gestor calcula bonificações
2. **Validação**: Setor financeiro valida valores
3. **Conclusão**: Geração de relatório para pagamento
4. **Auditoria**: Registro completo de todo processo

### 👥 Gestão Organizacional
- Cadastro de empresas, setores e colaboradores
- Múltiplos vínculos por colaborador
- Hierarquia de setores
- Cargos e níveis

### 🔐 Sistema de Permissões
- **5 perfis padrão:**
  - Administrador (acesso total)
  - Financeiro (validação e relatórios)
  - Gestor Administrativo (gestão ampla)
  - Gestor (gestão de equipe)
  - Colaborador (visualização própria)
- Permissões granulares por módulo e ação
- Controle de acesso por contexto (empresa/setor)

### 📑 Relatórios e Exportações
- Relatórios de bonificações validadas
- Exportação para impressão/pagamento
- Geração de lotes numerados
- Histórico completo de relatórios

## 🛠️ Tecnologias Utilizadas

### Backend
- **PHP 8.x** - Linguagem de programação
- **CodeIgniter 4** - Framework MVC robusto e performático
- **MySQL 8.0+** - Banco de dados relacional

### Frontend
- **HTML5** - Estrutura semântica
- **CSS3** - Estilização moderna
- **JavaScript (ES6+)** - Interatividade
- **Bootstrap 5** - Framework CSS responsivo
- **jQuery** - Manipulação DOM e AJAX
- **Chart.js** - Gráficos interativos
- **SweetAlert2** - Modais e alertas elegantes

### Bibliotecas Auxiliares
- **PhpSpreadsheet** - Manipulação de planilhas Excel
- **TCPDF/mPDF** - Geração de PDFs
- **PHPMailer** - Envio de e-mails
- **Encrypter** - Criptografia de dados sensíveis

## 🏗️ Arquitetura do Sistema

### Padrão MVC
```
┌─────────────┐       ┌──────────────┐       ┌─────────────┐
│    View     │ ◄───► │  Controller  │ ◄───► │    Model    │
│  (Interface)│       │   (Lógica)   │       │   (Dados)   │
└─────────────┘       └──────────────┘       └─────────────┘
```

### Camadas de Segurança
```
Cliente → Validação Frontend → Controller → Validação Backend
                                    ↓
                            Verificação de Permissões
                                    ↓
                              Model + Database
                                    ↓
                            Log de Auditoria
```

### Fluxo de Bonificação
```
Indicador → Meta → Atingimento → Cálculo → Validação → Relatório → Pagamento
    ↓         ↓         ↓           ↓           ↓           ↓
  Config   Definir  Inserir    Aplicar     Financeiro  Concluir
                              Regras
```

## 📦 Requisitos

### Servidor
- **PHP**: >= 8.0
- **Extensões PHP requeridas:**
  - `intl` (internacionalização)
  - `mbstring` (multibyte string)
  - `json` (manipulação JSON)
  - `mysqlnd` (MySQL Native Driver)
  - `xml` (manipulação XML)
  - `curl` (requisições HTTP)

### Banco de Dados
- **MySQL**: >= 8.0 ou **MariaDB**: >= 10.3

### Recomendações
- **Memória PHP**: >= 256MB
- **Upload Max**: >= 10MB (para importação de planilhas)
- **Post Max Size**: >= 10MB
- **Execution Time**: >= 60s (para processamentos grandes)

## 🚀 Instalação

### 1. Clone o Repositório
```bash
git clone https://github.com/seu-usuario/sistema-bonificacoes.git
cd sistema-bonificacoes
```

### 2. Configure o Ambiente
```bash
# Copie o arquivo de ambiente
cp env .env

# Edite as configurações do banco
nano .env
```

### 3. Configure o Banco de Dados
```env
database.default.hostname = localhost
database.default.database = sistema_bonificacoes
database.default.username = seu_usuario
database.default.password = sua_senha
database.default.DBDriver = MySQLi
```

### 4. Importe o Schema do Banco
```bash
mysql -u seu_usuario -p sistema_bonificacoes < bonificacoes_database.sql
```

### 5. Configure Permissões
```bash
chmod -R 755 writable/
chmod -R 755 public/uploads/
```

### 6. Instale Dependências (se usar Composer)
```bash
composer install
```

### 7. Acesse o Sistema
```
http://localhost/sistema-bonificacoes/
```

**Login Padrão:**
- **Usuário**: admin
- **Senha**: admin123 (alterar no primeiro acesso)

## 📁 Estrutura de Diretórios

```
sistema-bonificacoes/
├── app/
│   ├── Controllers/          # Controladores da aplicação
│   │   ├── Auth/            # Autenticação
│   │   ├── Dashboard/       # Dashboard
│   │   ├── Atingimentos/    # Gestão de atingimentos
│   │   ├── Bonificacoes/    # Gestão de bonificações
│   │   ├── Metricas/        # Indicadores e metas
│   │   └── Configuracoes/   # Configurações do sistema
│   │
│   ├── Models/              # Modelos de dados
│   │   ├── EmpresaModel.php
│   │   ├── SetorModel.php
│   │   ├── ColaboradorModel.php
│   │   ├── IndicadorModel.php
│   │   ├── BonificacaoModel.php
│   │   └── ...
│   │
│   ├── Views/               # Interfaces visuais
│   │   ├── layout/          # Layouts base
│   │   ├── components/      # Componentes reutilizáveis
│   │   ├── auth/            # Telas de autenticação
│   │   ├── dashboard/       # Dashboard
│   │   ├── atingimentos/    # CRUD de atingimentos
│   │   ├── bonificacoes/    # CRUD de bonificações
│   │   ├── metricas/        # Gestão de métricas
│   │   └── configuracoes/   # Configurações
│   │
│   ├── Helpers/             # Funções auxiliares
│   │   ├── hierarquia_helper.php
│   │   ├── permissoes_helper.php
│   │   └── formatacao_helper.php
│   │
│   ├── Libraries/           # Bibliotecas customizadas
│   │   ├── CalculoBonificacao.php
│   │   ├── ImportadorPlanilha.php
│   │   └── GeradorRelatorio.php
│   │
│   └── Config/              # Arquivos de configuração
│       ├── Routes.php
│       ├── Database.php
│       └── ...
│
├── public/                  # Arquivos públicos
│   ├── assets/
│   │   ├── css/            # Estilos
│   │   ├── js/             # Scripts
│   │   └── img/            # Imagens
│   ├── uploads/            # Uploads de usuários
│   └── index.php           # Entry point
│
├── writable/               # Arquivos gerados
│   ├── logs/              # Logs do sistema
│   ├── cache/             # Cache
│   └── session/           # Sessões
│
├── bonificacoes_database.sql   # Schema do banco
├── .env                        # Variáveis de ambiente
└── README.md                   # Este arquivo
```

## 🎨 Módulos do Sistema

### 🔐 Autenticação
- Login com validação
- Recuperação de senha
- Primeiro acesso / Definição de senha
- Alteração de senha
- Gestão de perfil

### 📊 Dashboard
- Visão geral de bonificações
- Gráficos de desempenho
- Filtros por período, empresa, setor, colaborador
- KPIs principais

### 🎯 Indicadores
- Cadastro de indicadores
- Configuração de tipos e unidades
- Definição de templates de importação
- Visualização detalhada

### 📈 Metas
- Definição de metas (mensal, trimestral, semestral, anual, fixa)
- Gestão por indicador
- Histórico de metas

### 💰 Bonificações
- Regras de bonificação por colaborador
- 8 tipos de cálculo diferentes
- Configuração de faixas e escalas
- Simulador de bonificações
- Gestão de níveis

### 📝 Atingimentos
- Inserção manual de valores
- Importação via planilhas
- Dashboard de atingimentos
- Validação automática

### ✅ Bonificações (Processo)
- Cálculo automático/manual
- Validação financeira
- Geração de relatórios
- Conclusão e fechamento

### ⚙️ Configurações
- Empresas, Setores, Cargos
- Colaboradores e vínculos
- Usuários e perfis
- Permissões granulares

## 🔄 Fluxo de Trabalho

### 1️⃣ Configuração Inicial (Administrador)
1. Cadastrar empresas e setores
2. Cadastrar colaboradores e vínculos
3. Criar indicadores
4. Definir metas
5. Configurar regras de bonificação

### 2️⃣ Operação Mensal (Gestor)
1. Inserir atingimentos (manual ou importação)
2. Sistema calcula bonificações automaticamente
3. Gestor revisa e pode recalcular se necessário

### 3️⃣ Validação (Financeiro)
1. Revisar bonificações calculadas
2. Validar valores
3. Adicionar observações se necessário

### 4️⃣ Conclusão (Financeiro)
1. Gerar relatório para pagamento
2. Concluir bonificações do período
3. Enviar para processamento de pagamento

### 5️⃣ Visualização (Colaborador)
1. Ver suas bonificações
2. Acompanhar histórico
3. Visualizar detalhamento de cálculos

## 🔒 Segurança

### Implementações de Segurança

- ✅ **CSRF Protection** - Proteção contra ataques CSRF
- ✅ **SQL Injection Prevention** - Prepared statements em todas queries
- ✅ **XSS Protection** - Sanitização de inputs e outputs
- ✅ **Criptografia de IDs** - IDs sensíveis criptografados nas views
- ✅ **Criptografia de Dados** - CPF e dados sensíveis criptografados
- ✅ **Validação Server-Side** - Validação rigorosa no backend
- ✅ **Controle de Acesso** - Verificação de permissões em todas rotas
- ✅ **Log de Auditoria** - Registro completo de operações
- ✅ **Sessões Seguras** - Configuração segura de sessões
- ✅ **Password Hashing** - Senhas com bcrypt

### Boas Práticas

```php
// Exemplo de uso do Encrypter Helper
$cpf_criptografado = encriptar($cpf);
$cpf_descriptografado = descriptar($cpf_criptografado);

// IDs sempre criptografados nas views
$id_criptografado = encriptar($bonificacao_id);
```

## 📈 Roadmap

### ✅ Fase 1 - MVP (Concluído)
- [x] Estrutura base do banco de dados
- [x] Sistema de autenticação
- [x] CRUD de empresas, setores, colaboradores
- [x] Gestão de indicadores
- [x] Sistema de permissões

### 🚧 Fase 2 - Core (Em Desenvolvimento)
- [ ] Cálculo de bonificações
- [ ] Fluxo de aprovação completo
- [ ] Dashboard interativo
- [ ] Importação de planilhas
- [ ] Geração de relatórios

### 📋 Fase 3 - Melhorias
- [ ] API REST para integrações
- [ ] Notificações por e-mail
- [ ] Exportação em múltiplos formatos
- [ ] Gráficos avançados
- [ ] Módulo de relatórios customizados

### 🔮 Fase 4 - Avançado
- [ ] Inteligência artificial para previsões
- [ ] Aplicativo mobile
- [ ] Integração com sistemas de RH
- [ ] Gamificação
- [ ] Multi-idioma

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

### Diretrizes
- Siga o padrão PSR-12 para código PHP
- Documente novas funcionalidades
- Adicione testes quando possível
- Mantenha compatibilidade com versões anteriores

## 📞 Suporte

- 📧 Email: seu-email@exemplo.com
- 🐛 Issues: [GitHub Issues](https://github.com/seu-usuario/sistema-bonificacoes/issues)
- 📖 Wiki: [Documentação Completa](https://github.com/seu-usuario/sistema-bonificacoes/wiki)

<p align="center">
  <a href="#-índice">⬆ Voltar ao topo</a>
</p>
