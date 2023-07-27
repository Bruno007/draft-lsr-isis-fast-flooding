#/bin/bash
# unset https_proxycurl -X 'POST' 'https://author-tools.ietf.org/api/render/text' -H 'accept: text/plain' -H 'Content-Type: multipart/form-data' -F 'file=@'$draft_name.xml';type=text/xml' -F 'apikey=DwEAAD_J9B6cHEICkCfskzKVzcIeU2HuIDMxx1H5BACEr7jT8_Ys8VUV8v9is-QA' --output output/$draft_name.txt
# unset http_proxy
# export http_proxy=http://localhost:3128
# export https_proxy=http://localhost:3128
draft_name=draft-ietf-lsr-isis-fast-flooding

curl -X 'POST' 'https://author-tools.ietf.org/api/validate' -H 'accept: application/json' -H 'Content-Type: multipart/form-data' -F 'file=@'$draft_name.xml';type=text/xml' -F 'apikey=DwEAAD_J9B6cHEICkCfskzKVzcIeU2HuIDMxx1H5BACEr7jT8_Ys8VUV8v9is-QA' | sed 's/\\n/\n/g' >  output/idnits.txt &
curl -X 'POST' 'https://author-tools.ietf.org/api/iddiff' -H 'accept: text/html' -H 'Content-Type: multipart/form-data' -F 'url_1='  -F 'url_2=' -F 'apikey=' -F 'doc_2=' -F 'doc_1='$draft_name -F 'file_2=@output/'$draft_name'.txt;type=text/plain' -F 'table=' -F 'file_1='  -F 'wdiff=' --output output/$draft_name.html

