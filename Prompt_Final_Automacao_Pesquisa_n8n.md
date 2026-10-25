# Desafio Criativo DIO — Planejando Automações com n8n Usando Bons Prompts

## Projeto: Organização automatizada de arquivos de pesquisa acadêmica

### Prompt final

Atue como um especialista em **n8n**, integração de serviços Google e planejamento de automações para pesquisa acadêmica.

**Objetivo da automação**

Planeje uma automação no n8n para identificar novos arquivos adicionados a uma pasta específica do Google Drive, registrar automaticamente suas informações em uma planilha do Google Sheets e enviar uma notificação por e-mail ao responsável pela pesquisa.

**Público**

Pesquisadores, estudantes de pós-graduação e profissionais que trabalham com coleta, organização e análise de dados.

**Ferramentas envolvidas**

- **n8n:** coordenação e execução do workflow.
- **Google Drive:** identificação de novos arquivos em uma pasta de pesquisa.
- **Google Sheets:** registro organizado dos metadados dos arquivos.
- **Gmail:** notificação por e-mail ao responsável.

**Fluxo desejado**

1. Monitorar uma pasta previamente definida no Google Drive para detectar novos arquivos adicionados.
2. Ao identificar um arquivo, coletar seu identificador único no Drive, nome, formato, data e hora de detecção e link de acesso. Se a data de criação estiver disponível, registrá-la separadamente da data de detecção.
3. Verificar se o item é um arquivo (não uma pasta) e se seu formato é permitido.
4. Consultar a planilha do Google Sheets pelo identificador único do arquivo para verificar se já existe um registro.
5. Se for um arquivo válido e ainda não registrado, inserir uma nova linha com os campos: ID do arquivo, nome, formato, data/hora de detecção, data de criação (se disponível), link e status da notificação.
6. Somente depois de confirmar o registro, enviar um e-mail ao responsável informando o nome, formato, data de detecção e link do arquivo recebido.
7. Atualizar o status da notificação na planilha para indicar envio bem-sucedido ou pendência e manter informações de falhas para acompanhamento.

**Regras e restrições**

- Monitorar apenas a pasta de pesquisa configurada.
- Aceitar somente arquivos nos formatos **PDF, CSV, XLSX e DOCX**; ignorar pastas e demais formatos.
- Evitar duplicidades utilizando o **ID único do Google Drive**, não apenas o nome do arquivo.
- Não registrar nem notificar novamente arquivos já presentes na planilha.
- Não enviar o e-mail antes da confirmação de que o registro foi salvo com sucesso.
- Se houver falha no Gmail após o registro, preservar a linha já criada e marcar a notificação como **PENDENTE** para permitir tratamento posterior sem duplicar o registro.
- Se Google Drive ou Google Sheets apresentarem erro, registrar a falha e impedir o envio indevido de notificações.
- Respeitar as permissões de acesso; não tornar arquivos privados públicos automaticamente e utilizar apenas as credenciais necessárias.
- Considerar possíveis limitações da frequência de verificação do gatilho utilizado no n8n.

**O que espero da sua resposta**

1. Explique quais **nós do n8n** devem ser usados em cada etapa (por exemplo, Google Drive Trigger, Edit Fields/Set, IF, Google Sheets e Gmail), sua função e a ordem das conexões.
2. Descreva as **condições de validação e os caminhos de decisão**, incluindo arquivos aceitos, arquivos ignorados, registros duplicados e erros.
3. Indique os **campos e a estrutura recomendada da planilha**, com um exemplo fictício de linha registrada.
4. Mostre como configurar, em termos gerais, as **credenciais e os parâmetros** necessários, sem solicitar senhas ou tokens no texto.
5. Apresente um **exemplo de assunto e corpo do e-mail** de notificação.
6. Forneça um **roteiro de testes** para validar arquivo novo, formato não permitido, arquivo duplicado e falha no envio de e-mail antes de ativar o fluxo.
7. Diferencie claramente o que é **planejamento proposto** do que exigiria configuração e testes reais no n8n. Não afirme que a automação já foi executada.

Organize a resposta em etapas claras e acessíveis a uma pessoa que está aprendendo a criar workflows no n8n.

---

### Sobre a entrega

Este arquivo contém o **prompt de planejamento** elaborado como atividade do Desafio Criativo da DIO. Ele não representa um workflow já implementado ou testado.
