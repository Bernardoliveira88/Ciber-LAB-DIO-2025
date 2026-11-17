# Ciber-LAB-DIO-2025
Repositório para bootcamp dio 2025

# 🛡️ Simulação de Ataques de Força Bruta e Análise de Vulnerabilidades com Kali Linux e Medusa



Relato prático e documentação técnica desenvolvidos durante o desafio de Cibersegurança da **DIO**. O objetivo deste laboratório foi configurar um ambiente controlado entre **Kali Linux** e **Metasploitable 2** para compreender, na prática, como falhas de configuração e credenciais fracas expõem serviços de rede e aplicações web, além de consolidar medidas de mitigação.



---



## 🎯 Visão Geral e Percepções do Laboratório



Mais do que apenas executar comandos automatizados, este projeto me permitiu enxergar o **ciclo completo de uma auditoria de credenciais**: desde o mapeamento inicial da superfície de ataque até a análise de como os dados trafegam no back-end de uma aplicação e como pequenas falhas de configuração comprometem um ambiente corporativo inteiro.



---



## 🔍 1. Reconhecimento e Mapeamento de Superfície (`Nmap`)



Antes de qualquer tentativa de exploração, utilizei o **Nmap** para nortear a análise e reconhecer o ambiente criado pelo Metasploitable 2.



* **Na prática:** A varredura permitiu identificar o endereço IP do alvo na rede interna e listar quais portas estavam abertas e quais serviços rodavam por trás delas (como FTP, HTTP e SMB).

* **Minha percepção:** Atacar sem reconhecimento é agir no escuro. O `nmap` funciona como uma bússola: ele mostra exatamente onde está a superfície de exposição e evita desperdício de tempo em serviços inativos.



```bash

# Exemplo de varredura utilizada para identificar portas e versões de serviços

nmap -sV [IP_DO_METASPLOITABLE]



# Criação rápida das listas de usuários e senhas para validação

echo -e "admin\nmsfadmin\nuser\ntest" > user.txt

echo -e "123456\npassword\nmsfadmin\nadmin" > pass.txt



# Exemplo de execução com Medusa direcionada ao alvo

medusa -h [IP_DO_METASPLOITABLE] -U user.txt -P pass.txt -M [MODULO_SERVICO]



├── README.md     # Documentação e relato técnico do laboratório

├── wordlists/     # Listas customizadas (user.txt e pass.txt)

└── images/      # Capturas de tela das varreduras e execuções
