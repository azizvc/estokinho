# Estokinho

Plugin do [Estokinho](https://estokinho.com.br) para o Cursor e para o Grok Bot. Os dois instalam o mesmo pacote pelo [Cursor Marketplace](https://cursor.com/marketplace).

O agente consulta e atualiza a conta de quem autorizar: estoque, vendas, clientes, fiado, despesas, orçamentos e NFC-e. O servidor MCP fica em `https://mcp.estokinho.com.br/mcp`. Não há token, senha nem segredo neste repositório. No primeiro uso, o cliente abre o navegador, a pessoa entra com a conta Estokinho e confirma **Permitir**.

## O que a conexão pode alterar

Depois da autorização, as tools gravam na conta real: produtos, estoque, vendas, clientes, despesas e NFC-e. Excluir, cancelar venda, perdoar fiado e emitir ou cancelar nota exigem confirmação da pessoa. Tools de proprietário e de administrador da plataforma seguem o mesmo papel da conta no site.

Termos: https://estokinho.com.br/termos  
Privacidade: https://estokinho.com.br/privacidade

## Como testar

1. Instale o plugin no Cursor (Customize) ou no Grok Bot.
2. Peça: "quem sou eu no Estokinho?"
3. Conclua o login no navegador se ele abrir.
4. Peça: "quais produtos estão abaixo do estoque mínimo?"

A resposta tem de vir das tools `estokinho_auth_eu` e `estokinho_produtos_estoque_minimo`. Se o conector estiver desconectado, o agente deve dizer que não consultou a conta.

## Reviewers

Remote MCP with OAuth (PKCE). Metadata: `https://mcp.estokinho.com.br/.well-known/oauth-protected-resource`. No user secrets are stored in this repo. The hosted server enforces the Estokinho account session.
