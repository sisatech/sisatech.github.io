# Apps Repository

Download or manage a local repository of Vorteil application packages. vcli
maintains a database of Vorteil applications that have been downloaded or
imported in order to provide helpful version control, data deduplication, and
a standardized location for publically distributed Vorteil applications.

Applications stored within the local repository have a name and a reference ID.
The name can include parent directories for organizational purposes. For
example, a "Hello, World!" application provided by Sisa-Tech Pty Ltd would
commonly be named "sisatech/helloworld". The reference ID is used for version
control when multiple versions of the same application exist within the
repository.

Other vcli commands that can accept a Vorteil package as an argument or flag can
access applications within the local repository by prefixing the location with
"apps:", like "apps:sisatech/helloworld". If a specific version of the app is
required, the location can have an optional suffix containing the reference ID,
like so: "apps:sisatech/helloworld:a9c9c21a0339".

## Example usage:

List the contents of the local vcli repository:
```
vcli apps list
```

Import a vorteil package to the repository:
```
vcli import <PATH_TO_VORTEIL_PACKAGE>
```

Tag an existing app version:
```
vcli apps tag <PATH_TO_STORED_APP> <TAG>
```
