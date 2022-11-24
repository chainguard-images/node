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
| `migration-20221122` | `sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87) | `amd64` |
| `latest` | `sha256:f53343db9fb0947efb410bf3c2dc5e2fafbb643c11eed8261f1018920f757fef`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f53343db9fb0947efb410bf3c2dc5e2fafbb643c11eed8261f1018920f757fef) | `amd64` |
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221123` | `sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d) | `amd64` |
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
        "docker-manifest-digest": "sha256:f53343db9fb0947efb410bf3c2dc5e2fafbb643c11eed8261f1018920f757fef"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "df57e1346f0adfdeaf6830a3dc34bd47e516d012",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIDcah8IB48IVYX0H44rQYZEFzvBbarBajrn2qdyI0PJMAiEA9N7nBiFiMmlDZs60E+pCKUKOM+yi1pGIzkF0c3/TG10=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI1ZmIxMWRjODM3NDdiN2VmYTg1ZDgyMTc4OTFhOGM3ZTM3NDQ3YTE2NzkzNDI0MTU3MjYzNmI3M2I1Y2FkNGM1In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FUUNJQ2tkeGNLOGhzUkpVdkN5bGVHZ2FVSzJXdmNHajhzdXg4L0V0ZjJKVUo4eEFpQnF0bysxTmtROEhXbk81M3ZLeUw0dXowZW5OelJlS3d1Qm5uVVNTV3VnUEE9PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhSRU5EUVhreVowRjNTVUpCWjBsVlltSmlTbUZXYzJoQk1XZHJZbkpyV0RKblN6WXZlRllyUVdSTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RCTlJFRjNUMFJGTkZkb1kwNU5ha2w0VFZSSk1FMUVRWGhQUkVVMFYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZtVUhsTkt6ZzFUME16ZFZWSloyOTBTbmQxWjFSRlIyWXpSV0ZuZW5kek5XVkhlbkVLUVZSRFVTOVliMGt6SzI5blZsVnJOekJJWml0SlFsbEpOVTloU1RrMk4wbEtWeXR0VXpCR2NWUXliRVZMWlcxd2JuRlBRMEZyZDNkblowcEpUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlYzUWpkVkNqQmtiRm81ZDFoR1NXeFZSbmx4T1VnelVVMXBTaTlaZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwZFNiVTVVWkd4TlZFMHdUbTFaZDFsWFVtMWFSMVpvV21wWk5FMTZRbWhOTWxKcVRYcFNhVnBFVVROYVZGVjRDazV0VVhkTlZFbDNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XVzlIUTJselIwRlJVVUl4Ym10RFFrRkpSV1pCVWpaQlNHZEJaR2RFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlUyMDVjbnBDUVVGQlJVRjNRa2hOUlZWRFNVTmxNSEJ4V2xGR1ZUSldMM0Z4U1ZRNFZWWUtUalZWWmpGdWJ6azRORWN3VjAxR1VtWjFaRFE0T0dOR1FXbEZRV3BuZUZVMlkxcDZUMkZxUVZndlExbFlaRkIzVUV4Q05XWkNXV2htZEVaTlpEaEVUQXAwTmxKSmVUZEJkME5uV1VsTGIxcEplbW93UlVGM1RVUmhVVUYzV21kSmVFRkxSRmhFVTJwemRFNUdWbmsyU21JdmMyWnhkRzR5TlZoVlQyNUVha2xUQ2tWUlUxcFJhM3ByVlRGeFNVb3pOMDVRUjFka1NWUkZRa0ZFTW5sRmIxRlFOMEZKZUVGS04zTkVhV2wyWlRnM1JYRldlWFF3VkN0dGVsSk1TbU5qUkVNS1ZqUllXV2Q0V2xKU1lWRlhPRVI0UlRSWFIwRlBVRlF3YWpWc2JIZ3lTbWsxYmtkVVYyYzlQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1669248502,
          "logIndex": 7721718,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "df57e1346f0adfdeaf6830a3dc34bd47e516d012",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3536591821",
      "sha": "df57e1346f0adfdeaf6830a3dc34bd47e516d012"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

