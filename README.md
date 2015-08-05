[![Travis](https://travis-ci.org/unfoldingWord-dev/Door43.svg)](https://travis-ci.org/unfoldingWord-dev/Door43)

### Door43 DokuWiki Code

This repo is our unified DokuWiki + plugins repo.

To setup for development:

1. Fork this Door43 repo into your own Github account with the Fork button at the top

2. Clone your forked copy of Door43 onto your machine
   ```
   git clone git@github.com:<username>/Door43.git
   ```

3. Update your webserver to have a virtual host that points to the Door43 directory. (If you instead have Door43 as a
   subdirectory in your htdocs directory, you will need to change the RewriteBase in the .htaccess file and then run this command so it doesn't commit
   it to the repo: `git update-index --assume-unchanged .htaccess`)

4. Make sure you are on the development branch:
   ```
   git checkout development
   ```

5. Make sure that your web server's process has write access to the conf and data directories and all files and subdirectories.
   Exaple:
   ```
   cd Door43
   chown -R www.www .
   or
   chmod -R a+rw .
   ```

6. Run the door43_bootstrap.sh Bootstrap script. (You will need to be working on a Linux box or through Git Bash shell on Windows)
   ```
   cd Door43
   ./door43_bootstrap.sh (install language repos when promted)
   ```

7. You can now go to http://&lt;your.door43.domain&gt;/home?do=login and login as admin, password admin.

### Updating Door43 and its submodules and other repos

* If you ever want to update your Door43 installation, run ./door43_update.sh (Will update Door43 repo, Submodule repos and language repos)

* You can add more languages this way:
  ```
  cd Door43
  ./install_language.sh <IETF Language Code(s)>
  ```
  Example (installs Chinese):
  ```
  ./install_language.sh zh
  ```

### Unit Testing

General instructions for unit testing in Dokuwiki can be found [here](https://www.dokuwiki.org/devel:unittesting).

Instruction for writing PHPUnit tests can be found on the [PHPUnit website](https://phpunit.de/manual/current/en/writing-tests-for-phpunit.html).

**IMPORTANT:** You should use `extends DokuWikiTest` instead of `extends PHPUnit_Framework_TestCase` when creating new
test cases.  For examples, see the files in the `_test/tests/test` directory.

Each code change should be accompanied by unit tests that show the feature is working correctly.  Run all unit tests
before you submit a pull request to be sure all tests are passing.  If a test is not passing, you need to figure out if
something you did broke the test and fix it.

