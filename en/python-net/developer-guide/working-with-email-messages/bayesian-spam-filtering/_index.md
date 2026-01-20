---
title: Using Bayesian Spam Filtering to Classify Emails in Python
ArticleTitle: Using Bayesian Spam Filtering to Classify Emails in Python
type: docs
weight: 70
url: /python-net/bayesian-spam-filtering/
---


## **Using Bayesian Spam Filtering**

Aspose.Email provides email filtering functionality using a Bayesian spam analyzer. It provides the [SpamAnalyzer](https://reference.aspose.com/email/python-net/aspose.email.antispam/spamanalyzer/) class for this purpose. This article shows how to train the filter to distinguish between spam and regular email based on a word database.

1. Specify the folder paths for the ham emails (ham_folder), spam emails (spam_folder), test emails (test_folder), and the database file (database_file) for the spam filter.
2. Define the helper function `print_result` to print whether a message is classified as spam or not based on the calculated spam probability.
3. Create Spam Analyzer using the database file, train it with emails from ham_folder (not spam) and spam_folder (spam), then save the trained database.
4. Load .eml files from 'test_folder', analyze each with SpamAnalyzer.test to get spam probability, and print the email subject and classification using 'print_result'.


```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode
from aspose.email.antispam import SpamAnalyzer
import os

ham_folder = "/hamFolder"
spam_folder = "/Spam"
test_folder = data_dir
database_file = "SpamFilterDatabase.txt"

def print_result(probability):
    if probability >= 0.5:
        print("The message is classified as spam.")
    else:
        print("The message is classified as not spam.")
    print("Spam Probability: " + str(probability))
    print()

def teach_and_create_database(ham_folder, spam_folder, database_file):
    analyzer = SpamAnalyzer(database_file)
    analyzer.teach_from_directory(ham_folder, True)
    analyzer.teach_from_directory(spam_folder, False)
    analyzer.save_database()

teach_and_create_database(ham_folder, spam_folder, database_file)

test_files = [f for f in os.listdir(test_folder) if f.endswith(".eml")]
analyzer = SpamAnalyzer(database_file)

for file in test_files:
    file_path = os.path.join(test_folder, file)
    msg = MailMessage.load(file_path)
    print(msg.subject)
    probability = analyzer.test(msg)
    print_result(probability)
```
