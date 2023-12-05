# Airflow Container Builder

### usage

1. click green `Use this template` button above
2. add your dependencies to `requirements.txt`
3. run `git tag v1.0.0` to build an image
4. run `git push --tags` to publish that image
5. the published image will appear to the right of your repo on github
6. to update your image, modify your `requirements.txt` and create a fresh tag
7. `git tag v1.0.1`
8. push the tag to publish the new image  `git push --tags`
