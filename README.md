# Finance Mail Hub · Cabana

Hub de triagem unificada para as 4 caixas departamentais financeiras da Cabana Burger.

## Arquivo único

- `finance_mail_hub.html` — abrir no navegador (Chrome/Edge recomendados)

## Login

- Usuário: `cabana`
- Senha: `cabana@2026`

## Caixas suportadas

- Fiscal (`fiscal@cabana.com.br`)
- Recebimento Fiscal (`recebimento@cabana.com.br`)
- Contas a Pagar (`contas@cabana.com.br`)
- Financeiro (`financeiro@cabana.com.br`)

## Configuração inicial

Após o primeiro login, o app abre o modal de Configurações pedindo 3 webhooks do Power Automate:

1. **Webhook de busca (GET)** — retorna emails das 4 caixas
2. **Webhook marcar lido (POST)** — sincroniza isRead com Outlook
3. **Webhook anexo (POST)** — busca conteúdo de anexos sob demanda

Os fluxos do Power Automate estão documentados separadamente.

## Funcionalidades

- Visão unificada das 4 caixas com filtros por caixa e status
- Detecção de duplicados via internetMessageId + fallback heurístico
- Marcar lido sincroniza com Outlook em todas as caixas onde o email duplicado existe
- Anexos baixados sob demanda; preview inline de PDF, imagens, XML, texto
- Compositor com formatação rica (Responder, Responder a todos, Encaminhar)
- Anexos do computador via upload ou drag-and-drop no editor
- Categorização local (Crítico, Sócios/Diretores, Em Andamento, Responder, Fornecedores, Ciência)

## Hospedagem

Por ser arquivo único, pode rodar de várias formas:

- **GitHub Pages** (recomendado) — mesma estratégia do MailCommand
- **Netlify** — drag-and-drop do arquivo
- **Local** — abrir o HTML direto no navegador

## Storage

Todos os dados ficam no localStorage do navegador:

- `cabana_mail_hub_v3` — categorizações e status
- `cabana_mail_hub_cfg_v3` — URLs dos webhooks
- `cabana_mail_hub_cache_v3` — cache de emails

Limpar cache do navegador apaga essas configurações.

## Notas técnicas

- Single-page application em vanilla JS
- Sem dependências externas além de fontes Google
- Compatível com navegadores modernos (Chrome, Edge, Firefox, Safari)
- Mobile responsivo limitado (uso recomendado em desktop)
