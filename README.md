# Get-Duplicate

[![Build Status](https://travis-ci.org/leojonathanoh/Get-Duplicate.svg?branch=master)](https://travis-ci.org/leojonathanoh/Get-Duplicate)

A Powershell module to find and list duplicate files.

To widen the duplicate search scope to be across all descendent files, use the `-Recurse` switch. By default, the scope is within the immediate folder.

To filter the search, use the `-Include`, `-Exclude`, and `-ExcludeDirectory` switches.

To list unique files, use the `-Inverse` switch.

The module supports pipelining either folder paths, or DirectoryInfo objects.

Additionally, `-AsHashtable` returns a hashtable containing:

```powershell
[string]$md5 = [arraylist]$files
```

## Install

```powershell
Install-Module -Name Get-Duplicate -Force
```

## Examples

```powershell
# Get duplicate files in 'C:/folder1' only
Get-Duplicate -Path 'C:/folder1'

# Get duplicate files in 'C:/folder1' and its descendents
Get-Duplicate -Path 'C:/folder1' -Recurse

# Get non-duplicate files in 'C:/folder1' and its descendents
Get-Duplicate -Path 'C:/folder1' -Recurse -Inverse

# Alternatively, you may pipeline folder paths
'C:/folder1' | Get-Duplicate

# Or  DirectoryInfo objects
Get-Item 'C:/folder1' | Get-Duplicate
```