# PICO — protótipo 3D de escalada

![preview](preview.jpg)

Um jogo de escalada em 3D feito em **um único arquivo HTML** com [Three.js](https://threejs.org/).
Inspirado na mecânica de **PEAK** (Aggro Crab & Landfall): você precisa subir uma montanha
controlado a **stamina**, escalando paredes íngremes e descansando nos platôs.

> Projeto de fã, feito do zero. Não é afiliado nem oficialmente ligado a PEAK.

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
| `SHIFT` | segurar/escalar (perto de uma parede) |
| `ESPAÇO` | pular / saltar da parede |
| `MOUSE` | olhar |
| `R` | voltar ao início |
| `ESC` | pausar |

## Como funciona

- **Terreno procedural:** a montanha é um heightmap analítico (cone + ruído + terraços),
  gerado no carregamento com cores por vértice e visual low-poly.
- **Física:** colisão por amostragem de altura, com limite de degrau (você não sobe paredão andando)
  e escorregão em encostas muito íngremes.
- **Escalada:** segurando `SHIFT` perto de uma superfície inclinada o personagem gruda na parede
  e se move no plano tangente. A stamina cai mais rápido ao subir.
- **Stamina:** gasta escalando, regenera em chão plano — planeje as paradas nos platôs.
- **Objetivo:** chegar na bandeira no cume antes que a stamina (e a paciência) acabem.

## Possíveis próximos passos

- Multijogador (o coração de PEAK) com WebSocket
- Sistema de lesões / resgate no meio da montanha
- Biomas diferentes conforme a altitude
- Sons de vento, passos e escalada
- Checkpoints (acampamentos) no caminho

## Stack

- Three.js (via CDN, import map)
- HTML/CSS/JS puros — sem build, sem dependências locais
