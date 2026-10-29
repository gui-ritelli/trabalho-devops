# Trabalho de DevOps — GitHub Actions e CHANGELOG Automático
ALUNOS: GUILHERME EDUARDO RITELLI DORTA (RA:250532)
        LIVIA ROMANO DE OLIVEIRA (RA:250446)

## 1. Sobre o projeto

Este projeto foi desenvolvido para a disciplina de DevOps com o objetivo de demonstrar o uso do Git para controle de versão e do GitHub Actions para automatizar tarefas durante o desenvolvimento de software.

O projeto contém uma página HTML simples de gerenciamento de produtos e uma automação que gera um arquivo `CHANGELOG.md` com o histórico recente de alterações do repositório.

## 2. Objetivos

- Praticar o controle de versão utilizando Git.
- Registrar alterações por meio de commits.
- Hospedar o código-fonte no GitHub.
- Criar uma automação utilizando GitHub Actions.
- Gerar automaticamente um changelog com o histórico dos commits.

## 3. Tecnologias utilizadas

- **HTML5:** estrutura da página do projeto.
- **Git:** controle de versão e registro das alterações.
- **GitHub:** hospedagem do repositório.
- **GitHub Actions:** execução automática do workflow.
- **Markdown:** documentação do projeto e histórico de alterações.

## 4. Estrutura do projeto

```text
TrabalhoDevops/
├── .github/
│   └── workflows/
│       └── changelog.yml
├── CHANGELOG.md
├── README.md
└── index.html
```

## 5. Como funciona a GitHub Action

O workflow está definido no arquivo `.github/workflows/changelog.yml`.

A automação é executada quando ocorre um `push` na branch `main` e realiza as seguintes etapas:

1. Obtém o código e o histórico do repositório.
2. Consulta os últimos 10 commits.
3. Gera ou atualiza o arquivo `CHANGELOG.md`.
4. Registra a atualização do changelog em um novo commit.
5. Envia a atualização para o repositório remoto.

O arquivo `CHANGELOG.md` permite consultar as alterações recentes sem precisar analisar manualmente todo o histórico do Git.

## 6. Como executar o projeto

### Pré-requisitos

- Git instalado.
- Conta no GitHub.
- Navegador web.
- Visual Studio Code (opcional, mas recomendado).

### Clonar o repositório

```bash
git clone https://github.com/gui-ritelli/trabalho-devops.git
cd trabalho-devops
```



EXPLICANDO BLOCOS DO CHANGELOG.md

BLOCO 1: - name: Gerar CHANGELOG
          run: |
          echo "# Histórico de alterações" > CHANGELOG.md
          echo "" >> CHANGELOG.md
          git log -10 --pretty=format:"- %h - %s (%ad)" --date=short >> CHANGELOG.md

BLOCO 2:       - name: Salvar CHANGELOG
          run: |
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add CHANGELOG.md
          git commit -m "docs: atualizar changelog [skip ci]" || exit 0
          git push
EXPLICACÃO: RUN | - Indica que o GitHub Actions deve executar os comandos de terminal escritos nas linhas seguintes e o símbolo | permite colocar vários comandos em um único bloco. Depois é configurado o usuario e o email e essas configurações permitem que o Git crie um commit sem precisar perguntar quem é o autor.

