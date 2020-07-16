
> [!NOTE]
> During our private beta, platform deployments are restricted to Google's Cloud Platform. More cloud providers are to follow, as driven by customer demand.

# Google Cloud Platform

Before getting started with Seashell, it is necessary to have a valid Google Cloud Platform (GCP) account, at least one project and a corresponding service account. Below is all the information needed to properly configure this project and setup its service account for use with Seashell.

Information about creating and managing projects within GCP can be found in the official documentation [here](https://cloud.google.com/resource-manager/docs/creating-managing-projects).


### Enable APIs
Seashell requires the following APIs to be enabled in the project:
- Compute Engine API
- Cloud SQL Admin API

Further information about enabling and managing GCP APIs can be found in the official documentation [here](https://cloud.google.com/apis/docs/getting-started#enabling_apis).

### Configure a service account
Besides enabling the APIs, a configured service account is also required. To create a service account for your GCP project, refer to the official documentation [here](https://cloud.google.com/iam/docs/creating-managing-service-accounts#creating).

Seashell requires the following roles to be granted to the service account:
- Service Account User
- Cloud SQL Client

Further information about managing GCP IAM roles/access to resources can be found in the official documentation [here](https://cloud.google.com/iam/docs/granting-changing-revoking-access).

### Generate service account's credential keys
In order for Seashell to have access to the service account, a credential key must be generated. To create this key for your service account, refer to the official documentation [here](https://cloud.google.com/iam/docs/creating-managing-service-account-keys#creating_service_account_keys).

Further information about creating and managing service account keys can be found in the official documentaion [here](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).
