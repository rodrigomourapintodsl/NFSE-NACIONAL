# Impressão NFS-e Nacional HTML

Este projeto é um template HTML/JS para a renderização do Documento Auxiliar da Nota Fiscal de Serviço Eletrônica (DANFSe) no Padrão Nacional, conforme a documentação oficial.

## Como Usar

Para renderizar a sua própria nota, basta editar o arquivo `Impressão Template.html` e injetar os seguintes campos com os dados desejados (status e o conteúdo do XML da nota retornado pela prefeitura/Sefin):

```javascript
var STAUTS_NFSE = ''; // STAUTS_NFSE (Ex: 'CANCELADA', 'SUBSTITUÍDA')
const xmlString = ''  // XML de retorno da NFS-e
```

Ao abrir o arquivo `Impressão Template.html` no navegador, ele utilizará as regras de layout e fará o parse do XML inserido para preencher os dados visuais.

## Fontes Oficiais

O mapeamento e as regras de renderização foram baseados nas seguintes documentações técnicas oficiais:

- **Nota Técnica (Layout DANFSe):** [nt-008-se-cgnfse-danfse-20260505.pdf](https://www.gov.br/nfse/pt-br/biblioteca/documentacao-tecnica/rtc/nt-008-se-cgnfse-danfse-20260505.pdf)
- **Estrutural do XML e Leiaute:** [anexo_i-sefin_adn-dps_nfse-snnfse-v1-01-20260209.xlsx](https://www.gov.br/nfse/pt-br/biblioteca/documentacao-tecnica/documentacao-atual/anexo_i-sefin_adn-dps_nfse-snnfse-v1-01-20260209.xlsx)

## Limitações e Melhorias Futuras (TODO)

Atualmente o script faz a varredura da maioria dos blocos essenciais, porém **falta melhorar e mapear** os seguintes itens relativos a tomadores do exterior e Comércio Exterior:

* **`cNaoNIF`**: Número de Identificação Fiscal do Tomador no Exterior.
* **`comExt`**: Grupo de informações de Exportação/Comércio Exterior. Um bloco de exemplo a ser mapeado em futuras iterações é:

```xml
<comExt>
  <mdPrestacao>2</mdPrestacao>
  <vincPrest>0</vincPrest>
  <tpMoeda>790</tpMoeda>
  <vServMoeda>1023.46</vServMoeda>
  <mecAFComexP>01</mecAFComexP>
  <mecAFComexT>01</mecAFComexT>
  <movTempBens>1</movTempBens>
  <mdic>0</mdic>
</comExt>
```
