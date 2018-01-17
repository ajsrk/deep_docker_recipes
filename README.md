# deep_docker_recipes

This project maintains set up instructions for deep learning development environments. The environments are containerized using docker.

I have not stringently adhered to the principle of minimal image sizes as the purpose of these container recipes is to serve as a means to quickly set up a rich development environment for deep learning on CPUs and GPUs.
For production, one would surely want to optimize the size of container images by excluding libraries that are not required for the given application can run; you might also want to give the Alpine Linux images a shot.

