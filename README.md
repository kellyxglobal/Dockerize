What is a Base image in Docker:
A quick analogy to understand the coffigurations in the docker file:

[Writing a dockerfile] === [Being given a computer with no OS and being told to install Chrom]

What you will end up doing. Work Flow:

[Install an OS] => [Start your default browser] => [Navigate to chrome.google.com] => [Download installer] => [Open file/folder explorer] => [Execute chrome_installer.exe] => [Execute chrome.exe]

The above explains why we need to execute FROM alpine as a base image which acts as "installing OS" in the above analogy.

{Why did we use alpine as a base image?}
		||
Why do you use Windows, MacOS, or Ubuntu
		||
{They come with a preinstalled set of 
programs that are useful to you}

ALPINE includes the default sets of programs that are very useful to what we are trying to accomplish. Since we are trying to run and set up redis, alpine has a set of program inside of it that are very useful for installing and running redis.
apk on the other hand is an apache package manager, a program pre-installed on alpine which we can use to automatically download and install redis for us.







The Build Process in Details:
	[FROM   ||  alpine]
		|| 
||======>[Download alpine image]
||
||	[RUN 	||  apk add --update redis]
||
||=====[Get image from previous step]
       [Create a container out of it]	====>	[Container]
       [Run 'apk add --update redis' in it] ==> [Container with modified FS]
       [Take snapshot of that container's FS] ==>[FS snapshot]
       [Shut down that temporary container]
||====>[Get image ready for next instruction]
||
||     [CMD	||	"redis-server"]
||
||=====[Get image from last step]
       [Create a container out of it]===>[container]
       [Tell a container it should
       run "redis-server" when started]==>[Container! with modified pri-command]
       [Shut down that temporary container]
       [Get image ready for next instruction]
  [		No mor steps!		]
[Output the image generated from the previous step.]



======
Rebuilding everything with Cache in Docker by modifying the Dockerfile:
custom image. Eg.
# use an existing docker image as a base
FROM alpine
# Downlaod and install a dependency
RUN apk add --update redis
RUN apk add --update gcc
# Tell the image what to do when it starts 
# as a container
CMD ["redis-server"]

Rebuild the Dockerfile



======
Tagging an Image in Docker: This simply means creating a container out using the image id. We can tag an image to a name that we can customize.
docker run <container ID>
docker build -t kellyxglobal/redis:latest .



======
Node Server Setup in Docker:
- Create Node JS web app
- Create a Docker file
- Build image from dockerfile
- Run image as container
- Connect to web app from a browser

