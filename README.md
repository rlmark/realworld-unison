# ![RealWorld Example App](logo.png)

> ### Unison codebase containing real world examples (CRUD, auth, advanced patterns, etc) that adheres to the [RealWorld](https://github.com/gothinkster/realworld) spec and API.


### [Demo](https://demo.realworld.build/)&nbsp;&nbsp;&nbsp;&nbsp;[RealWorld](https://github.com/gothinkster/realworld)


This codebase was created to demonstrate a fully fledged backend application built with **Unison** including CRUD operations, authentication, routing, pagination, and more.

We've gone to great lengths to adhere to the **Unison** community styleguides & best practices.

For more information on how to this works with other frontends/backends, head over to the [RealWorld](https://github.com/gothinkster/realworld) repo.

# How it works

This application uses the following stack: 

* Postgres - via docker
* [The Postgres Unison Client](https://share.unison-lang.org/@runarorama/postgres) - our client for connecting to a postgres instance
* [The Unison Cloud](https://www.unison.cloud/) with a Bring your own Cloud [BYOC](https://www.unison.cloud/byoc/) setup - a deployment platform making use of containers
  - The [Cloud client library](https://share.unison-lang.org/@unison/cloud) - for interacting with Cloud resources
* [The Routes library](https://share.unison-lang.org/@unison/routes) - for HTTP server endpoint definition

# Getting started
    
Unison does not use the file system for source code, therefore there are two source repositories. 

  * [A Git repository containing docker and sql setup](https://github.com/rlmark/realworld-unison).
  * [The Unison source code](https://share.unison-lang.org/@rlmark/realworld)
  
To get started, 

1. Ensure you have [Unison installed](https://www.unison-lang.org/docs/install-instructions/) 
2. `git clone` the `realworld-unison` git repository
3. At the root of the repository, in a separate terminal run `docker compose up` 
4. At the root of the repository, enter `ucm` in another terminal to start the codebase manager. 
  - Create a `scratch.u` file in your repo if you intend to edit Unison code for the project. 
  - Files with the `.u` extension will not be checked into version control
5. Run docker compose. 

If running locally, from the root of the project enter: 

```
docker compose up
```

If you are running in BYOC with docker: 

```
docker compose -f pg-docker-compose.yaml -f docker-compose.yml --env-file secrets-example.env --env-file .env up
```

6. Download the application code in the `ucm` with the following: 
       
``` ucm
scratch/main> clone @rlmark/realworld
```

7. Run the service on `localhost:8080` with the following in the `ucm` console:

``` ucm 
@rlmark/realworld/main> run deploy.serveLocalCloud
``` 

To teardown the postgres db and remove the tables and data run: 

```
docker compose -f pg-docker-compose.yaml down -v
```

To teardown the postgres db and all of the associated cloud-BYOC volumes: 

```
docker compose -f pg-docker-compose.yaml -f docker-compose.yml --env-file secrets-example.env --env-file .env down -v
```