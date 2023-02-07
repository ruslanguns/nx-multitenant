# Nx Multitenant Proof of Concept

This project is a proof of concept of an Automated Multi-Tenant Application

This monorepo includes two applications, an admin and a client application. The admin application will have a simple CRUD to add clients. When there is an activity with one of the clients from the admin dashboard, it will trigger a automated deployment pipeline with the respective values of each client, which will deploy the client application in a separated application with its own resources (ie. database, etc).

## Technologies

- [Nx](https://nx.dev/)
- [NextJs](https://nextjs.org/)
- [Github Actions]()
- [Docker](https://www.docker.com/)
- [Kubernetes](https://kubernetes.io/)
- [Helm](https://helm.sh/)
- [PrismaJS](https://www.prisma.io/)
- Database TBD

## Development server

Run `nx serve <admin | client>` for a dev server. Navigate to http://localhost:4200/. The app will automatically reload if you change any of the source files.

## Roadmap

- [x] Add admin app to the monorepo
- [x] Add client app to the monorepo
- [x] Add Dockerfile to build docker images
- [x] Add build-image script to build docker images
- [ ] Add push-image script to push docker images to a registry
- [ ] Add helm chart for deployment
- [ ] Add deploy script to deploy the helm chart
- [ ] Add CI/CD pipeline to test, build and release.
- [ ] Add CI/CD pipeline to manual deploy the admin app
- [ ] Add CI/CD pipeline to manual deploy the client app (this may be replaced by a pipeline trigger)
- [ ] Configure a pipeline trigger to deploy client via API
