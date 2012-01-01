#################
Predictable tests
#################

The predictable_tests module registers minimal tests which are predictable,
i.e. they always or never pass. You know which result to expect.

Here are some use cases where this module could help:

* in demo or tutorial: try tests that passes and others that fails;

* make sure that a continuous integration service acts as expected, i.e. test
  the deployment of such a service. When you deploy a continuous integration
  service, at first you want to be sure that it can run tests, and then that
  it handles "pass" and "fail" statuses. There comes predictable_tests;

* use "quick" tests. Standards tests bundled with Drupal or simpletest are
  quite slow to run. So predictable_tests will save us time where you just want
  to know whether you can successfully run tests or not;

* make sure there is no error in your installation. As examples, errors raised
  during tests could be related to Drupal or any module. Predictabletests'
  tests are really minimal, so the risk to get collateral errors is minimal.

Installation
============

With drush...

.. code-block: sh

  # Download and install predictable_tests
  drush dl predictable_tests
  drush en predictable_tests

Usage
=====

With bundled run-tests script:

.. code-block:: sh

  php scripts/run-tests.sh --php `which php` PredictableTests

With drush:

.. code-block:: sh

  # See available tests
  drush test-run
  # Run all tests (one fail, two pass)
  drush test-run --uri=http://example.com/ PredictableTests
  # Run a test which passes
  drush test-run --uri=http://example.com/ PredictableUnitTest
  # Run a test which fails
  drush test-run --uri=http://example.com/ PredictableFailTest
