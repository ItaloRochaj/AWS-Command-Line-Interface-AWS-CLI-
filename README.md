# Instalar e Configurar o AWS CLI

## Visão Geral do Laboratório
A AWS Command Line Interface (AWS CLI) é uma ferramenta de linha de comando que fornece uma interface para interagir com produtos e serviços da Amazon Web Services (AWS).

Você pode instalar a AWS CLI na sua máquina local ou em uma máquina virtual, como uma instância do Amazon Elastic Compute Cloud (Amazon EC2).

Nesta atividade, você instala e configura o AWS CLI em uma instância do Red Hat Linux, pois esse tipo de instância não tem o AWS CLI pré-instalado. Alguns tipos de instância, como o Amazon Linux, já vêm com o AWS CLI instalado.

Durante esta atividade, você estabelece uma conexão Secure Shell (SSH) com a instância, configura a instalação com uma chave de acesso para conectar-se a uma conta da AWS e pratica o uso da AWS CLI para interagir com o AWS Identity and Access Management (IAM).

![Arquitetura inicial](https://github.com/ItaloRochaj/AWS-Command-Line-Interface-AWS-CLI-/blob/main/project%20image/Captura%20de%20tela%20de%202025-02-11%2009-42-42.png)

### Objetivos
Após concluir este laboratório, você será capaz de:
- Instalar e configurar a AWS CLI.
- Conectar a AWS CLI a uma conta da AWS.
- Acessar o IAM usando a AWS CLI.

### Duração
Esta atividade leva aproximadamente **45 minutos** para ser concluída.

## Acessando o AWS Management Console
1. Na parte superior destas instruções, escolha **Iniciar Laboratório**.
2. Aguarde até que a mensagem "Status do laboratório: pronto" apareça.
3. Escolha **X** para fechar o painel Iniciar Laboratório.
4. Ao lado de **Start Lab**, escolha **AWS** para abrir o AWS Management Console.

> **Importante**: Não altere a região do laboratório, a menos que seja especificamente instruído a fazê-lo.

## Tarefa 1: Conectar-se à Instância do Red Hat EC2 usando SSH

### Usuários do Windows
1. No menu **Detalhes**, selecione **Mostrar**.
2. Baixe o arquivo **labsuser.ppk**.
3. Anote o **PublicIP**.
4. Instale o **PuTTY** (se necessário).
5. Abra o **putty.exe** e configure a sessão para conectar-se à instância.

### Usuários de macOS e Linux
1. No menu **Detalhes**, selecione **Mostrar**.
2. Baixe o arquivo **labsuser.pem**.
3. Copie o **PublicIP**.
4. Abra um terminal e execute os comandos:
   ```bash
   cd ~/Downloads
   chmod 400 labsuser.pem
   ssh -i labsuser.pem ec2-user@<endereco-ip>
   ```
5. Digite `yes` para conectar-se.

## Tarefa 2: Instalar a AWS CLI na Instância do Red Hat Linux
1. Baixe a AWS CLI:
   ```bash
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   ```
2. Descompacte o instalador:
   ```bash
   unzip -u awscliv2.zip
   ```
3. Instale a AWS CLI:
   ```bash
   sudo ./aws/install
   ```
4. Verifique a instalação:
   ```bash
   aws --version
   ```
5. Teste a AWS CLI:
   ```bash
   aws help
   ```

## Tarefa 3: Observar os Detalhes de Configuração do IAM no AWS Management Console
1. No AWS Management Console, pesquise **IAM** e escolha **IAM**.
2. No painel de navegação, escolha **Usuários** > **awsstudent**.
3. Na aba **Permissions**, escolha o ícone de seta ao lado de **lab_policy** e visualize o JSON.
4. Na aba **Security Credentials**, localize o **Access Key ID**.

## Tarefa 4: Configurar a AWS CLI para Conectar-se à Conta AWS
1. No terminal SSH, execute:
   ```bash
   aws configure
   ```
2. Preencha os valores solicitados:
   - **AWS Access Key ID**: copie e cole do AWS Management Console.
   - **AWS Secret Access Key**: copie e cole do AWS Management Console.
   - **Default region name**: digite `us-west-2`.
   - **Default output format**: digite `json`.

## Tarefa 5: Observar os Detalhes de Configuração do IAM Usando a AWS CLI
1. Execute o comando para listar os usuários do IAM:
   ```bash
   aws iam list-users
   ```

## Desafio da Atividade 1
Use a **AWS CLI Command Reference** para baixar o documento **lab_policy** em JSON.

### Dicas
- Liste as políticas do IAM filtrando por escopo local:
  ```bash
  aws iam list-policies --scope Local
  ```
- Use o **policy-arn** e **version-id** para obter a política JSON:
  ```bash
  aws iam get-policy-version --policy-arn arn:aws:iam::038946776283:policy/lab_policy --version-id v1 > lab_policy.json
  ```

## Resumo da Atividade
Você instalou e configurou a AWS CLI em uma instância do Red Hat Linux, conectou-se a uma conta AWS e utilizou a AWS CLI para interagir com o IAM.

### Principais Conclusões
- O AWS CLI permite gerenciar serviços AWS via linha de comando.
- Para conectar-se, é necessário um **Access Key ID** e **Secret Access Key**.
- O AWS Management Console requer login com usuário e senha.

## Conclusão
Parabéns! Você completou o laboratório com sucesso.

## Finalização do Laboratório
1. Escolha **Finalizar Laboratório** e confirme.
2. Um painel aparecerá indicando que os recursos estão sendo encerrados.
3. Feche o painel **End Lab**.

