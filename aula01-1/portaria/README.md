# Portaria Smart Canteiro

Página didática do curso **Fundamentos de IA e Análise de Dados** (SENAI "Orlando Laviero Ferraiuolo").
Ela pega o modelo que o aluno treinou no **Teachable Machine** e o transforma em uma "portaria" que funciona fora do site:
liga a webcam (ou recebe uma imagem), mostra **LIBERADO**, **BLOQUEADO** ou **CHAMAR PORTEIRO** e registra cada decisão.

> Protótipo para sala de aula. Não use como controle de acesso real.

---

## Como usar (aluno)

1. No Teachable Machine, com o modelo treinado: **Exportar modelo** › aba **Tensorflow.js** › deixe marcado **Carregar (link partilhável)** › clique em **Carregar o meu modelo** (Upload my model).
2. Espere: enquanto o link mostra `.../models/[...]`, o modelo **ainda não foi enviado**. Quando o `[...]` virar um código (`https://teachablemachine.withgoogle.com/models/AbC12xYz9/`), copie o link.
3. Abra a página, cole o link e clique em **Carregar modelo**.
4. Escolha **Webcam** ou **Imagem do computador** (ex.: a pasta `teste` do Smart Canteiro).
5. Ajuste a **regra do humano**: abaixo dessa certeza, a página mostra **CHAMAR PORTEIRO**.

Dica: dá para abrir a página já com o modelo carregado: `.../index.html?modelo=LINK_DO_MODELO`.

### Nomes das classes

A página reconhece os nomes e pinta a decisão:

| Nome da classe (contém) | Decisão |
|---|---|
| liberado, autorizado, aprovado, OK | 🟢 LIBERADO |
| bloqueado, negado, defeito, sem EPI | 🔴 BLOQUEADO |
| ninguém, vazio, fundo | ⚪ AGUARDANDO |
| qualquer outro nome | mostra o próprio nome |

Por isso ela funciona também com o modelo de peças da Aula 01 (**OK** / **Defeito**).

## Como publicar no GitHub Pages (professor)

1. No repositório: **Add file** › **Upload files** › envie `index.html` e este `README.md` › **Commit**.
2. **Settings** › **Pages** › Source: **Deploy from a branch** › Branch: **main** e pasta **/ (root)** › **Save**.
3. Em 1 a 2 minutos o link aparece no topo da mesma tela (`https://SEU-USUARIO.github.io/NOME-DO-REPO/`).

A webcam só funciona em endereço **https** (o GitHub Pages já é) ou em `localhost`.

---

## Resumo para a turma

### O caminho de um projeto de IA de imagem
**Coletar imagens › separar em classes › treinar › testar com imagens novas › definir a regra do humano › colocar para funcionar.**
É o mesmo caminho das ferramentas profissionais (Google Vertex AI, Azure Custom Vision, Edge Impulse). Só muda o tamanho.

### Onde aplicar
| Onde | Ideia | Projeto no Teachable Machine |
|---|---|---|
| Portaria de obra ou fábrica | Conferir EPI antes de entrar | Imagem |
| Linha de produção | Peça boa × peça com defeito | Imagem |
| Almoxarifado | Reconhecer ferramenta ou material pela foto | Imagem |
| Reciclagem | Separar plástico, papel e metal | Imagem |
| Manutenção | Avisar quando o som da máquina muda | Áudio |
| Ergonomia | Alertar postura errada ao levantar peso | Postura |

### Como levar o modelo para fora do site
- **Página web (TensorFlow.js):** link do modelo + código, como esta página.
- **Raspberry Pi ou celular (TensorFlow Lite):** roda sem internet, num computador pequeno com câmera.
- **Arduino (modelo embarcado):** liga a resposta da IA a um LED, alarme ou cancela.

### Cuidados
- **Dados:** poucos exemplos, luz diferente ou só um tipo de pessoa/peça = IA que erra no mundo real.
- **Teste:** sempre com imagens que a IA **nunca viu**, no local, na luz e no ângulo de verdade.
- **Humano na decisão:** abaixo de uma certeza combinada, quem decide é uma pessoa.
- **LGPD:** imagem de pessoa é dado pessoal e rosto é dado biométrico (dado sensível). Precisa de finalidade clara, aviso e cuidado com o armazenamento.
- **Viés:** se a IA viu pouco de algum grupo, ela erra mais com ele. É uma das críticas feitas ao Smart Sampa.
- **Protótipo não é produto:** o Teachable Machine serve para provar a ideia. Um sistema real precisa de muito mais dados, testes e responsáveis.
