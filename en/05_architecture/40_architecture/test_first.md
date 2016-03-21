# Test-First

## Test Partition

Test can be defined by domain departments members or by software developers. Technically these tests are mapped to unit- or integration-tests.

1. Unit: Are testing on unit level only.
2. Integration: Are testing the various integrations based on their configurations.

## unit test
On the level of one unit we can test either pure functions (if there are no side effects) or behavior (if there are side effects and we want to test them). Best Practices for unit tests are:
1. To build our test data entities, we use the builder pattern. Test-Data-Builders are located in unit test source folder.
2. To build more complex nets of test data entities, we use test data fixtures. Test-Data-Fixtures are located in unit test source folder.

While pure functional test are quite easy, the behavioral test bring in some preconditions:
1. We have to use strictly Dependency Injection (e.g. use spring)
2. All modules not belonging to our unit under test will be represented by a mock.

## integration test
Integration tests are defined for on specific configuration. If there are many configurations under test, there should be many sets of integration tests. Best Practices for integration tests are:
1. Setup your persistence to a defined state.
2. Generate your test data synthetically by using the unit-test test builders.
3. Rollback transaction after you've done the test.

## Further usefull tools
* greenmail for emails.
* Mockito for mock-injection.