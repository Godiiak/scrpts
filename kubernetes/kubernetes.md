Добавить имя пода в переменные окружения:  
`$ export SOURCE_POD=$(kubectl get pod -l app=service-a-app -o jsonpath='{.items..metadata.name}')`

Выполнить запрос из пода приложения:  
`$ kubectl exec "$SOURCE_POD" -c container_name -- curl -sSI http://example.org | grep  "HTTP/"`

Посмотреть лог приложения:  
`$ kubectl logs $SOURCE_POD > app-$(date +%F).log`

Посмотреть лог envoy-proxy сайдкара приложения:
`$ kubectl logs -l app=istio-ingressgateway -n istio-system -c istio-proxy`