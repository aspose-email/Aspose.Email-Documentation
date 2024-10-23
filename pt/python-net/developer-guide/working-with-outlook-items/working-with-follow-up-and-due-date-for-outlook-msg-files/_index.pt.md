---
title: "Trabalhando com Sinalização de Acompanhamento e Data de Vencimento para Arquivos MSG do Outlook"
url: /pt/python-net/trabalhando-com-sinalizacao-de-acompanhamento-e-data-de-vencimento-para-arquivos-msg-do-outlook/
weight: 50
type: docs
---


Uma bandeira de acompanhamento marca uma mensagem de email para algum tipo de ação. O Microsoft Outlook permite que os usuários sinalizem mensagens e, na configuração da bandeira, atribuam uma data de vencimento para o acompanhamento. O Microsoft Outlook envia um lembrete ao destinatário para lembrar que devem acompanhar o email. Sinalizar emails e definir datas de vencimento programaticamente permite que os desenvolvedores de software automatizem certos tipos de emails e ajudem os destinatários a lembrar-se de tomar uma ação. Por exemplo, pode ser usado para enviar mensagens mensais a uma equipe de vendas para lembrá-los de completar seus relatórios; ou para enviar uma mensagem a todos os funcionários para lembrá-los de uma reunião da empresa. Aspose.Email para .NET suporta a configuração de sinalização de acompanhamento e data de vencimento para os objetos MapiMessage usando FollowUpManager e FollowUpOptions. Existem várias variantes nas quais a bandeira de acompanhamento pode ser configurada em uma mensagem. Todas elas são usadas no exemplo de código abaixo:

1. Definir uma bandeira de acompanhamento para uma mensagem
1. Adicionar uma data de vencimento e uma data de lembrete a uma mensagem
1. Adicionar uma bandeira à mensagem de um destinatário.
1. Marcar como completo.
1. Remover bandeira.
1. Ler opções de acompanhamento.

## **Configurando uma bandeira de Acompanhamento**

O seguinte snippet de código mostra como configurar uma bandeira de Acompanhamento.

```py
import aspose.email as ae
from datetime import datetime, timedelta

# Criar uma nova MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Esta mensagem testará se as opções de acompanhamento podem ser adicionadas a uma nova mensagem MAPI."

# Converter MailMessage para MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Definir opções de acompanhamento
dt_start_date = datetime(2013, 5, 23, 14, 40, 0)
dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)
dt_due_date = dt_reminder_date + timedelta(days=1)

options = ae.mapi.FollowUpOptions("Acompanhar", dt_start_date, dt_due_date, dt_reminder_date)

# Definir opções de acompanhamento para o MapiMessage
ae.mapi.FollowUpManager.set_options(mapi, options)

# Salvar o MapiMessage
mapi.save("SetFollowUpFlag_out.msg")
```

## **Configurando Acompanhamento para Destinatários**
O seguinte snippet de código mostra como configurar Acompanhamento para destinatários.

```py
import aspose.email as ae
from datetime import datetime

# Criar uma nova MailMessage
mail_msg = ae.MailMessage()
mail_msg.from_address = ae.MailAddress("from@domain.com")
mail_msg.to.append(ae.MailAddress("to@domain.com"))
mail_msg.body = "Esta mensagem testará se as opções de acompanhamento podem ser adicionadas a uma nova mensagem MAPI."

# Converter MailMessage para MapiMessage
mapi = ae.mapi.MapiMessage.from_mail_message(mail_msg)

# Marcar a mensagem como rascunho
mapi.set_message_flags(ae.mapi.MapiMessageFlags.UNSENT)

dt_reminder_date = datetime(2013, 5, 23, 16, 40, 0)

# Adicionar a bandeira de acompanhamento para destinatários
ae.mapi.FollowUpManager.set_flag_for_recipients(mapi, "Acompanhar", dt_reminder_date)

# Salvar o MapiMessage
mapi.save("SetFollowUpForRecipients_out.msg")
```

## **Marcando uma bandeira de Acompanhamento como Completa**

O seguinte snippet de código mostra como marcar a bandeira de Acompanhamento como completa.

```py
import aspose.email as ae

# Carregar o MapiMessage do arquivo
mapi_message = ae.mapi.MapiMessage.load("Message.msg")

# Marcar a mensagem como completa
ae.mapi.FollowUpManager.mark_as_completed(mapi_message)

# Salvar o MapiMessage atualizado
mapi_message.save("MarkedCompleted_out.msg")
```
## **Removendo uma bandeira de Acompanhamento**
O seguinte snippet de código mostra como remover a bandeira de Acompanhamento.

```py
import aspose.email as ae

# Carregar o MapiMessage do arquivo
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Limpar a bandeira de acompanhamento
ae.mapi.FollowUpManager.clear_flag(mapi_message)

# Salvar o MapiMessage atualizado
mapi_message.save("RemoveFollowUpflag_out.msg")
```

## **Ler opções de bandeira de acompanhamento para uma mensagem**

O seguinte snippet de código mostra como ler as opções de bandeira de acompanhamento para uma mensagem.

```py
import aspose.email as ae

# Carregar o MapiMessage do arquivo
mapi_message = ae.mapi.MapiMessage.load("message.msg")

# Obter as opções de acompanhamento
options = ae.mapi.FollowUpManager.get_options(mapi_message)
```