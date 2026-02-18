# 🏥 Atesta-SUS - Sistema Nacional de Atestados Médicos Digitais

Sistema inspirado no modelo estoniano X-Road para emissão, validação e auditoria de atestados médicos digitais, integrado ao SUS.

## 🎯 Funcionalidades Principais

### 🔐 **4 Perfis de Usuário**

1. **Médico** - Emite atestados digitais com assinatura única
2. **Paciente** - Visualiza e compartilha atestados recebidos
3. **Empresa/RH** - Valida autenticidade de atestados
4. **Auditor** - Fiscaliza e monitora o sistema

### 🛡️ **Segurança e Privacidade (LGPD)**

- **Separação de Dados:**
  - **Clínicos** (sigilosos): CID, diagnóstico, sintomas, tratamento
  - **Administrativos** (públicos): nome, período, médico responsável

- **Sistema de Auditoria:** Todo acesso é registrado e rastreável
- **Hash Único:** Cada atestado possui identificador criptográfico único
- **QR Code:** Validação rápida e segura via smartphone

### ✨ **Funcionalidades por Perfil**

#### 👨‍⚕️ Médico
- Emissão digital de atestados
- Histórico de atestados emitidos
- Estatísticas de afastamentos

#### 👤 Paciente
- Visualização de atestados recebidos
- Compartilhamento seguro com empresas
- Logs de quem acessou seus atestados (transparência total)

#### 🏢 Empresa/RH
- Validação instantânea via hash ou QR Code
- Acesso APENAS a dados administrativos (LGPD)
- Sem acesso a informações clínicas

#### 🔍 Auditor
- Dashboard com estatísticas do sistema
- Logs de auditoria completos
- Gráficos e métricas em tempo real

## 🚀 Tecnologias

### Backend
- **FastAPI** - Framework Python moderno
- **MongoDB** - Banco de dados NoSQL
- **JWT** - Autenticação segura
- **QRCode** - Geração de códigos de validação
- **Bcrypt** - Hash de senhas

### Frontend
- **React** - Interface moderna e responsiva
- **Tailwind CSS** - Estilização
- **Lucide React** - Ícones
- **Recharts** - Gráficos
- **Sonner** - Notificações

## 📦 Instalação

### Backend
```bash
cd backend
pip install -r requirements.txt
python -m uvicorn server:app --reload --host 0.0.0.0 --port 8001
```

### Frontend
```bash
cd frontend
yarn install
yarn start
```

## 🔑 Usuários Demo

| Perfil | CPF/CNPJ | Senha | Nome |
|--------|-----|-------|------|
| Médico | 111.111.111-11 | demo123 | Dr. João Silva |
| Paciente | 222.222.222-22 | demo123 | Maria Santos |
| Empresa | 00.000.000/0000-00 | demo123 | Empresa Tech LTDA |
| Auditor | 444.444.444-44 | demo123 | Carlos Auditor |

## 📋 Fluxo de Uso

### 1. Emissão (Médico)
1. Login com credenciais de médico
2. Clicar em \"Novo Atestado\"
3. Informar CPF do paciente e dados clínicos
4. Sistema gera hash único e QR Code

### 2. Visualização (Paciente)
1. Login como paciente
2. Ver histórico completo de atestados
3. Visualizar dados clínicos (sigilosos)
4. Compartilhar hash com empresa

### 3. Validação (Empresa)
1. Login como empresa
2. Inserir hash fornecido pelo funcionário
3. Sistema valida e exibe APENAS dados administrativos
4. QR Code disponível para impressão

### 4. Auditoria (Auditor/Governo)
1. Login como auditor
2. Dashboard com estatísticas gerais
3. Logs de todos os acessos ao sistema
4. Gráficos de atestados ativos/expirados

## 🔒 Segurança Implementada

- ✅ **JWT Tokens** com expiração de 7 dias
- ✅ **Senhas hasheadas** com bcrypt
- ✅ **Separação de dados** clínicos/administrativos
- ✅ **Auditoria completa** de acessos
- ✅ **Hash único** inviolável por atestado
- ✅ **Validação pública** sem expor dados sensíveis
- ✅ **Controle de permissões** por tipo de usuário

## 🌐 API Endpoints

### Autenticação
- `POST /api/auth/register` - Cadastro
- `POST /api/auth/login` - Login
- `GET /api/auth/me` - Usuário atual

### Atestados
- `POST /api/atestados` - Criar (médico)
- `GET /api/atestados/medico` - Listar do médico
- `GET /api/atestados/paciente` - Listar do paciente
- `GET /api/atestados/validar/{hash}` - Validação pública
- `GET /api/atestados/{id}/logs` - Logs de auditoria

### Auditoria
- `GET /api/stats` - Estatísticas (auditor)
- `GET /api/audit/recent` - Logs recentes (auditor)

## 🎨 Design

- **Tema Neo-Clinical** - Moderno e profissional
- **Cores Principais:**
  - Indigo (confiança)
  - Emerald (verificado)
  - Rose (alerta)
- **Tipografia:**
  - Outfit (headings)
  - Inter (body)
  - JetBrains Mono (código/hash)

## 🏗️ Arquitetura

```
Sistema Atesta-SUS
├── Backend (FastAPI)
│   ├── Autenticação JWT
│   ├── CRUD Atestados
│   ├── Sistema de Logs
│   └── Validação Pública
│
├── Frontend (React)
│   ├── Landing Page
│   ├── Login/Registro
│   ├── 4 Dashboards
│   └── Validação Pública
│
└── MongoDB
    ├── users
    ├── atestados
    └── audit_logs
```

## 🌍 Inspiração: Modelo Estoniano

O sistema foi inspirado no **X-Road** da Estônia, que integra sistemas governamentais de forma segura e transparente:

- **Descentralização:** Dados ficam na origem
- **Interoperabilidade:** Sistemas diferentes se comunicam
- **Auditoria:** Todo acesso é rastreado
- **Privacidade:** Cidadão sabe quem acessou seus dados

## 📊 Estatísticas do Sistema

- ✅ 4 perfis de usuário implementados
- ✅ Sistema de logs auditáveis
- ✅ Validação pública via QR Code
- ✅ Conformidade LGPD
- ✅ Interface responsiva

## 🎯 Próximas Melhorias

1. **Integração Gov.br** (autenticação real)
2. **Blockchain** para logs imutáveis
3. **Notificações** push e email
4. **App Mobile** nativo
5. **Integração ConecteSUS**
6. **Assinatura Digital** ICP-Brasil
7. **API para sistemas de RH** (integração Totvs, Senior, etc)

## 📄 Licença

GPLv3 - Software Público Brasileiro

## 👥 Contato

guilhermegustavo.so@gmail.com

Sistema desenvolvido para o SUS Brasil - 2026

---

**Atesta-SUS** - Digitalizando a saúde pública com segurança e transparência 🇧🇷
