# git-tag-versioning
Demonstrate git tags as version store

# Show all tags
```
git tag -l --format='%(creatordate)%09%(refname:strip=2)%09%(objectname)'

Tue Feb 15 13:34:13 2022 +0200  serviceA-v0.1.0 11cf794ac1e2b0ee56eaaa35ffda4b2ee7d6fc24
Tue Feb 15 13:44:12 2022 +0200  serviceA-v0.2.0 7da03b814de56d6cc291dc9be7c66577e99aeb44
Tue Feb 15 13:36:42 2022 +0200  serviceB-v0.1.0 90a944a83299570ec243794d55638670f96bbf63
Tue Feb 15 13:43:43 2022 +0200  serviceB-v0.2.0 00ff286e59d37a7cbe4397fe9b305d0b5d827032
Tue Feb 15 13:37:30 2022 +0200  serviceC-v0.1.0 4ea98f28595353b34acbe668e5d5de85dc093d69
Tue Feb 15 13:44:15 2022 +0200  serviceC-v0.2.0 79eb963526efdf24eac61ad7dae78a453f2049c6
```

# Show versions of specific service
```
git tag -l "serviceA*" --format='%(creatordate)%09%(refname:strip=2)%09%(objectname)'

Tue Feb 15 13:34:13 2022 +0200  serviceA-v0.1.0 11cf794ac1e2b0ee56eaaa35ffda4b2ee7d6fc24
Tue Feb 15 13:44:12 2022 +0200  serviceA-v0.2.0 7da03b814de56d6cc291dc9be7c66577e99aeb44
```

# Show versions of serviceA at specific point in time
```
git log -q --tags --pretty=format:'%d' --after='2022-02-15 11:30:00' --before='2022-02-15 11:37:00' | grep serviceA | sed 's/(tag: serviceA-\(.*\))/\1/'

v0.1.0
```

Querying version of a service by date requires tooling on top of `git` because `git tag` does not support date filters.
