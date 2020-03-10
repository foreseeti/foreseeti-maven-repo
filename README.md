# foreseeti-maven-repo

This document describes what [foreseeti](https://www.foreseeti.com/)'s maven repository is and how to use it, as well as how to get alpha builds of [securiCAD Professional](https://www.foreseeti.com/securicad-professional/) that are compatible with the latest [MAL compiler](https://mal-lang.org/).

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

## Alpha builds of securiCAD Professional

Since the MAL compiler hasn't made a non-snapshot release, updates to the MAL compiler are pushed to the OSSRH snapshot repository as they are merged. To match this, the artifacts in foreseeti's maven repository are also updated to support the latest MAL compiler. This can introduce compatibility issues with the public release of securiCAD Professional. To enable you to use the latest MAL compiler, foreseeti offers alpha builds of securiCAD Professional in Amazon AWS. Your credentials described above will also give you access to these alpha builds.

To list and download the alpha builds, you need to download and install the [AWS Command Line Interface](https://aws.amazon.com/cli/).

To list available alpha build, use the following command:
```
aws s3 ls s3://alpha.securicad.com
```
This command could produce the following output:
```
2020-03-09 16:10:59  183095976 securiCAD-1.6.2-Professional-linux.gtk.x86_64.tar.gz
2020-03-09 16:11:23  181762198 securiCAD-1.6.2-Professional-macosx.cocoa.x86_64.dmg
2020-03-09 16:11:48  180500767 securiCAD-1.6.2-Professional-macosx.cocoa.x86_64.tar.gz
2020-03-09 16:12:13  183481938 securiCAD-1.6.2-Professional-win32.win32.x86_64.zip
2020-03-09 16:12:37  195650816 securiCAD-1.6.2-Professional-windows-installer.exe
2020-03-09 16:07:41         13 version.txt
```

The file `version.txt` contains the current version of the alpha build that is available in the s3 bucket, e.g. `1.6.2_alpha2`.

When you have decided which file to get, you can download it with the following command:
```
aws s3 cp s3://alpha.securicad.com/securiCAD-1.6.2-Professional-linux.gtk.x86_64.tar.gz .
```
This will download the requested file to your current directory.

## MAL license for securiCAD Professional

A MAL license for securiCAD Professional enables additional support for MAL languages. To request a MAL license, you need to generate a hardware token in `File > Licensing > Generate Token` and send it to support@foreseeti.com. Once you get a license file, you can enter it into securiCAD Professional in `File > Licensing > Replace License`.

Once securiCAD Professional restarts, a dialog should appear where you select which MAL language jar file to use. If the dialog doesn't appear, you might have to manually replace the license. This can be done by copying your license file to securiCAD Professional's workspace directory, and giving it the exact name `securiCAD.license`. On windows, that could be `C:\Users\joe\securiCAD\workspace\securiCAD.license`, on macOS, that could be `/Users/joe/securiCAD/workspace/securiCAD.license`, and on linux, that could be `/home/joe/securiCAD/workspace/securiCAD.license`.
