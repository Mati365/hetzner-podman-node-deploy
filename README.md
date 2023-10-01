# hetzner-podman-node-deploy

Example of standalone Bun.js application deployment to Hetzner Cloud using Rootless Podman Quadlet systemd services

## Description

The project shows an example deployment of a Bun.js (and possibly Node.js) application using Ansible to a Hetzner VPS.

The infrastructure consists of:

1. Hetzner ARM CAX11 server (provision made by Ansible)
2. NGINX and Letsencrypt
3. Fish Shell
4. Podman Quadlet containers that runs under deploy user with autoupdate containers
5. Docker registry

## How to run it?

1. Go to create project on hetzner.com, add primary IP named `app-primary-ip`
2. Point your DNS to `app-primary-ip` IPv4 address
3. Set these secrets to registry:

    ```bash
      HCLOUD_KEY: <your hcloud read & write key>
      REGISTRY_USERNAME: <specify username for podman registry>
      REGISTRY_PASSWORD: <specify password for podman registry>
      WEBSITE_DOMAIN: <specify site domain name without protocol e.g `example.site.org`>
    ```

4. Paste your public SSH keys to all users dirs present in `infra/keys/authorized/`
5. Run `deploy-hetzner.yml` workflow by `git push origin main:hetzner`
6. Enter your `Hello World` site and enjoy!

## License

MIT License

Copyright (c) 2023 Mateusz Bagiński

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
