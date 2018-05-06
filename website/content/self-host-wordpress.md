---
title: Self Host WordPress
image: wordpress-docker.png
---

### How to self-host WordPress with free SSL/TLS certificate and practically no limits on visits/month or bandwidth?

## Stack

- Armor `0.4.11`
  - Proxy server
  - Automatically installs SSL/TLS certificate from [Let’s Encrypt](https://letsencrypt.org)
- WordPress `4.9.4`
- MySQL `5.7`

## Step 1: Provision a machine

{{< provision >}}

## Step 2: Install Docker

{{< docker >}}

## Step 3: Configure

1. Create directories

    ```sh
    mkdir -p /opt/wordpress/armor
    cd /opt/wordpress
    ```

2. Create a file `armor/config.yaml` with the following content:

    {{< embed "docker/wordpress/armor.yaml" >}}

    Replace `<DOMAIN>` with your domain

3. Create a file `docker-compose.yaml` with the following content:

    {{< embed "docker/wordpress/docker-compose.yaml" >}}

## Step 4: Start services

```sh
docker-compose up -d
```

## Step 5: Setup domain

1. If you don't already have a domain, register one {{< domain >}}
2. Go to you domain's DNS management console and create an `A` record with name `@` and value `<PUBLIC_IP>`

## Step 6: Complete setup

1. Browse to your `<DOMAIN>` and continue with the setup

## Step 6: Setup backup

TBD

## Troubleshooting

### View logs

```sh
cd /opt/wordpress
docker-compose logs -f
```