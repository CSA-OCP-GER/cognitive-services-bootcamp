# Hints for Challenge 3

Create a new `Python 3.6 Notebook` in [Azure Notebooks](https://notebooks.azure.com/). Next, create a `Speech` API Key in the Azure Portal:

![alt text](../images/speech_api_service.png "Speech API Service")

As region, we'll be using `West Europe` in this example. You can find your API key under the service, then `Keys`.

You can use this file [`test.wav`](../data/test.wav) for testing.

## Text-to-Speech

First, we need to request a token from the `Issue Token endpoint` of the Speech API. Each token is valid for 10 minutes, hence we can either reuse it multiple times (to minimize network traffic and latency), or request a new one for each call:

```python
import requests, json
import IPython.display as ipd

api_key = "xxxx" # Enter your API key here

token_url = "https://westeurope.api.cognitive.microsoft.com/sts/v1.0/issuetoken"
headers = {'Ocp-Apim-Subscription-Key': api_key}

response = requests.post(token_url, headers=headers)
token = response.text

print("Token: " + token)
```

Once we have the token, we can form our request for generating speech:

```python
url = "https://westeurope.tts.speech.microsoft.com/cognitiveservices/v1"
headers = {'Authorization': token,
           'Content-Type': 'application/ssml+xml',
           'User-Agent': 'Test',
           'X-Microsoft-OutputFormat': 'riff-16khz-16bit-mono-pcm'}

data = "<speak version='1.0' xmlns='http://www.w3.org/2001/10/synthesis' xml:lang='en-US'> \
<voice name='Microsoft Server Speech Text to Speech Voice (en-US, JessaRUS)'> \
    Hello, welcome to the Cognitive Services Bootcamp!  \
</voice></speak>"

response = requests.post(url, headers=headers, data=data)
audio_data = response.content

print(response.headers)
```

We can just write it out to a `*.wav` file and then download or play it:

```python
with open("test.wav", "wb") as f: 
    f.write(audio_data)
    
ipd.Audio('test.wav')
```

There are [many different voices](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/language-support#text-to-speech) available to choose from. By updating the [XML request](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-text-to-speech#specify-a-voice), we can easily specify a different voice or language. From here on, it should be easy to generate German speech.

## Speech-to-Text

Let's take the generated or provided `test.wav` from the example before and convert it back to text. Again, let's first create a token:

```python
import requests, json

api_key = "xxx" # Enter your API key here

token_url = "https://westeurope.api.cognitive.microsoft.com/sts/v1.0/issuetoken"
headers = {'Ocp-Apim-Subscription-Key': api_key}

response = requests.post(token_url, headers=headers)
token = response.text

print("Token: " + token)
```

Now that we have a token, we can call the speech-to-text endpoint and include the `wav` data:

```python
url = "https://westeurope.stt.speech.microsoft.com/speech/recognition/conversation/cognitiveservices/v1"

headers = {'Authorization': 'Bearer ' + token,
           'Accept': 'application/json',
           'Ocp-Apim-Subscription-Key': api_key,
           'Content-Type': 'audio/wav; codec=audio/pcm; samplerate=16000'}

params = {'language': 'en-US', 'format': 'detailed'}

with open("test.wav", 'rb') as f:
    data = f.read()

response = requests.post(url, headers=headers, params=params, data=data)
print(json.dumps(response.json(), indent=2))
```

For recognizing longer text with multiple sentences, you can follow the [following tutorial](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/quickstart-python).

***Note:***

As of May 2019, also compressed audio is supported (e.g., MP3s), see [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-use-codec-compressed-audio-input-streams),

Besides that, the speech-to-text API expects audio with the following specifics:
* 16-bit WAV format with PCM or OGG format with OPUS
* Single channel (mono) at 8 or 16 KHz

More details, see [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/how-to-use-audio-input-streams).

Now that we've converted the user's speech into text, we can detect the intent of the text in the next challenge!