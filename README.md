# Atividade — SSH, Flask e Contêineres

Atividade de **Redes de Computadores** (IFSP Jacareí) feita por **Pedro de Moraes Machado**.
Baseada no material do professor: https://github.com/tardellirs/aula-redes-ssh

O objetivo é colocar um jogo da cobrinha feito em **Flask** no ar, aprendendo **SSH**,
**deploy** e **contêineres (Docker)**.

## Como foi feito

Como não havia servidor na nuvem disponível, o servidor foi **simulado** com um contêiner
Docker (Ubuntu 24.04 com `sshd`), acessado por `ssh -p 2222 root@localhost`. O conteúdo
das três partes é o mesmo da atividade original.

1. **Parte 1 — SSH:** conexão, comandos básicos do Linux e chave `ed25519`.
2. **Parte 2 — Flask:** clonar o projeto, rodar nas portas 5000 e 80 e ver o site cair ao fechar o SSH.
3. **Parte 3 — Docker:** `docker build` e `docker run -d --restart unless-stopped`, mantendo o site no ar.

## Estrutura

```
.
├── app/                    # Flask + Dockerfile + jogo da cobrinha
├── prints/                 # prints de cada entrega
└── FOLHA-DE-ENTREGA.md     # respostas e prints das 16 entregas
```

## Rodar o site localmente

```bash
cd app
docker build -t cobrinha .
docker run -d --name cobrinha --restart unless-stopped -p 8080:5000 cobrinha
```

Acesse `http://localhost:8080`.
