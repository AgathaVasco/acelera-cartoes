# 📘 Guia do Projeto — Conflex / Acelera / P4H

Documento de referência para continuar os projetos em qualquer computador.
Mantido na nuvem (GitHub) para nunca se perder.

---

## 🗂️ Visão geral — são 2 sistemas

### 1) Controle de Cartões de Crédito (app web)
- **Link do app:** https://agathavasco.github.io/acelera-cartoes/
- **O que faz:** controle de faturas dos cartões e extrato bancário, importação de PDF, conciliação, relatório contábil (CSV), anexos de notas/comprovantes.
- **Abas e empresas:**
  - Acelera Corretora → Banco do Brasil, Unicred
  - P4H Saúde → Itaú P4H
  - Planoo Tecnologia → Extrato Planoo (conta corrente Itaú, com Entradas e Saídas)
- **Login:** cada usuário entra com e-mail e senha. Tem "Esqueci minha senha".
- **Categorias inteligentes:** quando você confirma uma categoria (na importação ou editando um lançamento), o app memoriza "fornecedor → categoria" e já sugere sozinho nos próximos meses.
- **Plano de contas por empresa:** em ⚙ Categorias há um seletor "Plano da empresa" — cada empresa (Acelera, P4H, Planoo) tem suas próprias categorias e códigos contábeis. Enquanto uma empresa não for personalizada, ela usa o cadastro geral antigo.

### 2) Central Contábil P4H (arquivo no computador)
- **Arquivo:** `P4H_Central_Automacoes_1.html` (abre direto no navegador, dois cliques)
- **O que faz:** automação contábil de Unimed, Adepol e Uniodonto — Faturamento, Recebimento, PPSC, gerar/atualizar base de coparticipação, exportação para o Domínio.
- ⚠️ **Não está na nuvem.** Precisa COPIAR esse arquivo para o computador novo.

---

## ☁️ Onde estão as contas (todas grátis)

| Serviço | Para que serve | Como entrar |
|---|---|---|
| **GitHub** | Guarda o código do app de cartões | Conta da Agatha (login com e-mail/GitHub) |
| **Supabase** | Banco de dados + login do app de cartões | Entra com o **GitHub** (botão "Continuar com o GitHub") |
| ~~Netlify~~ | (desativado — sem créditos) | Não usar mais; trocamos pelo GitHub Pages |

- **Projeto Supabase:** `acelera-cartoes`
- **Hospedagem do app:** GitHub Pages (Settings → Pages → branch `main` / root)

---

## 💻 Como continuar no computador NOVO

### Para o app de Cartões:
1. Instale o **GitHub Desktop** (desktop.github.com) e entre com sua conta GitHub.
2. **File → Clone repository** → escolha **acelera-cartoes** → Clone.
3. Pronto — o código está na sua máquina e conectado ao GitHub.
4. (Opcional) Instale o **LibreOffice** se precisar rodar scripts Python locais.

### Para a Central Contábil P4H:
1. Copie o arquivo `P4H_Central_Automacoes_1.html` do computador antigo (pen drive / OneDrive / e-mail).
2. No computador novo, é só dar dois cliques pra abrir no navegador.

---

## ✏️ Como fazer mudanças no app de Cartões (fluxo)
1. Peça a alteração ao Claude (ou edite o `index.html`).
2. No **GitHub Desktop**: escreva um resumo no campo **Summary** (o de cima!), clique **Commit to main**, depois **Push origin**.
3. Aguarde ~1 minuto → o app atualiza sozinho no link do GitHub Pages.
4. No navegador, recarregue com **Ctrl + Shift + R**.

---

## 👥 Controle de acesso por empresa (app de Cartões)
- **Authentication (Supabase)** = quem pode ENTRAR (e-mail + senha).
  - Criar usuário: Authentication → Users → Add user → marcar **"Auto Confirm User"**.
- **Tabela `acessos` (Supabase)** = o que cada um VÊ (qual empresa).
  - Quem **não** está na tabela → vê **todas** as empresas.
  - Quem está → vê só as empresas listadas (uma linha por empresa). Use `Todas` para acesso total.
  - O e-mail no Authentication precisa ser **igual** ao da tabela `acessos`.

---

## 🧱 Estrutura técnica (resumo)
- **App de cartões:** um único arquivo `index.html` (HTML + CSS + JavaScript). Sem framework.
- **Banco (Supabase):** tabelas `lancamentos`, `config`, `acessos` + Storage `comprovantes` (anexos).
- **Logo:** embutida no próprio HTML (base64).

---

## 🆘 Se precisar de ajuda
- Para mudanças no app ou na Central Contábil, descreva o que quer para o Claude.
- Guarde este guia — ele fica em https://github.com/AgathaVasco/acelera-cartoes (arquivo `GUIA-DO-PROJETO.md`).
