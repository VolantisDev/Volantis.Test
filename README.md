# Volantis.TestLib

## Introduction

This library can serve as a testing framework for complex AutoHotKey libraries and applications.

After some basic setup, and as long as you follow some basic class file naming guidelines, test files can
be created for each class, and TestLib can automatically run all tests in your application and generate a
report in different formats, including fully rendered HTML results.

## Installation

The current recommended approach to installing this library is by adding it as a submodule to your project.  This allows you to easily update to the latest version of the library, while keeping the files within your application directory for easy include file building.

## Usage

TestLib fits in easily with applications structured in a way that allows it to easily find things.

The recommended structure is:
- A parent directory containing your entire class library
- Classes can be anywhere under the parent directory, including nested structures
- Classes should each have their own file, and the file should be named after the class (e.g. a class MyApp would be named MyApp.ahk)
- The IncludeBuilder/IncludeWriter classes in Volantis.CoreLib can be used to automatically create and update an include file for your library, which TestLib uses to find your classes

Given the above structure, test classes should be created alongside the class they are testing, named like [ClassName].test.ahk. For example, if you have a class named MyApp in a file named MyApp.ahk, you would create a test class named MyAppTest located in a file named MyApp.test.ahk.

The same IncludeBuilder and IncludeWriter classes can be used to create an include file for your test classes, which TestLib will use to find your test classes without them being a part of your main include file.

Finally, you can create a test runner in your application, commonly named after your main application AHK file with the Test suffix. For example, if your main application file is named MyApp.ahk, you would create a test runner named MyAppTest.ahk. The test runner loads your include files and then calls a TestRunner and ResultViewer class.

Volantis.ProjectStarter contains the skeleton of a fully-testable application that can be used as the basis for a new project or referenced to retrofit an existing project.

## TestLib Dependency

An important note is that using any of the *.test.ahk classes requires Volantis.TestLib, however it is not listed under dependencies or devDependencies of this library because this library is a dependency of TestLib.
