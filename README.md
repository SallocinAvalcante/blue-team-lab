Mini SOC Lab (Zabbix + Splunk + Snort)
Este projeto demonstra um laboratório simples de Security Operations Center (SOC) rodando em um servidor EC2. O objetivo é mostrar como integrar ferramentas de monitoramento, análise de logs e detecção de intrusão em um ambiente real.

Ferramentas utilizadas
Zabbix → Monitoramento de CPU, memória e disponibilidade do servidor.

Splunk → Coleta e análise de logs do sistema (ex.: tentativas de login falhas).

Snort → IDS para detectar tráfego suspeito (ex.: ICMP ping).

Estrutura do repositório
mini-soc-lab/ ├── README.md ├── docker-compose.yml ├── configs/ │ └── local.rules └── screenshots/ ├── zabbix-dashboard.png ├── zabbix-trigger.png ├── splunk-query.png └── snort-alert.png

Passo a passo resumido
1. Preparação
Instalar Docker e Docker Compose.

Criar diretório soc-lab com subpastas configs e screenshots.

2. Zabbix
Subir containers via docker-compose.

Configurar trigger simples (CPU > 80%).

Evidência: print do dashboard e trigger disparado.

3. Splunk
Subir container via docker-compose.

Configurar coleta de /var/log/auth.log e /var/log/syslog.

Rodar query: index=main "Failed password"

Evidência: print da query mostrando tentativas de login falhas.

4. Snort
Instalar no host via apt.

Criar regra em configs/local.rules para detectar ICMP ping.

Executar Snort e gerar alerta com ping.

Evidência: print do console mostrando alerta.

Evidências
Adicione aqui os prints que estão na pasta screenshots/:

Zabbix Dashboard

Zabbix Trigger

Splunk Query

Snort Alert

Conclusão
Este laboratório demonstra três pilares de um SOC:

Monitoramento (Zabbix)

Análise de logs (Splunk)

Detecção de intrusão (Snort)

Com isso, é possível identificar problemas de desempenho, falhas de autenticação e tráfego suspeito em tempo real.
