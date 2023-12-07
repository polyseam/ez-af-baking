<img src="./docs/img/ez-af-baker.png" height="400" width="1200"/>

<br/>
<br/>

<center>
<h1>EZ AF Baking</h1>
for baking Airflow images with custom dependencies
</center>

## Usage

### Setup Repo

Click the
[Use this template](https://github.com/new?template_name=ez-af-baking&template_owner=polyseam)
button!

### Set Requirements

1. Pull down the repo
2. Add your dependencies to `requirements.txt`

### Push Code to GitHub

1. `git add .`
2. `git commit -m "added dependencies"`
3. `git push`

### Publish Image to the Container Registry

Automation will publish your image when you push a tag to the repo.

1. run `git tag v1.0.0` to designate an image version
2. run `git push --tags` to publish that version
3. the published images should be shown in the GitHub packages tab over there ↗️

### using the image in Airflow Kubernetes (optional)

Now that you have an image in the [GitHub Container Registry](https://ghcr.io),
you need to be able to consume it from Airflow.

- If you are using Polyseam's [CNDI](https://github.com/polyseam/cndi), here is
  [an example here showing how to securely apply that secret for your Airflow Container Image](./docs/examples/cndi).

- There is also an
  [example provided here](./docs/examples/plain/registry-secret.yaml) if you are
  using Airflow on Kubernetes without CNDI.

In either case once you've applied the Secret you just need to tell Airflow to
use it in your Helm Chart's values:

```yaml
values:
  registry:
    secretName: airflow-image-pull-secret
  images:
    airflow:
      repository: 'ghcr.io/johnstonmatt/my-baked-image'
      tag: v1.0.0
```
