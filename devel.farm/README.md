# devel.farm

## Variables 

Variable Precedence least to greatest

- **Play vars_files**
  > Set in `devel.farm.yml`
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

### Build menus
---

```
podman build -t netboot.devel.farm.menus -f Dockerfile-build.devel.farm.menus .
```

### Build disks
---

```
podman build -t netboot.devel.farm.disks -f Dockerfile-build.devel.farm.disks .
```

### Build all
---

```
podman build -t netboot.devel.farm -f Dockerfile-build.devel.farm .
```

## Output

### Output menus
---

```
podman run --rm -it -v $(pwd):/buildout:Z netboot.devel.farm.menus
```

### Output disks
---

```
podman run --rm -it -v $(pwd):/buildout:Z netboot.devel.farm.disks
```

### Output all
---

```
podman run --rm -it -v $(pwd):/buildout:Z netboot.devel.farm
```