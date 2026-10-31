# Aleória RPG Tools — extensão para Owlbear Rodeo

Painel em português para fichas, recursos, iniciativa, rolagens e condições do sistema Aleória. Interface dark fantasy.

## O que já funciona
- Cadastro/edição/exclusão de fichas com seis atributos e modificadores.
- Controle manual de PV e PE atuais/máximos.
- CA estimada conforme a fórmula do livro: `10 + metade do mod. RES (arredondada para baixo) + armadura + maior entre proficiência na armadura e Reflexos + escudo`, com ajustes de Exposto/Protegido.
- Deslocamento e carga calculados com os valores editáveis da ficha.
- Ordem de iniciativa, avanço de turno e contador de rodadas.
- Dados d4, d6, d8, d10, d12, d20 e expressões como `2d8+3`.
- Teste de atributo/perícia com modificador do atributo e bônus de perícia.
- Rolagem de ataque (1d20 + atributo + proficiência) e dano por peso da arma (leve 1d6, média 1d8, pesada 1d12).
- Catálogo de condições transcrito/resumido do livro, com intensidade, duração anotável e remoção.
- Registro de rolagens e ações.
- Sincronização dos dados da campanha entre participantes usando o metadata da cena do Owlbear Rodeo; fora de uma sala, usa armazenamento local.

## Requisitos
- Node.js 18 ou superior (recomendado 20+).
- Uma conta/sala do Owlbear Rodeo.

## Rodar localmente
```bash
npm install
npm run dev
```
O Vite exibirá um endereço local, normalmente `http://localhost:5173/`.

## Instalar para testar no Owlbear
1. Mantenha `npm run dev` em execução.
2. No Owlbear Rodeo, abra o perfil e escolha **Add Extension / Adicionar extensão**.
3. Cole `http://localhost:5173/manifest.json` como URL do manifesto.
4. Crie/abra uma sala e habilite a extensão.
5. Clique no ícone Aleória RPG Tools no topo da sala.

O endereço localhost só funciona para testar no mesmo computador. Para jogar com outras pessoas, publique o conteúdo de `dist/` em um host estático HTTPS.

## Gerar versão de produção
```bash
npm run build
```
A pasta `dist/` conterá `index.html`, `manifest.json`, `icon.svg` e os arquivos compilados. Publique o conteúdo de `dist/` na raiz de um site HTTPS. Depois, em **Add Extension**, use `https://SEU-DOMINIO/manifest.json`.

Hospedagem não está incluída neste ZIP: a extensão está pronta como projeto e precisa ser publicada num endereço HTTPS para seus jogadores instalarem.

## Notas de regras e limites
- A fórmula de CA implementada segue o texto do livro, mas os campos de proficiência/Reflexos e bônus de escudo são editáveis porque o livro apresenta esses componentes em seções distintas.
- PV/PE máximos ficam editáveis. O cálculo integral exige os dados-base da raça e classe e as rolagens/valores escolhidos em cada nível; o painel não inventa esses valores.
- A iniciativa padrão rola `1d20 + mod. DES + bônus de Reflexos` (campo Reflexos na ficha).
- A extensão não automatiza duração ou escalada de condições: o livro deixa parte desses encerramentos dependentes da fonte e da decisão do Mestre.
- A sincronização é por metadados da cena atual. Trocar de cena pode significar um conjunto de dados diferente.

## Estrutura
- `public/manifest.json` — manifesto do Owlbear Rodeo.
- `src/main.js` — lógica da aplicação e integração SDK.
- `src/style.css` — interface responsiva dark fantasy.


## Publicar sem instalar programas (GitHub Pages)

Este projeto já está preparado para o repositório GitHub chamado `aleoria-rpg-tools`. Envie os arquivos do projeto para a branch `main` de um repositório público com esse nome. O workflow em `.github/workflows/deploy.yml` compila e publica a extensão automaticamente. Em seguida, no repositório, abra **Settings → Pages** e confirme que a publicação usa **GitHub Actions**. Aguarde a execução em **Actions** terminar com sucesso.

O link do manifesto terá este formato: `https://SEU-USUARIO.github.io/aleoria-rpg-tools/manifest.json`. Troque `SEU-USUARIO` pelo seu nome de usuário do GitHub e adicione esse link no Owlbear Rodeo em **Extensions → Add Extension**.
