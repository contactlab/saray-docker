# [Saray](https://github.com/contactlab/saray) & Docker

> Wrapper of Saray and Nginx as Docker containers (with `docker-compose`)

Docker and [`docker-compose`](https://docs.docker.com/compose/install/) must be installed.

# Containers  

- Nginx (official Docker image)
- Ubuntu Xenial (official Docker image)  
  NodeJs (7.x)  
  [PM2-docker](http://pm2.keymetrics.io/docs/usage/docker-pm2-nodejs/) (latest)  
  [Saray](https://github.com/contactlab/saray) (latest)

# Build 

    $ git clone https://github.com/contactlab/saray-docker.git saray-docker && cd $_
    $ docker-compose build

# Required files/folder 

The runner for PM2 and Saray should be like the follow and placed within the `root` directory of the project, called `run.js`:

`run.js`
```js

const {exec} = require('child_process');

exec('saray --port=3000 --path=/src/data --endpoint='yourApiEndPoint' --log /src/logs.log --pfer-api', (error, stdout, stderr) => {
  console.log(error);
  console.log(stdout);
  console.log(stderr);
});

```

The `data` folder with the stubbed APIs should be placed within the `root` directory of the project.  

> NOTE: The `docker-compose.yml` can be modified and re-built as you want.

# Run

Simply run `docker-compose`:

    $ docker-compose up

Now you can check your [localhost:3001](http://localhost:3001) and everything should be up and running!
You can also add new stubs into the `data` folder.

Run in `deamon` mode: 

    $ docker-compose up -d 

# License
Released under the [Apache 2.0](LICENSE) license.

