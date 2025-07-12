---
title: Guia Definitivo Criando um Blog com Hugo, GitHub Pages e Submodules
tags: hugo github tutorial linux git  submodule site-estatico 
creation_date: 2025-07-12 
source: https://youtu.be/LIFvgrRxdt4?si=xrPCxpXPiRashUd5
---

# Guia Definitivo: Criando um Blog com Hugo, GitHub Pages e Submodules

Este guia completo e consolidado ensina a criar, manter e publicar um blog de alta performance, utilizando o gerador de site estático **Hugo** e a hospedagem gratuita do **GitHub Pages**. O método utiliza **Git Submodules** para criar um fluxo de trabalho limpo e profissional, separando o código-fonte do site publicado.

**Vídeo de Referência:** [Assista](https://youtu.be/LIFvgrRxdt4?si=xrPCxpXPiRashUd5 "null") ao tutorial em vídeo aqui

## 1. Pré-requisitos e Ferramentas

Antes de começar, certifique-se de que você tem as seguintes ferramentas instaladas e configuradas:

- ✅ **Uma conta no GitHub**: Essencial para hospedar o código e o site.
    
- ✅ **Git**: O sistema de controle de versão que gerenciará todo o projeto.
    
- ✅ **Hugo**: O gerador de site estático.
    

#### ▶️ Instruções de Instalação para Usuários Linux

A instalação do Hugo no Linux é simples. Use o gerenciador de pacotes da sua distribuição:

- **Debian/Ubuntu:**
    
    ```
    sudo apt update && sudo apt install hugo
    ```
    
- **Arch Linux:**
    
    ```
    sudo pacman -S hugo
    ```
    
- **Fedora/CentOS:**
    
    ```
    sudo dnf install hugo
    ```
    

> Para outras distribuições ou para obter a versão mais recente, consulte a [página oficial de instalação do Hugo](https://gohugo.io/installation/linux/ "null").

## 2. Setup Inicial do Projeto (Feito Apenas Uma Vez)

Siga estes passos para configurar a estrutura do seu projeto.

#### Passo 1: Criar os Repositórios no GitHub

Você precisa de **dois** repositórios:

1. **Repositório** de **Código-Fonte**: Onde o conteúdo do seu blog (posts, tema, configurações) será armazenado.
    
    - _Exemplo de nome_: `meu-blog-fonte` (pode ser público ou privado).
        
2. **Repositório de Publicação**: Onde o site estático (HTML/CSS/JS) será hospedado.
    
    - _Nome obrigatório_: `seu-usuario.github.io` (precisa ser público para o GitHub Pages funcionar).
        

#### Passo 2: Configurar o Projeto Localmente

1. **Clone o repositório de código-fonte** para a sua máquina:
    
    ```
    git clone [https://github.com/seu-usuario/meu-blog-fonte.git](https://github.com/seu-usuario/meu-blog-fonte.git)
    cd meu-blog-fonte
    ```
    
2. **Crie a estrutura do site Hugo** dentro do repositório:
    
    ```
    # O ponto "." cria o site no diretório atual.
    # O --force evita erros caso a pasta já contenha arquivos (como o README.md).
    hugo new site . --force
    ```
    
3. **Adicione um tema**. A melhor prática é usar um submódulo para o tema também, facilitando atualizações futuras:
    
    ```
    git submodule add [URL_DO_REPOSITORIO_DO_TEMA] themes/[nome-do-tema]
    ```
    
4. **Configure o arquivo `hugo.toml`** (ou `config.toml`) na raiz do projeto:
    
    ```
    baseURL = "[https://seu-usuario.github.io/](https://seu-usuario.github.io/)"
    languageCode = "pt-br"
    title = "O Título Incrível do Meu Blog"
    theme = "nome-do-tema"
    ```
    
    > **Atenção:** O `baseURL` é o passo mais importante para garantir que os links e estilos do seu site funcionem corretamente quando publicados.
    

#### Passo 3: Conectar os Repositórios com Git Submodule

Esta é a etapa chave que conecta seu desenvolvimento à publicação.

1. **Delete a pasta `public`** se o Hugo a tiver criado automaticamente:
    
    ```
    rm -rf public
    ```
    
2. **Adicione o seu repositório de publicação como um submódulo**:
    
    ```
    # Este comando diz ao Git: "A pasta 'public' neste projeto é, na verdade,
    # um clone do repositório 'seu-usuario.github.io'".
    git submodule add -b main [https://github.com/seu-usuario/seu-usuario.github.io.git](https://github.com/seu-usuario/seu-usuario.github.io.git) public
    ```
    
3. **Faça o commit inicial da estrutura do projeto-fonte**:
    
    ```
    git add .
    git commit -m "Configuração inicial do projeto do blog com tema e submódulo de publicação"
    git push origin main
    ```
    

## 3. O Fluxo de Trabalho para Publicar (Seu Dia a Dia)

Este é o processo que você repetirá sempre que quiser escrever um novo post ou atualizar seu blog.

#### Passo 1: Criar e Escrever Conteúdo

1. **Crie um novo arquivo de post**:
    
    ```
    hugo new posts/meu-novo-post-incrivel.md
    ```
    
2. **Edite o arquivo** em `content/posts/`. Adicione seu texto, imagens e o que mais desejar.
    
3. **Remova o status de rascunho**: No cabeçalho do arquivo (frontmatter), altere `draft: true` para `draft: false` ou simplesmente remova a linha para que o post seja publicado.
    

#### Passo 2: Visualizar Localmente

Antes de publicar, sempre verifique se tudo está como esperado.

```
# O argumento -D (ou --buildDrafts) inclui os rascunhos na visualização.
hugo server -D
```

Acesse `http://localhost:1313` no seu navegador para ver seu site em tempo real.

#### Passo 3: Publicar as Alterações

Este é um processo de duas etapas de commit: uma para o site público e outra para o seu código-fonte.

1. **Gere os arquivos estáticos do site**: Na raiz do seu projeto (`meu-blog-fonte`), execute:
    
    ```
    hugo
    ```
    
    > O Hugo irá construir seu site e colocar todos os arquivos HTML/CSS/JS finais dentro da pasta `public`.
    
2. **Publique o site (commit no submódulo)**:
    
    ```
    # Entre na pasta do site público
    cd public
    
    # Adicione e faça o commit de todas as alterações (novos posts, páginas, etc.)
    git add .
    git commit -m "Publica novo post: Meu Novo Post Incrível"
    
    # Envie para o GitHub Pages, tornando as alterações públicas
    git push origin main
    
    # Volte para a raiz do projeto-fonte
    cd ..
    ```
    
    > Neste momento, seu site já está sendo atualizado online!
    
3. **Salve o estado do seu trabalho (commit no projeto-fonte)**: O repositório principal (`meu-blog-fonte`) percebeu que a pasta `public` (o submódulo) foi atualizada. Você precisa registrar essa mudança.
    
    ```
    # Adicione a nova referência do submódulo e qualquer outra alteração
    git add .
    
    # Faça o commit registrando o que você fez
    git commit -m "Cria conteúdo: Meu Novo Post Incrível"
    
    # Envie as alterações do código-fonte para o GitHub
    git push origin main
    ```
    
    > Este passo é crucial para manter a consistência. Se você clonar seu projeto em outra máquina, o Git saberá exatamente qual versão do site publicado corresponde a esta versão do código-fonte.
    

