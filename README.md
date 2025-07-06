Aqui está uma versão aprimorada do README.md com emojis, badges e seu e-mail de contato conforme solicitado:

---

# 📝 Blog Pessoal com Hugo (Blowfish) + Obsidian + GitHub Actions + GitHub Pages

[![Hugo](https://img.shields.io/badge/Hugo-Static%20Site%20Generator-blueviolet?logo=hugo)](https://gohugo.io/)
[![Theme: Blowfish](https://img.shields.io/badge/Theme-Blowfish-0099ff?logo=blowfish)](https://blowfish.page/)
[![GitHub Actions](https://github.com/peixoto-ops/blog/actions/workflows/deploy.yml/badge.svg)](https://github.com/peixoto-ops/blog/actions)
[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-3276b1?logo=github)](https://pages.github.com/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

---

## 🎯 Objetivo

- Transformar minhas anotações do Obsidian (em Markdown) em um blog moderno, responsivo e fácil de manter.
- Automatizar o processo de atualização do blog sempre que novas notas forem adicionadas ou editadas.
- Utilizar apenas ferramentas gratuitas e open source.

## 🚀 Stack Principal

- **Obsidian**: Local de criação e organização das notas (arquivos Markdown).
- **Hugo**: Gerador de site estático.
- **Tema Blowfish**: Tema escolhido para o blog Hugo.
- **GitHub Actions**: Automatização do build e deploy.
- **GitHub Pages**: Hospedagem gratuita do blog.

## 📁 Estrutura Inicial do Projeto

```
/
├── content/            # Onde as notas do Obsidian serão copiadas/convertidas
├── .github/
│   └── workflows/      # Automação com GitHub Actions
├── themes/
│   └── blowfish/       # Tema Hugo Blowfish
├── config.toml         # Configuração do Hugo
├── README.md           # Este arquivo
```

## 🔄 Fluxo Inicial

1. **Notas no Obsidian:**  
   Crie normalmente suas notas em Markdown no Obsidian.

2. **Sincronização:**  
   As notas serão copiadas ou sincronizadas para a pasta `content/` deste repositório (pode ser manual ou automatizado futuramente).

3. **Build Automático:**  
   Quando houver updates, o GitHub Actions executa:
   - Build do site Hugo usando o tema Blowfish.
   - Deploy automático para o GitHub Pages.

## 🛠️ Passos Iniciais

1. **Configurar Hugo e o tema Blowfish**
   - Instale o Hugo em sua máquina.
   - Crie a estrutura do projeto (`hugo new site .`).
   - Adicione o tema Blowfish como submódulo ou copie para a pasta `themes/`.

2. **Configurar GitHub Pages**
   - Ative o GitHub Pages no repositório (branch `gh-pages` ou `/docs`).
   - Adicione as configurações necessárias ao `config.toml`.

3. **Criar Workflow de Deploy**
   - Adicione um workflow do GitHub Actions em `.github/workflows/deploy.yml` para build e deploy automático.

## 🔜 Próximos Passos (Iterativos)

- 🔗 Automatizar a conversão/sincronização de notas do Obsidian para a pasta `content/`.
- 🏷️ Melhorar o mapeamento de tags, links internos e mídia das notas.
- 🎨 Customizar o tema Blowfish conforme preferências pessoais.
- 🔌 Adicionar plugins ou scripts para enriquecer o conteúdo.

## 📚 Referências

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Blowfish Theme](https://blowfish.page/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

## 📬 Contato

Dúvidas? Sugestões? Me envie um e-mail: **luizpeixoto@duck.com**

---

Sinta-se à vontade para sugerir alterações, pedir exemplos de arquivos de configuração ou abrir issues para dúvidas e melhorias! 🚀
