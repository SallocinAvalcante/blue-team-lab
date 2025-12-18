# 🛡️ Mini SOC Lab (Zabbix + Splunk + Snort)

Este projeto demonstra um laboratório simples de Security Operations Center (SOC) rodando em um servidor EC2.  
O objetivo é mostrar como integrar ferramentas de monitoramento, análise de logs e detecção de intrusão em um ambiente real.

---

## 📂 Estrutura do Repositório

- blue-team-lab/
  - README.md
  - docker-compose.yml
  - configs/
    - local.rules
  - screenshots/
    - Zabbix/
    - Snort + Splunk/



---

## 🚀 Ferramentas Utilizadas

- **Zabbix** → Monitoramento de CPU, memória e disponibilidade do servidor.  
- **Splunk** → Coleta e análise de logs do sistema (ex.: tentativas de login falhas, em nosso caso eventos simulados em demo.log).  
- **Snort** → IDS para detectar tráfego suspeito (ex.: ICMP ping).  

---

## ⚙️ Passo a Passo Resumido

**Preparação**  
- Instalar Docker e Docker Compose.  
- Criar diretório `soc-lab` com subpastas `configs` e `screenshots`.  

**Zabbix**  
- Subir containers via `docker-compose`.  
- Configurar trigger simples (CPU > 80%).  
- Evidência: prints do dashboard e trigger disparado.  

**Splunk**  
- Subir container via `docker-compose`.  
- Configurar coleta de arquivos customizados (demo.log) via Data Input.  
- Ajustar event break para Every line e timestamp %Y-%m-%d %H:%M:%S. 
- Evidência: prints do Splunk mostrando o container saudável, interface aberta e configuração de Data Input. 

**Snort**  
- Instalar no host via `apt`.  
- Criar regra em `configs/local.rules` para detectar ICMP ping.  
- Executar Snort e gerar alerta com ping.  
- Evidência: print do console mostrando alerta.  

---

## 📸 Evidências

Todas as imagens estão na pasta `screenshots/` e mostram o ambiente funcionando em tempo real.

### 🔹 Zabbix
- ![Subindo Docker](screenshots/Zabbix/Subindo%20Docker.png)
- ![Configuração IP](screenshots/Zabbix/Configura%C3%A7%C3%A3o%20IP%20%20na%20zabbix_agentd.conf.png)
- ![Alteração IP Host](screenshots/Zabbix/Alteração%20IP%20Host%20para%20comunicar%20com%20agente.png)
- ![ZBX Verde](screenshots/Zabbix/ZBX%20verde.png)
- ![Criando Trigger](screenshots/Zabbix/Criando%20Trigger.png)
- ![Trigger Funcionando](screenshots/Zabbix/Trigger%20Funcionando%20no%20Problems.png)
- ![Dashboard Server](screenshots/Zabbix/DashBoard%20server.png)
- ![Latest Data](screenshots/Zabbix/Latest%20Data%20Pos%20Execucao%20Trigger.png)

### 🔹 Snort
- ![Snort ativo](screenshots/Snort%20+%20Splunk/Snort/Snort%20ativo.png)
- ![Snort configurado](screenshots/Snort%20+%20Splunk/Snort/Snort%20configurado%20para%20monitorar.png)
- ![Snort monitorando ping](screenshots/Snort%20+%20Splunk/Snort/Snort%20Monitorando%20ping´s.png)

### 🔹 Splunk
- ![Saída do Docker](screenshots/Snort%20+%20Splunk/Saida%20do%20docker%20adicionando%20splunk%20e%20snort.png)
- ![Splunk Healthy](screenshots/Snort%20+%20Splunk/Splunk/Splunk%20Healthy%20no%20terminal.png)
- ![Splunk aberto](screenshots/Snort%20+%20Splunk/Splunk/Splunk%20aberto.png)
- ![Data Input](screenshots/Snort%20+%20Splunk/Splunk/Data%20Input.png)

---

## 🎯 Conclusão

Este laboratório demonstra três pilares de um SOC:

- **Monitoramento (Zabbix)**  
- **Análise de logs (Splunk)**  
- **Detecção de intrusão (Snort)**  

Com isso, é possível identificar problemas de desempenho, falhas de autenticação e tráfego suspeito em tempo real.
