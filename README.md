# gitlab

This project is to run a dockerised gitlab server and runner(s). 

Note: Firewall must be disabled to allow access to ports exposed by gitlab server

docker-compose up -d

After the services are up, we add gitlab to localhost at /etc/hosts and then we can visit gitlab:9090 to get the registration token for the shared gitlab runners. The runners can be scaled up as required. Each runner must be registered using the following command:

docker exec -it gitlab_runner_1 gitlab-runner register -n   --url http://gitlab:9090/ --registration-token <token> --executor docker   --description "My Docker Runner"   --docker-image "docker:latest"   --docker-privileged --docker-extra-hosts "gitlab:<ipaddress of host>"

