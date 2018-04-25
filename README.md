# comp698-final

Final project is to replicate the architecture we have worked on
this semester with a new project.  Follow the tasks below and when
you're done, ensure your README.md file contains an explaination
of the project.  Ensure the README.md file contains a summary of the project which includes at a minimum the following information:

* Why use git?
* Why write an application in golang?
* What purpose does Travis CI serve?
* What is the purpose of terraform?
* Why use virtualized resources?
* Include a diagram of the architecture from laptop to GCP
* Why use bash commands vs clicking through UI?
* Why docker vs installing application directly on the host?
* What protections are there against accidentally introducing bad code into production?

Along the way, make sure that you:

* use meaningful commit messages
* make all changes beyond initial setup are made through pull requests

Tasks:

1) Create a new Github repo

* repository should be named comp698-final
* initialize it with a README.md
* clone it to your laptop
* configure the Github repo to protect your master branch
	* require status checks before merging
	* including administrators

2) initial hello world application

* create a hello world server using this source [helloworld-source](https://github.com/mathyourlife/comp698-final/tree/helloworld-source)

3) add Dockerfile

* Create a Dockerfile based on the content here [helloworld-dockerfile](https://github.com/mathyourlife/comp698-final/tree/helloworld-dockerfile) or see the diff of what is changed [diff](https://github.com/mathyourlife/comp698-final/compare/helloworld-source...helloworld-dockerfile)

4) add travis ci PR validation

* add a `.travis.yml` file through a PR based on this source [helloworld-travisci](https://github.com/mathyourlife/comp698-final/tree/helloworld-travisci) or see the diff of what is changed [diff](https://github.com/mathyourlife/comp698-final/compare/helloworld-dockerfile...helloworld-travisci)

5) update travis ci for PR validation and functional testing

* trigger a build and make sure it passes

6) add GCP build trigger

* trigger should build new docker images based on changes to master
* publish images to your GCP project with the `gcr.io/$PROJECT_ID/$REPO_NAME:$COMMIT_SHA` format
* ensure the comp698-final repo is able to build a new image by triggering a build

7) create terrform to deploy hello world version to 1 staging server

* add terraform configuartion files to your github repo in a terraform subdirectory
* use the terraform-configuration server to deploy a hello world server to a "staging" server with an external ip address
* ensure your webpage loads

8) update application code to full

* update your application code to a javascript bootstrapped server based on the source [bootstrap-source](https://github.com/mathyourlife/comp698-final/tree/bootstrap-source) or see the diff of what is changed [diff](https://github.com/mathyourlife/comp698-final/compare/helloworld-travisci...bootstrap-source)
* from the next version of the application [bootstrap-source](https://github.com/mathyourlife/comp698-final/tree/bootstrap-source)
	* update the main.go, main_test.go, Dockerfile, functional-test.sh files
	* include the static directory
* ensure the merged changes successfully build a new image in GCP

9) update terraform to deploy full app to 1 staging server and hello world to 1 prod server

* update the terraform configuration files
* use the terraform-configuration server to move the hello world server to a "prod" instance and the bootstrap server to a "staging" server
* ensure the "prod" server loads a hello world response
* ensure the "staging" server loads a bootstrap server (use a `http://[ip address]/home`)
