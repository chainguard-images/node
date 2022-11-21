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
| `latest` | `sha256:e7398b03fa4ac499e9397663e0c1a394a62b7e1480d702e6af44f012d0444c1e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:e7398b03fa4ac499e9397663e0c1a394a62b7e1480d702e6af44f012d0444c1e) | `amd64` |
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221120` | `sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09) | `amd64` |
| `migration-20221119` | `sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974) | `amd64` |


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
        "docker-manifest-digest": "sha256:e7398b03fa4ac499e9397663e0c1a394a62b7e1480d702e6af44f012d0444c1e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "0a1c575740101c28ebc159a6cb458346218a0803",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCID1Tl/czMptmQcZQAnJdleFJdIfe8v1mcBScXDE55u2MAiBHJoKz8HFAMBM3JnjESKDpfCu3oMHdSxv4NyQ8kQ4KPQ==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiIwNWUxNzE5OGIzM2IwNDY0M2QxMmIxMTMwN2Q4NTNiYzgyN2M0MjU2NDhlZjRhNzAwNmQwNzJkMGU2YTQxMGMyIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUQ5dWdLNFdESFlkMnpCSTYxVXpvYi9sQ0pzRUZhWEhCTlg4VlBPSDloVm5BSWdZN2QrSFJ1VVVERm14VnV0c3ovdXZqNldiNGl0RXZqWTFyRk5KSHBqVVVNPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhSRU5EUVhreVowRjNTVUpCWjBsVlFXSkZOQ3RCWWs5UGNWUlNVMmRhYlZkVVNub3pVMVl3WmxOM2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1hoTlJFRXhUMVJWZDFkb1kwNU5ha2w0VFZSSmVFMUVSWGRQVkZWM1YycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV3YTBWRWFWTmxSbGh1VjIxRUwwSmtVWHBhY0dkeVFVdEhaV1ZpYWxaNllXcG5aMU1LVUU1VU1XUndVbGs1VjBkaVEwbGtVVmt3ZFVWeEsxSjZiekpHZFhCc2JpOUJlRnByU0dGWFdtMVlTSGwxUVVkcFZYRlBRMEZyZDNkblowcEpUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZEUjAxdkNtcEdiVGcxT1ZWb1l5dGhjSEkyUWtKVFQyeExUV000ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUkNhRTFYVFRGT2VsVXpUa1JCZUUxRVJtcE5hbWhzV1cxTmVFNVViR2hPYlU1cFRrUlZORTE2VVRKTmFrVTBDbGxVUVRSTlJFMTNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XVzlIUTJselIwRlJVVUl4Ym10RFFrRkpSV1pCVWpaQlNHZEJaR2RFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlUxaHpkR0ZsUVVGQlJVRjNRa2hOUlZWRFNWRkVXbTlHTlhvM1NFNDNZa0l3UTJoRmNWb0tZWFowWm14TFpUZHhRMGRXUm14RE1GZFRjVTA1TUdONlQzZEpaMDV3YzFOd1owNU5hSEV3Wm1SV2N5dEpZa1JuUVhCcVdqWXpLemd2VG5VM1pIUllRUXA2U0RWTmFUQkZkME5uV1VsTGIxcEplbW93UlVGM1RVUmhVVUYzV21kSmVFRlFZbmhpZW1rck0xUklaV2R1VkdnMVoweHBlbHB6TjJkdVpHa3JkRVo0Q2pCT05YTldXbmw1T1RCdWJYWXJZMHhuVWxoaU0wUjFMelpPZDFKWk0wTXlXWGRKZUVGTlIzUnBiM2RsWVZkcFEyaEdTMFI0VFRseE1YY3hjRWRhTTFBS1oySk9VM0pPVldocVIzRmlRa3BFYkc4elpIZHhUbFpqVDB4UldrVTRORmgyWjBkWk5VRTlQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1668992393,
          "logIndex": 7507308,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "0a1c575740101c28ebc159a6cb458346218a0803",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3510577046",
      "sha": "0a1c575740101c28ebc159a6cb458346218a0803"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

