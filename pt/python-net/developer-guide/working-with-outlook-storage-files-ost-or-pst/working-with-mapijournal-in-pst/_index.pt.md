---
title: "Trabalhando com MapiJournal em PST"
url: /pt/python-net/trabalhando-com-mapijournal-em-pst/
weight: 70
type: docs
---
  
## **Adicionando MapiJournal ao PST**  
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiJournal à subpasta Journal de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiJournal a um PST:  
  
1. Crie um objeto MapiJournal  
1. Defina as propriedades do MapiJournal usando um construtor e métodos.  
1. Crie um PST usando o método PersonalStorage.create().  
1. Crie uma pasta pré-definida (Journals) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método add_mapi_message_item().  
  
O seguinte trecho de código mostra como criar um MapiJournal e, em seguida, adicioná-lo à pasta de diário de um arquivo PST recém-criado.  
  
  
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}  
## **Adicionando Anexos ao MapiJournal**  
O seguinte trecho de código mostra como adicionar anexos ao MapiJournal.  
  
```py  
import os  
from datetime import datetime, timedelta  
from aspose.email.mapi import MapiJournal  
  
data_dir = "caminho_para_diretorio_de_dados"  
attach_file_names = [os.path.join(data_dir, "Desert.jpg"), os.path.join(data_dir, "download.png")]  
  
journal = MapiJournal("testJournal", "Este é um diário de teste", "Chamada telefônica", "Chamada telefônica")  
journal.start_time = datetime.now()  
journal.end_time = journal.start_time + timedelta(hours=1)  
journal.companies = ["empresa 1", "empresa 2", "empresa 3"]  
  
for attach in attach_file_names:  
    journal.attachments.append(attach, open(attach, 'rb').read())  
  
journal.save(os.path.join(data_dir, "AddAttachmentsToMapiJournal_out.msg"))  
```  