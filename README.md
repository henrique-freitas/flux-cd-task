# flux-cd-task

This was an interesting test to do, I had never used the FluxCD tool and it seems to be an interesting tool for some applications, however it has some vulnerabilities, (is an interesting alternative between FluxCD and ArgoCD)

![image](https://user-images.githubusercontent.com/23500408/168316826-3b7fcde6-8ae4-4663-9cf8-5242c56a1757.png)

For this specific project I used Starboard Helm Chart where a simple application of the http echo hashcorp with the word "hello world" was deployed, it works in the minicube and the performance is good.

I separated two environments for this, one for prod and one for release or staging, this is a good way to not break anything in production even if the application is a simple http echo.


For the notification test I created an alert-slack.yaml to test the notifications, to use just put your token where the slack-url is, I strongly recommend using amazon SSM or Vault to store the secret values

```bash
apiVersion: notification.toolkit.fluxcd.io/v1beta1
kind: Provider
metadata:
  name: slack
  namespace: flux-system
spec:
  type: slack
  channel: flux-cd-test
  secretRef:
    name: slack-url
```
see how the notification looks in slack:

<img width="1215" alt="gitfluxcd" src="https://user-images.githubusercontent.com/23500408/168318551-0d3f55db-7c9a-4f44-bb19-29a6caa000b8.png">

and why Starboard?

first Starboard worked very well with fluxCd

Starboard is a completely open source tool that integrates with other security tools to scan your workloads and make security reports accessible through the Kubernetes API - K8s all the way

https://aquasecurity.github.io/starboard/v0.15.4/

in short working with FluxCD was fun and interesting, it's worth the discussion if it would replace the other CiCds on the market


