# Table of Contents

- [Introduction](#introduction)
    - [Purpose](#purpose)
- [Terms](#terms)
- [Path determination](#path-determination)
    - [Global app data](#global-app-data)
    - [Per user app data](#per-user-app-data)

# Introduction

## Purpose

The app data spec's purpose is to standardize determination of where app
data is stored in the context of a given app & platform/OS.

## Terms

- environment variable: as defined by
  [wikipedia](https://en.wikipedia.org/wiki/Environment_variable)
- user: as defined by
  [wikipedia](https://en.wikipedia.org/wiki/User_(computing))

# Path determination

The path of app data can be determined via the following templates
where:

- ${env:NAME} represents environment variable resolved at runtime

## Global app data:

Global app data represents globally applicable app data, i.e. not
specific to a user.

| OS      | Path template                | Reference                                                                                                                                                                              |
|:--------|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows | ${env:ProgramData}           | [msdn.microsoft.com](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457(v=vs.85).aspx) (FOLDERID_ProgramData)                                                           |
| OSX     | /Library/Application Support | [developer.apple.com](https://developer.apple.com/library/content/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html) (Application Support directory) |
| Linux   | /var/lib                     | [refspecs.linuxfoundation.org](http://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html#varlibVariableStateInformation)                                                                |

## Per user app data:

Per user app data represents user specific app data.

| OS      | Path template                       | Reference                                                                                                                                                                              |
|:--------|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows | ${LOCALAPPDATA}                     | [msdn.microsoft.com](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457(v=vs.85).aspx) (FOLDERID_LocalAppData)                                                          |
| OSX     | ${HOME}/Library/Application Support | [developer.apple.com](https://developer.apple.com/library/content/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html) (Application Support directory) |
| Linux   | ${HOME}                             | conventional                                                                                                                                                                           |

