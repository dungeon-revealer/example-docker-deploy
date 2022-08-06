# example-docker-deploy

This is a minimal example to deploy dungeon-revealer behind a proxy using Docker.
This is written for Linux/Mac terminals.
If you are using Windows, you'll have to translate the commands yourself.

0. Setup your domain and the machine which dungeon-revealer will run on (a computer at home, a cloud VPS, etc.). 
   Make sure your domain is pointing at the public IP address of the machine.
   There are many ways to achieve this, so it is beyond the scope of this tutorial.
   However, you will need the domain (or IP address) to continue this tutorial.
1. Make sure `git`, `docker`, and `docker-compose` are installed on the machine. If you are using a VPS, this is likely already done for you or something you can choose when provisioning.
2. Clone this repo on the machine that will serve dungeon-revealer.
   ```
   git clone https://github.com/dungeon-revealer/example-docker-deploy
   ```
3. Enter the `example-docker-deploy` directory and edit some files.
   Any section wrapped in angled brackets, `<>` needs to be changed to reflect your setup.
   If you are unfamiliar with editing files in the terminal, `nano` is probably your best bet because it displays its key combos.
   1. Get into the correct directory using `cd example-docker-deploy`.
   2. Edit the `<YOUR_DOMAIN>` section of `caddy/Caddyfile` to be your domain from step 0.
     This could be `yourdomain.com` or `dr.yourdomain.com` if you are using a subdomain (`dr` could be whatever you want).
   3. Edit the various `<>` sections in `docker-compose.yml`.
      1. Anything with `/ABSOLUTE/PATH/TO` needs to be replaced with the absolute path to the current directory, for example `/home/user/example-docker-deploy`.
         You can easily get this by running `pwd` to print the working directory.
      2. The dungeon-revealer password variables need to be replaced with your chosen passwords.
         **Note:** these passwords need to be strong since dungeon-revealer will be publicly accessible.
4. Run `docker-compose up -d` to start dungeon-revealer and the proxy.
      **Note:** after they have started, you can run `docker logs dun_rev` or `docker logs caddy`
5. Go to your domain in the browser and you should see dungeon-revealer!

