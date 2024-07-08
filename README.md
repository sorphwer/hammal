# hammal

Build self-hosted docker mirror in cloudflare.

1. run `pnpm install `
2. copy `wrangler.toml.sample` to `wrangler.toml`
3. create a Worker in cf, replace `name` and `account_id` in `wrangler.toml`
4. run `npx wrangler kv:namespace create hammal_cache` and copy the `id` in output.
5. replace `kv id` in `wrangler.toml`
6. run `pnpm run deploy`
7. add custom domain in Worker trigger
8. Use your custom domain as docker registry mirror:

   ```
   cat /etc/docker/daemon.json
    {
      "registry-mirrors": [
        "https://hammal.example.com"
      ]
    }
   ```

Notes: You can use `cp daemon.json /etc/docker/daemon.json`, and run `sudo service docker restart` then `docker info` to check if registry is updated.
