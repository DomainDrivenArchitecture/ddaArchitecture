#Testing

TODO: 
* Add context for resources & tests
* introduce xBox-Tests
* introduce test Scopes
* introduce cost @analysis

To test the installation (e.g. when performing an integration test) there is a seperate phase called **test**.

![](../../resources/testing.png)


##Resources

In the first step **test resources** are defined. A test resource is an output of a linux shell script. For example `ps -A` to test for a running process after install or also the raw content of a file using `cat /etc/hosts`.

Defining the resources is required to perform tests not only on the remote node machine, but also on the machine running the JVM. When resources are defined their output is transfered to the JVM machine and can be interpreted and tested. There must be no credentials or secrets in resources since they might be saved and displayed in test results.

Outputs and scripts for creation of resources are saved in `/home/pallet/state/resources-$TIMESTAMP`. There is a link from `/home/pallet/state/resources-current` to the latest resources.

All resources must be identified using a unique key. To guarantee uniqueness of keys one should use namespaced keywords in clojure, e.g. `::my-resource`. The key of a resource corresponds to the filename in the resource folder.


##Tests

There can be multiple tests and each crate can define own tests or use tests that are provided by other crates. If any test fails the execution of other tests is continued.

##Local test

A **local test** is a test performed on the executing node using already defined resources. There is no further interaction between the executing node and the target node.

A local test...

* is a clojure function getting the resource as input.
* evaluates to `nil` or `false` iff the test failes.
* may output additional information on stdout, which are collected in the test-result.
* can easily be unit-tested since no executions on a remote node are involved.

##Remote tests

A **remote test** is a test performed on the target node. It is specified by a shell script and its exit code corresponds with the test result. 

In detail the test script...

* receives the specified resource on stdin.
* must exit with code 0 iff the test passes.
* can print additional information to stdout.
* is more difficult to test than local tests (since a test framework for shell script must be integrated).

Remote tests are useful if additional server state is required.
