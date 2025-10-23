# Utilizando Git

## Oque é git?
O Git é um sistema de controle de versão que serve para salvar, acompanhar e gerenciar alterações em arquivos, principalmente em projetos de programação. Ele permite voltar a versões anteriores, trabalhar em equipe sem perder mudanças e unir códigos de diferentes pessoas de forma organizada.

##  1. Configuração inicial

Antes de começar a programar o git, é muito importante se identificar primerio para que não perca o trabalho. Então com os comandos abaixo é possivel colocar o seu nome e email. Além disso pode definir o VS code como editor padrão.

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
git config --global core.editor "code --wait"   # Define o VS Code como editor padrão (opcional)
git config --list                                # Verifica as configurações atuais
```

---

##  2. Criar e iniciar um repositório

Depois de terminar a configuração inicial, crie uma pasta do seu projeto.

```bash
mkdir meu_projeto
cd meu_projeto
git init
```

> O comando `git init` cria um repositório local, gerando a pasta oculta `.git`.

---

## 3. Alterar a branch padrão de `master` para `main`

o Git cria o primeiro ramo (branch) do projeto com o nome master.
Mas, seguindo as boas práticas e padrões mais atuais, recomenda-se mudar o nome dessa branch principal para main, que tem o mesmo propósito, mas usa uma nomenclatura mais moderna e inclusiva.

```bash
git branch -m master main
```

Se quiser definir main como padrão para novos repositórios:

```bash
git config --global init.defaultBranch main
```

---

## 4. Criar arquivos e verificar status


```bash
echo "Meu primeiro arquivo" > readme.txt
git status
```

> `echo "Meu primeiro arquivo" > readme.txt` basicamente transfere o texto "Meu primeiro arquivo" ao `readme.txt`

> `git status` mostra arquivos novos, modificados ou prontos para commit.

---

## 5. Adicionar arquivos à área de staging

```bash
git add readme.txt       # adiciona um arquivo específico
git add .                # adiciona todos os arquivos do diretório
git status
```

> A área de staging é onde os arquivos ficam “preparados” antes do commit.


---

## 6. Fazer o primeiro commit

O commit é como um “salvamento oficial” no histórico do projeto. Ele registra todas as alterações feitas até aquele momento, criando um ponto de controle que pode ser consultado ou revertido no futuro.

```bash
git commit -m "Primeiro commit - adiciona readme.txt"
```


---

## 7. Ver histórico e detalhes

Esses comandos mostram o histórico dos commits realizados.
O comando `git log` exibe todos os detalhes, enquanto `git log --oneline` mostra uma versão resumida e mais fácil de ler.
Já o `git show` exibe informações completas sobre um commit específico.

```bash
git log
git log --oneline
git show
```



---

## 8. Editar arquivos e registrar mudanças

Esses comandos permitem editar um arquivo e salvar as mudanças.
O `git status` mostra o que foi modificado, o `git diff` exibe as diferenças em relação à última versão, e o `git add` prepara o arquivo para ser incluído no próximo commit.
Por fim, o `git commit` registra oficialmente essas alterações.

```bash
echo "Adicionando nova linha" >> readme.txt
git status
git diff
git add readme.txt
git commit -m "Atualiza readme.txt com nova linha"
```



---

## 9. Desfazer mudanças
Esses comandos são usados para corrigir erros antes de um commit.
O primeiro descarta mudanças que ainda não foram adicionadas, e o segundo remove o arquivo da área de preparação (staging area), permitindo revisar ou ajustar o que será enviado.
```bash
git restore readme.txt
git restore --staged readme.txt
```


---

## 10. Criar e alternar entre branches

Branches são linhas separadas de desenvolvimento dentro do projeto.
Com esses comandos, você pode criar novas branches e alternar entre elas, permitindo trabalhar em novas funcionalidades sem alterar o código principal.

```bash
git branch
git branch nova_funcionalidade
git switch nova_funcionalidade
```



---

## 11. Fazer commits em outra branch
Aqui você está fazendo alterações e salvando-as dentro de uma branch diferente.
Isso é útil para desenvolver novos recursos sem interferir no trabalho principal da branch principal.
```bash
echo "Nova feature" > feature.txt
git add feature.txt
git commit -m "Adiciona nova feature"
```



---

## 12. Voltar e mesclar mudanças

Esses comandos servem para unir o que foi feito em uma branch secundária com a branch principal (`main`).
O `git merge` combina as alterações, atualizando o projeto com as novas implementações.

```bash
git switch main
git merge nova_funcionalidade
```

---

## 13. Excluir branches locais
Depois de mesclar as mudanças, você pode excluir a branch que não é mais necessária.
Isso ajuda a manter o repositório mais organizado e limpo.

```bash
git branch -d nova_funcionalidade
```

---

## 14. Ignorar arquivos com `.gitignore`

Crie um arquivo chamado `.gitignore` e adicione os arquivos ou pastas que o Git deve ignorar:

```
*.log
*.tmp
node_modules/
```

Depois:

O arquivo `.gitignore` define o que o Git não deve rastrear, como arquivos temporários ou pastas de dependências.
Isso evita que arquivos desnecessários sejam incluídos no repositório.


```bash
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```

---

## 15. Visualizar informações úteis

Esses comandos ajudam a visualizar o estado do repositório.
O `git status` mostra o que foi alterado, `git log` exibe o histórico, `git diff` mostra as diferenças entre versões e `git show HEAD` mostra detalhes do último commit.
O `--graph` adiciona uma visualização das ramificações.

```bash
git status
git log --oneline --graph --decorate
git diff
git show HEAD
```

---

## 16. Exemplo de fluxo completo
Esse é um exemplo de fluxo básico de trabalho com Git.
Você inicia o repositório, cria arquivos, salva versões, desenvolve em uma branch separada e depois junta tudo novamente na branch principal, mantendo o histórico bem organizado.

```bash
git init
echo "Aula prática Git local" > readme.txt
git add .
git commit -m "Primeiro commit"
git branch dev
git switch dev
echo "Nova versão em desenvolvimento" >> readme.txt
git add .
git commit -m "Atualiza versão dev"
git switch main
git merge dev
git log --oneline --graph
```
## 17. Clonagem e configuração local

Esse exemplo abaixo é o uso do comando git clone, que basicamente pega todos os arquivos que existem no repositório remoto e manda para o seu despositivo local.

```bash
git clone <URL do seu repositório>
git checkout -b documentacao-colaboracao
```
O comando checkout alterna entre branches (ramificações), navegar por commits antigos e restaurar arquivos no seu repositório Git

---

## 18. Uso do GitFluence e Comandos de integração

A documentação deve explicar os principais **comandos de integração** entre o repositório **local** (no seu computador) e o **remoto** (no GitHub).

```bash
git push -u origin documentacao-colaboracao  
git branch -a
```
`git branch -a`: Mostra todas as branches disponíveis, tanto as locais quanto as do repositório remoto.

`git push -u origin`:Envie a nova ramificação para o repositório remoto 

---

### GitFluence

O **GitFluence** pode ser usado como ferramenta de apoio para gerar esses comandos automaticamente, facilitando o aprendizado e o uso do Git.

![imagem GitFluence](https://media.discordapp.net/attachments/1341900461396988094/1430990555805909043/image.png?ex=68fbc94f&is=68fa77cf&hm=851b5ef35d778f9c47b9abc82253dae0ff82e772dec503692264f10d9fd76519&=&format=webp&quality=lossless)

---

## 19. Integração e Colaboração (GitHub)

Essa parte trata de como **compartilhar e integrar seu trabalho com outras pessoas** através do GitHub, especialmente quando o projeto é colaborativo.


Depois de enviar o seu branch para o GitHub, o próximo passo é abrir um **Pull Request (PR)**.
Um PR serve para propor que suas alterações sejam revisadas e, se aprovadas, mescladas ao repositório principal.

**Passos para abrir um Pull Request:**

1. Acesse o seu fork no GitHub.
2. O GitHub normalmente sugerirá automaticamente a abertura de um PR.
3. Crie o PR a partir do seu branch (por exemplo, `documentacao-colaboracao`) para o branch principal (`main`) do repositório original.

---

Se o seu repositório no GitHub for **privado**, você precisa conceder acesso manualmente para que outras pessoas possam contribuir.

**Passo a passo:**

1. Acesse o repositório no GitHub.
2. Clique em **Settings (Configurações)**.
3. No menu lateral, abra a seção **Access** e selecione **Collaborators (Colaboradores)**.
4. Clique no botão verde **Add people (Adicionar pessoas)**.
5. Pesquise o colaborador pelo nome de usuário, nome completo ou e-mail.
6. Clique no nome correto e, em seguida, em **Add [NOME] to REPOSITORY**.
7. O GitHub enviará um convite por e-mail para o colaborador, que precisará **aceitar o convite** para ter acesso ao repositório e poder fazer commits.

---

## 📘 Créditos

Material criado para fins educacionais na aula prática de **Git Local**,  
ministrada por *Anderson R. M. Gomes* 🧑‍🏫

---

**🚀 Próximos passos:**  
Na próxima aula, você aprenderá a conectar este repositório local ao GitHub com os comandos `git remote`, `git push` e `git pull`.
