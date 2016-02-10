# downloads.stackato.com

## Overview

This repository contains scripts for managing downloads.stackato.com.

## Usage

```shell
git clone https://github.com/hpcloud/downloads.stackato.com.git
cd downloads.stackato.com
rebuild/index
```

## How does it work?

When you run `rebuild/index`:
- It queries the object store for a list of downloads.
- This list of downloads is used to construct a lightweight mock locally.
- The script traverses this mock bucket, and builds an `index.html` in each directory.
- `index.html` contains links to objects immediately under this directory (not subdirectories).
- Once all the indexes are generated, it uploads the results to the object store.

When you run `rebuild/website-configuration`
- It queries the object store for a list of downloads.
- It queries the current configuration of the object store.
- It generates a new configuration with `/latest` references pointing to the latest releases.

## I don't want to actually upload anything!

```shell
rebuild/index --dryrun
```
