![Image](https://user-images.githubusercontent.com/108484798/203839587-153923ef-8e9c-40d3-828b-2ad46b71136e.jpg)

# Azure App Service Full Docker CI/CD
Small example of a CI/CD workflow

On Code change and pull request on github, the Code will be testet.

If test looks good, next step is merging.

After merge the publish workflow will dockerize the code from github,
push it on dockerhub and Azure App Service will fetch it as the new version of the webapp

## Tools used
- [FastAPIScrapeGameNews](https://github.com/PatrickDegner/FastAPIScrapeGameNews) - My FastAPI repo
- [GitHub](https://github.com) - Push the Code
- [Docker](https://docker.com) - Create the container
- [DockerHub](https://hub.docker.com/) - Push the container
- [GitHub Actions](https://github.com/features/actions) - Workflow to test and deploy
- [Azure APP Service](https://azure.microsoft.com/de-de/products/app-service/#overview) - Push the container and host the code

## How it works

The App is deployed on Azure

![image](https://user-images.githubusercontent.com/108484798/203843733-c6fdd524-3d31-4720-a695-fd7d19cfb4cb.png)


On change,

![image](https://user-images.githubusercontent.com/108484798/203844154-ef775030-022a-4410-a7e5-2c22c6cbc390.png)

and pull request from dev branch, github actions triggers its testing workflow


- [The tests.yml](https://github.com/PatrickDegner/Azure_App_Service_Docker_CICD/blob/master/.github/workflows/tests.yml) - the test workflow

- [The unittests](https://github.com/PatrickDegner/Azure_App_Service_Docker_CICD/blob/master/tests/test_app.py) - the unittests


![image](https://user-images.githubusercontent.com/108484798/203846451-5cfe3039-0c91-4701-a670-bc16587e444b.png)
![image](https://user-images.githubusercontent.com/108484798/203846531-9016b19f-31da-4100-a119-c4608fce4e0a.png)

The pull request looks fine we merge and the next workflow will run to deploy the app on docker/dockerhub and azure app service

1. The code will be dockerized
- [The Dockerfile](https://github.com/PatrickDegner/Azure_App_Service_Docker_CICD/blob/master/Dockerfile) - Create the container
2. The image will be pushed to dockerhub and published on Azure App Service
- [The Workflow yml](https://github.com/PatrickDegner/Azure_App_Service_Docker_CICD/blob/master/.github/workflows/deploy.yml) - Run Workflow

![image](https://user-images.githubusercontent.com/108484798/203847115-abd04519-c3a4-4b7e-a547-4851b380c6ef.png)

After deployment the Webapp will show the new headline

![image](https://user-images.githubusercontent.com/108484798/203847307-b78e4e79-7843-40d0-8447-2e2d562bd73a.png)


All done! :)
