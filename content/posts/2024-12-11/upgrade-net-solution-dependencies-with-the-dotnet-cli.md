---
draft: false
date: 2024-12-11T09:03:44Z
title: "Upgrading .NET dependencies: Essential dotnet CLI commands"
description: Quick reference guide for managing .NET package updates using dotnet CLI commands. Learn to list outdated packages, upgrade specific versions, and handle bulk updates.
categories: [.NET, CLI, bash, shell, tips]
isNote: true
---

Need to update your .NET packages? Here are the key commands you'll need:

### Check for Updates:
```shell
dotnet list package --outdated
```

### Update Packages:
Single package (latest version):
```shell
dotnet add package PackageName
```

Specific version:
```shell
dotnet add package PackageName --version 1.2.3
```

### Bulk updates:
While there's no built-in command to update everything, you can use `dotnet-outdated`:

```shell
dotnet tool install --global dotnet-outdated-tool
dotnet outdated -u  # Updates all packages
```

**Pro tip:** Always backup, and test after upgrading. Add `--prerelease` if you need preview versions.