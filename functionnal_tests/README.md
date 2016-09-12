# Behat


## Functionnal tests ?

High level testing, close to end user
Browser automation

## Components ?

Guerkin: high level language

```cucumber
 1: Feature: Some terse yet descriptive text of what is desired
 2:   Textual description of the business value of this feature
 3:   Business rules that govern the scope of the feature
 4:   Any additional information that will make the feature easier to understand
 5: 
 6:   Scenario: Some determinable business situation
 7:     Given some precondition
 8:       And some other precondition
 9:     When some action by the actor
10:       And some other action
11:       And yet another action
12:     Then some testable outcome is achieved
13:       And something else we can check happens too
14: 
15:   Scenario: A different situation
16:       ...
```

Behat: official PHP Cucumber implementation for Behaviour Driven Development (BDD)

Mink: Behat extension to integrate with broser (Goutte => simple HTTP scrapping from Symfony or Selenium, needed for JS)

## Installation

Install PHP components with composer commands

```
composer require behat/behat behat/mink-selenium2-driver behat/mink-extension
```

Selenium server is needed:

*   `java -jar selenium-server-standalone-2.53.0.jar -Dwebdriver.chrome.driver=/usr/lib/chromium-browser/chromedriver`
*   nothing needed for FF, extra package (*chromedriver*, distribution dependant) for Chrome + parameter below

You may also use docker images, they are working out of the box, but:
*   you have no display (you should open VNC port if you want to see the browser)
*   on Linux, docker containers have no access to internet if host (running the containers) is connected on WIFI

## Setup 

```
$ ./vendor/behat/behat/bin/behat --init
+d features - place your *.feature files here => Guerkin scenario files
+d features/bootstrap - place your context classes here => step definitions, PHP code \o/
+f features/bootstrap/FeatureContext.php - place your definitions, transformations and hooks here
```

Check available steps: 

```
$ LANG=C ./vendor/behat/behat/bin/behat -dl
=> empty !
```

Edit defaut context, and extend MinkContext


Basic steps (fill/press) (behat -dl)
```
$ LANG=C ./vendor/behat/behat/bin/behat -dl
default | Given /^(?:|I )am on (?:|the )homepage$/
default | When /^(?:|I )go to (?:|the )homepage$/
default | Given /^(?:|I )am on "(?P<page>[^"]+)"$/
default | When /^(?:|I )go to "(?P<page>[^"]+)"$/
default | When /^(?:|I )reload the page$/
default | When /^(?:|I )move backward one page$/
default | When /^(?:|I )move forward one page$/
default | When /^(?:|I )press "(?P<button>(?:[^"]|\\")*)"$/
default | When /^(?:|I )follow "(?P<link>(?:[^"]|\\")*)"$/
default | When /^(?:|I )fill in "(?P<field>(?:[^"]|\\")*)" with "(?P<value>(?:[^"]|\\")*)"$/

```

## Tests writing

Ready to edit tests!

## Tests execution

This should cover the following points: 
*   How to write custom steps
*   Pb of css and xpath filters => if we have no id/name in HTML source, we need to rely on custom selectors (trainline with EmberJS, Iflya380 with React)
*   "Element is not visible/clickable" error (scrollToView)
*   Intellij integration
*   setValue() pb (trainline)

![Behat exec](./behat_console_exec.png)

## Tooling

Decent Intellij integration: code completion, step generation, PHPUnit like exec console

![Behat intelij](./behat_intellij.png)

# Robotframework

## Installation

Global installation (to have `robot` in path)

```
pip install robotframework robotframework-selenium2library robotframework-extendedselenium2library
```

No need for a Selenium server \o/ browser launched by robot
To use Chrome, ChromeDriver must be in the PATH

## Setup

Done in *.robot files

Browser familly + screen resolution all defined in the same file

## Tests writing

Commands available here:

http://robotframework.org/Selenium2Library/Selenium2Library.html

## Tests execution

```
robot *.robot
```

![Robot exec](./robot_console_exec.png)


Keywords (instead of Steps)

## Tooling

Ride UI https://github.com/robotframework/RIDE /!\ Python 3 support is still in progress, conflict with newer wxGtk versions on modern Linux distributions

HTML output provided natively ![Robot web_output](./robot_web_output.png)

Intellij: limited code completion, exec thru external tools

# Sumup

Try to always use regular HTML forms, set "id" attributes to be able to use reliable/simpler selectors (#action_button)

Starting writing tests from the start of the project (easier + can be used for regression tests)

Beware with animations (slows down test execution due to the need of wait() calls)
