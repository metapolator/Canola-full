# Canola
Project folder for Metapolator with the Canola font


## create canola.mp from scratch

```bash
$ metapolator init
$ metapolator import -g `cat subset.txt` ../canolaSource.ufo canola.mp/base
```

You need to set up a first "UI-Master" for Metapolator. Open `canola.mp/data/com.metapolator/project.yaml` in a text editor and change its content to:

```yaml
masters:
  base:
    cpsFile: base.cps
    propertiesFile: base.db
    skeleton: skeleton.base
  master-regular:
    cpsFile: master-canola.cps
    skeleton: skeleton.base
```



