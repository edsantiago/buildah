## buildah-containers "1" "March 2017" "buildah"

## NAME
buildah containers - List the working containers and their base images.

## SYNOPSIS
**buildah** **containers** [*options* [...]]

## DESCRIPTION
Lists containers which appear to be Buildah working containers, their names and
IDs, and the names and IDs of the images from which they were initialized.

## OPTIONS

**--all, -a**

List information about all containers, including those which were not created
by and are not being used by Buildah.  Containers created by Buildah are
denoted with an '*' in the 'BUILDER' column.

**--json**

Output in JSON format.

**--noheading, -n**

Omit the table headings from the listing of containers.

**--notruncate**

Do not truncate IDs in output.

**--quiet, -q**

Displays only the container IDs.

## EXAMPLE

buildah containers
```
CONTAINER ID  BUILDER  IMAGE ID     IMAGE NAME                       CONTAINER NAME
29bdb522fc62     *     3fd9065eaf02 docker.io/library/alpine:latest  alpine-working-container
c6b04237ac8e     *     f9b6f7f7b9d3 docker.io/library/busybox:latest busybox-working-container
```

buildah containers --quiet
```
29bdb522fc62d43fca0c1a0f11cfc6dfcfed169cf6cf25f928ebca1a612ff5b0
c6b04237ac8e9d435ec9cf0e7eda91e302f2db9ef908418522c2d666352281eb
```

buildah containers -q --noheading --notruncate
```
29bdb522fc62d43fca0c1a0f11cfc6dfcfed169cf6cf25f928ebca1a612ff5b0
c6b04237ac8e9d435ec9cf0e7eda91e302f2db9ef908418522c2d666352281eb
```

buildah containers --json
```
[
    {
        "id": "29bdb522fc62d43fca0c1a0f11cfc6dfcfed169cf6cf25f928ebca1a612ff5b0",
        "builder": true,
        "imageid": "3fd9065eaf02feaf94d68376da52541925650b81698c53c6824d92ff63f98353",
        "imagename": "docker.io/library/alpine:latest",
        "containername": "alpine-working-container"
    },
    {
        "id": "c6b04237ac8e9d435ec9cf0e7eda91e302f2db9ef908418522c2d666352281eb",
        "builder": true,
        "imageid": "f9b6f7f7b9d34113f66e16a9da3e921a580937aec98da344b852ca540aaa2242",
        "imagename": "docker.io/library/busybox:latest",
        "containername": "busybox-working-container"
    }
]
```

## SEE ALSO
buildah(1)
