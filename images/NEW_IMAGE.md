# Adding new image

Adding new images to drupal-docker organization requires some manual steps on Github, Travis and Docker Rgistry. 

## Github

1. Create repository. Name should be consistent with name of image (i.e. drupaldocker/redis -> redis)
1. Add MIT Licence (see under [License Policy](/POLICY.md#LICENSE)).
1. Hide Github Wikis.
1. Add new repository to team "Images" with Write access.
1. Add master branch to protected branches.
1. Turn on "Protect this branch", "Require pull request reviews before merging", and "Require status checks to pass before merging"

## Travis

1. Enable tests for new repository.
1. Turn on "Build only if .travis.yml is present" option
1. Add .travis.yml to repository (find [example](https://github.com/drupal-docker/php/blob/master/.travis.yml) in other repositories).

## Docker hub

1. Create automated build within drupaldocker organisation.
1. Go to "Build Settings" and add all tags required for new repository.
1. Add repository link (upstream images)
