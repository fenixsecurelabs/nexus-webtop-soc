### Underground Nexus - Security Operation Center node
> Current Version v0.1.0

Latest images

`docker pull pyrrhus/soc-admin-webtop:amd64-latest`

Signed images and its digest for verification. (v0.1.0)

Each of these images has being signed with `cosign` and also has `SBOM` generated with `syft`. Lastly, `attestation` is attached but it is experimental.

```bash
pyrrhus/soc-admin-webtop:amd64-latest
sha256:e250caa63d880b2a30391047bb1a84531437aa2c440f4f7e1283446267b14228

# Download the generated SBOM
COSIGN_EXPERIMENTAL=1 cosign download sbom \
  pyrrhus/soc-admin-webtop:amd64-latest --output-file <NEWFILE>.spdx

# Download the generated attestation
COSIGN_EXPERIMENTAL=1 cosign download attestation \
  pyrrhus/soc-admin-webtop:amd64-latest --output-file <NEWFILE>.att
```

**Docker Image Building Workflow**

Registries:
1. Dockerhub (pyrrhus/soc-admin-webtop)
2. Azure Container Registry
3. GitLab Container Registry (coming soon)
4. GitHub Container Registry (coming soon)

**Experimental**

Currently, SOC (Security-Operation-Center) is built using `linuxserver/webtop` and its desktop environment is `XFCE`. At the time when I was building the Dockerfile, I was testing different desktop environment, and for my own personal reason, I am using `XFCE`. However, the default build will be added soon.

This image comes preinstalled with `GitKraken` and `Suricata`. This is an optional SOC environment that can be expanded with whatever tools you want to add.

Future plans is to build two separate platforms `linux/amd64` and `linux-arm64`.

At this time, the container are signed with Azure KMS key. Before I was testing different keys, but for the moment, I am using multiple keys to see how easy it is to use.