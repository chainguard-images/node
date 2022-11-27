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
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221127` | `sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696) | `amd64` |
| `migration-20221121` | `sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f) | `amd64` |
| `migration-20221124` | `sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4) | `amd64` |
| `latest` | `sha256:234f42d8740945f12a744b8c13e0ac9a197aca802d8d71b6d9b765622864e04c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:234f42d8740945f12a744b8c13e0ac9a197aca802d8d71b6d9b765622864e04c) | `amd64` |
| `migration-20221119` | `sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974) | `amd64` |
| `migration-20221120` | `sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09) | `amd64` |
| `migration-20221122` | `sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87) | `amd64` |
| `migration-20221123` | `sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d) | `amd64` |
| `migration-20221125` | `sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d) | `amd64` |
| `migration-20221126` | `sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5) | `amd64` |


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
        "docker-manifest-digest": "sha256:234f42d8740945f12a744b8c13e0ac9a197aca802d8d71b6d9b765622864e04c"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "7b90b4525ec569a778895c1ccf9850ce670f54f1",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICHmvLiaEf1MnJBTyCfRUA+ooOozLMSKZfQZs6cOmup7AiB5GvTyZUxb/Ed3tcGvKUWw8xBbd0Fzp0AF81jKqamSRg==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwYmU0OWFjNDNlNDU2MGQ4NTE3Yjk1YWVjMDI5NTQyN2VmNzhkYTY4MjE0MDliMGUzNzg4NzMwN2ViM2U5MDFiIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJSE5hb3ZRTDJjTmFnNEpwMVdhdnpPRUVwdEZldjN6QjI0QWIzdlQrRWw1QUFpQldIbGk3TTNjc3ViVE5PRXJCNVRScGFYV1paaDRlVytZajVBN0RIT2ROcVE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUndla05EUVhrMlowRjNTVUpCWjBsVlZHVktlbTE1U2tocEswaE9SM2RTTkhRNVNHMVhVVXhFVmxoamQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1ROTlJFRjRUVlJSTUZkb1kwNU5ha2w0VFZSSk0wMUVRWGxOVkZFd1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV2Y1c1NmF6bDFUVUZRUW1KWkwxbGFVV1UyZWpGaFMyRk1PV1Y0UW5oSlVrdFJVblVLYldGNlQyMXNTV2RVV0hrMU0wTnRXRXA1UzJoSGRrZ3hWelV6Um5aYVZqbEZhUzlVZDFGRE1XOHdOVzVGV21VelJVdFBRMEZyTUhkblowcEtUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZDV1VKUUNqbHBlQ3RES3poTFZreGhZbFo2U210eGNHbEVja2RWZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUmthVTlVUW1sT1JGVjVUbGRXYWs1VVdUVlpWR016VDBSbk5VNVhUWGhaTWs1dFQxUm5NVTFIVG14T2FtTjNDbHBxVlRCYWFrVjNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XWE5IUTJselIwRlJVVUl4Ym10RFFrRkpSV1pSVWpkQlNHdEJaSGRFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlV6SmlVRlU1UVVGQlJVRjNRa2xOUlZsRFNWRkRUbE5xYUhFMFJ6aFVMelJET1dkYVIyNEtNemtyYTBveVQzVnVSbmx5YW05bU5VNDRhR2hhYW5kQk1uZEphRUZQWlhWNU5ISnNNMnd3YkdkWk1YRnNXWFJHVTNSdVdHRnhiV2t6YzB4WVpIaEpWd3BNTkZGbWF6VTBOVTFCYjBkRFEzRkhVMDAwT1VKQlRVUkJNbU5CVFVkUlEwMUVLemhhYkVGcVUwd3ZaRXhPUkdkUmJWRkllRlJSYUZreWEzRmtXSEJxQ2s5aVZTdFBVMnQ2V2tsRVdUQjRkazFuUkdGdmRsWXZjbFVyYUZWbldrZFRkM2RKZDJaQ1Z6TXJjamRMT0RaWFpVaEZaREpSUzFCd04wcFhZVzlOUnpVS1FUZE9OemxPY0RsVE4xYzRiMlpCY1hKT0syRjVUazB6VkUxTlRHSnhZVTVZUkhsc0NpMHRMUzB0UlU1RUlFTkZVbFJKUmtsRFFWUkZMUzB0TFMwSyJ9fX19",
          "integratedTime": 1669507907,
          "logIndex": 7917104,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "7b90b4525ec569a778895c1ccf9850ce670f54f1",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3555926194",
      "sha": "7b90b4525ec569a778895c1ccf9850ce670f54f1"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

