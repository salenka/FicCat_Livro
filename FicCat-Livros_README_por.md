# FicCat - Gerador de Ficha Catalográfica para Livros

Autor: Sandra Alencar 
Organização: Universidade Estadual Paulista (UNESP)  
Licença do repositório: Creative Commons Atribuição (CC-BY)

## Descrição
Aplicação web estática que gera fichas catalográficas de publicação monográfica a partir de um formulário. Permite pré-visualizar a ficha, ajustar fonte/tamanho, exportar como imagem PNG e gerar uma pré-visualização A4/PDF com opções de licença e créditos.

## Principais funcionalidades
- Formulário com seções: suporte, título e subtítulo, edição, responsável intelectual (pessoa/entidade/evento), contribuidores, publicação, descrição física, série, notas, ISBN e códigos de catalogação.
- Regras de formatação aplicadas automaticamente (autor/entidade/evento; múltiplos responsáveis; formatação de série e notas).
- Exportação:
  - PNG via `html2canvas`
  - Pré-visualização A4/PDF via `html2pdf.js`
- Editor de créditos com `Quill`.
- Persistência temporária no browser via `localStorage` para transferir dados entre `index.html` e `a4.html` e salvar preferências (fonte/tamanho).

## Estrutura principal do repositório
- `index.html` — formulário principal e visualização da ficha.
- `formScript.js` — lógica de interação do formulário, validações e gatilhos (botões).
- `cardScript.js` — montagem/formatacao da ficha (`getFicha()`, `getCodigos()`, `getServico()`, `getBibliotecario()`).
- `functions.js` — utilitários e funções de exportação (`geraFicha()`, `geraPNG()`).
- `a4.html` — página de pré-visualização A4/PDF.
- `a4.js` — carrega dados do `localStorage` e aciona `html2pdf`.
- `style.css` — estilos.
- `IMG/` — ícones (ex.: imagens de licenças).

## Como executar localmente
Recomendado servir os arquivos via servidor HTTP local (para evitar problemas com módulos ES e CORS).

Usando Python 3:
```bash
python3 -m http.server 8000
```
Node (http-server):

```
npx http-server -p 8000
```
Abrir: 

http://localhost:8000 ou http://localhost:8080

Também é possível abrir index.html diretamente, mas o comportamento com módulos ES pode variar entre navegadores.

# Uso rápido
- Abrir index.html.
- Preencher o formulário.
- Clicar em Gerar Ficha Catalográfica para visualizar.
- Ajustar fonte/tamanho se necessário.
- Clicar em Baixar imagem para PNG ou Pré-visualizar PDF para abrir a4.html e gerar/baixar o PDF.

# Regras de negócio importantes (resumo)
- Suporte: físico ou digital. Se digital, adiciona [recurso eletrônico] ao título e pede extensão do arquivo.
- Responsabilidade intelectual: pessoa (autor/organizador/coordenador/compilador/editor/anônima), entidade ou evento — cada tipo tem formatação específica.
- Múltiplos responsáveis/contribuidores: regras de formatação para 2, 3, ou 4+ ([et al.]).
- Comporta até duas editoras ou publicadoras.
- Comporta até duas notas, além da nota de ISBN.
- Códigos de catalogação (CDD, CDU, Cutter, PHA) aparecem apenas se selecionados e tornam o campo associado obrigatório.
- Serviço de catalogação e bibliotecário são exibidos com gênero (bibliotecária/bibliotecário) e CRB quando fornecidos.

# Limitações conhecidas
- Aplicação totalmente client-side (sem backend); dados não são sincronizados entre dispositivos.
- Validações são realizadas no cliente; ainda pode exigir revisão bibliográfica manual para conformidade estrita.
- Geração de PDF depende de html2pdf.js e pode variar visualmente entre navegadores.

# Licença
Este repositório está licenciado sob CC-BY (Creative Commons Atribuição). Ao usar/redistribuir, por favor atribua crédito a Sandra Alencar / Universidade Estadual Paulista (UNESP).
#Contato / Maintainer
salenka@gmail.com
#Recursos adicionais
Bibliotecas usadas: Quill, html2pdf.js, html2canvas, Bootstrap 4.