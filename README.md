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

PHING build files
-----------------

The `phing` directory contains some sample build files for [Phing](http://www.phing.info). If the
project is written with PHP, it should be equipped with such a script that allows to perform
the management actions.

Project manager instructions:

1. Copy `build.xml` and `build.properties-dist` to your project directory tree.
2. **DO NOT** rename `build.properties-dist` to `build.properties`. This should be done by the end users
3. Add **build.properties** to `.gitignore`
4. Edit `build.xml`, and fix the project name and the copying file tasks in the `build` target.
5. In addition, you should also update the PHAR file lists in the `dist` target.
6. Commit the modifications.

End-user instructions:

1. Rename `build.properties-dist` to `build.properties`:
2. Open this file in the editor.
3. Configure the options to reflect your system and project status.
4. Pay a careful attention to the version numbers and the FTP data.
5. `build.properties` **must not** be commited to the repository!

Available targets:

* `clean` - cleans the build directories.
* `prepare` - creates the build directories.
* `build` - builds the release files in the build directory.
* `dist` - creates the release packages: TAR.GZ, TAR.BZ2, ZIP, PHAR, PEAR2 package.
* `deploy` - deploys the release packages to the project website server through FTP.

Work-in-progress targets:

* `git-feature-start`
* `git-feature-finish`
* `git-release-start`
* `git-release-finish`
* `git-hotfix-start`
* `git-hotfix-finish`

They will be used to ease the Git repository management with the [approved workflow](http://nvie.com/posts/a-successful-git-branching-model/).
Unfortunately, some of them cannot be completed right now due to the lack of necessary options in Phing 2.4.x.

Headers
-------

Various file header collection:

* `PHPClass.php` - the skeleton of the PHP class file.