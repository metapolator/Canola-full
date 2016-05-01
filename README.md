# Canola
Project folder for Metapolator with the Canola font


## create canola.mp from scratch

The `mom` command is in https://github.com/graphicore/Atem-MOM/blob/master/bin/mom I symlinked it into my users bin directory as `mom`.

An import from UFO always creates a "Base-Master". We use the `base-` prefix as a convention to mark it up.

```bash
$ mom init canola.mp
$ mom import -g `cat subset.txt` canolaSource.ufo canola.mp/base-regular
```

Now you need to set up a first "UI-Master" for Metapolator.

*NOTE* the `master-` prefix is important, it tells Metapolator that this is a "UI-Master" (not an Instance-Master and not a Base-Master)

```bash
$ mom derive base-regular canola.mp/master-regular
```

To complete the new "UI-Master" and make it functional a piece of CPS must be inserted:

```bash
$ echo "@import 'lib/metapolator/metamaster.cps';" > canola.mp/data/com.metapolator/CPS/master-regular.master.cps
```

The new Master `master-regular` should be added to the "session" a mechanism that is intended to make large projects managable by not loading everything at once. Edit the file `canola.mp/data/com.metapolator/project.yaml` to tell Metapolator that it should open the master on startup:

```
session:
  masters: [master-regular]
```



The resulting Metapolator-Project `.mp` file (directory) looks like this:

```bash
$ tree canola.mp
canola.atem.mp/
├── data
│   └── com.metapolator
│       ├── CPS
│       │   └── master-regular.master.cps
│       ├── MOM
│       │   ├── base-regular.master.yaml
│       │   ├── master-regular.master.yaml
│       │   └── multivers.yaml
│       └── project.yaml
├── glyphs
│   └── contents.plist
├── layercontents.plist
└── metainfo.plist
```


