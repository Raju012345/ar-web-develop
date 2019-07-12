[![Build Status](https://travis.innovate.ibm.com/ESInnovationLab/ar-web.svg?token=y3yz3mxcSqS1APhnSgJA&branch=develop)](https://travis.innovate.ibm.com/ESInnovationLab/ar-web)

# Accounts Receivable Front-End

# Table of Contents

  * [Overview](#overview)
  * [Prerequisites](#prerequisites)
  * [Add SSH Keys for Github](#add-ssh-keys-for-github)
    * [Mac OS](#mac-os)
    * [Windows](#windows)
  * [Troubleshooting](#troubleshooting)
    * [NPM install error on Windows](#npm-install-error-on-windows)

# Overview
This repository exclusively contains the front-end UI of the Accounts Receivable project. This project will be deployed to Bluemix Dedicated using the CloudFoundry `staticfile-buildpack`.

# Prerequisites

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - [Set it up for Github, connecting over SSH](https://help.github.com/articles/set-up-git/)
2. Install [Python v2.7.x](https://www.python.org/downloads/release/python-27) (v3.x is not supported by `node-gyp`)
3. Install [Node.js v6.9.2 or higher](https://nodejs.org/en/download/)

For Windows users, see [these additional notes](#windows) below.

## Windows Additional Notes

In Windows, somehow you might encounter strange issues. We strongly recommend you to follow these instructions to setup your environment.  The tools used in this project require Windows 7 or higher, with these additional prerequisites:

1. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git#Installing-on-Windows)
  - Use these configuration options:
    1. **Adjusting your PATH environment**: _Use Git from the Windows Command Prompt_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/ff1b2ee4-e9dd-11e5-97e7-14e0dfa59aa5)
    2. **Configuring the line ending conversions**: _Checkout as-is, commit Unix-style line endings_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/c6b5472a-e9dc-11e5-97c2-6ab971319396)
    3. **Configuring the terminal emulator to use with Git Bash**: _Use Windows' default console window_ ![Screenshot](https://media.github.ibm.com/download/user/1226/files/031e5c82-e9de-11e5-9035-66e30151fc3c)
2. Install Python v2.7.x (v3.x is not supported by `node-gyp`)
  - Download and run the [official installer](https://www.python.org/downloads/release/python-27)
  - Add the Python installation directory (default: `C:\Python27`) to the `PATH` environment variable
    1. Right click _My Computer_ and choose _Properties_
    2. Open the _Advanced_ tab and click the _Environment Variables_ button
    3. Look for the variable named `PATH`
      - If it does not exist, create it by clicking on _New..._
      - If it exists, click on _Edit..._
    4. Add the Python installation directory in its value
      - ![Screenshot](https://media.github.ibm.com/download/user/1226/files/1ebc2424-e9de-11e5-961d-94a74c7c68cd)
3. Install Microsoft Visual Studio C++ 2013 ([Express](https://www.microsoft.com/en-gb/download/details.aspx?id=44914) version works well)
  - This is needed by `node-gyp`. Read about it in the [`node-gyp` installation instructions](https://github.com/nodejs/node-gyp#installation)
  - There are alternate instructions in [this node-gyp Github issue](https://github.com/nodejs/node-gyp/issues/629#issuecomment-153196245)

# Add SSH Keys for Github

## Mac OS

1. In **MacTerminal**, paste the command below, substituting in your GitHub email address. It will create a new ssh key, using the provided email as a label.

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
3. Then at the prompt, you will be asked for a secure passphrase.

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```
4. Ensure ssh-agent is enabled by running:

```
$ eval "$(ssh-agent -s)"
```
5. Add your SSH key to the ssh-agent by running:

```
$ ssh-add ~/.ssh/id_rsa
```
6. Copy the SSH key to your clipboard by running:

```
$ pbcopy < ~/.ssh/id_rsa.pub
```
Note: If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

7. Then log into [Github](http://github.ibm.com/). Click your profile photo (top right corner), then click Settings.

8. In the user settings sidebar (left side), click SSH keys.

9. Click Add SSH key.

10. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".

11. Paste the previously copied key (step 6) into the "Key" field.

12. Click Add key and confirm the action.

13. Open Terminal again and enter:

```
$ ssh -T git@github.ibm.com
```
14. Verify that the fingerprint in the message you see matches the following message, then type yes:

```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
It's Done! Just verify that the resulting message contains your username.

## Windows

Note: all commands must be run in **Git Bash**

1. In **Git Bash**, paste the text below, substituting in your GitHub email address. It will create a new ssh key, using the provided email as a label.

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
2. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
3. Then at the prompt, you will be asked for a secure passphrase.

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```
4. Ensure ssh-agent is enabled by running the following:

```
$ eval "$(ssh-agent -s)"
```
5. Add your SSH key to the ssh-agent by running:

```
$ ssh-add ~/.ssh/id_rsa
```
6. Copy the SSH key to your clipboard by running:

```
$ clip < ~/.ssh/id_rsa.pub
```
Note: If your SSH key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.

7. Then log into [Github](http://github.ibm.com/). Click your profile photo (top right corner), then click Settings.

8. In the user settings sidebar (left side), click SSH keys.

9. Click Add SSH key.

10. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Windows machine, you might call this key "Personal Windows Machine".

11. Paste the previously copied key (step 6) into the "Key" field.

12. Click Add key and confirm the action.

13. Open **Git Bash** again and enter:

```
$ ssh -T git@github.ibm.com
```
14. Verify that the fingerprint in the message you see matches the following message, then type yes:

```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
It's Done! Just verify that the resulting message contains your username.

# Developer Install

1. Checkout the source code
  - Latest and greatest is in `develop`
  - Test activities should be performed on `test`
  - Production should use `master`
  - Select the `develop` branch as your origin. Note: The `master` branch is not for active development; it is the stable branch where only releases are tagged from.

  ```sh
  git clone -b develop git@github.ibm.com:ESInnovationLab/ar-web.git
  cd ar-web
  ```
2. Install the application's dependencies by issuing the following command from ar-web directory

  ```sh
  npm install
  ```
3. Run the application with `npm run local`
4. Access the application in a browser at http://localhost:3000
  - Any changes in `.js` and `.html` files will automatically reload the browser
  - Any changes in `.scss` files will be automatically streamed to the browser and update the current view without reloading
  - Any changes in vendored files (JS, CSS, fonts, images, etc.) is not automatically built. You need to stop `npm run local` and run it again.
  - NOTE: Some exceptions thrown during linting terminate the `npm run local` process. If that happens, you need to run `npm run local` again.

# Configure the npm registry for accessibility package

## Overview

`@ibma/aat` is a NodeJS Module that allows you to perform integrated accessibility testing within a continuous integration pipeline such as Travis CI.

`@ibma/aat` is a NodeJS module that scans a Selenium WebDriver or parsed document. It allows you to perform integrated accessibility testing within a continuous integration pipeline such as Travis CI while using a variety of test frameworks such as Cucumber, Mocha, or Jasmine. `@ibma/aat` allows users to scan HTML nodes/widgets, URLs, local files, HTML documents, and HTML content in the form of a string. Aside from just performing accessibility scanning, `@ibma/aat` provides a framework to validate accessibility scan results against baseline files and/or simply failing the testcases based on the levels of violations found during the scan.

**Table of Contents**

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Install](#install)
    - [Authentication](#authentication)
    - [Install Locally](#install-locally)
    - [Install on Travis CI](#install-on-travis-ci)
      - [Generate Personal Auth Token](#generate-personal-auth-token)
      - [Enabling CI](#enabling-ci)
- [Configuration](#configuration)
  - [Configuring `AAT`](#configuring-aat)
- [Usage](#usage)
- [APIs](#apis)
  - [AAT.getCompliance(`content`, `label`, `callback`)](#aatgetcompliancecontent-label-callback)
  - [AAT.assertCompliance(`actualResults`)](#aatassertcomplianceactualresults)
  - [AAT.getDiffResults(`label`)](#aatgetdiffresultslabel)
  - [AAT.getBaseline(`label`)](#aatgetbaselinelabel)
  - [AAT.diffResultsWithExpected(`actual`, `expected`, `clean`)](#aatdiffresultswithexpectedactual-expected-clean)
  - [AAT.stringifyResults(`results`)](#aatstringifyresultsresults)
- [Errors](#errors)
- [FAQ](#faq)
- [Feedback](#feedback)
  - [Reporting bugs](#reporting-bugs)

## Getting Started

1. Setup and Initialize - Follow the [Prerequisites](#prerequisites) and [Install](#install) instructions.
1. Configure AAT - Follow the [Configuration](#Configuration) instructions.
1. Learn how to use APIs to perform accessibility scans - Refer to [Usage](#usage) and [APIs](#apis) documentation.
1. Give us feedback.

### Prerequisites

1. Install NodeJS and NPM: [via installer](http://w3.hursley.ibm.com/java/jim/ibmsdksfornodejs/ibmsdksfornodejsversion4/index.html)
1. Some testing framework (e.g., mocha, jasmine)
1. Browser automation / parser (e.g., Selenium, Zombie)

### Install

#### Authentication

IBM's npm Enterprise instance is configured to use IBM's GitHub Enterprise SSO (OAuth) authentication, which is a 2 step authentication process.

Login using registry
```console
$ npm login --registry=https://npm-registry.whitewater.ibm.com --scope=@ibma
```

When prompted for `username`, `password`, and `email`, simply provide your w3Id credentials.
After doing so, the npm client will be granted an unresolved token that is stored in your `~/.npmrc` file.

i.e.

```concole
devans@<hostname>:~$ npm login --registry=https://npm-registry.whitewater.ibm.com --scope=@ibma
Username: devans
Password: <w3id passowrd>
Email: (this IS public) devans@ca.ibm.com
Logged in as devans to scope @ibma on https://npm-registry.whitewater.ibm.com/.
```

For more information, visit the npm Enterprise docs: https://npme.npmjs.com/docs/cli/configuration.html#single-sign-on-authentication-saml-oauth-20

#### Install Locally

Perform the steps outlined at [Authentication](#authentication) before trying to install this module.

Install `@ibma/aat` plugin from IBM npm server locally:

```sh
$ npm install @ibma/aat --registry https://npm-registry.whitewater.ibm.com --save-dev
```

Note: The first time you try to install after [Authentication](#authentication) it could fail with the following error message:

> npm ERR! visit https://github.ibm.com/login/oauth/authorize?redirect_uri=...... to validate your session : @ibma/aat

Open this link in your browser, then try again

#### Install on Travis CI

##### Generate Personal Auth Token

To integrate npm Enterprise with Travis CI you need to generate a `.npmrc` file that references IBM's npm Enterprise instance with an authentication token. Follow the instructions outlined at [Authentication](#authentication) and then refer to the steps below.

Look in your `~/.npmrc` file, you will see an entry that looks something like this:

`//npm-registry.whitewater.ibm.com/:_authToken=[NPM_TOKEN]`

Copy `[NPM_TOKEN]` somewhere safe.

##### Enabling CI

Now that you have a token:

* Enable CI for your repo on Travis CI (Whitewater TravisCI is https://travis.ibm.com)
* [Define Variable in Repository Settings](https://docs.travis-ci.com/user/environment-variables#Defining-Variables-in-Repository-Settings) called `NPM_TOKEN` and set this equal to `[NPM_TOKEN]` from [Generate Personal Auth Token](#generate-personal-auth-token)
* Create/update your `.travis.yml` file in your project that looks like this:

    ```yaml
    language: node_js
    node_js:
    - "node"
    before_install:
    - printf "@ibma:registry=https://npm-registry.whitewater.ibm.com/\n//npm-registry.whitewater.ibm.com/:_authToken=${NPM_TOKEN}" >> .npmrc
    ```

* Now in your `package.json` you can simply add the following:

    ```json
    {
      "devDependencies": {
        "@ibma/aat": "^1.1.0"
      }
    }
    ```

For further information, see the official npm Enterprise docs: https://npme.npmjs.com/docs/workflow/travis.html

Note: The first time you try to install it will fail with the following error message:

> npm ERR! visit https://github.ibm.com/login/oauth/authorize?redirect_uri=...... to validate your session : @ibma/aat

Open this link in your browser, then try again.
This will be case inside Travis CI environment as well, but once you have visited the URL it will authenticate your `NPM_TOKEN` so you can continue to use it in TRAVIS CI.

## Configuration

### Configuring `AAT`

Configuring `AAT` plugin involves constructing a `.aat.yml` file in the project root, which will contain all the configuration
options for `AAT`. Following is the structure of the `.aat.yml` file:

```yml
# required - Provide the authentication token available at http://ibm.biz/A11yToolsLandingPage
# i.e: authToken: 00000000-0000-0000-0000-000000000000/00000000-0000-0000-0000-000000000000
authToken:

# optional - Specify the rule archive
# i.e. For May rule archive use ruleArchive: 2017MayDeploy
# Default: latest
# Refer to README.md FAQ section below to get the rule archive ID.
ruleArchive : latest

# optional - Specify one or many policies to scan.
# i.e. For one policy use policies: IBM_Accessibility_2017_02
# i.e. Multiple policies: IBM_Accessibility_2017_02,IBM_Accessibility_BETA or refer to below as a list
# Default: null (all policies)
# Refer to README.md FAQ section on details to get the policy ID.
policies:
    - IBM_Accessibility_2017_02

# optional - Specify one or many violation levels on which to fail the test
#            i.e. If specified violation then the testcase will only fail if
#                 a violation is found during the scan.
# i.e. failLevels: violation
# i.e. failLevels: violation,potential violation or refer to below as a list
# Default: violation, potentialviolation
failLevels:
    - violation
    - potentialviolation

# optional - Specify one or many violation levels which should be reported
#            i.e. If specified violation then in the report it would only contain
#                 results which are level of violation.
# i.e. reportLevels: violation
# i.e. reportLevels: violation,potentialviolation or refer to below as a list
# Default: violation, potentialviolation, recommendation, potentialrecommendation, manual
reportLevels:
    - violation
    - potentialviolation
    - recommendation
    - potentialrecommendation
    - manual

# Optional - Which type should the results be outputted to
#   outputFormat: json
# Default: json
outputFormat:
    - json

# Optional - Specify labels that you would like associated to your scan
#
# i.e.
#   label: Firefox,master,V12,Linux
#   label:
#       - Firefox
#       - master
#       - V12
#       - Linux
# Default: N/A
label:
    - master

# optional - Where the scan results should be saved.
# Default: results
outputFolder: results

# optional - Where the baseline results should be loaded from
# Default: baselines
baselineFolder: test/baselines

# optional - Should Hidden content be scanned
# true --> Yes scan hidden content
# false --> Don't scan hidden content
# Default: false
checkHiddenContent: false
```

## Usage

Following is how to perform an accessibility scan within your testcases and verifying the scan results:

```javascript
// Perform the accessibility scan using the AAT.getCompliance API
AAT.getCompliance(testDataFileContent, testFile, function (results) {

    // Call the AAT.assertCompliance API which is used to compare the results with baseline object if we can find one that
    // matches the same label which was provided.
    var returnCode = AAT.assertCompliance(results);

    // In the case that the violationData is not defined then trigger an error right away.
    expect(returnCode).toBe(0, "Scanning " + testFile + " failed.");

    // Mark the testcases as done, when using jasmine as the test framework.
    done();
});
```

Refer to [Examples](https://github.ibm.com/IBMa/Tools-Boilerplates/tree/master/IBM-AAT/nodejs) for sample usage scenarios.

## APIs

### AAT.getCompliance(`content`, `label`, `callback`)

Execute accessibility scan on provided content. Content can be in the following form:
* HTML content (String)
* Single node/widget (HTMLElement)
* Local file path (String)
* URL (String)
* Document node (HTMLDocument)
* Selenium WebDriver (WebDriver)

Note: When using Selenium WebDriver the AAT.getCompliance API will only take Selenium WebDriver (WebDriver) instance.

Using a callback mechanism (`callback`) to extract the results and perform assertion using AAT APIs.

* `content` - (String | HTMLElement | HTMLDocument | Selenium WebDriver) content to be scanned for accessibility violations.
* `label` - (String) unique label to identify this accessibility scan from others. Using "/" in the label allows for directory hierarchy when results are saved.
* `callback` - (Function) callback that is invoked (indicating success). The callback will be invoked with the ```results```
as a parameter to the callback function provided. Following is the outline of the results object which will be passed to the callback function:

```javascript
var results = {
    scanID: "12c6717d-69c4-4fe7-ab30-4e16067a0f5a",
    toolID: "@ibma/aat-v1.1.0",
    label: "src/HelloWorld.html",
    URL: "https://www.ibm.com/ca-en/",
    summary: {
        counts: {
            violation: 1,
            potentialviolation: 0,
            recommendation: 0,
            potentialrecommendation: 0,
            manual: 0
        },
        scanTime: 29,
        ruleArchive: "May 2017 Deployment (2017MayDeploy)",
        policies: [
            "IBM_Accessibility_2017_02"
        ],
        reportLevels: [
            "violation",
            "potentialviolation",
            "recommendation",
            "potentialrecommendation",
            "manual"
        ],
        startScan: 1470103006149
    },
    reports: [
        {
            frameIdx: 0,
            frameTitle: "Frame 0",
            issues: [
                {
                    severityCode: "eISHigh",
                    messageCode: "wcag20.tech.aria.OrphanedContent",
                    ruleId: "1088",
                    help: "idhi_accessibility_check_g1088.html",
                    msgArgs: [],
                    bounds: {
                        left: 10,
                        top: 11,
                        height: 24,
                        width: 163
                    },
                    level: "violation",
                    xpath: "/html[1]/body[1]/a[1]",
                    snippet: "\<a href='#navskip'\>"
                }
            ]
        }
    ]
}
```

Refer to `actualResults` parameter in [AAT.assertCompliance](#aatassertcomplianceactualresults) API for more details about the properties of results object.

### AAT.assertCompliance(`actualResults`)

Perform assertion on the scan results. Will perform one of the following assertions based on the condition that is met:

1. In the case of a baseline file is provided and available in memory for these scan results, a compare of baseline to `actualResults` will be made. In this case if `actualResults` matches baseline, it returns 0, otherwise returns 1. For this case, assertion is only run on the xpath and ruleId.

2. In the case of NO baseline file is provided for this particular scan, assertion will be made based on the provided `failLevels`. In this case, it returns 2 if there are failures based on failLevels. (violation level matches at least one provided in the `failLevels` object)

* `actualResults` - (Object) results for which assertion needs to be run. Properties include:
  * **scanID**, (String) auto generated UUID used to assoicate a session.
  * **toolID**, (String) tool ID for the tool that generated these results.
  * **label**, (String) label provided to identify unique scans results. (provided through AAT.getCompliance API)
  * **URL**, (String) contains URL when URL was scanned using AAT.getCompliance API. (provided through AAT.getCompliance API)
  * **summary**, (Object) summary of the scan which these results are for. Properties include:
    * **counts**, (Object) number of violations based on the violation level. Properties include:
      * **violation**, (Int) total number of violations.
      * **potentialviolation**, (Int) total number of potential violations.
      * **recommendation**, (Int) total number of recommendation.
      * **potentialrecommendation**, (Int) total number of potential recommendation.
      * **manual**, (Int) total number of manual checks.
    * **scanTime**, (Int) total number of milliseconds it took to perform the scan.
    * **ruleArchive**, (String) rule archive used for this particular scan result.
    * **policies**, (Array) policies used for this particular scan result.
    * **reportLevels**, (Array) list of violations level on which to report about. (save to file)
    * **startScan**, (Int) start time of the scan in milliseconds since epoch, GMT
  * **reports**, (Array) list of reports in the case of multiple iframes are present on the single page. (iframe scanning not support yet)
    Each array element is an object compromised of the following properties:
    * **frameIdx**, (Int) frame index on the page represented as an integer value.
    * **frameTitle**, (String) title of the frame on the page which was scanned.
    * **issues**, (Array) detailed list of violations. Each array element is an object compromised of the following properties:
      * **severityCode**, (String) severity code for this particular violation.
      * **messageCode**, (String) message code for this particular violation. Used to map the localized message string.
      * **ruleId**, (String) rule ID for this particular violation.
      * **help**, (String) help file name for this particular violation.
      * **msgArgs**, (Array) list of tokens to help provide a detailed error description of the issue.
      * **bounds**, (Object) provides the pixel position of the element on which this violation triggered. Properties include:
        * **left**, (Int) left pixel position of the element.
        * **top**, (Int) top pixel position of the element.
        * **height**, (Int) height pixel position of the element.
        * **width**, (Int) width pixel position of the element.
      * **level**, (String) violation level for this particular violation.
      * **xpath**, (String) xpath to the element on which this particular violation was triggered.
      * **snippet**, (String) snippet for the element on which this particular violation was triggered.

Returns `0` in the case actualResults matches baseline or no violations fall into the failLevels

Returns `1` in the case actualResults DON'T match baseline

Returns `2` in the case that there is a failure based on failLevels.

Returns `-1` in the case that an exception has occured during scanning and the results reflected that.

### AAT.getDiffResults(`label`)

Retrieve the diff results based on label in the case API `AAT.assertCompliance(...)` returns 1, when actualResults DON'T match baseline.

* `label` - (String) label for which to get the diff results for. (should match the one provided for AAT.getCompliance(...))

Returns a diff object, where **left hand side (lhs) is actualResults** and **right hand side (rhs) is baseline**.
Refer to [deep-diff](https://github.com/flitbit/diff#simple-examples) documentation for the format of the diff object,
and how to interpret the object.

Returns `undefined` if there are no differences.

### AAT.getBaseline(`label`)

Retrieve the baseline result object based on the label provided.

* `label` - (String) label for which to get the baseline for. (should match the one provided for AAT.getCompliance(...))

Returns `object` which will follow the same structure as the results object outlined in [AAT.getCompliance](#aatgetcompliancecontent-label-callback)
and [AAT.assertCompliance](#aatassertcomplianceactualresults) APIs.

Returns `undefined` in the case baseline is not found for the label provided.

### AAT.diffResultsWithExpected(`actual`, `expected`, `clean`)

Compare provided `actual` and `expected` objects and get the differences if there are any.

* `actual` - (Object) actual results which need to be compared.
Refer to [AAT.assertCompliance](#aatassertcomplianceactualresults) APIs for details on properties include.
* `expected` - (Object) expected results to compare to.
Refer to [AAT.assertCompliance](#aatassertcomplianceactualresults) APIs for details on properties include.
* `clean` - (boolean) clean the `actual` and `expected` results by converting the objects to match with a basic compliance
compare of only xpath and ruleID

Returns a diff object, where **left hand side (lhs) is actualResults** and **right hand side (rhs) is baseline**.
Refer to [deep-diff](https://github.com/flitbit/diff#simple-examples) documentation for the format of the diff object,
and how to interpret the object.

Returns `undefined` if there are no differences.

### AAT.stringifyResults(`results`)

Retrieve the readable stringified representation of the scan results.

* `results` - (Object) results which need to be stringified.
Refer to [AAT.assertCompliance](#aatassertcomplianceactualresults) APIs for details on properties include.

Returns `String` representation of the scan results which can be logged to console.

## Errors

### Error: labelNotProvided

This is a subtype of `Error` defined by the `AAT` plugin. It is considered a programming error.
`labelNotProvided` is thrown from `AAT.getCompliance(...)` method call when a label is not provided to
function call for the scan that is to be performed. Note: A label must always be provided when calling
`AAT.getCompliance(...)` function.

### Error: labelNotUnique

This is a subtype of `Error` defined by the `AAT` plugin. It is considered a programming error.
`labelNotUnique` is thrown from `AAT.getCompliance(...)` method call when a unique label is not provided to
function call for the scan that is to be performed. Note: Across all accessibility scans the label provided
must always be unique.

### Error: RuleArchiveInvalid

This is a subtype of `Error` defined by the `AAT` plugin. It is considered a programming error.

`RuleArchiveInvalid` is thrown from `[AAT.getCompliance(...)]` during verification of rule archive on the configuration files.
The error occurs when the provided `ruleArchive` value in the configuration file is invalid.

### Error: ValidPoliciesMissing

This is a subtype of `Error` defined by the `AAT` plugin. It is considered a programming error.

`ValidPoliciesMissing` is thrown from `[AAT.getCompliance(...)]` method call when no valid policies are in the configuration file.
Note: The valid policies will vary depending on the selected `ruleArchive`.

## E2E testing

### E2E testing in local environment
Steps to run E2E testing in local environment:
- Make sure you export funtional ID password before runiing test command.
- Option 1: Export everytime before you run test
```
FUNCTIONAL_ID_ADMIN_PWD=pastePasswordHere npm run test
```
- Option 2: You can add permanent env variable to your `~/.bash_profile`, then you can run test command without export command:
```
export FUNCTIONAL_ID_ADMIN_PWD=pastePasswordHere
```

###

## FAQ

* How do I get a list of the available `ruleArchive, policies` and their ID's?
   1. Navigate to URL http://ibm.biz/A11yToolsLandingPage
   2. Login using w3id credentials
   3. Once navigated to "Organizations" page either select an existing organization or create a new one
   4. Click on your organization and wait to be naviagated to "Tools" page
   5. Select "Rules" tab to view information about policies
   6. Once on the "Rules" page you can select a policy from the dropdown
   7. Once policy is selected, on the page it will provide description, policy ID to use in CI tools, details on which checkpoints are covers and which rules cover a specific checkpoint.

## Feedback

Feel free to provide any feedback by starting a New Topic in [Forum](https://w3-connections.ibm.com/forums/html/forum?id=11111111-0000-0000-0000-000000005126).

### Reporting bugs

If you think you've found a bug, please report the bug by starting a New Topic in [Forum](https://w3-connections.ibm.com/forums/html/forum?id=11111111-0000-0000-0000-000000005126).

# Troubleshooting

The following issues have been faced at our end, you you can find some recommendations here.

## NPM install error on Windows
* If you run `npm install` and get this error: `MSBUILD : error MSB3428: Could not load the Visual C++ component "VCBuild.exe".`
  - ![Screenshot](https://media.github.ibm.com/download/user/1226/files/5d8d8d50-e9de-11e5-941e-bf1bd844a45c)
  - Solution:
    1. Install Microsoft Visual Studio C++ 2013 (see notes on [Windows](#windows-additional-notes))
    2. Run `npm cache clean`
    3. Run `npm install` again
* If you need to upgrade `npm`:
  - Launch Windows PowerShell as Administrator, then run the following commands:

    ```bat
    Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force
    npm install -g npm-windows-upgrade
    npm-windows-upgrade
    ```
* If you need to reinstall or rebuild native Node.js modules:
  - You should clear your `npm` cache first:

    ```bat
    npm cache clean
    ```
* If you got a travis build failed at `gulp lint failed, exiting...` then you need to remove all node modules under /node_modules folder and then run `npm install` again due to one/some node module(s) has been published a new version.
