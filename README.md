debops-examples-2
=================

All the roles found in `./roles` should install successfully. Note that some roles have a 'role_name' set in `meta/main.yml`. In these instances, the role_name value should be used. If no role_name value is set, then the role name is the subdirectory name. 

After successfull install, the `~/.ansible/content/roles` directory, on the local file system, should contain the following directories:

```
~/.ansible
    content/
        roles/
            <namespace>.apache/
            <namespace>.foo/
            <namespace>.example/
            <namespace>.example-2/
```

In the above example, &lt;namespace&gt; is determined by Galaxy CLI based on the resource passed to the `install` command. Suppose this repository is imported into Galaxy under the Galaxy Namespace 'foo', and the user passes a Galaxy resource as follows:

```
$ ansible-galaxy-cli content-install -t role foo.debops-examples-2 
```

The above will install all roles found in `foo.debops-examples-2`, resulting in the following directory tree: 

```
~/.ansible
    content/
        roles/
            foo.apache/
            foo.foo/
            foo.example/
            foo.example-2/
```

Now suppose that the user passes an SCM+URL resource to the installer, as in the following example:

```
$ ansible-galaxy-cli content-install -t role git+https://github.com/atestuseraccount/debops-examples-2.git 
```

Because the project exists in the GitHub namespace `atestuseraccount`, the roles should be installed with a namespace of `atestuseraccount`. The resulting installed directory tree will look like the following:

```
~/.ansible
    content/
        roles/
            atestuseraccount.apache/
            atestuseraccount.foo/
            atestuseraccount.example/
            atestuseraccount.example-2/
```
