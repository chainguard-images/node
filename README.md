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
| `migration-20221121` | `sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:2c7abf4e55d8b91f6c2b1c261a860dbb56cbe4d6a515176a7f1c1aa5007e7a1f) | `amd64` |
| `migration-20221123` | `sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:3e3ba7226d326765fef34c93be54c6294ac0aaa1267771c36e25c04b8989886d) | `amd64` |
| `migration-20221124` | `sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:efee73ebe1f35daec1a0377763c436e3d378ab9d2784f2c623105f89aa01ade4) | `amd64` |
| `migration-20221126` | `sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:73fb5e2bb1f0d3f268508ec6ccdffe88f28feabd2c7cc0493ff8fe0cca024ed5) | `amd64` |
| `migration-20221127` | `sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:8f81040d8ec1a1a90d2a5333e5c68f231f843335b1e8ff2f587c53a35d2b1696) | `amd64` |
| `latest` | `sha256:6387beb64ba808ed4dfb25d01b0e359d34778ab338b3457996aac79cf79d6c4d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6387beb64ba808ed4dfb25d01b0e359d34778ab338b3457996aac79cf79d6c4d) | `amd64` |
| `migration-20221118` | `sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6dbd59a8783ad039bfef149fdd22d1df208afb6243101bbe48c6d822a6f5bcbf) | `amd64` |
| `migration-20221120` | `sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:40897cc80c52b40aca2d18d5ebf5ccd1d25a4161a2a695deeff6577532e40c09) | `amd64` |
| `migration-20221125` | `sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4d7f7da2e9bfdd6c9975d7733ef4452235aa43c862f100f2c65a5b2292f60d4d) | `amd64` |
| `18` `18.12` `18.12.1` `18.12.1-r0` `migration` `migration-20221128` | `sha256:95843000474c9ee8091b5143277f4350f86904f6c0789cd65311606240a9dbad`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:95843000474c9ee8091b5143277f4350f86904f6c0789cd65311606240a9dbad) | `amd64` |
| `migration-20221119` | `sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:01557999deafb21e13c5165361d0007a60bba3b07c59189e5c8123aae865c974) | `amd64` |
| `migration-20221122` | `sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fb0270140d0b6dcbeafaf254e619acde39601e84b8ce640c3928230e13985a87) | `amd64` |


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
        "docker-manifest-digest": "sha256:6387beb64ba808ed4dfb25d01b0e359d34778ab338b3457996aac79cf79d6c4d"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "dbbc4c910eadb58089a2396ab3285854eda5b538",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/node",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCICVtRupqUpahcQZ6mWITKGbcNb73Jjg0HqlFP8cp7BZ+AiBNqPSabvEfBmhAhmXQpiEUxBzgnY8KhZhLXgjPVZO+jw==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJjNzc0M2QzZWNiODcwM2I1NWUzYWQ3ODczOTI2M2MzZWZkYjNkYzZmOWUyZjE1MTM0NGVhYjU5NDZlZjdkNGEzIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJR1VvL0ZFYTRJWHBlVEFoTkRIWGhYeTZOZXJlVGpJWVN5NnJPbkZxRGh6MkFpRUFweTlLSDBwSGtWQlRUVWxESlIwTFBsa1RRclQxR2h5aE1ER25SQU9waVZRPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnhSRU5EUVhreVowRjNTVUpCWjBsVlFuRkdVRnB1WTA4NFNHSTVjMVpGU2tseU5XYzJkRUZ2TTFwTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RSTlJFRjNUMVJCZVZkb1kwNU5ha2w0VFZSSk5FMUVRWGhQVkVGNVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZwVDIxUE9HaFBOMmwwYjJFdmMyRTJlWGhWTUUwcmRsVlNjelkxU0dGV1UzbHNkVllLUW5nelYxTm9Xa2xhU0VnNGExQXpTMk5DYXpncldtbHVUMUZDZEZsblZXMW1SV2h1YUZOU1ZHWnhkV2RtTjJ0MmFEWlBRMEZyZDNkblowcEpUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZITXpZMkNqUnlNMlJ6VjFCdlMwUTVlV1Z6U1hreFNHZGFkRzVuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDFwbldVUldVakJTUVZGSUwwSkdkM2RYYjFwWllVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5TlhaYVIxVjJURzFrY0dSSGFERlphVGt6WWpOS2NscHRlSFprTTAxMlkyMVdjMXBYUm5wYVV6VTFXVmN4YzFGSVNteGFiazEyQ21GSFZtaGFTRTEyWWxkR2NHSnFRVFZDWjI5eVFtZEZSVUZaVHk5TlFVVkNRa04wYjJSSVVuZGplbTkyVEROU2RtRXlWblZNYlVacVpFZHNkbUp1VFhVS1dqSnNNR0ZJVm1sa1dFNXNZMjFPZG1KdVVteGlibEYxV1RJNWRFMUNXVWREYVhOSFFWRlJRbWMzT0hkQlVVbEZRMGhPYW1GSFZtdGtWM2hzVFVSWlJ3cERhWE5IUVZGUlFtYzNPSGRCVVUxRlMwZFNhVmx0VFRCWmVtdDRUVWRXYUZwSFNURlBSRUUwVDFkRmVVMTZhekpaVjBsNlRXcG5NVTlFVlRCYVYxSm9DazVYU1RGTmVtZDNTRUZaUzB0M1dVSkNRVWRFZG5wQlFrSkJVVTlSTTBwc1dWaFNiRWxHU214aVIxWm9ZekpWZDBwQldVdExkMWxDUWtGSFJIWjZRVUlLUWxGUlYxa3lhR2hoVnpWdVpGZEdlVnBETVhCaVYwWnVXbGhOZG1KdE9XdGFWRUZrUW1kdmNrSm5SVVZCV1U4dlRVRkZSMEpCT1hsYVYxcDZUREpvYkFwWlYxSjZUREl4YUdGWE5IZG5XVzlIUTJselIwRlJVVUl4Ym10RFFrRkpSV1pCVWpaQlNHZEJaR2RFWkZCVVFuRjRjMk5TVFcxTldraG9lVnBhZW1ORENtOXJjR1YxVGpRNGNtWXJTR2x1UzBGTWVXNTFhbWRCUVVGWlV6ZHJUbVI0UVVGQlJVRjNRa2hOUlZWRFNWRkVlWEJWYVRCbk9HWnNjRU5HTm1wR2FFVUtNWGhGY2pnclYwTkVaM0pGU25CeWVqaGpZMEphZVc4cmIwRkpaMEV3V1ZWcGMxUm9RMmhyWjBacFVqSTRSSFZWTWxWTmVYcG1WRlZ5UWtKMlR5OXVZZ3BFU21KRk1UVjNkME5uV1VsTGIxcEplbW93UlVGM1RVUmhVVUYzV21kSmVFRk5lakpGYVVSM1UxaFJSV0ZVTTJoQ1VqQmpkSEpwVkdGSGRWVlZibVJNQ21SRE1FOW5VMWRHZFcxTVEzZDJhbTVUTmpGb1UwWlVUM1ZTYUZaNlJFZzNVbWRKZUVGTFdqSkdjak5EYUd0QlJrZHRjV1pzYTJWVVNVODBhMVF4V21nS05IUnhlazgzVW5OTFFrVk1RVFZsTTNCNFZGWk9XbGgzZEZwMGRWRkpaR0ZoVTB4bFYzYzlQUW90TFMwdExVVk9SQ0JEUlZKVVNVWkpRMEZVUlMwdExTMHRDZz09In19fX0=",
          "integratedTime": 1669594146,
          "logIndex": 7976957,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/node/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/node",
      "githubWorkflowSha": "dbbc4c910eadb58089a2396ab3285854eda5b538",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3560585536",
      "sha": "dbbc4c910eadb58089a2396ab3285854eda5b538"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

