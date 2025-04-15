**Set up Google Cloud**
First, download Google Cloud SDK and installed it locally
Then choose the default project you are working on in the account by using:
  gcloud config set project <your-project-name>
  
Next, enable Artifact Registry
Then, I created a repository in the Artifact Registry in Australia Southeast 2. If you did not 
choose the location, the default will be US and it would not work
  gcloud artifacts repositories create my-repo --repository-format=docker --location=australia-southeast2

Then, to use the repository, I need to authenticate with Google Cloud, using this command.
  gloud auth configure-docker australia-southeast2-docker.pkg.dev
This will allow me to upload to the repository

**Working with the image**
First, I get the files from the last task 5.1P to a new folder sit323-2025-prac5d.
Then open the code, build a new docker image:
  docker build -t gcr.io/<your-project-id>/my-repo/<image-name> .
  
In the docker tools, I will push the image to the repository
It will ask me for the tag for the image, I used this:
australia-southeast2-docker.pkg.dev/<project-id>/my-repo/<image-name>

**Confirming the process**
After pushing, if I go to my-repo repository, I will see sit323-task5p has been uploaded.
To test the microservice, in the terminal, I will use:
 docker run -p 3040:3040 australia-southeast2-docker.pkg.dev/<project-id>/my-repo/<image-name>


 
