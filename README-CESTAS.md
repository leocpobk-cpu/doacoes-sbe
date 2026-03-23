# 🛒 Sistema de Doação de Cestas Básicas - SBE

Sistema simplificado e independente para registro e acompanhamento de doações de cestas básicas.

## 📋 Páginas Criadas

### 1. **cestas.html** - Página de Doação
- Interface simples e intuitiva para o público geral
- **Dados PIX exibidos**: Chave 65 98134-6852 | Favorecido: Ana Julia Magno Fonseca
- **Valores pré-definidos**: 4 opções de cestas com valores de referência
  - Cesta Básica 34 itens - Culinária em Casa 17kg - R$ 214,99
  - Cesta Básica 51 itens - Familiar Plus 39kg - R$ 394,99
  - Cesta Básica 46 itens - Familiar I 37kg - R$ 379,99
  - Cesta Básica 23 itens - Essencial Mega 12kg - R$ 114,99
  - Valor Livre (doador escolhe o valor)
- **Campo de valor editável**: Os valores pré-definidos são apenas referências
- **Totalização automática**: Calcula automaticamente Valor × Quantidade = Total
  - Exemplo: R$ 214,99 × 6 = R$ 1.289,94
- **Upload de comprovante**: Anexe comprovante de PIX (imagem ou PDF, máx 5MB)
- Campos obrigatórios: nome, tipo de cesta, valor e quantidade
- Campos opcionais: telefone, comprovante e observação
- Formatação automática de telefone
- Mensagem de sucesso após registro
- Incentivo a doações de qualquer valor
- Design responsivo para mobile

### 2. **relatorio-cestas.html** - Página de Relatório
- Visualização de todas as doações de cestas
- Filtros por mês e ano
- Estatísticas em tempo real:
  - Total de cestas doadas
  - Total de doadores
  - Cestas do mês atual
  - **Total arrecadado em valores**
- Lista detalhada com:
  - Número do recibo
  - Nome do doador
  - Quantidade de cestas
  - **Valor da doação (quando informado)**
  - Data/hora da doação
  - Telefone (se informado)
  - Observações (se houver)
  - **Ícone de anexo (📎)**: Clique para visualizar comprovante
  - **Botão para anexar/substituir comprovante**: Adicione comprovante posteriormente

## 🎨 Características do Design

- **Cor principal**: Laranja (#FF9800) - mantendo identidade SBE
- **Tema**: Gradientes suaves e amigáveis
- **Ícones**: Emojis para melhor visualização
- **Responsivo**: Funciona perfeitamente em celulares
- **Animações**: Transições suaves e feedback visual

## 🔗 Banco de Dados

Ambas as páginas usam a mesma tabela `doacoes_sbe` do Supabase:
- **Filtro**: `tipo_doacao = 'cesta_basica'`
- **Campos utilizados**:
  - `numero_recibo` (gerado automaticamente)
  - `doador_nome`
  - `tipo_doacao` (sempre 'cesta_basica')
  - `quantidade` (número de cestas)
  - `valor` (valor monetário da doação em R$)
  - `telefone` (opcional)
  - `observacao` (opcional)
  - `anexo_url` (URL do comprovante no Supabase Storage)
  - `anexo_nome` (nome original do arquivo anexado)
  - `ano` e `mes` (automáticos)

- **Storage**: Comprovantes armazenados no bucket `anexos-sbe` do Supabase
  - Caminho: `cestas/{id_doacao}/{timestamp}_{nome_arquivo}`
  - Formatos aceitos: Imagens (JPG, PNG, etc.) e PDF
  - Tamanho máximo: 5MB por arquivo

## 🚀 Como Usar

### Para Doadores:
1. Acesse `cestas.html`
2. Preencha seu nome
3. Veja os **dados PIX** no topo da página (Chave: 65 98134-6852 | Favorecido: Ana Julia Magno Fonseca)
4. Selecione o tipo de cesta (ou escolha "Valor Livre")
5. O valor será preenchido automaticamente (mas pode ser alterado)
6. Informe a quantidade de cestas
7. **Veja o total calculado automaticamente**: Ex: R$ 214,99 × 6 = R$ 1.289,94
8. Se fez PIX, **anexe o comprovante** (opcional mas recomendado)
9. Opcionalmente, adicione telefone e mensagem
10. Clique em "Registrar Doação"

**Importante**: Os valores pré-definidos são apenas referências baseadas em preços de mercado. Você pode doar qualquer valor! Toda contribuição é bem-vinda. 💚

### Para Visualizar:
1. Acesse `relatorio-cestas.html`
2. Use os filtros para ver doações específicas
3. Veja estatísticas gerais no topo da página
4. **Clique no ícone 📎** para visualizar comprovantes anexados
5. Use o **botão "📎 Anexar/Substituir Comprovante"** para adicionar comprovante posteriormente

### Para Visualizar:
1. Acesse `relatorio-cestas.html`
2. Use os filtros para ver doações específicas
3. Veja estatísticas gerais no topo da página

## 📱 Responsividade

- Desktop: Layout otimizado em até 1000px
- Tablet: Ajustes automáticos de grid
- Mobile: Layout de coluna única, botões full-width

## 🔄 Integração

Este sistema é **independente** do sistema principal de doações (`index.html` e `relatorio.html`), mas:
- Usa o mesmo banco de dados
- Compartilha a mesma infraestrutura Supabase
- Pode ser publicado no mesmo domínio GitHub Pages

## 📞 Suporte

Leonardo Oliveira - 65 98134-6852 (WhatsApp)

---

**Desenvolvido para SBE - Sociedade Beneficente Evangélica | IEAD Coophamil**
