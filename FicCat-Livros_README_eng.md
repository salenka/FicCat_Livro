

```markdown
# FicCat - Book Cataloging Card Generator

Author: Sandra Alencar
Organization: São Paulo State University (UNESP)  
Repository license: Creative Commons Attribution (CC-BY)

## Description
Static web application that generates cataloging cards for monograph publication from a form. It supports previewing the result, adjusting font/size, exporting as PNG, and producing an A4/PDF preview including license and credits.

## Key features
- Form with sections: support (physical/digital), title and subtitle, edition, intellectual responsibility (person/entity/event), contributors, publication, physical description, series, notes, ISBN and cataloging codes.
- Automatic formatting rules (author/entity/event, multiple contributors, series/notes formatting).
- Export:
  - PNG via `html2canvas`
  - A4/PDF preview via `html2pdf.js`
- Credits editor using `Quill`.
- Temporary persistence in `localStorage` to transfer data between `index.html` and `a4.html` and save preferences.

## Repository structure (main files)
- `index.html` — main form and card preview.
- `formScript.js` — UI logic, validation and button handlers.
- `cardScript.js` — composes/formats the final card (`getFicha()`, `getCodigos()`, `getServico()`, `getBibliotecario()`).
- `functions.js` — utilities and export functions (`geraFicha()`, `geraPNG()`).
- `a4.html` — A4/PDF preview page.
- `a4.js` — loads data from `localStorage` and triggers `html2pdf`.
- `style.css` and `IMG/` (assets).

## Run locally
Serve files with a simple HTTP server to avoid module/CORS issues.

Python 3:
```bash
python3 -m http.server 8000
```
Node (http-server):

```
npx http-server -p 8000
```
Open: 

http://localhost:8000/index.html

# Quick usage
- Open index.html.
- Fill the form.
- Click Gerar Ficha Catalográfica to preview.
- Adjust font/size as needed.
- Click Baixar imagem for PNG or Pré-visualizar PDF to open a4.html and produce the PDF.
## Business rules summary
- Support: physical or digital. Digital adds [recurso eletrônico] to the title and requests file extension.
- Intellectual responsibility: person, entity, or event with specific formatting for each.
- Multiple contributors/responsibles: formatted differently for 2, 3, or 4+ (uses [et al.]).
- Cataloging codes (CDD, CDU, Cutter, PHA) appear only when selected and make corresponding inputs required.
- Cataloging service and librarian are displayed with gendered term (bibliotecária/bibliotecário) and CRB when provided.
# Known limitations
- Client-side only, no backend or remote persistence.
- Client-side validation—may require human review for strict bibliographic rules.
- PDF rendering may vary by browser.
# License
This repository is licensed under CC-BY. Please attribute Sandra Alencar / Universidade Estadual Paulista (UNESP) when reusing.
# Contact / Maintainer
salenka@gmail.com
