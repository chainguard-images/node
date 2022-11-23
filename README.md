# node

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/chainguard-images/node/actions/workflows/release.yaml/badge.svg)](https://github.com/chainguard-images/node/actions/workflows/release.yaml)

WORK IN PROGRESS

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/node:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `latest` | `sha256:58ba8340fe18c64d46f8a6bdfd41a7cc9e0aa774eca842110f8df2158b58cdb8`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:58ba8340fe18c64d46f8a6bdfd41a7cc9e0aa774eca842110f8df2158b58cdb8) | `amd64` |
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221122` | `sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87) | `amd64` |
| `migration-20221119` | `sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974) | `amd64` |
| `migration-20221120` | `sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09) | `amd64` |
| `migration-20221121` | `sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f) | `amd64` |


## Usage

Minimal container image for running NodeJS apps

The image specifies a default non-root `node` user (UID 65532), and a working directory at `/app`, owned by that `node` user, and accessible to all users.

It specifies `NODE_PORT=3000` by default.

### Example

Navigate to the `example/` directory:

```
cd example/
```

The Dockerfile is based on Docker's [Build your Node image](https://docs.docker.com/language/nodejs/build-images/) tutorial, but uses the Chainguard node base image instead.

Build the application on the node base image.

```
docker build \
  --tag node-docker \
  --platform=linux/amd64 \
  .
```

Then you can run the image:

```
docker run \
  --rm -it \
  -p 8000:8000 \
  --platform=linux/amd64 \
  node-docker
```

...and test to see that it works:

```
curl --request POST \
  --url http://localhost:8000/test \
  --header 'content-type: application/json' \
  --data '{"msg": "testing" }'
```


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/node:latest | jq
```

Output:
```
Verification for cgr.dev/chainguard/node:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/node"
      },
      "image": {
        "docker-manifest-digest": "sha256:58ba8340fe18c64d46f8a6bdfd41a7cc9e0aa774eca842110f8df2158b58cdb8"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "93bcdb0384f3ec8975a88646b95d903b5cc44bb8",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICPuDQTwWonDrLyGbQHCyQZO2qgYRdq7loGZ9enIUpvzAiAh1nq3CT22IlE0YmXXgTvp6WE5wr0+vAylyb7+CACa/A==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1OTEwYzhkM2I2ZWFlNDA1ZDQ5ZGY2MmJkMjAzODA3YzE0ZjFhZTA5NzVlM2VmZjJmZWNlZjFkZmEzNjg1YTdjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRGRDVC9jR1oySWtLV0pWK0NZMWp6L1FrbnNib2MxQWRZOUFPRks2TUJ3akFpQmdkUnBlNjk5Z2hJb1AvOWhOdTN2OWJDd2FZbEhOd1N1TXkyNktaRExSMlE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUndla05EUVhreVowRjNTVUpCWjBsVlNsVmpkM2xTYzB0YVFqZHFObkF6U2xKWE5sbG1TSEZwVHl0TmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hwTlJFRjNUMFJWTlZkb1kwNU5ha2w0VFZSSmVrMUVRWGhQUkZVMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZJWkc1d05HaHFlbkZCWW5kVVMydFlaR2RoUVZWa1kwaHVWWGt2ZHpGUmVGVkphV2NLZDFsa1JFeG5Wa0pFT0RObWVIUXpUaXRaTDI1dU5IaDVlRlJQYkd0V1ExWjZNRGRxVkVvemRGRTVWM2QwWlZJclV6WlBRMEZyZDNkblowcEpUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZMVkdWYUNteE9UV1ZFWWpFNFREWlZNRTkyYURCMWVpOXZUVEZyZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUnJlbGx0VG10WmFrRjZUMFJTYlUweVZtcFBSR3N6VGxkRk5FOUVXVEJPYlVrMVRsZFJOVTFFVG1sT1YwNXFDazVFVW1sWmFtZDNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XVzlIUTJselIwRlJVVUl4Ym10RFFrRkpSV1pCVWpaQlNHZEJaR2RFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlUyZ3dVQzk2UVVGQlJVRjNRa2hOUlZWRFNWRkRVVGczWlU1UE9FUnVWMVZsYVZsQ1ltUUtSWEJMYm1SQ2VscEJNRzVSU2pKdk5sRmFZVEJ4SzFWV1pXZEpaME0wV21sVlZHWnBRbU5FT0d0U1NIbG9aRGgyYTA5YVdYY3hTbmRSTjBsTFFtMWxaUXBKYjFaSGFsQm5kME5uV1VsTGIxcEplbW93UlVGM1RVUmhRVUYzV2xGSmQySXdSMWwyZVVWcWRHZFhSVzlTZEdWMldWZDNZMk5TVkZkQlNYRnJTRXBoQ2xGTWJXdDVaMHRuYzI0cmVESkliM1UzVkRkWVUxbFVSMnQyUkZGeU15OUpRV3BGUVhSUFJXUlZkSGhUT1NzNFZIWTNUMUpQTmxoSlRGSkxOa3BEUm1vS1JsZzNiSHAyWkU1WllXVXdRMmt4YkVWM1kyeHRRME5uVmxkWlZXSTNVVTlaWVhaS0NpMHRMUzB0UlU1RUlFTkZVbFJKUmtsRFFWUkZMUzB0TFMwSyJ9fX19",
          "integratedTime": 1669162145,
          "logIndex": 7651147,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "93bcdb0384f3ec8975a88646b95d903b5cc44bb8",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3528095881",
      "sha": "93bcdb0384f3ec8975a88646b95d903b5cc44bb8"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

