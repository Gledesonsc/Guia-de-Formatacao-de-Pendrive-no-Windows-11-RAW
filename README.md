# 💻 Guia de Como Remover Partições RAW e Criar uma Única Partição FAT32 no Windows 11

---

### 📋 **Sumário**
1. [Introdução](#introdução)
2. [Requisitos](#requisitos)
3. [Passo a Passo](#passo-a-passo)
   - [Abrindo o Diskpart](#abrindo-o-diskpart)
   - [Listando os Discos Conectados](#listando-os-discos-conectados)
   - [Selecionando o Disco Correto](#selecionando-o-disco-correto)
   - [Excluindo Partições](#excluindo-partições)
   - [Criando uma Nova Partição](#criando-uma-nova-partição)
   - [Formatando para FAT32](#formatando-para-fat32)
4. [Conclusão](#conclusão)

---

### 📝 **Introdução**

Neste documento, vamos te guiar pelo processo de remoção de partições com formato **RAW** e criação de uma única partição no formato **FAT32** em um pendrive, usando o comando `diskpart` no **Windows 11**. 👨‍💻

As partições RAW podem causar problemas de leitura e uso do dispositivo, então é importante saber como removê-las para que seu pendrive funcione corretamente em sistemas modernos.

---

### 🔧 **Requisitos**
- Um computador com **Windows 11** 🖥️
- Pendrive conectado ao sistema 🖱️
- Acesso ao **Prompt de Comando** como administrador

---

### 🔨 **Passo a Passo**

#### 🔍 **Abrindo o Diskpart**

1. Pressione `Windows + S`, digite **cmd** e clique com o botão direito no **Prompt de Comando**.
2. Escolha **Executar como administrador**.

Abra o **Diskpart** com o comando abaixo:

```bash
diskpart
```

---

#### 💾 **Listando os Discos Conectados**

Liste todos os discos conectados ao seu computador usando o comando:

```bash
list disk
```

Agora, identifique o número do seu pendrive com base no tamanho listado.

---

#### 🛠️ **Selecionando o Disco Correto**

Substitua `X` pelo número do disco que corresponde ao seu pendrive:

```bash
select disk X
```

Por exemplo, se o número do pendrive for **Disco 4**, o comando será:

```bash
select disk 4
```

---

#### 🗑️ **Excluindo Partições**

Agora, vamos listar as partições no pendrive para poder excluir uma por uma:

```bash
list partition
```

Para cada partição listada, faça o seguinte:

1. Selecione a partição:

```bash
select partition Y
```

Onde `Y` é o número da partição (por exemplo, `select partition 1`).

2. Exclua a partição (caso não funcione normalmente, utilize o **override**):

```bash
delete partition override
```

Repita esses passos para todas as partições até que o pendrive fique sem partições.

---

#### 🛠️ **Criando uma Nova Partição**

Com todas as partições removidas, você pode criar uma nova partição principal:

```bash
create partition primary
```

---

#### 📝 **Formatando para FAT32**

Agora, formate essa nova partição no sistema de arquivos **FAT32**:

```bash
format fs=fat32 quick
```

Se quiser atribuir uma letra específica para o pendrive (por exemplo, **D**):

```bash
assign letter=D
```

---

### ✅ **Conclusão**

Agora, seu pendrive está completamente formatado em **FAT32** e pronto para uso. 🎉  
Se encontrar qualquer problema, basta seguir os passos novamente ou ajustar a formatação conforme necessário.

---

### 📚 **Referências**

- [Documentação Microsoft sobre o Diskpart](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/diskpart)
  
---
