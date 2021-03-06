# docker-wordpress-selenium
Quickstart template for hosting WordPress web-app and testing it with Selenium Grid, all using Docker Compose.

Refer to the following articles for more detail.
- [Quickstart guide for Compose and WordPress](https://docs.docker.com/compose/wordpress/).
- [The docker-selenium Github repo](https://github.com/SeleniumHQ/docker-selenium).

# Instructions

## 1. Install Docker CE and Docker Compose.

For installing Docker, just follow the official documentation on the topic. It can be found [here](https://docs.docker.com/install/).

The preferred way of installing Docker Compose would be using `pip`. Just run the following command.
```console
$ pip install docker-compose
```

Detailed instructions on installing Docker Compose can be found [here](https://docs.docker.com/compose/install/).

## 2. Build and run the the Wordpress Compose.

Run `docker-compose up -f wordpress.yaml -d` from your project directory. The output would be something like the following.

```console
$ sudo docker-compose up -f wordpress.yaml -d
Creating network "wordpressdockerquickstart_default" with the default driver
Creating volume "wordpressdockerquickstart_dbdata" with default driver
Pulling db (mysql:5.7)...
5.7: Pulling from library/mysql
2a72cbf407d6: Pull complete
38680a9b47a8: Pull complete
...
Digest: sha256:691c55aabb3c4e3b89b953dd2f022f7ea845e5443954767d321d5f5fa394e28c
Status: Downloaded newer image for mysql:5.7
Pulling wordpress (wordpress:latest)...
latest: Pulling from library/wordpress
ec5ac8875de7: Pull complete
69aff47f3112: Pull complete
...
Digest: sha256:201d004f55669dd2c0884f00fc44145fb0da8cafa465bf22cbaacecaf81138d4
Status: Downloaded newer image for wordpress:latest
Creating wordpressdockerquickstart_db_1 ... done
Creating wordpressdockerquickstart_wordpress_1 ... done
```

Once it's done, you can open WordPress at `http://YOUR_IP:8000`. Afterwords, follow the famous five-minute installation of WordPress to boot up your site.

## 3. Build and run the Selenium Grid Compose.

Run the following from your project directory. 
```console
$ sudo docker-compose -f selenium-grid.yaml up -d
```

The output would be similar as of step 2. Once it's done, you can access the Selenium Grid console at `http://localhost:4444/grid/console`.

## 4. Run the tests.

Install the Python3 selenium bindings.
```console
$ pip3 install selenium
```

Then, run the tests as
```console
$ python3 -m unittest
..
----------------------------------------------------------------------
Ran 2 tests in 7.686s

OK
```
