# Netboot.xyz overrides for devel.farm

- Role default overrides: `devel.farm/user_overrides.yml`
- Required endpoint vars: `endpoints.yml`
- ~~Custom endpoint vars: `devel.farm/endpoints.yml` (endpoints_overrides)~~
    - Combine `endpoints` w/ `endpoints_overrides` or keep sperate for use in custom templates (`endpoints_custom`)?
- Custom menu vars: `devel.farm/custom.yml`
- Custom menu j2 templates: `devel.farm/menus`
- Custom build Dockerfile: `Dockerfile-build.devel.farm`

## Build

```
podman build -t netboot.devel.farm -f Dockerfile-build.devel.farm .
```

## Output

```
podman run --rm -it -v $(pwd):/buildout:Z netboot.devel.farm
```