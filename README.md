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
| `latest` | `sha256:569c1e6c27b57d64dc682b63656557b2289b9521cd31033aaef589baa90d1767`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:569c1e6c27b57d64dc682b63656557b2289b9521cd31033aaef589baa90d1767) | `amd64` |


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
        "docker-manifest-digest": "sha256:569c1e6c27b57d64dc682b63656557b2289b9521cd31033aaef589baa90d1767"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "3fbeb047d09fba3ea65fb71580a419920013bd10",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIFSJDzzBVcCI/Uv/f+n+Rkoiqmb1TPRPsJ2VdWkKjKapAiEA0SwyEjbFjBLzzT03w3ls5Zu5DgJhj1PWdT6juAOs0ww=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwMTY2YjM0NmFmZDVjMTdhZWViYmU5NGEzNTI5ZmU3YWUwMGY5NGNjMzU2MDc3ZjcxOTM5OWY4NTc5YTVmNmNiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJRk1Gdm00YmNIcnM2dVZYZG02UCtlYmdocjNmSzVHUWFROGtIenNEcXZGN0FpQiszMEM0cVFXSGlFYWtlTCttTzc1MlZ1SFEya3R4dGk2cE5iOVVhRFR5dmc9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhWRU5EUVhrMlowRjNTVUpCWjBsVlZURlVUVzQyUVdabU0wZEZaVXd3YlVSck5XdHpTV2g1UzBSdmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRSTlJFVjNUbXBSTUZkb1kwNU5ha2w0VFZSRk5FMUVSWGhPYWxFd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZaVG1WRldtSnBVa0Z1V214UmMzbzFUblZ5TW01YWNXMVpZMGxpVFd3dmRFODJZbU1LT0ZGcWVDOUpUMXAwWWtjNGFuWkRSVTE0WmxwQmNXZ3hNMUVyVml0U0syRjRVek4wUkVWaGVIbFhVSGRTTm1sU05HRlBRMEZyTUhkblowcEtUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlV4SzFSMkNscDBkWFZHTDJzcldIWmpSbFJtWWpWb1RsUnpOMlpCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUk9iVmx0Vm1sTlJGRXpXa1JCTlZwdFNtaE5NbFpvVG1wV2JWbHFZM2hPVkdkM1dWUlJlRTlVYTNsTlJFRjRDazB5U210TlZFRjNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XWE5IUTJselIwRlJVVUl4Ym10RFFrRkpSV1pSVWpkQlNHdEJaSGRFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlUwbFNhRWRuUVVGQlJVRjNRa2xOUlZsRFNWRkVjVkpEYWxwVFdVcDJZVk5yTkVsd1pWWUtTMngxVGt4a05HTkhWM0JuTlVoRk9HRktUVTB5ZGpabVpHZEphRUZRTnpGQ2FDOVRLMU5YYVUxRWVIQlFNaXRrUldVcmNXOXNjbVZrUWlzdlZYSXhWd28xYkhab1pFRXpUazFCYjBkRFEzRkhVMDAwT1VKQlRVUkJNbXRCVFVkWlEwMVJSRWxuVGxkSFYyczJiVWhYWlVSQ1ZESTVOWEZrVlhCSGEyNTJXVGg1Q2sxeFVsbzRaek0xTUVWTVRUUjVhakpTUkdKTk1VZHJSMUV4YzBFdmJHeDBVVk13UTAxUlJHWnVaMjVVWTNoR1pVTlNZVWhMTUc1V2FUSXZXR00wY0hrS1FXWTBTRUpYYkhSelIyOUdZbXBpZDA1eEt6aE9aalJNYkdaa1lXOXpVbVYyTUU5QlEyVmpQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1668733609,
          "logIndex": 7310509,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "3fbeb047d09fba3ea65fb71580a419920013bd10",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3493315357",
      "sha": "3fbeb047d09fba3ea65fb71580a419920013bd10"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

