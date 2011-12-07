###############
PredicableTests
###############

The predicabletests module registers minimal tests which are predicable,
i.e. they always or never pass. You know which result to expect.

Here are some use cases where this module could help:

* in demo or tutorial: try tests that passes and others that fails;

* make sure that a continuous integration service acts as expected, i.e. test
  the deployment of such a service. When you deploy a continuous integration
  service, at first you want to be sure that it can run tests, and then that
  it handles "pass" and "fail" statuses. There comes predicabletests;

* use "quick" tests. Standards tests bundled with Drupal or simpletest are
  quite slow to run. So predicabletests will save us time where you just want
  to know whether you can successfully run tests or not;

* make sure there is no error in your installation. As examples, errors raised
  during tests could be related to Drupal or any module. Predicabletests'
  tests are really minimal, so the risk to get collateral errors is minimal.

Installation
============

With drush...

.. code-block: sh

  # Download and install predicabletests
  drush dl predicabletests
  drush en predicabletests

Usage
=====

With bundled run-tests script:

.. code-block:: sh

  php scripts/run-tests.sh --php `which php` PredicableTests

With drush:

.. code-block:: sh

  # See available tests
  drush test-run
  # Run all tests (one fail, two pass)
  drush test-run --uri=http://example.com/ PredicableTests
  # Run a test which passes
  drush test-run --uri=http://example.com/ PredicableUnitTest
  # Run a test which fails
  drush test-run --uri=http://example.com/ PredicableFailTest
