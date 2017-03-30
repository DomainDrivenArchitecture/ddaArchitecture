#Testing

TODO: 
* Add context for resources & tests
* introduce xBox-Tests
* introduce test Scopes
* introduce cost @analysis

To integration test a given installation (e.g. when performing an integration test) we use phase called **test**.

![](../../resources/testing.png)

The test itself is separated into two steps:
* Collect resources from target: Collecting resources from target system is executed on target and may not change targets state (with exception of /tmp and /home/pallet/state ). 
* Test against expectation: The resources are transported to executing system and can be tested there against expectation.


## Collect Resources

In the first step **test resources** are defined. A test resource is an output of a linux shell script. For example `ps -A` to test for a running process after install or also the raw content of a file using `cat /etc/hosts`.

Defining the resources is required to perform tests not only on the remote node machine, but also on the machine running the JVM. When resources are defined their output is transfered to the JVM machine and can be interpreted and tested. There must be no credentials or secrets in resources since they might be saved and displayed in test results.

Outputs and scripts for creation of resources are saved in `/home/pallet/state/resources-$TIMESTAMP`. There is a link from `/home/pallet/state/resources-current` to the latest resources.

All resources must be identified using a unique key. To guarantee uniqueness of keys one should use namespaced keywords in clojure, e.g. `::my-resource`.


## Execute Tests

There can be multiple tests and each crate can define own tests or use tests that are provided by other crates. If any test fails the execution of other tests is continued. 

A Test ...

* is a clojure function getting the resource as input.
* evaluates to `nil` or `false` if the test fails.
* may output additional information on stdout, which are collected in the test-result.
* can easily be unit-tested since no executions on a remote node are involved.

TODO: Move this information to relization part
##Remote tests

A **remote test** is a test performed on the target node. It is specified by a shell script and its exit code corresponds with the test result. 

In detail the test script...

* receives the specified resource on stdin.
* must exit with code 0 iff the test passes.
* can print additional information to stdout.
* is more difficult to test than local tests (since a test framework for shell script must be integrated).

Remote tests are useful if additional server state is required.
