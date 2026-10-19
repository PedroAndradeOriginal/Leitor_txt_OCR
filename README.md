HC4 · Leitor de Textos

https://pedroandradeoriginal.github.io/Leitor_txt_OCR/

Aplicação web para transformar prints e fotos em texto editável usando OCR. Cole uma imagem, confira o resultado e copie o texto ou baixe um arquivo `.txt`.

O reconhecimento é executado no navegador, sem necessidade de instalar um servidor de aplicação ou configurar uma chave de API.

## Recursos

- Colagem de imagens com **Ctrl + V**.
- Entrada por arrastar e soltar ou seleção de arquivo.
- Reconhecimento automático ao adicionar a imagem.
- Suporte a PNG, JPG e WEBP de até **20 MB** por imagem.
- Idiomas: português e inglês combinados, português, inglês ou espanhol.
- Prévia da imagem ao lado do texto reconhecido.
- Texto editável, com contador de caracteres.
- Cópia para a área de transferência e download em TXT com codificação UTF-8.
- Botão **Limpar** para remover imagem, texto, nome do arquivo e resultado salvo.
- Restauração do último texto neste navegador.
- Temas claro e escuro, com preferência persistida.
- Diálogo de privacidade e identidade visual HC4.
- Layout ajustado à altura da janela, com rolagem interna para textos longos.

## Como usar

1. Abra a aplicação.
2. Se necessário, escolha o idioma do texto **antes** de enviar a imagem.
3. Faça um recorte da tela. No Windows, use **Win + Shift + S**.
4. Clique na caixa de entrada à esquerda e pressione **Ctrl + V**.
5. Aguarde o reconhecimento automático.
6. Confira o print e revise o texto à direita.
7. Use **Copiar texto** ou **Baixar TXT** para aproveitar o resultado.

Também é possível arrastar uma imagem para a caixa ou clicar em **Selecionar imagem salva**.

Cada leitura bem-sucedida substitui o texto anterior. Se a leitura falhar, o texto anterior é mantido. A aplicação processa uma imagem por vez.

### Limpar a leitura

O botão **Limpar** volta a operação ao estado inicial: remove o print, o texto, o nome do arquivo, o progresso e o resultado salvo no navegador. O idioma retorna a **Português + inglês**. A preferência de tema é preservada.

## Executar localmente

Baixe ou clone o repositório e mantenha a estrutura dos arquivos.

Para um uso rápido, abra `index.html` no Chrome ou Edge. Caso o navegador restrinja o OCR ou a área de transferência ao abrir arquivos locais, execute a aplicação por HTTP local.

Com Python 3 instalado, abra um terminal na pasta que contém `index.html` e execute:

```bash
python -m http.server 8000 --bind 127.0.0.1
```

Depois, acesse [http://127.0.0.1:8000](http://127.0.0.1:8000).

Não há etapa de compilação nem instalação de dependências por npm. É necessário acesso à internet para carregar o mecanismo de OCR e os arquivos de idioma, especialmente no primeiro uso.

## Publicar no GitHub Pages

1. Envie os arquivos da aplicação para um repositório, com `index.html` na raiz.
2. No GitHub, abra **Settings → Pages**.
3. Em **Build and deployment**, selecione **Deploy from a branch**.
4. Escolha a branch desejada e a pasta **`/ (root)`**.
5. Salve e aguarde a publicação.

A aplicação é estática e pode ser hospedada em um serviço que sirva HTML, CSS, JavaScript e os arquivos da pasta `assets`. Prefira HTTPS para compatibilidade com as funções de área de transferência.

## Estrutura do projeto

```text
.
├── index.html                   # Interface e diálogo de privacidade
├── styles.css                   # Layout, identidade HC4 e temas
├── app.js                       # Entrada de imagens, OCR, edição e exportação
├── theme.js                     # Alternância de tema e diálogo de privacidade
├── assets/
│   ├── logo-hc4.png              # Logo original
│   └── logo-hc4-round.svg        # Logo circular e favicon
└── README.md
```

## Tecnologias

- HTML, CSS e JavaScript.
- [Tesseract.js](https://github.com/naptha/tesseract.js), versão 5.1.1, para reconhecimento de texto no navegador.
- Canvas API para preparar a imagem.
- Clipboard API para copiar o texto.
- Blob API para gerar o arquivo TXT.
- `localStorage` para persistir o último texto, o idioma e a preferência de tema.

O script do Tesseract.js é carregado pelo jsDelivr. O mecanismo também baixa os recursos necessários para o reconhecimento.

## Privacidade e armazenamento

- **A imagem é processada no navegador** e não é enviada a um servidor para reconhecimento.
- A aplicação faz requisições de rede para carregar o OCR e os arquivos de idioma. Portanto, não é uma aplicação totalmente offline.
- O último texto e o idioma são armazenados no `localStorage` deste navegador e dispositivo. Não há sincronização entre dispositivos.
- A aplicação não persiste a imagem no `localStorage`; após recarregar a página, o texto pode ser restaurado, mas a prévia precisa ser enviada novamente.
- **Limpar** remove o resultado salvo pela aplicação. Isso não apaga cópias já feitas na área de transferência ou arquivos TXT já baixados.
- A escolha de tema é armazenada separadamente e permanece após a limpeza.
- O código da aplicação não inclui cadastro, autenticação, analytics ou banco de dados remoto.

## Limitações e dicas de leitura

O OCR pode trocar caracteres, perder trechos ou alterar a ordem de leitura em imagens com várias colunas, tabelas, fundos complexos ou baixa resolução. Revise o resultado antes de utilizá-lo.

Para melhorar a extração:

- Recorte somente o conteúdo que deseja reconhecer.
- Prefira imagens nítidas, com letras maiores e bom contraste.
- Evite fotos inclinadas, sombras, reflexos e compressão excessiva.
- Selecione o idioma adequado antes de enviar a imagem.
- Para documentos com várias colunas, teste um recorte de cada coluna separadamente.

Este leitor produz **texto livre**. Ele não reconstrói tabelas em planilhas nem preserva a diagramação original do documento.

### A cópia automática não funcionou?

O navegador pode restringir o acesso à área de transferência. Quando a cópia automática falha, a aplicação seleciona o texto para que você possa pressionar **Ctrl + C**. Também é possível usar **Baixar TXT**.

### O OCR não carregou?

Verifique a conexão com a internet e se a rede permite o carregamento dos recursos externos. O primeiro reconhecimento pode demorar mais devido ao download do mecanismo e dos idiomas.

## Autoria

Desenvolvido por **Pedro Andrade**, com identidade visual **HC4**.
