# SVN on docker!
Quick notes on setting up a lightweight SVN server that is accessible via http (WebDav) and the svn custom protocol (svn://).

credits to : https://medium.com/@elle.florio/the-svn-dockerization-84032e11d88d

## Pre-reqs

- Docker (see ['Install Docker for Mac'](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac))
- SVN (should be installed on your Mac by default)

## Steps
This guide uses a lightweight svn-server docker image called [elleFlorio/svn-docker](https://github.com/elleFlorio/svn-docker). To set up

- 1 ) Create an svn-root volume to hold your svn-server repos on your docker host
  ```sh
  $ docker volume create svn-root
  ```
- 2 ) Run the docker container and set your _working directory_ to **/home/svn**
  ```sh
  $ docker run -dit --name svn-server -v svn-root:/home/svn -p 7443:80 -p 3690:3690 -w /home/svn elleflorio/svn-server
  ```
- 3 ) Configure a username and password to access http protocol
  ```sh
  $ docker exec -t svn-server htpasswd -b /etc/subversion/passwd svnadmin <password>
  ```
- 4 ) Verify that the svn services is up and showing 0 repos available
  ```sh
  $ svn info svn://localhost:3690/
  
  svn: E170013: Unable to connect to a repository at URL 'svn://localhost:3690'
  svn: E210005: No repository found in 'svn://localhost:3690'
  ```

- 5 ) Log in to your svn server using URL: http://localhost:7443/svn. You should see an empty listing with "Collection of Repositories" string on top
- 6 ) Create a test svn repo using svnadmin command. verify repo exsits both in command line and web page

  ```sh
  $ docker exec -it svn-server svnadmin create Test
  ```
  
  ```sh
  $ docker exec -it svn-server ls -al Test

  total 16
  drwxr-xr-x   8 primetheus  staff  272 Jun  7 15:22 .
  drwxr-xr-x   3 primetheus  staff  102 Jun  7 15:22 ..
  -rw-r--r--   1 primetheus  staff  246 Jun  7 15:22 README.txt
  drwxr-xr-x   6 primetheus  staff  204 Jun  7 15:22 conf
  drwxr-sr-x  15 primetheus  staff  510 Jun  7 15:22 db
  -r--r--r--   1 primetheus  staff    2 Jun  7 15:22 format
  drwxr-xr-x  11 primetheus  staff  374 Jun  7 15:22 hooks
  drwxr-xr-x   4 primetheus  staff  136 Jun  7 15:22 locks
  ```

  ```sh
  $ svn info svn://localhost:3690/Test

  Path: Test
  URL: svn://localhost:3690/Test
  Relative URL: ^/
  Repository Root: svn://localhost:3690/Test
  Repository UUID: 626ee621-fc48-49e1-8733-3f850e997e67
  Revision: 0
  Node Kind: directory
  Last Changed Rev: 0
  Last Changed Date: 2017-06-07 15:22:54 -0500 (Wed, 07 Jun 2017)
  ```

## Load test subversion repo
Let's load a test SVN repository, located [here](https://svn.code.sf.net/p/ultrastardx/svn). 

- Dump SVN repo to local Docker container
  ```sh
  $ docker exec -it svn-server sh -c "svnrdump dump https://svn.code.sf.net/p/ultrastardx/svn | gzip > /tmp/ultrastardx.dump.gz"
  ```
- Create new repo to host code
  ```sh
  $ docker exec -it svn-server svnadmin create ultrastardx
  ```
- Load in the SVN dump archive (make sure your dashes and quotes aren't funky here)
  ```sh
  $ docker exec -it svn-server sh -c "gunzip -c /tmp/ultrastardx.dump.gz | svnadmin load ultrastardx"
  ```
- Check to see that repo has been loaded properly
  ```sh
  $ svn info svn://localhost:3690/ultrastardx
  ```

## login to the docker: 
  ```sh
 docker exec -it svn-server sh
  ```
