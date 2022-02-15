# git-tag-versioning
Demonstrate git tags as version store

# Show all tags
```
git tag -l --format='%(creatordate)%09%(refname:strip=2)%09%(objectname)'
```

# Show versions of specific service
```
git tag -l "serviceA*" --format='%(creatordate)%09%(refname:strip=2)%09%(objectname)'
```

# Show versions of serviceA at specific point in time
```
git log -q --tags --pretty=format:'%d' --after='2022-02-15 11:30:00' --before='2022-02-15 11:37:00' | grep serviceA | sed 's/(tag: serviceA-\(.*\))/\1/'
```
