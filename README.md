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
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `latest` | `sha256:35d5c25f249caaf82436fd9619361654cb2b92deafdc17bd63ea613d2e80219f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:35d5c25f249caaf82436fd9619361654cb2b92deafdc17bd63ea613d2e80219f) | `amd64` |


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
        "docker-manifest-digest": "sha256:35d5c25f249caaf82436fd9619361654cb2b92deafdc17bd63ea613d2e80219f"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "031e31d089a75043dcbdf17f72a329cb290501a3",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEYCIQDxwH6Yh6IeprvhrOQepE37xzxevp49NH3i6Hs/UHyD6QIhAPYYwKyADhY+P6Ir5LkWsT8UpYQTfwrmm9pe+Y6LWf1R",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhYmFhYjFkYWMxY2YyN2YyNzZhNzAwOWJmNjRjY2UxY2Y4MjhjNGIyYmE4ZTdmMWI2MjY0ZjFmYzk5MWMxMzNlIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUN5OEFrRTZkNTF0QVl5cVIzOWZlZ2tOK010L1Y5ekg0c1locEN2VVdtOEtRSWhBS29BVjBzblBqOGg3bzUxSnl4d3B4R05UTEl3THB3WG1Wc1Y4ZDM1RnRSaSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhSRU5EUVhrMlowRjNTVUpCWjBsVlVtbG9TRkJVUkhJdlRtdFBORkJqVkN0eVpIbFhLM0YyU213MGQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRWTlJFRXhUMVJSTWxkb1kwNU5ha2w0VFZSRk5VMUVSWGRQVkZFeVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZxTm5CcVRIbFJkbXRhVkhaVFdVNVVWVUpoTVUxcEszRmFVV3hDVEZsUVlWaEViVUlLUTA4eVFVOHdaRWxWU21SblEwdEpXWHBKYW5oRWEwNUhNM0ppYURVNWJIVlJiWGxsVlVOck1sWjFXRU5SUTFoUVIwdFBRMEZyTUhkblowcEtUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZSVW5SYUNtdDNaMnBzVEZGc1FtUktZa1V2TVRGaE5tdEZiMnhuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwUkJlazFYVlhwTlYxRjNUMFJzYUU1NlZYZE9SRTVyV1RKS2ExcHFSVE5hYW1ONVdWUk5lVTlYVG1sTmFtdDNDazVVUVhoWlZFMTNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XWE5IUTJselIwRlJVVUl4Ym10RFFrRkpSV1pSVWpkQlNHdEJaSGRFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlUwNWFaemxhUVVGQlJVRjNRa2xOUlZsRFNWRkVUMUpITlM5T1RsZG5aMDF0VVhSRUsyNEtNRFZSSzJaUFlUSndhWG94TkVObU9GSkRkekZ0ZVRBd1VIZEphRUZRZUM5R1RWWm1PVk5VYkRaMVRsZFlTR1Z2UmtnclpsTTFiV3hvT0ZBMFIxcGpWZ3B1U1M5M2JtNDFkVTFCYjBkRFEzRkhVMDAwT1VKQlRVUkJNbWRCVFVkVlEwMVJSRWQyTUhGelFrWlBiRlpRZEhGclFsVXlVbUk0VXpOVVRTODViMmh6Q25wQ1Z5dHhibmRaYkhVNWNUTnFablpFZWpOWGFuRnVjMHBGWjBjNU5tYzRVWEpqUTAxQ1oyWnZRM28xV0RJd2JrNU1NVU16TnpZeFExQldjMUJ4VldJS1NVdFJZekJ1ZW01TFEycERkR0pRTUN0NmRtTktlVk5yVDI1TmEwNVhNbXd4TVdGWE1HYzlQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1668819590,
          "logIndex": 7383153,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "031e31d089a75043dcbdf17f72a329cb290501a3",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3501344215",
      "sha": "031e31d089a75043dcbdf17f72a329cb290501a3"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

