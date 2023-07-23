# IronCorp
Here is my Python exploit to explore the SSRF vulnerability in the IronCorp machine on TryHackMe. 

You can read my post about this machine at: https://medium.com/@gutierrematheus/iron-corp-tryhackme-iron-corp-walkthrough-eng-88b0f263275

<h2>How to use</h2>
Just open 9001 port using nc and execute the exploit.py. It will do all the necessary validations (validate if you remembered to listen on port 9001 , generate shell.ps1 with your VPN IP that it will get by itself, check which port it can use to open a web server for the target to download shell.ps1, among others.)

My discord: gutierre0x80
______________________________________________________________________________________________________________________________________________________________________________________________________________________

<h2>S2</h2>

![script](https://github.com/Gutierre0x80/IronCorp/assets/63872706/0298f5ae-8c57-45cf-b7fa-7857710dc71c)

[EN]

1- The code begins by importing necessary libraries and modules, such as "sys," "psutil" (for obtaining system information), "http.server," and "socketserver" (for creating a web server), "threading" (for executing tasks in the background), "requests" (for making HTTP requests), "time" (for adding delays), "urllib.parse" (for encoding and decoding URLs), and "netifaces" (for getting network interface information).

2- Next, two functions are defined: "urlencode" and "urldecode," which are used for encoding and decoding strings for use in URLs.

4- The exploit uses the URL "http://admin.ironcorp.me:11025/?r=" to send commands to the target server and the URL "http://internal.ironcorp.me:11025/name.php?name=Equinox|" to perform Server-Side Request Forgery (SSRF) command injection and download the "shell.ps1" file on the target machine.

5- The "check_port" function is defined to check if a given port is in use by inspecting the system's network connections using the "psutil" library.

6- The first step of the exploit is to check if port 9001 is available on the system. If it's not available, it displays a message asking the user to run "nc -vnlp 9001" to listen on that port.

7- Next, the exploit obtains the IP address of the "tun0" network interface (assuming it is a VPN) and checks if port 1234 is in use. If it's in use, it increments the port number (1235, 1236, etc.) and continues checking until it finds an available port.

8- The code creates the "shell.ps1" file with a PowerShell script that establishes a TCP connection to the user's VPN IP address on port 9001. This will allow remote execution of PowerShell commands on the target machine.

9- It then starts a web server on the available port to serve the "shell.ps1" file for download on the target machine.

10- The code generates two different payloads to be used in an SSRF command injection. The first payload is used to make the web server on the target machine download the "shell.ps1" file and save it to "E:\xampp\htdocs\internal\shell.ps1". The second payload is used to execute the "shell.ps1" script on the target machine.

11- After a brief delay, the exploit sends the request containing the second payload to the SSRF injection URL "http://internal.ironcorp.me:11025/name.php?name=Equinox|", which will result in the execution of the "shell.ps1" script on the target machine.
______________________________________________________________________________________________________________________________________________________________________________________________________________________
[PT BR]

1- O código começa importando as bibliotecas e módulos necessários, como "sys", "psutil" (para obter informações do sistema), "http.server" e "socketserver" (para criar um servidor web), "threading" (para executar tarefas em segundo plano), "requests" (para enviar solicitações HTTP), "time" (para adicionar pausas), "urllib.parse" (para codificar e decodificar URLs) e "netifaces" (para obter informações da interface de rede).

2- Em seguida, há duas funções definidas: "urlencode" e "urldecode", que são usadas para codificar e decodificar strings para uso em URLs.

4- O exploit usa a URL "http://admin.ironcorp.me:11025/?r=" para enviar comandos ao servidor-alvo e a URL "http://internal.ironcorp.me:11025/name.php?name=Equinox|" para realizar a injeção de comando Server-Side Request Forgery (SSRF) e baixar o arquivo "shell.ps1" na máquina-alvo.

5- A função "check_port" é definida para verificar se uma determinada porta está em uso, verificando as conexões de rede do sistema usando a biblioteca "psutil".

6- A primeira etapa do exploit é verificar se a porta 9001 está disponível no sistema. Caso não esteja disponível, ele exibirá uma mensagem para o usuário executar "nc -vnlp 9001" para ouvir a porta.

7- Em seguida, o exploit obtém o endereço IP da interface de rede "tun0" (supondo que seja uma VPN) e verifica se a porta 1234 está em uso. Se estiver, ele aumenta o número da porta (1235, 1236, etc.) e continua verificando até encontrar uma porta disponível.

8- O código cria o arquivo "shell.ps1" com um script PowerShell que estabelece uma conexão TCP com o endereço IP da VPN do usuário na porta 9001. Isso permitirá a execução remota de comandos PowerShell na máquina-alvo.

9- Em seguida, o exploit inicia um servidor web na porta disponível para disponibilizar o arquivo "shell.ps1" para download na máquina-alvo.

10- Ele gera dois payloads diferentes para serem usados em uma injeção de comando SSRF. O primeiro payload é usado para fazer com que o servidor web na máquina-alvo baixe o arquivo "shell.ps1" e o salve em "E:\xampp\htdocs\internal\shell.ps1". O segundo payload é usado para executar o script "shell.ps1" na máquina-alvo.

11- Após aguardar um breve período, o exploit envia a requisição contendo o segundo payload para a URL de injeção de comando "http://internal.ironcorp.me:11025/name.php?name=Equinox|", o que resultará na execução do script "shell.ps1" na máquina-alvo.

