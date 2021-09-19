# devel.farm

## Variables 

Variable Precedence least to greatest

- **Play vars_files**
  > Set in `devel.farm/site.yml`
  - `endpoints.yml`
    > Required endpoint vars
    > 
    > Should `endpoints.yml` be included in `defaults/main.yml`?
    >
    > Combine `endpoints` w/ `endpoints_overrides` or keep sperate for use in custom templates only (`endpoints_custom`)?
  - `devel.farm/user_overrides.yml`
    > Domain specific overrides
    >
    > Default play uses `user_overrides.yml`
- **Extra vars**
  > Set in `Dockerfile-build.devel.farm`
  - `devel.farm/custom.yml`
    > Vars used in custom menu templates

## Custom Templates

- `devel.farm/menus/*.j2`
  > Custom ipxe menu j2 templates
  >
  > `COPY devel.farm/menus/ /etc/netbootxyz/custom/`

## Build

```
podman build -t netboot.devel.farm -f Dockerfile-build.devel.farm .
```

## Output

```
podman run --rm -it -v $(pwd):/buildout:Z netboot.devel.farm
```