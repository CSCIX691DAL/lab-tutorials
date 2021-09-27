# Running The App

In Windows, generating a dockerized laravel project
requires a relatively complex Windows Subsystem for Linux (WSL) setup.
Therefore, we are skipping that.
Just clone this repository, and you have a dockerized 
laravel project in the `lab-1/php/hello-laravel` directory.

Run the following command

```shell
docker-compose run --rm --name hello-laravel-running -p 80:80 laravel.test
```

You will see output similar to the following
![image](https://user-images.githubusercontent.com/13452649/134986615-ee62cb2e-10f8-488c-b32c-24e9bdad7b4e.png)

Now visit http://localhost. You have the site running.

![image](https://user-images.githubusercontent.com/13452649/134986737-43692279-1915-446e-86c2-ce8fdef6074f.png)

Good luck for your exploration!
