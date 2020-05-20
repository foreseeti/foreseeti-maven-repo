# foreseeti-maven-repo

This document describes what [foreseeti](https://www.foreseeti.com/)'s maven repository is and how to use it, as well as how to use [securiCAD Professional](https://www.foreseeti.com/securicad-professional/) with [MAL](https://mal-lang.org/).

The process described in this document might change at any time. If you are experiencing problems, please check this page.

## About

foreseeti's maven repository contains code that is required to compile a MAL language into a jar file that is compatible with foreseeti's securiCAD products.

## Getting access

To get access to foreseeti's maven repository, you can contact support@foreseeti.com. When you get access, you will receive your credentials as a text file named `credentials`. This file looks something like this:
```
[default]
aws_access_key_id=AKIAIOSFODNN7EXAMPLE
aws_secret_access_key=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
```

These credentials are for your personal use, and should be kept secret. If your credentials have been stolen, please contact support@foreseeti.com.

This file needs to be stored in a directory called `.aws` in your home directory. On Windows, that could be `C:\Users\joe\.aws\credentials`, on macOS, that could be `/Users/joe/.aws/credentials`, and on linux, that could be `/home/joe/.aws/credentials`.

Once your credentials file is stored in the correct location, maven can automatically find it and use it to access foreseeti's maven repository.

## securiCAD Professional

The current release of securiCAD Professional, version 1.6.2, can be downloaded from <https://get.securicad.com/>.

## MAL license for securiCAD Professional

A MAL license for securiCAD Professional enables additional support for MAL languages. To request a MAL license, you need to generate a hardware token in `File > Licensing > Generate Token` and send it to support@foreseeti.com. Once you get a license file, you can enter it into securiCAD Professional in `File > Licensing > Replace License`.

Once securiCAD Professional restarts, a dialog should appear where you select which MAL language jar file to use. If the dialog doesn't appear, you might have to manually replace the license. This can be done by copying your license file to securiCAD Professional's workspace directory, and giving it the exact name `securiCAD.license`. On windows, that could be `C:\Users\joe\securiCAD\workspace\securiCAD.license`, on macOS, that could be `/Users/joe/securiCAD/workspace/securiCAD.license`, and on linux, that could be `/home/joe/securiCAD/workspace/securiCAD.license`.
