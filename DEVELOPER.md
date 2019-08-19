Developer documentation
=======================

### Releasing

Maven repository is no longer the main source of releases, but WinSW can be deployed there on-demand.
Some projects (e.g. [Jenkins](https://jenkins.io)) still depend on WinSW from the Maven repository.

1. Make sure you have passed the Release steps above
2. Modify the `winsw.version` property to the the release version (`WINSW_VERSION`)
3. Modify version field to `${WINSW_VERSION}-SNAPSHOT`
4. Run `mvn release:prepare release:perform`
