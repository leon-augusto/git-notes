# git-notes

- [Inicializando um Repositório e Realizando o Primeiro Commit](#inicializando-um-repositório-e-realizando-o-primeiro-commit)
- [Padrões de Mensagens de Commit](#padrões-de-mensagens-de-commit)
- [Desfazendo Commits no Git](#desfazendo-commits-no-git)
- [Git Merge vs. Git Rebase](#git-merge-vs-git-rebase)
- [Workflow com Rebase](#workflow-com-rebase)


## Inicializando um Repositório e Realizando o Primeiro Commit

1. **Inicializando um Repositório:**
   ```
   git init
   ```

2. **Adicionando um Arquivo ao Staging Area:**
   ```
   git add README.md
   ```

3. **Realizando o Primeiro Commit:**
   ```
   git commit -m "first commit"
   ```

4. **Criando e Mudando para a Branch Principal (main):**
   ```
   git branch -M main
   ```

5. **Conectando ao Repositório Remoto no GitHub:**
   ```
   git remote add origin https://github.com/leon-augusto/git-notes.git
   ```

6. **Enviando o Commit Inicial para o Repositório Remoto:**
   ```
   git push -u origin main
   ```

## Padrões de Mensagens de Commit

- **Resumo e Descrição:**
  ```
  git commit -m "Resumo" -m "Descrição"
  ```

- Tipos de Commit:
  - **feat:** Adição de nova feature.
  - **fix:** Resolução de um bug.
  - **style:** Atualização relacionada à estilização.
  - **refactor:** Refatoração de código.
  - **test:** Adição ou modificação de testes.
  - **docs:** Atualização de documentação.
  - **chore:** Manutenção regular do código.

  Exemplo:
  ```
  git commit -m "feat: Implementação do chat na home page" #jira-230
  ```

## Desfazendo Commits no Git

1. **Removendo Alterações em um Arquivo não Commitado:**
   ```
   git checkout -- arquivoindesejado.txt
   ```

2. **Desfazendo Alterações no Staging Area:**
   ```
   git reset arquivoindesejado.txt
   ```

3. **Desfazendo o Último Commit sem Descartar Alterações:**
   ```
   git reset HEAD~1
   ```

4. **Desfazendo o Último Commit e Descartando Alterações:**
   ```
   git reset --hard HEAD~1
   ```

5. **Revertendo um Commit Específico:**
   ```
   git revert 11a5b
   ```

## Git Merge vs. Git Rebase

- Ambos são usados para mesclar alterações de duas branches diferentes.
- **Git Merge:**
  - Gera um novo commit.
  - Não reescreve o histórico.

- **Git Rebase:**
  - Deixa o histórico linear e mais simples.
  - Alguns commits são reescritos.

**Importante:**
- Evitar rebase na branch master.
- Realizar rebase da master em outras branches.

## Workflow com Rebase

1. **Atualizando a Master Remota:**
   ```
   git checkout master
   git pull --rebase origin master
   ```

2. **Atualizando a Branch Remota:**
   ```
   git checkout sua-branch
   git pull --rebase origin sua-branch
   ```

3. **Mesclando a Master na Sua Branch:**
   ```
   git rebase master
   ```

4. **Commitando e Repetindo Diariamente:**
   - Pegando novidades da master e da sua branch remota.

5. **Finalizando a Funcionalidade/Correção:**
   ```
   git checkout master
   git merge sua-branch --no-ff
   ```
