In the context of working with AI models—especially language models like chatGPT —"temperature" is a parameter that controls the randomness or creativity of the model's responses.

🧠 What Temperature Does
Low temperature (e.g., 0.0–0.3):

Makes the model more deterministic and focused.

It tends to pick the most likely next word or phrase.

Useful for tasks requiring accuracy, consistency, or factuality (e.g., coding, math, legal writing).

High temperature (e.g., 0.7–1.0):

Introduces more diversity and creativity.

The model explores less likely but more imaginative options.

Great for storytelling, brainstorming, or poetry.

🎯 Example
If you ask a model to complete the sentence:

"The cat jumped over the..."

At temperature 0.2, it might say:

"...fence and ran away."

At temperature 0.9, it might say:

"...moon, chasing dreams made of cheese."

⚙️ Behind the Scenes
Technically, temperature affects the probability distribution over possible next tokens. A lower temperature sharpens the distribution (less randomness), while a higher temperature flattens it (more randomness).

```
import openai
import os

from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv()) # read local .env file

openai.api_key  = os.getenv('OPENAI_API_KEY')
```

```
def get_completion(prompt, model="gpt-3.5-turbo",temperature=0): # Andrew mentioned that the prompt/ completion paradigm is preferable for this class
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=temperature, # this is the degree of randomness of the model's output
    )
    return response.choices[0].message["content"]
```

