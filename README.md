Invenzzia Tools
===============

This is a simple utility repository for keeping various tools and utility scripts
used during the Invenzzia Group development. If you belong to Invenzzia Group, you
must use them as a base for your projects. If you look for some utility tools,
feel free to use them as you wish.

The repository is maintained by Tomasz Jędrzejewski and Jacek Jędrzejewski.

Testing suite
-------------

A testing suite based on PHPUnit 3.5 is stored within the directory `/tests`. In
order to use it in your projects, you should copy it to your project directory
tree, configure `bootstrap.php` file and fill with your tests.

Directory description:

* `\TestSuite` namespace stores the unit test code. It should be registered in the
  autoloader.
* `\Extra` namespace stores the extra hand-coded mocks that cannot be reproduced
  with pure PHPUnit for various reasons.
* `\cache` - file cache should go here.
* `\coverage` - a directory for dumping the code coverage analysis.
* `\data` - additional test data should be stored here.
* `\bootstrap.dist.php` - a sample bootstraping file. You should modify it for your
  own purposes. In the development environment, you should copy it to `bootstrap.php`
  and configure to match your system settings and library paths.
* `coverage.xml` - PHPUnit configuration that generates a code coverage dumping
* `no-coverage.xml` - PHPUnit configuration that does not generate a code coverage dumping.

Testing strategies:

* avoid using global state, especially in static private elements,
* each test **must** be run in the process isolation. Add the `@runTestsInSeparateProcesses`
  annotation to the test suite class header,
* ensure that the cache is not propagated between tests,
* add `AllTests.php` file with `AllTests` class at every namespace level. It should configure
  PHPUnit to run all the tests from this particular namespace.
* `TestSuite\AllTests.php` should run all the tests in the test suite.

Remember about:

* adding `tests/bootstrap.php` to `.gitignore`
* adding `tests/cache/*` to `.gitignore`
* adding `tests/coverage/html/*` to `.gitignore`

PHAR generator
--------------

To be done.

PHING build files
-----------------

To be done.

Headers
-------

Various file header collection:

* `PHPClass.php` - the skeleton of the PHP class file.