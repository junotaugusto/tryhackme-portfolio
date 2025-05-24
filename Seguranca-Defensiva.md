# DEFENSIVE SECURITY INTRO

## INTRODUÇÃO

No módulo anterior, aprendemos sobre **segurança ofensiva (offensive security)**, que tem como objetivo identificar e explorar vulnerabilidades nos sistemas para aprimorar as medidas de segurança.

➡ A ideia da segurança ofensiva é “pensar como o atacante” para descobrir falhas antes que os criminosos as encontrem. Envolve simulações de ataques controlados, como *pen tests*.

Isso inclui:

- Explorar erros de software
- Aproveitar configurações inseguras
- Tirar vantagem de políticas de controle de acesso mal aplicadas

➡ **Políticas de controle de acesso** são regras que determinam quem pode acessar o quê.

Red teams e testadores de penetração (**penetration testers**) são especialistas nessas técnicas ofensivas.

➡ Red teams simulam ataques reais para testar a defesa da organização.  
➡ Pen testers fazem análises mais pontuais e com escopo definido.

---

## SEGURANÇA DEFENSIVA

A **segurança defensiva (defensive security)** foca em:

- **Prevenir** que invasões aconteçam
- **Detectar e responder** a invasões que ocorrem

➡ O objetivo é mitigar os danos o mais rápido possível.

**Blue teams** fazem parte da segurança defensiva.

➡ Eles monitoram, analisam e reagem a ameaças reais.

---

## Tarefas da Segurança Defensiva

1. **Conscientização dos usuários**
   - Treinar usuários sobre segurança
   - Ensinar boas práticas, como não clicar em links suspeitos

2. **Documentação e gerenciamento de ativos**
   - Conhecer todos os sistemas e dispositivos que precisam ser protegidos

3. **Atualizações e correções**
   - Manter todos os sistemas atualizados para evitar exploração de falhas conhecidas

4. **Configuração de dispositivos de segurança preventiva**
   - **Firewalls**: Controlam o tráfego de entrada e saída
   - **IPS (Intrusion Prevention System)**: Bloqueia tráfego malicioso automaticamente

5. **Logging e monitoramento**
   - Detectar comportamentos anômalos na rede
   - Ex: Dispositivos não autorizados ou tráfego incomum fora do expediente

---

## Tópicos Relacionados

- **SOC (Security Operations Center)**
- **Threat Intelligence (Inteligência de Ameaças)**
- **DFIR (Digital Forensics and Incident Response)**
- **Análise de Malware**

---

## CENTRO DE OPERAÇÕES DE SEGURANÇA (SOC)

O **SOC** monitora redes e sistemas 24/7 para detectar ameaças.

Principais áreas de interesse:

- **Vulnerabilidades**
- **Violações de política**
- **Atividade não autorizada**
- **Intrusões na rede**

➡ Detecção rápida é essencial para minimizar danos.

---

## INTELIGÊNCIA DE AMEAÇAS

A **Threat Intelligence** coleta e analisa informações sobre possíveis adversários.

Adversários incluem:

- Grupos patrocinados por governos
- Grupos de ransomware

Processo:

1. **Coleta**: Logs internos, fóruns públicos
2. **Processamento**: Estruturação dos dados
3. **Análise**: Compreender os atacantes e gerar recomendações

➡ Ajuda a antecipar ataques e orientar defesas com base em ameaças reais.

---

## FORENSE DIGITAL

A **forense digital** investiga crimes cibernéticos e analisa evidências digitais.

Áreas de foco:

- **Sistema de arquivos**: Programas, arquivos criados/excluídos
- **Memória**: Ataques em execução na RAM
- **Logs do sistema**: Atividades registradas pelos sistemas
- **Logs da rede**: Tráfego suspeito ou malicioso

---

## RESPOSTA A INCIDENTES

**Incidente**: Qualquer evento que possa comprometer a segurança (ex: ataque, má configuração, violação de política)

Exemplos:

- Rede indisponível
- Defacing de site
- Roubo de dados

### Fases da Resposta a Incidentes:

1. **Preparação**
2. **Detecção e Análise**
3. **Contenção, Erradicação e Recuperação**
4. **Atividade Pós-Incidente**

➡ Reduzir danos e restaurar rapidamente os sistemas.

---

## ANÁLISE DE MALWARE

**Malware (malicious software)** inclui:

- **Vírus**: Se anexam a outros programas e se espalham
- **Trojan Horse**: Disfarçado como programa legítimo
- **Ransomware**: Criptografa arquivos e exige resgate

### Tipos de Análise:

- **Estática**: Sem executar o malware, exige conhecimento em assembly
- **Dinâmica**: Executa o malware em ambiente controlado para observar o comportamento

➡ Compreender o malware é essencial para se proteger dele.

---
