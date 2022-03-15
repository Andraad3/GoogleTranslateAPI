# Criar variavel de ambiente no arquivo .bashrc:
- export GOOGLE_APPLICATION_CREDENTIALS="/home/joao/Documents/Dguests/GoogleTranslateAPI/googleCredentials.json"

# Chamada para traduzir usando post:
	curl -X POST \
	-H "Authorization: Bearer "$(gcloud auth application-default print-access-token) \
	-H "Content-Type: application/json; charset=utf-8" \
	-d @request.json \
	"https://translation.googleapis.com/language/translate/v2"

# -d @request.json \ 
 Serve para mandar o JSON a ser traduzido
