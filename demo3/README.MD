# Demo3 Knative

This is a Repository of sample in order to use AWS Lambda function with knative

## Func

Build and deploy application from source [code](app.go) hosted in Github and push artifact to docker registry

Have a look on: [How to deploy your lambda without dockerfile](../demo7/README.MD)

## Prerequisite

- Have set credential for your remote registry
- A dockerfile

## Demo

Deploy buildtemplate for kanico:

```
kubectl apply -f ../buildtemplate/kaniko.yaml
```

Deploy your application:
```
kubectl apply --filename service.yaml
```

Retrieve your knative istio ingress gateway
```
kubectl get svc knative-ingressgateway --namespace istio-system
```

Check your knative application url
```
kubectl get ksvc
```

Perfom Test:
```
curl -H "Host: lambda.default.example.com" http://af4<REDACTED>.amazonaws.com --data '{"Name": "Miam"}'
```

## Remarks

Observe that your deployment will scale down to zero if your function is never used