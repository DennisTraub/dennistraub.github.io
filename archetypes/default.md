---
date: '{{ .Date }}'
title: '{{ replace .File.ContentBaseName "-" " " | lower | humanize }}'
draft: false
categories: [""]
---
