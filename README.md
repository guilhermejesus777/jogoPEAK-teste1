# PICO — protótipo 3D de escalada

![preview](preview.jpg)

Um jogo de escalada em 3D feito em **um único arquivo HTML** com [Three.js](https://threejs.org/),
inspirado em **PEAK** (Aggro Crab & Landfall): uma ilha, uma montanha, um cume — e uma
**stamina** que não deixa você errar.

> Projeto de fã, feito do zero. Não é afiliado nem oficialmente ligado a PEAK.

## Jogar online

**https://guilhermejesus777.github.io/jogoPEAK-teste1/**

## Como jogar

```bash
# qualquer servidor estático serve, por exemplo:
npx serve .
# ou
python -m http.server 8123
```

Depois abra `http://localhost:8123` no navegador.

Também dá para abrir o `index.html` direto — precisa de internet só para carregar o Three.js do CDN.

## Controles

| Tecla | Ação |
| --- | --- |
| `WASD` | andar |
| `SHIFT` | segurar / escalar (perto de uma parede) |
| `ESPAÇO` | pular / saltar da parede |
| `1` | usar energético (+stamina) |
| `2` | usar bandagem (cura lesão) |
| `MOUSE` | olhar (pointer lock ou arrastando com o botão esquerdo) |
| `Q` `E` | girar a câmera |
| `RODA` | zoom |
| `R` | voltar ao último acampamento |
| `ESC` | pausar |

> Se o mouse não girar a câmera (alguns navegadores/iframes bloqueiam o *pointer lock*),
> **arraste com o botão esquerdo** que funciona igual.

## O que tem no jogo

- **Uma montanha só**, numa ilha, com biomas por altitude: praia, mata, rocha e neve no cume.
- **Expedição cooperativa**: você e mais 3 alpinistas (BIA, TOCO e LILA), cada um com roupa e
  mochila próprias, que escalam junto, comentam o caminho e aparecem no HUD de conversa.
- **Itens pelo caminho**: **energéticos** (tecla `1`, recuperam stamina) e **bandagens**
  (tecla `2`, curam perna quebrada). Os itens brilham no cenário.
- **Zonas por altitude** com aviso na tela: praia → mata → rocha → neve → cume.
- **Frio**: acima da linha da neve a stamina regenera devagar e drena mais rápido.
  Fogueiras aquecem e curam a lesão.
- **Lesão**: queda feia quebra a perna — você anda e escala mais devagar até usar bandagem.
- **Neve** em partículas e **clima** que mudam conforme a altitude.
- **Personagem estilo escoteiro do PEAK**: cabeça redonda, óculos, gorro, jaqueta e mochila com
  saco de dormir e bandeirinha.
- **Escalada**: segure `SHIFT` numa parede, suba/desça/lateralize pela superfície.
  Quanto mais íngreme, mais devagar (e mais stamina).
- **Stamina**: cai escalando, regenera em platôs — planeje as paradas.
- **Acampamentos**: 3 fogueiras no caminho viram checkpoint, enchem a stamina e curam.
- **Tela de vitória** com tempo, altitude, itens usados e quedas.
- Água com ondas, ilhas ao fundo, árvores, nuvens e pássaros.

## Como funciona (por baixo)

- **Terreno procedural:** heightmap analítico (cone + ruído + terraços + praia),
  malha low-poly com cores por vértice.
- **Física:** colisão por amostragem de altura, limite de degrau (não sobe paredão andando)
  e escorregão em encostas íngremes.
- **Escalada:** o jogador gruda na superfície e anda no plano tangente; a âncora é mantida em
  `(x, z)` e a altura vem do heightmap, então a velocidade é corrigida pela inclinação.

## Próximos passos possíveis

- Multijogador (o coração de PEAK) com WebSocket
- Sistema de lesão / resgate
- Corda, pitons e equipamento
- Mais biomas e um cume com "endgame"

## Stack

- Three.js (via CDN, import map)
- HTML/CSS/JS puros — sem build, sem dependências locais
