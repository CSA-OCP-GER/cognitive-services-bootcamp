# Welcome!

In this repository you will find the materials and challenges for the "Azure AI - Bilder, Text und Sprache mit Azure AI verstehen und durchsuchbar machen" bootcamp.

The associated bootcamp teaches you how to deploy and use the following two Azure technologies:

* [Azure Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services/)
* [Azure Search](https://azure.microsoft.com/en-us/services/search/) (including Cognitive Search)

The bootcamp is organized as five independent challenges, each one containing a high-level description and a few hints in case you get stuck.

# Challenges

You can solve these challenges in a programming language of your choice (some even in `curl` :hammer:). For sake of convenience, we are providing hints in `Python`, which you can easily (and for free) run in [Azure Notebooks](https://notebooks.azure.com). SDK Support for `C#` or `.NET Core` is available for most challenges. Especially Azure Search features an easy-to-use `.NET SDK`. You can find code examples in the Azure documentation for the associated services.

## Challenge 1 (Azure Search & Cognitive Search)

:triangular_flag_on_post: **Goal:** Deploy an Azure Search instance and index a PDF-based data set 

1. Deploy an [Azure Search](https://docs.microsoft.com/en-us/azure/search/search-create-service-portal) instance
1. Index the unstructured PDF data set from [here](data/search-dataset-pdf.zip) - which document contains the term `Content Moderator`?

:question: **Questions:** 

1. What is an Index? What is an Indexer? What is a Data Source? How do they relate to each other?
1. Why would you want to use replicas? Why would you want more partitions?
1. How would you index `json` documents sitting in Azure Blob?

:triangular_flag_on_post: **Goal:** Index an unstructured data set with Cognitive Search

1. Add another index to the Azure Search instance, but this time enable Cognitive Search
1. Index an existing data set coming from `Azure Blob` (data set can be downloaded [here](data/search-dataset-cognitive.zip)) - which document contains the term `Pin to Dashboard`?

:question: **Questions:** 

1. Given a Machine Learning model that can detect beer glasses images (we'll do that in the next challenge) - how could be leverage this in Azure Search?

:see_no_evil: [Hints for challenge 1](hints/challenge_01.md)

## Challenge 2 (Azure Cognitive Services - Vision & Custom Vision)

:triangular_flag_on_post: **Goal:** Leverage OCR to make a hand-written or printed text document in images machine-readable

In the language of your choice (Python solution is provided), write two small scripts that

1. Convert hand-written text from an image into text - Test data: [1](https://bootcamps.blob.core.windows.net/ml-test-images/ocr_handwritten_1.jpg), [2](https://bootcamps.blob.core.windows.net/ml-test-images/ocr_handwritten_2.jpg)
1. Convert printed text from an image into text - Test data: [1](https://bootcamps.blob.core.windows.net/ml-test-images/ocr_printed_1.jpg), [2](https://bootcamps.blob.core.windows.net/ml-test-images/ocr_printed_2.jpg)

:question: **Questions:** 

1. How well does the OCR service work with German text? How well with English?
1. What happens when the image is not oriented correctly?

:triangular_flag_on_post: **Goal:** Detect beer glasses in images

1. Use [Custom Vision](https://customvision.ai) to detect beer glasses in images - [Image Dataset for training and testing](https://bootcamps.blob.core.windows.net/ml-test-images/beer_glasses.zip)

:question: **Questions:** 

1. What could we do to increase the detection performance?
1. What happens if the beer glasses are really small in the image?

:see_no_evil: [Hints for challenge 2](hints/challenge_02.md)

## Challenge 3 (Azure Cognitive Services - Speech)

:triangular_flag_on_post: **Goal:** Leverage Speech-to-Text and Text-to-Speech

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Convert written text into speech (German or English)
1. Convert speech into written text (German or English)

Now that we have converted a user's speech input into text, we'll try to determine the intent of that text in the next challenge.

:question: **Questions:** 

1. What happens if you transcribe a long audio file with the speech-to-text API (>15s)?
1. What happens if you select the wrong language in the text-to-speech API? How could you solve this problem?

:see_no_evil: [Hints for challenge 3](hints/challenge_03.md)

## Challenge 4 (Azure Cognitive Services - Language)

:triangular_flag_on_post: **Goal:** Make your application understand the meaning of text

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Translate the input text into English or German (using the Text Translator API)
1. Detect the intent and entities in text (German or English) - see examples below (using [luis.ai](https://luis.ai))

Let's use an example where we want to detect a Pizza order from the user. The user should also be able to cancel the order.

LUIS example data:

```
2 Intents: "CreateOrder", "CancelOrder"

Utterances:

(CreateOrder) Ich moechte eine Pizza Salami bestellen 
(CreateOrder) Vier Pizza Hawaii bitte 

(CancelOrder) Bitte Bestellung 123 stornieren
(CancelOrder) Cancel bitte Bestellung 42
(CancelOrder) Ich will Order 933 nicht mehr

(None) Wieviel Uhr ist heute?
(None) Wie ist das Wetter in Berlin?
(None) Bitte Termin fuer Montag einstellen
```

:question: **Questions:** 

1. Why do we need to fill the `None` intent with examples?
1. What is the `Review endpoint utterances` feature in LUIS?

:see_no_evil: [Hints for challenge 4](hints/challenge_04.md)

# Challenge 5 (Azure Cognitive Services - Search)

:triangular_flag_on_post: **Goal:** Write a script for auto-suggestion of text

1. Leverage Bing Autosuggest to make predictions on how to continue a half written sentence

:question: **Questions:** 

1. What other services does Bing Search offer?
1. What does the service in case of a denial-of-service (DoS) attack?

:see_no_evil: [Hints for challenge 5](hints/challenge_05.md)
