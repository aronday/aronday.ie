# aronday.ie

## this is a site generator using Hugo. 

### To build:
```
hugo -s hugo -d ../public
```

### To deploy to Firebase:

0. enable KMS
1. get a token: `firebase login:ci`
2. encrypt it:
```
echo -n $TOKEN | gcloud kms encrypt \
  --plaintext-file=- \
  --ciphertext-file=- \
  --location=global \
  --keyring=aronday-ie \
  --key=firebase | base64
```
3. paste encrypted token into cloudbuild.yaml

## To build in Cloud Build
### Prerequisites
* Build and push two builders to GCR:
  * github.com/GoogleCloudPlatform/cloud-builders-community/firebase
  * /tools/hugo-builder
  
  
## TODOs
* eliminate the on-the-fly install of jq
