# snort3

include = 'rules/local.rules',

https://hub.docker.com/repository/docker/joaoprdo/snort3/general
joaoprdo/snort3:latest


Comando para validar config:
snort -T  -c /opt/snort3/etc/snort/snort.lua

Caminho do dir:
/opt/snort3/etc/snort

O arquivo que precisar ajustar as config e colocar os import é o snort.lua

Comando para executar 
snort -c /opt/snort3/etc/snort/snort.lua -i enp0s3 -v


Tem que usar o -A para poder ver os logs de melhor forma:
snort -A alert_full -c /opt/snort3/etc/snort/snort.lua -i enp0s3 -v


Execucao normal:
snort -c /opt/snort3/etc/snort/snort.lua -i enp0s3 -v

mkdir -p /opt/snort3/logs
chmod 755 /opt/snort3/logs



--------------------------------------------------------------------------
-- 7. configure outputs
---------------------------------------------------------------------------

-- event logging
alert_full = { 
    file = true,
    limit = 10
}

-- Para logs rápidos também
alert_fast = { 
    file = '/opt/snort3/logs/alert_fast.txt' 
}

-- packet logging (se quiser capturar pacotes)
log_pcap = { 
    filename = '/opt/snort3/logs/snort.pcap',
    limit = 100
}

-- file logging personalizado
file_log = { 
    filename = '/opt/snort3/logs/file.log'
}

-- configuração do diretório de logs
logdir = '/opt/snort3/logs'
