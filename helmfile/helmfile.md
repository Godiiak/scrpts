Отладка шаблонов:  
`$ helm template . > out.yaml`

Для того что бы рендерить шаблоны не в один файл, можно использовать awk:
`$ awk '/---/{if(l) print l>fn; x=$0} !/---/{l=l"\r\n"$0} END {print l>fn} /^  name:/{fn=$2}' out.yaml`