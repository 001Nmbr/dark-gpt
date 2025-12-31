import g4f.cookies

from g4f.client import Client

import base64

# Dictionary mapping model names to pr

ovider names

model_provider_mapping = {

'gpt-3.5-turbo': 'DDG',

'gpt-40': None,

'mixtral_8x7b': 'HuggingFace',

'blackbox': 'Blackbox',

'meta': 'Meta Al',

'llama3_70b_instruct': 'Meta Al',

# Add more models and providers as n eeded

}

# Dictionary mapping display model nam

es to internal model names

display_model_mapping =

{

'gpt 3.5 turbo': 'gpt-3.5-turbo',

'gpt 40': 'gpt-40',

'llama 3': 'llama3_70b_instruct',
Mixtral 70b': 'mixtral_8x7b',

'BlackBox': 'blackbox',

'Meta Al': 'meta',

def get_provider(model: str) -> str:

"""Get provider name based on the mo del."""

return model_provider_mapping.get(m odel, ")

def get_model(display_model: str) -> str:

"""Get internal model name based on he display model name.""

return display_model_mapping.get(dis play_model, ")

def get_bot_response(prompt, internal_m odel, provider_name):

client = Client()

response = client.chat.completions.

create(

model=internal_model,

messages=[{"role": "user", "conte
nt": prompt}],

provider=provider_name,

cookies=g4f.cookies.get_cookies

('bing')

return response.choices[0].messag

e.content
