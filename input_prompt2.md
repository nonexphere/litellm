Estamos recebendo os seguinte LOGs:

<logs>

</logs>



A situação é a seguinte: Estams usando o modelo com nome gemini-2.5-pro e temos 21 keys dele, o esperado é que seja feito a rotação entre elas, loadbalancer.Uma vez que essas keys tem um rate limit bem restrito pela google e precisamos dessa estrategia apra ao ficar sem conexão. E também temos 2 keys para o modelo gemini-2.5-pro-preview que deve agir como fallback que tem rate limits mais altos porém é extremamente caro.
A api deveria tratar o erro internamente tentando a chamada novamente em outras keys/deployments ou indo para o fallback