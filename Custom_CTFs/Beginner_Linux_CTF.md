# CTFs Personalizados

[TOC]

## Beginner Linux CTF

+ Adaptado de: https://s0cket7.com/beginner-linux-ctf/



#### Nível - 0

Credenciais disponibilizadas:

+ user: user1

+ pass: qwerty123!

```bash
ssh user1@linuxctf
```


#### Nível - 1

```bash
# Criada pasta oculta ".here"
mkdir ~/.here
echo JustS1art3ng > pass
```

+ user: user2

+ pass: JustS1art3ng



#### Nível - 2

```bash
# Criado ficheiro com nome contendo carateres especiais
echo tH1rDuSe4# > $!Password&

#solução
cat -- \$\!Password\&
```

+ user: user3

+ pass: tH1rDuSe4#



#### Nível - 3

```bash
# Criada Chave SSH
ssh-keygen

# Adicionada chave pública ao ficheiro ~/.ssh/authorized_keys
echo <public key> >> ~/.ssh/authorized_keys

# Permissões ficheiro authorized_keys
chmod 700 authorized_keys


#Solução
scp -r user3@localhost:/home/user3/password private_key
chmod 600 private_key
ssh -i <private_key> <user4@localhost>
```

+ user: user4

+ pass:  Não tem. Ficou apenas com chave ssh privada



#### Nível - 4

```bash
# Criar ficheiro executável (código abaixo)
touch code.c
gcc -c code.c -o password.txt
cp password.txt /home/user4

#Criar diretorias aleatórias
mkdir -p /home/user4/asdk/pDqd/kpdak/bcdn/opqwFpmdq/qwmks/qwekpk/pks
mkdir -p /home/user4/asaowjw/qwoieoi/dasdpo/JHUhbjs/KmnkSsa/ssdl
mkdir -p /home/user4/32njjnj2K/asasdppps0/knk34JsaO/kmwHG32/askmdlm/qwjoq

# Calcular hash da password
echo flag{1StFl@g} > /home/user4/asdk/pDqd/kpdak/bcdn/--qazWtGji
```

+ user: user5
+ pass: absalon251321


+ **Primeira Flag**

  + flag{1StFl@g}

```c
# Criar ficheiro executável

#include <stdio.h>
int main(void){
  printf("You may find the file --qazWtGji interesting\n");
  printf("Password: 43d751055509e1c871799dca310be29b796ed1e0ef6c0cf3a53d55c06f62faf7\n");
    return 0;
}
```



#### Nível - 5

```bash
# Criar dica de comando para correr ficheiro com outro grupo associado
man sg > /home/user5/group.txt

# Criar ficheiro com password
echo s0MthingN3W! > password.txt

# Criar grupo e definir permissões
chmod 540 group.txt
chmod 540 password.txt
groupadd -p absalon251321 password
chgrp user5 group.txt
chgrp password password.txt


#Solução
sg password -c 'cat password.txt' 
```

+ user: user6
+ pass:  s0MthingN3W!



#### Nível - 6

Análise PCAP com tráfego SMTP:

+ Perguntas:
  + Quantos emails de spam referentes a Sextortion foram recebidos? 
  
    + R: 50
    
    ```bash
    ls | cat -n
    ```
  
  + Quantos subjects distintos existem (considerar o assunto até ao !)? 
    
    + R: 33
    
    ```bash
    ls | cut -d "-" -f 1 | sort -u | cat -n
    ```
  
  + Qual o subject mais utilizado? 
    
    + R: I won´t warn you again!
    
    ```bash
    ls | cut -d "-" -f 1 | sort | uniq -c
    ```

  + Quantos senders distintos foram utilizados? 
  
    + R: 48
    
    ```bash
    grep -i FROM: *.eml | cut -d "<" -f 2 | sort -u | cat -n
    ```
  + Quais os senders utilizados mais do que uma vez? 
  
    + R: YourLife01@6073.com e YourLife63@2266.com
    
    ```bash
    grep -i FROM: *.eml | cut -d "<" -f 2 | sort | uniq -c
    ```
  + Qual o primeiro destinatário destes emails, ordenado por ordem alfabética decrescente? Corresponde à pssword do próximo user
  
    + R: mr_msvn4_09@yahoo.com
    
    ```bash
    grep To: *.eml | cut -d ":" -f 3 | sort | uniq -c
    ```
  
+ user: user7
+ pass: mr_msvn4_09@yahoo.com



#### Nível - 7

Análise PCAP com tráfego FTP:

+ Perguntas:
  + Existem objectos descarregados de um servidor de FTP que contém malware neste PCAP. Qual o nome e o IP desse servidor? 
  
    + R:  ftp.psg420.com e 216.55.163.106 (filtro Wireshark: ftp.request.command)
    
  + Quantos são estes ficheiros? 
    
    + R: 5
    
  + Qual o seu tipo? 
    
    + R: PE32+ executable (GUI) x86-64, for MS Windows

  + Quais as Hashes destes ficheiros, calculadas com o algoritmo SHA256? 
  
    + R: (filtro Wireshark: ftp-data)

      32e1b3732cd779af1bf7730d0ec8a7a87a084319f6a0870dc7362a15ddbd3199
      ca34b0926cdc3242bbfad1c4a0b42cc2750d90db9a272d92cfb6cb7034d2a3bd	
      4ebd58007ee933a0a8348aee2922904a7110b7fb6a316b1c7fb2c6677e613884	
      10ce4b79180a2ddd924fdc95951d968191af2ee3b7dfc96dd6a5714dbeae613a
      08eb941447078ef2c6ad8d91bb2f52256c09657ecd3d5344023edccf7291e9fc
    
  + Foram exportados ficheiros para o servidor de FTP? 
  
    + R: Sim
  + Quantos e qual o seu nome?
  
    + R: 5 e 1052543721_logs.html
  
  + Estes ficheiros têm conteúdo igual?
  
    + R: Sim

  + Quais as duas contas de utilizador distintas comprometidas (email e banco) Nota: A password dá acesso ao próximo nível?
  
    + R: alton.quinn e alton.quinn@cliffstone.com
  + Qual a password associada às contas anteriores? Dica: A password para acesso ao servidor de FTP dá acesso ao próximo nível?
  
    + R: P@ssw0rd$
+ user: user8
+ pass: {6r_6e#TfT1p



#### Nível - 8

```bash
hist#Criar diretorias aleatórias
mkdir -p /home/user8/asdk/pD343qd/kpdak/bcdn/opqwFpmdq/qwmks/qwekpk/pks/fassnflans
mkdir -p /home/user8/as34aotywjw/qwo43ieoi/dasdposcvahjks/JHUhbjs/KsdjkhfmnkSsa/ssdl/fasndnakj
mkdir -p /home/user8/32njjnj2K/asasddserppps0/knk3sdfs4JsaO/kmwHG32/askmdlm/qwjoqask7bdka
mkdir -p /home/user8/as34atyrowjw/qheoi/dacvahjks/JHUhbjs/KsdjkhfmnkSsa/ssdl/fasoasdonakj
mkdir -p /home/user8/34tyyyaowjw/qwo43hjhjieoi/dasdpohjjhgjscvahjks/JHU55hbjs/Ksdjkhf55Ssa/ssdl/sasdasdww
mkdir -p /home/user8/oiuouighjg/qo43ihj/dashjks/JHUhbjs/Ksdjksa/ss544dl/fasnjdss64akj
```



+ Perguntas:
  + Encontre um ficheiro chamado **database.txt.gpg** e uma wordlist chamada **list.txt**. Qual é a password do ficheiro cifrado? (Dica: Utilize a wordlist na ordem inversa)
    + R: wolverine
    
    ```sql
    #Credentials for Database
    sgdb=Mysql
    username=dbadmin
    pass=W3bsh0pAdm1n#
    
    #Create DB User
    CREATE USER 'dbadmin'@'localhost' IDENTIFIED BY 'W3bsh0pAdm1n#';
    GRANT ALL PRIVILEGES ON * . * TO 'dbadmin'@'localhost';
    
    #Create a gpg file
    gpg -c --cipher-algo AES-256 --encrypt <data.txt> 
    ```
    
  + Quantos utilizadores apresentam o perfil de admin?
    + R: 5
  
+ **Segunda Flag**

  + flag{S3c0nDFl@g}
  ```sql
  select * from product where name like '%flag%';
  ```
  
+ user: user9
+ pass: olympics2021



#### Nível - 9
+ **Terceira Flag**

  + flag{tH1rdFl@g#YouR0cK}
  ```bash
  #Criar ficheiro na raiz do utilizador root
  echo flag{tH1rdFl@g#YouR0cK} | base64 > flag_final.txt
  ```

