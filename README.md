# Atividade de Criptoanálise e BruteForce

### Atividade da disciplina de Segurança de Dados, para fins estritamente acadêmicos.

# Ferramentas:

* John the Ripper

é um cracker de senha, 
disponível para Vários sistemas operacionais. 
Seu objetivo principal é detectar 
senhas fracas do Unix. Também pode ser utilizado para
gerar wordlists de senhas cadidatas para máscaras específicas,
o Mask Mode é uma maneira rápida de produzir senhas candidatas a 
partir de uma "máscara" que descreve como a palavra deve ser gerada,
por exemplo: **?u?l?l** , gerará todas as palavras possíveis 
de três letras, sendo a primeira letra maiúscula e as demais
minúsculas.

**Para gerar uma wordlist contento senhas caditadas no formato: 4 números e 2 letras minúsculas,
utiliza-se o comando:**

```sh
$ time john -mask=?d?d?d?d?l?l --stdout > wordlist.txt
```

Saída:
```sh
6760000p 0:00:00:00 100,00% (2019-02-08 10:07) 16900Kp/s 7777qq

real	0m1,455s
```
Foram geradas 6760000 palavras em aproximadamente 1,5 segundos, e o arquivo contém 46MB
```sh
$ du -h wordlist.txt
46M	wordlist.txt
```

**Para gerar uma wordlist contento senhas caditadas no formato: 6 números e 2 letras minúsculas,
utiliza-se o comando:**
```sh
$ time john -mask=?d?d?d?d??d?dl?l --stdout > wordlist.txt
```

Saída:
```sh
676000000p 0:00:01:21 100,00% (2019-02-08 10:05) 8336Kp/s 777777qq

real	1m35,233s
```
Foram geradas 676000000 palavras em aproximadamente 1,35 minutos, e o arquivo contém 5,7GB
```sh
$ du -h wordlist.txt 
5,7G	wordlist.txt
```
* WPScan

é um software livre, para uso não comercial,
scanner de vulnerabilidade WordPress caixa preta escrito 
para profissionais de segurança e mantenedores de blog 
para testar a segurança de seus sites. Com ele, é possivel 
descobrir possíveis vulnerabilidades em sites WordPress, para
eventualmente, corrigí-las no futuro.

Usar a ferramenta é bem simples, basta utilizar o comando:
```sh
$ wpscan --url http://sitewordpress.com 
```
Em alguns sites, pode ser necessário acrescentar ```sh--stealthy``` , que é um alias para 
```sh--random-user-agent```, de forma que as requisições são enviadas
com cabeçalhos(User-Agent) aleatórios.

* Hydra

é um cracker de login baseado em ataques 
de força bruta que protocolos de ataque. 
Essa ferramenta possibilita que 
pesquisadores e consultores de segurança mostrem 
como seria fácil obter acesso não autorizado a um 
sistema remotamente.

Uma das formas de uso dessa ferrameta, é utilizar 
uma wordlist(conjunto de senhas candidatas)
pré definida e o comando:

```sh
$ hydra -l test@email.net -P wordlist.txt url.com.br https-form-post "/login:email=^USER^&password=^PASS^:S=Success" -V
```
O Hydra irá utilizar as senhas armazenadas no arquivo: ```wordlist.txt```
para tentar realizar o login no endereço: ```url.com.br``` com o email já 
conhecido: ```test@email.net``` com o protocolo ```https-form-post```, e as opções adicionais, 
neste caso parâmetros do formulário(usuário e senha) e mensagem de sucesso. 

## Equipe:
* [Fernanda Vieira](https://github.com/fernandasj) 

* [Rogério Araújo](https://github.com/rodgeraraujo) 
