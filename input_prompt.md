Estamos recebendo os seguinte LOGs:

<logs>
05:22:41 - LiteLLM Proxy:ERROR: common_request_processing.py:332 - litellm.proxy.proxy_server._handle_llm_api_exception(): Exception occured - No deployments available for selected model, Try again in 2000 seconds. Passed model=gemini-2.5-pro-preview. pre-call-checks=False, cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd', {'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}), ('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040061.2287984, 'cooldown_time': 2000}), ('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91', {'exception_received': 'litellm.RateLimitError: RateLimitError: MistralException - Requests rate limit exceeded', 'status_code': '429', 'timestamp': 1745039683.7739124, 'cooldown_time': 2000})]
Traceback (most recent call last):
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/proxy/proxy_server.py", line 3391, in chat_completion
    return await base_llm_response_processor.base_process_llm_request(
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/proxy/common_request_processing.py", line 244, in base_process_llm_request
    responses = await llm_responses
                ^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 950, in acompletion
    raise e
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 926, in acompletion
    response = await self.async_function_with_fallbacks(**kwargs)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3379, in async_function_with_fallbacks
    raise original_exception
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3346, in async_function_with_fallbacks
    response = await run_async_fallback(
               ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router_utils/fallback_event_handlers.py", line 161, in run_async_fallback
    raise error_from_fallbacks
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3193, in async_function_with_fallbacks
    response = await self.async_function_with_retries(*args, **kwargs)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3488, in async_function_with_retries
    self.should_retry_this_error(
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3685, in should_retry_this_error
    raise error
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3462, in async_function_with_retries
    response = await self.make_call(original_function, *args, **kwargs)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 3580, in make_call
    response = await response
               ^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 1089, in _acompletion
    raise e
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 971, in _acompletion
    deployment = await self.async_get_available_deployment(
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 6096, in async_get_available_deployment
    raise e
  File "/home/venvs/litellm/lib/python3.11/site-packages/litellm/router.py", line 5998, in async_get_available_deployment
    raise exception
litellm.types.router.RouterRateLimitError: No deployments available for selected model, Try again in 2000 seconds. Passed
</logs>


Na aplicação que esta usando a API estamos recebendo a seguinte resposta:


</logs2>
Retrying in 8.0 seconds...
litellm.RateLimitError: RateLimitError: OpenAIException - No deployments available for
selected model, Try again in 2000 seconds. Passed model=gemini-2.5-pro-preview.
pre-call-checks=False,
cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd',
{'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is
overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'',
'status_code': '503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}),
('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received':
'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try
again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503',
'timestamp': 1745040061.2287984, 'cooldown_time': 2000}),
('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91', {'exception_received':
'litellm.RateLimitError: RateLimitError: MistralException - Requests rate limit exceeded',
'status_code': '429', 'timestamp': 1745039683.7739124, 'cooldown_time': 2000})]
The API provider has rate limited you. Try again later or check your quotas.
Retrying in 16.0 seconds...
litellm.RateLimitError: RateLimitError: OpenAIException - No deployments available for selected model, Try again in 2000
seconds. Passed model=gemini-2.5-pro-preview. pre-call-checks=False,
cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd', {'exception_received': 'b\'{\\n
"error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n    "status":
"UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}),
('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received': 'b\'{\\n  "error": {\\n
"code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n
}\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040061.2287984, 'cooldown_time': 2000}),
('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91', {'exception_received': 'litellm.RateLimitError:
RateLimitError: MistralException - Requests rate limit exceeded', 'status_code': '429', 'timestamp': 1745039683.7739124,
'cooldown_time': 2000})]
The API provider has rate limited you. Try again later or check your quotas.
Retrying in 32.0 seconds...


Me parece que nao esta conseguindo executar os fallbacks e continuamos recebendo erros:

litellm.APIConnectionError: APIConnectionError: OpenAIException - litellm.InternalServerError:
litellm.InternalServerError: VertexAIException - b'{\n  "error": {\n    "code": 503,\n    "message":
"The model is overloaded. Please try again later.",\n    "status": "UNAVAILABLE"\n  }\n}\n'
Retrying in 0.2 seconds...
litellm.APIConnectionError: APIConnectionError: OpenAIException - litellm.InternalServerError:
litellm.InternalServerError: VertexAIException - b'{\n  "error": {\n    "code": 503,\n    "message":
"The model is overloaded. Please try again later.",\n    "status": "UNAVAILABLE"\n  }\n}\n'
Retrying in 0.5 seconds...
litellm.RateLimitError: RateLimitError: OpenAIException - No deployments available for selected model,
Try again in 2000 seconds. Passed model=gemini-2.5-pro-preview. pre-call-checks=False,
cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd',
{'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is
overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code':
'503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}),
('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received': 'b\'{\\n
"error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n
"status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040061.2287984,
'cooldown_time': 2000}), ('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91',
{'exception_received': 'litellm.RateLimitError: RateLimitError: MistralException - Requests rate limit
exceeded', 'status_code': '429', 'timestamp': 1745039683.7739124, 'cooldown_time': 2000})]
The API provider has rate limited you. Try again later or check your quotas.
Retrying in 1.0 seconds...
litellm.RateLimitError: RateLimitError: OpenAIException - No deployments available for selected model,
Try again in 2000 seconds. Passed model=gemini-2.5-pro-preview. pre-call-checks=False,
cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd',
{'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is
overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code':
'503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}),
('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received': 'b\'{\\n
"error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n
"status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040061.2287984,
'cooldown_time': 2000}), ('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91',
{'exception_received': 'litellm.RateLimitError: RateLimitError: MistralException - Requests rate limit
exceeded', 'status_code': '429', 'timestamp': 1745039683.7739124, 'cooldown_time': 2000})]
The API provider has rate limited you. Try again later or check your quotas.
Retrying in 2.0 seconds...
litellm.RateLimitError: RateLimitError: OpenAIException - No deployments available for selected model,
Try again in 2000 seconds. Passed model=gemini-2.5-pro-preview. pre-call-checks=False,
cooldown_list=[('9ca5d601573d1b2b5c7b99d4672e881f530188c50a5669861a33a1a712d3f0dd',
{'exception_received': 'b\'{\\n  "error": {\\n    "code": 503,\\n    "message": "The model is
overloaded. Please try again later.",\\n    "status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code':
'503', 'timestamp': 1745040057.6443443, 'cooldown_time': 2000}),
('8842c90a424bd7cd8905a1bbe7f058f3a3d4736907d05e9011fb533d59a7ebee', {'exception_received': 'b\'{\\n
"error": {\\n    "code": 503,\\n    "message": "The model is overloaded. Please try again later.",\\n
"status": "UNAVAILABLE"\\n  }\\n}\\n\'', 'status_code': '503', 'timestamp': 1745040061.2287984,
'cooldown_time': 2000}), ('50f51d85945aab1338517f2160dbd2ee5260b0b5b980321e7d16fea366b21c91',
{'exception_received': 'litellm.RateLimitError: RateLimitError: MistralException - Requests rate limit
e

</logs2>



A situação é a seguinte: Estams usando o modelo com nome gemini-2.5-pro e temos 21 keys dele, o esperado é que seja feito a rotação entre elas, loadbalancer.Uma vez que essas keys tem um rate limit bem restrito pela google e precisamos dessa estrategia apra ao ficar sem conexão. E também temos 2 keys para o modelo gemini-2.5-pro-preview que deve agir como fallback que tem rate limits mais altos porém é extremamente caro.
A api deveria tratar o erro internamente tentando a chamada novamente em outras keys/deployments ou indo para o fallback