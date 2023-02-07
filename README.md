# Nx Multitenant Proof of Concept

This project will create a proof of concept of an automated Multi-Tenant Application that is highly available and provides a secure, reliable, and high-performance platform. Leveraging the power of Nx, Next, CI&CD, Docker, and Kubernetes will enable us to quickly scale the application and provide an optimal user experience.

This monorepo includes two applications, an admin and a client application. The admin application will have a simple CRUD to add clients. When there is an activity with one of the clients from the admin dashboard, it will trigger a automated deployment pipeline with the respective values of each client, which will deploy the client application in a separated application with its own resources (ie. database, etc).

## Development server

Run `nx serve <admin | client>` for a dev server. Navigate to http://localhost:4200/. The app will automatically reload if you change any of the source files.

## TODOs

- [x] Add admin app to the monorepo
- [x] Add client app to the monorepo
- [x] Add Dockerfile to build docker images
- [x] Add build-image script to build docker images
- [ ] Add push-image script to push docker images to a registry
- [ ] Add helm chart for deployment
- [ ] Add deploy script to deploy the helm chart
- [ ] Add CI/CD pipeline to test, build, push and deploy the application (standalone)<sup>[1](#1)</sup>

### References:

##### 1

The CI/CD pipeline should be able to deploy the application in a standalone environment, where the admin and client apps are deployed separately. Since there will be more requirements to make a multitenant app.
