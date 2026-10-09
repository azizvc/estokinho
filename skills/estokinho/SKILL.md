---
name: estokinho
description: Opera a conta Estokinho (estoque, vendas, clientes, fiado, despesas, orçamentos e NFC-e) pelas tools do conector estokinho. Use quando a pessoa pedir para consultar ou alterar o estoque, o caixa, os clientes ou as notas da loja.
---

# Estokinho

O conector fala com a conta de quem autorizou o plugin. Não invente quantidade, preço, cliente nem número de nota. Se a tool falhar ou não estiver autorizada, diga isso e pare.

## Antes de alterar qualquer coisa

1. Chame `estokinho_auth_eu` para saber quem está logado, o papel (`owner` ou `collaborator`) e se é administrador da plataforma.
2. Se a loja não estiver clara e houver mais de uma, chame `estokinho_lojas_listar` e pergunte qual usar.
3. Leia o registro atual (`estokinho_produtos_obter`, `estokinho_vendas_listar`, `estokinho_clientes_obter`) antes de atualizar.

Valores de dinheiro estão em reais. Datas seguem o que a tool pedir. Não recalcule estoque, plano ou permissão por conta própria: a API já faz isso.

## O que cada grupo faz

- Conta e painel: `estokinho_saude`, `estokinho_auth_eu`, `estokinho_painel`, `estokinho_empresa_obter`, `estokinho_empresa_atualizar`
- Produtos e estoque: `estokinho_produtos_listar`, `estokinho_produtos_por_codigo`, `estokinho_produtos_estoque_minimo`, `estokinho_estoque_posicao`, `estokinho_estoque_movimentar`, `estokinho_movimentacoes_listar`
- Vendas, pedidos e orçamentos: `estokinho_vendas_listar`, `estokinho_vendas_criar`, `estokinho_vendas_finalizar`, `estokinho_pedidos_criar`, `estokinho_orcamentos_listar`, `estokinho_orcamentos_converter`
- Clientes e fiado: `estokinho_clientes_listar`, `estokinho_fiado_resumo`, `estokinho_fiado_receber`
- Despesas e relatórios: `estokinho_despesas_listar`, `estokinho_relatorio`
- NFC-e: `estokinho_nfce_consultar`, `estokinho_nfce_emitir`, `estokinho_nfce_danfe`

Tools `estokinho_usuarios_convidar`, `estokinho_usuarios_ativar` e `estokinho_convite_revogar` exigem proprietário. Tools `estokinho_admin_*` só funcionam para o e-mail administrador da plataforma; nos demais casos a API responde 403.

## Confirme antes de gravar

Mostre um resumo curto e espere um sim explícito antes de:

- criar, alterar, arquivar ou excluir produto, serviço, categoria, cliente, loja ou despesa
- movimentar estoque, criar ou finalizar venda, cancelar ou excluir venda
- receber ou perdoar fiado
- emitir ou cancelar NFC-e
- convidar, ativar ou revogar colaborador
- mudar plano, blog, ajuda ou suporte com tools `estokinho_admin_*`

Consulta, listagem e `estokinho_saude` não precisam dessa confirmação.

## Se o conector não responder

401 pede autorização de novo no navegador. 403 é falta de permissão, não um erro para contornar. 503 significa que a API está fora; não afirme que a alteração foi salva.
