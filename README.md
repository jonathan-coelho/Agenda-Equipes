# 🎬 Escala Multimídia

> Sistema de agendamento e gestão da equipe de multimídia.

---

## 📋 Sobre o Projeto

A **Escala Multimídia** é uma aplicação web desenvolvida para facilitar a organização da equipe técnica responsável. Através de um calendário interativo, os membros da equipe podem visualizar os cultos programados, se inscrever nas vagas disponíveis e gerenciar substituições — tudo de forma simples e centralizada.

O sistema é integrado a uma API hospedada no **Google Apps Script**, que persiste os dados em uma planilha do Google Sheets, eliminando a necessidade de um servidor dedicado.

---

## ✨ Funcionalidades

### Para os Membros da Equipe
- 📅 **Calendário mensal** com visualização por turno (Manhã, Tarde e Noite)
- 🔍 **Detalhes por dia** — clique em qualquer data para ver os cultos e vagas disponíveis
- ✅ **Inscrição em vagas** com um clique (Entrar)
- ❌ **Remoção da escala** até 7 dias antes da data
- 🔄 **Substituição** — troca de voluntário em uma vaga específica
- 💾 **Identificação salva** localmente no navegador (sem necessidade de login)

### Para Administradores
- ➕ **Criação de cultos** com data, turno, horário e título personalizados
- 📋 **Auditoria completa** de todas as ações realizadas
- 🔐 **Código de acesso** protegendo o painel administrativo

---

## 🎛️ Funções da Equipe

Cada culto possui **6 vagas**, uma para cada função:

| Função | Descrição |
|--------|-----------|
| 🎚 **Mesa** | Operação da mesa de som |
| ✂️ **Corte** | Direção e corte ao vivo |
| 📷 **Cam 1** | Câmera 1 |
| 📷 **Cam 2** | Câmera 2 |
| 📷 **Cam 3** | Câmera 3 |
| 🖥 **Vmix** | Operação do software de transmissão |

---

## ⚙️ Regras de Negócio

- Cada pessoa pode ocupar **apenas 1 vaga por função** por culto
- Máximo de **2 inscrições por pessoa no mesmo dia**
- Remoção e substituição permitidas somente com **7 ou mais dias de antecedência**
- O botão "Sair" só é habilitado para o próprio inscrito (verificação por nome)

---

## 🏗️ Arquitetura
```
┌─────────────────────────────┐
│        Frontend (HTML)       │
│  - Interface do calendário   │
│  - Modal de detalhes do dia  │
│  - Painel administrativo     │
└────────────┬────────────────┘
             │ fetch() — REST
             ▼
┌─────────────────────────────┐
│    Google Apps Script API    │
│  - Endpoint único (Web App)  │
│  - Lógica de negócio         │
│  - Auditoria de ações        │
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│       Google Sheets          │
│  - Cultos cadastrados        │
│  - Inscrições por vaga       │
│  - Log de auditoria          │
└─────────────────────────────┘
```

---

## 🚀 Como Usar

### 1. Configurar a API

No arquivo `escala-ibrem.html`, localize a linha:
```javascript
const API_URL = "https://script.google.com/macros/s/SEU_ID_AQUI/exec";
```

Substitua pela URL do seu **Web App** publicado no Google Apps Script.

### 2. Abrir no navegador

Basta abrir o arquivo `escala-ibrem.html` diretamente no navegador — não é necessário servidor web.

### 3. Identificação

Digite seu nome no campo **"Sua identificação"** e clique em **Salvar**. O nome fica armazenado localmente e será usado para associar suas inscrições.

### 4. Navegar no calendário

Use as setas **◀ ▶** para navegar entre os meses. Clique em qualquer dia com cultos para ver os detalhes e se inscrever.

---

## 🔐 Acesso Administrativo

1. Clique no botão **Admin** no canto superior direito
2. Informe o **código administrativo**
3. Clique em **Salvar** para armazenar o código localmente

Com o código salvo é possível criar cultos e consultar o log de auditoria por período.

---

## 🎨 Design

Interface com identidade visual alinhada à IBREM:

- **Tema escuro** (black & white) com paleta sóbria e ministerial
- **Tipografia** com `Playfair Display` (serifada, elegante) nos títulos e `Inter` no corpo
- **Detalhe dourado** (`#c9a96e`) na cruz e elementos de destaque
- **Tela de carregamento** de 5 segundos com animação da logo IBREM
- **Toasts** de notificação no lugar de `alert()` nativos
- **Responsivo** para desktop e dispositivos móveis

---

## 📁 Estrutura do Projeto
```
escala-ibrem/
│
├── escala-ibrem.html     # Aplicação completa (single-file)
└── README.md             # Este arquivo
```

> O projeto é intencionalmente um **single-file**, facilitando distribuição e hospedagem sem dependências de build.

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|------------|-----|
| HTML5 / CSS3 / JavaScript (Vanilla) | Frontend completo |
| Google Apps Script | Backend / API REST |
| Google Sheets | Banco de dados |
| Google Fonts (Playfair Display + Inter) | Tipografia |

---

## 📞 Contato

**IBREM — Igreja Batista Resplandecente Estrela da Manhã**  
Rua Santa Terezinha, nº 655 — Santa Terezinha, Juiz de Fora/MG  
🌐 [www.ibrem.com.br](http://www.ibrem.com.br)

---

*Desenvolvido para uso interno da equipe de multimídia da IBREM.*
