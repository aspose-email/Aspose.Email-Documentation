---
title: "Carregando e Salvando Mensagens"
url: /pt/python-net/loading-and-saving-message/
weight: 30
type: docs
---


## **Detectando Formatos de Arquivo**
A API Aspose.Email fornece a capacidade de detectar o formato de arquivo da mensagem fornecida. O método DetectFileFormat da classe FileFormatUtil pode ser usado para isso. As seguintes classes e métodos podem ser utilizados para detectar o formato de arquivo carregado.

- Enum [FileFormatType](https://reference.aspose.com/email/python-net/aspose.email/fileformattype/)
- Classe [FileFormatInfo](https://reference.aspose.com/email/python-net/aspose.email/fileformatinfo/)
- Classe [FileFormatUtil](https://reference.aspose.com/email/python-net/aspose.email.tools/fileformatutil/)
- Método detect_file_format(stream)
- Método detect_file_format(file_path)

O seguinte trecho de código mostra como detectar formatos de arquivos.

```py
from aspose.email.tools import FileFormatUtil

# Detectar o formato do arquivo e obter o formato carregado detectado
info = FileFormatUtil.detect_file_format(data_dir + "message.msg")
print("O formato da mensagem é: " + str(info.file_format_type))
```
## **Carregando uma Mensagem com Opções de Carregamento**
O seguinte trecho de código mostra como carregar uma mensagem com opções de carregamento.

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions

# Carregar arquivos Eml, html, mhtml, msg e dat
mail_message = MailMessage.load(data_dir + "message.eml", EmlLoadOptions())
MailMessage.load(data_dir + "description.html", HtmlLoadOptions())
MailMessage.load(data_dir + "message.mhtml", MhtmlLoadOptions())
MailMessage.load(data_dir + "message.msg", MsgLoadOptions())

# Carregando com opções personalizadas
eml_load_options = EmlLoadOptions()
eml_load_options.preferred_text_encoding = "utf-8"
eml_load_options.preserve_tnef_attachments = True

MailMessage.load(data_dir + "description.html", eml_load_options)

html_load_options = HtmlLoadOptions()
html_load_options.preferred_text_encoding = "utf-8"
html_load_options.should_add_plain_text_view = True
html_load_options.path_to_resources = data_dir

MailMessage.load(data_dir + "description.html", html_load_options)
```
### **Preservando o Formato da Mensagem Incorporada durante o Carregamento**

```py
from aspose.email import MailMessage, EmlLoadOptions, HtmlLoadOptions, MhtmlLoadOptions, MsgLoadOptions
from aspose.email.tools import FileFormatUtil

eml_load_options = EmlLoadOptions()
eml_load_options.preserve_embedded_message_format = True

mail = MailMessage.load(data_dir + "message.eml", eml_load_options)

file_format = FileFormatUtil.detect_file_format(mail.attachments[0].content_stream).file_format_type

print("Formato do arquivo da mensagem incorporada: " + str(file_format))
```
## **Salvando e Convertendo Mensagens**
Aspose.Email torna fácil converter qualquer tipo de mensagem para outro formato. Para demonstrar essa funcionalidade, o código neste artigo carrega três tipos de mensagens do disco e as salva de volta em outros formatos. A classe base [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/) e as classes [EmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/emlsaveoptions/), [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/), [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/), [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) para configurações adicionais ao salvar [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) podem ser usadas para salvar mensagens em outros formatos. O artigo mostra como usar essas classes para salvar um e-mail de exemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
### **Carregando EML e Salvando como EML**
O seguinte trecho de código mostra como carregar uma mensagem EML e salvá-la no disco no mesmo formato.

```py
from aspose.email import MailMessage, SaveOptions

# Inicializar e carregar um arquivo EML existente especificando o MessageFormat
mail_message = MailMessage.load(data_dir + "message.eml")

mail_message.save(data_dir + "LoadAndSaveFileAsEML_out.eml", SaveOptions.default_eml)
```
### **Carregando EML e Salvando como EML Preservando os Limites Originais**
O seguinte trecho de código mostra como carregar EML e salvar como EML preservando os limites originais.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType

mail_message = MailMessage.load(data_dir + "message.eml")

# Salvar como eml com limites originais preservados
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)

mail_message.save(data_dir + "PreserveOriginalBoundaries_out.eml", eml_save_options)
```
### **Salvando como EML Preservando Anexos TNEF**
O seguinte trecho de código mostra como salvar como EML preservando anexos TNEF.

```py
from aspose.email import MailMessage, EmlSaveOptions, MailMessageSaveType, FileCompatibilityMode

mail_message = MailMessage.load(data_dir + "message.eml")

# Salvar como eml com anexo preservado
eml_save_options = EmlSaveOptions(MailMessageSaveType.eml_format)
eml_save_options.file_compatibility_mode = FileCompatibilityMode.PRESERVE_TNEF_ATTACHMENTS

mail_message.save(data_dir + "PreserveTNEFAttachment_out.eml", eml_save_options)
```
### **Carregando EML, Salvando para MSG**
O seguinte trecho de código mostra como carregar uma mensagem EML e convertê-la para MSG usando a opção apropriada da [SaveOptions](https://reference.aspose.com/email/python-net/aspose.email/saveoptions/).

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar e carregar um arquivo EML existente especificando o MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Salvar a mensagem de email no disco no formato ASCII e no formato Unicode
eml.save(data_dir + "AnEmail_out.msg", SaveOptions.default_msg_unicode)
```
### **Salvando como MSG com Datas Preservadas**
A classe [MsgSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/msgsaveoptions/) permite que você salve a mensagem fonte como um arquivo de Mensagem do Outlook (MSG) preservando datas. O seguinte trecho de código mostra como salvar como MSG com datas preservadas.

```py
from aspose.email import MailMessage, MsgSaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar e carregar um arquivo EML existente especificando o MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

# Salvar como msg com datas preservadas
msg_save_options = MsgSaveOptions(MailMessageSaveType.outlook_message_format_unicode)
msg_save_options.preserve_original_dates = True

eml.save(data_dir + "outTest_out.msg", msg_save_options)
```
### **Salvando MailMessage como MHTML**
Diferentes opções de MHTML podem ser usadas para obter os resultados desejados. O seguinte trecho de código mostra como carregar uma mensagem EML em [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) e convertê-la para MHTML.

```py
from aspose.email import MailMessage, SaveOptions, MailMessageSaveType, FileCompatibilityMode

# Inicializar e carregar um arquivo EML existente especificando o MessageFormat
eml = MailMessage.load(data_dir + "message.eml")

eml.save(data_dir + "AnEmail_out.mhtml", SaveOptions.default_mhtml)
```
#### **Convertendo para MHTML com Configurações Opcionais**

A classe [MhtSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtsaveoptions/) fornece opções adicionais para salvar mensagens de email em formato MHTML. O enumerador [MhtFormatOptions](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) torna possível escrever informações adicionais da mensagem de email na saída MHTML. Os seguintes campos adicionais podem ser escritos:

 - NONE - Nenhuma configuração específica é especificada.
 - WRITE_HEADER - Indica que informações do cabeçalho devem ser escritas.
 - WRITE_OUTLINE_ATTACHMENTS - Indica que anexos de contorno devem ser escritos.
 - WRITE_COMPLETE_EMAIL_ADDRESS - Indica que o endereço de email completo deve ser escrito em todos os cabeçalhos de email.
 - NO_ENCODE_CHARACTERS - Indica que nenhuma codificação de transferência de caracteres deve ser usada.
 - HIDE_EXTRA_PRINT_HEADER - Indica que o Cabeçalho da Página ficará invisível.
 - WRITE_COMPLETE_TO_EMAIL_ADDRESS - Indica que o endereço de email completo deve ser escrito no cabeçalho ‘Para’.
 - WRITE_COMPLETE_FROM_EMAIL_ADDRESS - Indica que o endereço de email completo deve ser escrito no cabeçalho ‘De’.
 - WRITE_COMPLETE_CC_EMAIL_ADDRESS - Indica que o endereço de email completo deve ser escrito no cabeçalho ‘Cc’.
 - WRITE_COMPLETE_BCC_EMAIL_ADDRESS - Indica que o endereço de email completo deve ser escrito no cabeçalho ‘Bcc’.
 - RENDER_CALENDAR_EVENT - Indica que o texto do evento do calendário deve ser escrito na saída mhtml.
 - SKIP_BYTE_ORDER_MARK_IN_BODY - Indica que os bytes do Byte Order Mark(BOM) devem ser escritos no corpo.
 - RENDER_V_CARD_INFO - Indica que o texto da VCard AlternativeView deve ser escrito na saída mhtml.
 - DISPLAY_AS_OUTLOOK - Indica que o cabeçalho De será exibido como no Outlook.
 - RENDER_TASK_FIELDS - Indica que os campos de Tarefa específicos devem ser escritos na saída mhtml.

O seguinte trecho de código mostra como converter um arquivo eml para MHTML com configurações opcionais.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MailMessageSaveType, FileCompatibilityMode

# Carregar um arquivo EML existente
eml = MailMessage.load(data_dir + "message.eml")

# Salvar como mht com cabeçalho
mht_save_options = MhtSaveOptions()

# Especificar as opções de formatação necessárias
# Aqui estamos especificando para escrever informações de cabeçalho na saída sem escrever cabeçalho de impressão extra
# e os cabeçalhos de saída devem ser exibidos como os cabeçalhos originais na mensagem
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.HIDE_EXTRA_PRINT_HEADER | MhtFormatOptions.DISPLAY_AS_OUTLOOK

# Verificar a codificação do conteúdo do corpo quanto à validade.
mht_save_options.check_body_content_encoding = True

eml.save(data_dir + "outMessage_out.mht", mht_save_options)
```
#### **Renderizando Eventos de Calendário ao Converter para MHTML**
As [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/python-net/aspose.email/mhtformatoptions/) renderiza os eventos do calendário na saída MTHML.
O seguinte trecho de código mostra como renderizar eventos de calendário ao converter para MHTML.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

file_name = "message.msg"

# Carregar o arquivo MSG
msg = MailMessage.load(data_dir + file_name)

# Criar opções de salvamento em MHT
options = MhtSaveOptions()
options.mht_format_options = MhtFormatOptions.WRITE_HEADER | MhtFormatOptions.RENDER_CALENDAR_EVENT

# Salvar a mensagem como MHTML
msg.save(data_dir + "Meeting with Recurring Occurrences.mhtml", options)
```
#### **Exportando Email para MHT sem Imagens Inline**

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode

# Carregar o arquivo EML
eml = MailMessage.load(data_dir + "message.eml")

# Criar opções de salvamento em MHT
mht_save_options = MhtSaveOptions()
mht_save_options.skip_inline_images = True

# Salvar a mensagem como MHTML sem imagens inline
eml.save(data_dir + "EmlToMhtmlWithoutInlineImages_out.mht", mht_save_options)
```
#### **Exportando Email para MHT com Fuso Horário Personalizado**
A classe [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) fornece a propriedade TimeZoneOffset para definir o fuso horário personalizado ao exportar para MHT. O seguinte trecho de código mostra como exportar um email para MHT com fuso horário personalizado.

```py
from aspose.email import MailMessage, MhtSaveOptions, MhtFormatOptions, MhtTemplateName, MailMessageSaveType, FileCompatibilityMode
from datetime import timedelta

# Carregar o arquivo EML
eml = MailMessage.load(data_dir + "message.eml")

# Definir a hora local para a data da mensagem
eml.time_zone_offset = timedelta(hours=-8)

# As datas serão renderizadas pelo fuso horário do sistema local
mht_save_options = MhtSaveOptions()
mht_save_options.mht_format_options = MhtFormatOptions.WRITE_HEADER
eml.save(data_dir + "ExportEmailToMHTWithCustomTimezone_out.mhtml", mht_save_options)
```
### **Exportando Email para EML**
O seguinte trecho de código mostra como exportar um email para eml.

```py
from aspose.email import MailMessage, SaveOptions

# Carregar o arquivo EML
msg = MailMessage.load(data_dir + "message.eml")

# Salvar a mensagem de email como EML
msg.save(data_dir + "ExporttoEml_out.eml", SaveOptions.default_eml)
```
### **Salvando Mensagem como HTML**
A classe [HtmlSaveOptions](https://reference.aspose.com/email/python-net/aspose.email/htmlsaveoptions/) permite exportar o corpo da mensagem para HTML com a opção de salvar recursos incorporados. O seguinte trecho de código mostra como salvar a mensagem como HTML, onde o valor padrão de embed_resources é verdadeiro.

```py
from aspose.email import MailMessage, SaveOptions, HtmlSaveOptions, HtmlFormatOptions

# Carregar o arquivo EML
message = MailMessage.load(data_dir + "message.eml")

# Salvar a mensagem de email como HTML
message.save(data_dir + "SaveAsHTML_out.html", SaveOptions.default_html)

# OU

eml = MailMessage.load(data_dir + "message.eml")
options = HtmlSaveOptions()
options.embed_resources = False
options.html_format_options = (
    HtmlFormatOptions.WRITE_HEADER
    | HtmlFormatOptions.WRITE_COMPLETE_EMAIL_ADDRESS
)  # salvar os cabeçalhos da mensagem para o HTML de saída usando as opções de formatação
eml.save(data_dir + "SaveAsHTML1_out.html", options)
```

### **Salvando Mensagem como Arquivo de Modelo do Outlook (.oft)**
O seguinte trecho de código mostra como salvar a mensagem como arquivo de modelo do outlook (.oft).

```py
from aspose.email import MailMessage, SaveOptions

eml = MailMessage("test@from.to", "test@to.to", "assunto do modelo", "Corpo do modelo")

oft_eml_file_name = "EmlAsOft_out.oft"
options = SaveOptions.default_msg_unicode
options.save_as_template = True
eml.save(data_dir + oft_eml_file_name, options)
```