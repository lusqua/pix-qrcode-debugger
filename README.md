# Validador de QR Code Pix

Este projeto consiste em uma página HTML simples e estática que permite:
1. Inserir o conteúdo de um QR Code Pix (em formato EMV/TLV).
2.	Visualizar o QR Code gerado (usando a biblioteca QRCode.js).
3.	Fazer o parse dos campos (tags EMV) e validar o CRC16.
4.	Exibir as informações extraídas em uma tabela.
5.	Detectar e fazer requisição GET para um link (geralmente no subcampo 25 dentro de 26), exibindo o retorno separadamente.

## Estrutura do Projeto
- 	index.html: Página principal que contém todo o código necessário.
- 	HTML/CSS para a interface simples.
- 	JavaScript para:
- Cálculo do CRC16 (padrão EMV).
- Parse dos campos TLV (Tag-Length-Value).
- Geração do QR Code (usando qrcode.min.js).
- Realização de requisição GET (via fetch) caso seja encontrado um link no QR Code.

## Como Executar
1.	Faça o download ou clone este repositório.
2.	Abra o arquivo index.html em qualquer navegador moderno (Chrome, Firefox, Edge, Safari, etc.).
3.	Na área de texto, cole o conteúdo do QR Code Pix (a string EMV/TLV).
4.	Clique em “Validar QR Code”.
- O preview do QR Code será exibido no topo.
- As informações do QR Code (tags, valores, validação de CRC, etc.) serão exibidas em uma tabela.
- Se o QR Code contiver um link (geralmente em 26/25), a página fará uma requisição GET e mostrará a resposta no final.

## Observações
- O projeto utiliza a biblioteca QRCode.js para geração do QR Code visual.
- O CRC16 é calculado de acordo com o polinômio 0x1021, padrão EMV para QR Codes Pix.
- A requisição GET é feita com a função nativa fetch do navegador.
- Em alguns casos, se o payload do QR Code for muito grande, a biblioteca pode apresentar um erro de overflow. Para minimizar esse problema, utilizamos o nível de correção de erro L (baixo) ao gerar o QR Code.
- Se o link retornado pelo parse não tiver http:// ou https://, adicionamos automaticamente https://.

Exemplos de Uso
- Copiar e colar no campo de texto um payload Pix no formato EMV/TLV:

```
00020101021226850014br.gov.bcb.pix2563qrcodepix.bb.com.br/...
```

- Visualizar a imagem do QR Code gerada.
- Checar se o CRC (tag 63) é válido (campo isValid).
- Observar se existe um link em 26/25 e ver o resultado da requisição na seção “Resultado da Requisição”.

## Compatibilidade
- Navegadores modernos (Chrome, Firefox, Edge, Safari) que suportam:
- ECMAScript 6+.
- A API fetch.
- Não é necessário servidor ou backend — basta abrir o index.html localmente.

## Licença

Este projeto é fornecido sem licenciamento específico. Fique à vontade para utilizá-lo e modificá-lo conforme necessário.