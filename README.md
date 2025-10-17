# TURTLE ROS2 Workspace Template

This is a template to be used as a template for a ROS 2 workspace.

## Using this template

Requires:
 * Docker: [Download](https://www.docker.com/products/docker-desktop/)
 * WSL2 (Windows Only): [Enable](https://learn.microsoft.com/en-us/windows/wsl/install)
 * Visual Studio Code: [Download](https://code.visualstudio.com/)
    * Dev Containers Extension: [Install](vscode:extension/ms-vscode-remote.remote-containers)
 * Git: [Download](https://git-scm.com/)

First, create a copy of this template on GitHub. Clone the new repository. If developing on Windows, enable WSL. Open Docker Desktop and ensure Docker is running.

Open the template folder in Visual Studio Code. Ensure the Dev Containers Extension is installed. Click the >< button in the bottom left, and select `Reopen in Container`. ROS will be downloaded and installed in the container.

**Caution**: Docker containers are temporary. The files written to the workspace folder will be saved, but all other folders and packages installed in the container will be removed when the container is closed. Be sure to record all workspace dependencies in your `package.xml` files or `devcontainer.json` `postStartCommand`.