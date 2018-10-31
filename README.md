# Welcome!

In this repository you will find the materials and challenges for the "Bilder, Text und Sprache mit Azure AI verstehen und durchsuchbar machen" bootcamp.

The associated bootcamp teaches you how to deploy and use the following two Azure technologies:

* [Azure Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services/)
* [Azure Search](https://azure.microsoft.com/en-us/services/search/) (including Cognitive Search)

The bootcamp is organized as five independent challenges, each one containing a high-level description and a few hints in case you get stuck.

# Challenges

You can solve these challenges in a programming language of your choice (some even in `curl` :hammer:). For sake of convenience, we are providing hints in `Python`, which you can easily (and for free) run in [Azure Notebooks](https://notebooks.azure.com). SDK Support for `C#` or `.NET Core` is available for most challenges. You can find code examples in the Azure documentation for the associated services.

## Challenge 1a (Azure Search)

**Goal:** Deploy an Azure Search instance and index a structured data set 

1. Deploy an [Azure Search](https://docs.microsoft.com/en-us/azure/search/search-create-service-portal) instance
1. Index the structured data set from [here](TODO)

**Questions:** 

1. TODO QUESTION 1
1. TODO QUESTION 2
1. TODO QUESTION 3

:see_no_evil: [Hints for challenge 1a](hints/challenge_01a.md)

## Challenge 1b (Azure Cognitive Search)

**Goal:** Index an unstructured data set

1. Reuse the Azure Search index from before but add an new index
1. Index an existing data set coming from `Azure Blob` (data set can be downloaded [here](TODO))

**Questions:** 

1. TODO QUESTION 1
1. TODO QUESTION 2
1. TODO QUESTION 3

:see_no_evil: [Hints for challenge 1b](hints/challenge_01b.md)

## Challenge 2a (Azure Cognitive Services - Vision)

**Goal:** Leverage OCR to make a hand-written or printed text document (image) machine-readable

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Convert hand-written text from an image into text - Test data: [1](TOOD), [2](TOOD)
1. Convert printed text from an image into text - Test data: [1](TOOD), [2](TOOD)

**Questions:** 

1. TODO QUESTION 1
1. TODO QUESTION 2
1. TODO QUESTION 3

:see_no_evil: [Hints for challenge 2a](hints/challenge_02a.md)

## Challenge 2b (Azure Cognitive Services - Custom Vision)

**Goal:** TODO

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Convert written text from an image into speech (German or English) - Test data: [1](TOOD), [2](TOOD)
1. Use [Custom Vision](https://customvision.ai) to detect parked cars in drone images

**Questions:** 

1. TODO QUESTION 1
1. TODO QUESTION 2
1. TODO QUESTION 3

:see_no_evil: [Hints for challenge 2b](hints/challenge_02b.md)

## Challenge 3 (Azure Cognitive Services - Speech)

**Goal:** Leverage Speech-to-Text and Text-to-Speech

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Convert written text into speech (German or English)
1. Convert speech into written text (German or English)

Now that we have converted a user's speech input into text, we'll try to determine the intent of that text in the next challenge.

**Questions:** 

1. What happens if you transcribe a long audio file with the speech-to-text API (>15s)?
1. What happens if you select the wrong language in the text-to-speech API? How could you solve this problem?

:see_no_evil: [Hints for challenge 3](hints/challenge_03.md)

## Challenge 4 (Azure Cognitive Services - Language)

**Goal:** Make your application understand the meaning of text

In the language of your choice (Python solution is provided), write two small scripts or apps that

1. Translate the input text into English or German
1. Detect the intent and entities in text (German or English)

Data:

```
TODO
```

[Hints for challenge 4](hints/challenge_04.md)

# Challenge 5 (Azure Cognitive Services - Search)

**Goal:** Write a script for auto-suggestion of text

1. Leverage Bing Autosuggest to make predictions on how to continue a half written sentence

**Questions:** 

1. TODO QUESTION 1
1. TODO QUESTION 2
1. TODO QUESTION 3

[Hints for challenge 5](hints/challenge_05.md)
