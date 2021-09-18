# Netboot.xyz overrides for devel.farm

- Role default overrides: `devel.farm/overrides.yml`
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