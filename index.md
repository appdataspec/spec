# Table of Contents

- [Introduction](#introduction)
    - [Purpose](#purpose)
- [Terms](#terms)
    - [ENVIRONMENT_VARIABLE](#user)
    - [MUST](#must)
    - [USER](#user)
- [Path determination](#path-determination)
    - [Global app data](#global-app-data)
    - [Per user app data](#per-user-app-data)

# Introduction

## Purpose

The app data spec's purpose is to determine where app data is stored on a given platform/OS.

## Terms

### ENVIRONMENT_VARIABLE

As defined by
[wikipedia](https://en.wikipedia.org/wiki/Environment_variable)

### MUST

As defined by [RFC 2119](https://tools.ietf.org/html/rfc2119)

### USER

As defined by
[wikipedia](https://en.wikipedia.org/wiki/User_(computing))

# Path determination

The path of app data [MUST](#must) be determined via hydration of the
following templates where:

- ${env:NAME} represents an
  [ENVIRONMENT_VARIABLE](#environment_variable) resolved at runtime

## Global app data:

Global app data represents globally applicable app data, i.e. not
specific to a [USER](#user).

| OS      | Path template                | Reference                                                                                                                                                                              |
|:--------|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows | ${env:ProgramData}           | [msdn.microsoft.com](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457(v=vs.85).aspx) (FOLDERID_ProgramData)                                                           |
| OSX     | /Library/Application Support | [developer.apple.com](https://developer.apple.com/library/content/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html) (Application Support directory) |
| Linux   | /var/lib                     | [refspecs.linuxfoundation.org](http://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html#varlibVariableStateInformation)                                                                |

## Per user app data:

Per user app data represents [USER](#user) specific app data.

| OS      | Path template                       | Reference                                                                                                                                                                              |
|:--------|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows | ${LOCALAPPDATA}                     | [msdn.microsoft.com](https://msdn.microsoft.com/en-us/library/windows/desktop/dd378457(v=vs.85).aspx) (FOLDERID_LocalAppData)                                                          |
| OSX     | ${HOME}/Library/Application Support | [developer.apple.com](https://developer.apple.com/library/content/documentation/General/Conceptual/MOSXAppProgrammingGuide/AppRuntime/AppRuntime.html) (Application Support directory) |
| Linux   | ${HOME}                             | conventional                                                                                                                                                                           |

