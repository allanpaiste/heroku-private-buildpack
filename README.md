# heroku-private-buildpack

This supports loading a build pack from a private git repository.

It hooks in only to the release and compile api.

## Usage

1. Add the buildpack: 

  ```shell
  heroku buildpacks:add --index 1 https://github.com/allanpaiste/heroku-private-buildpack.git -a my-application
  ```

1. Add a file in the project root `.heroku-private-build.lst` that would contain plain list of private build pack repository URLs:

  ```text
  git@github.com:my-company/my-secrent-buildpack-a.git
  git@github.com:my-company/my-secrent-buildpack-b.git
  ```

3. Add the base64 enocded deploy key to the BUILDPACK_SSH_KEY env variable
    
   ```shell
   heroku config:set BUILDPACK_SSH_KEY=$(cat path/to/your/keys/id_rsa | base64)
   ```