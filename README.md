```
.
|-- README.md                       <- this file
|-- main.tf                         <- providers, VPC data source, SG, EC2,
|                                      S3 bucket, ECR data ref, inline cloud-init
|-- variables.tf                    <- all input variables
|-- outputs.tf                      <- public IP and SSH command outputs
|-- manifests/
|   |-- configmap.yaml              <- Minecraft env vars (EULA, MOTD, VERSION,
|   |                                  MEMORY, TYPE)
|   |-- pvc.yaml                    <- PersistentVolumeClaim, 5Gi, local-path
|   |-- deployment.yaml             <- Deployment: Recreate, probes, resources,
|   |                                  pinned ECR image, mounts PVC at /data
|   |-- service.yaml                <- LoadBalancer Service on TCP 25565
|   `-- cron-backup.yaml            <- CronJob every 10 min, syncs /data to S3
`-- .github/
    `-- workflows/                  <- CI/CD from Ops 3: build and push image
                                       to ECR on tag
```
