# Notes INI Playbook

## Brief overview:
The Notes INI Playbook application helps the administrators and LOB (line of business) users (who use HCL Notes) to enable and disable the 
INI debug parameters on the user’s Notes client for the troubleshooting purpose. It also helps to track 
the status of Notes client debugging of all users. The application is easy to use for both administrators 
and LOB users.

## Target audience:
The target audience of this application are the administrators and the LOB users who use HCL Notes.

## Relevant versions:
The application can run on any version of Notes client starting from v9.0.x and above.

## Documentation & Quickstart

See the [documentation](docs/index.md) and the [Quickstart](docs/quickstart.md) for details

## Enhancement requests and issues:
The enhancement requests and issues should be reported here at Github portal only.

## Issues
For issues relating specifically to the Dockerfiles and scripts, please use the [GitHub issue tracker](issues)

## Contributing
We welcome contributions following [our guidelines](CONTRIBUTING.md).

## Supported environments

The project is supported on Docker Desktop, Docker Server, Podman, Rancher Desktop, Kubernetes (K8s) and OpenShift.
See detailed information about [supported run-time and build environments](docs/concept_environments.md).

## License
The Dockerfiles and associated scripts are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0.html). 

License for the products that can be installed within the images is as follows:
* HCL Domino Enterprise Server 12 under the [HCL License Agreement](https://www.hcltechsw.com/wps/portal/resources/license-agreements)
* HCL Domino Volt under the [HCL License Agreement](https://www.hcltechsw.com/wps/portal/resources/license-agreements)
* HCL Notes Traveler under the [HCL License Agreement](https://www.hcltechsw.com/wps/portal/resources/license-agreements)

Note that HCL Domino and add-on products are commercial software - The software licenses agreement does not permit further distribution of the docker image that was built using this script.
