---
title: "[[ .Title ]]" 
description: "[[ .Description ]]"
image: "[[ .Banner ]]"
date: [[ .CreationDate.Format "2006-01-02T15:04:05+07:00" ]]
lastmod: [[ .LastModified.Format "2006-01-02T15:04:05+07:00" ]]
author: "[[ .Author ]]"
tags:[[ range .Tags ]]
    - "[[ .Name ]]"[[end]]
categories:[[ range .Categories ]]
    - "[[ .Name ]]"[[end]]
draft: false
---

[[- /* Check if it is a hackthebox active machine */ -]]
[[$hackTheBox := 0]]
[[$active := 0]]
[[range .Categories -]]
    [[if eq .Name "hackthebox" -]]
        [[$hackTheBox = 1]]
    [[end -]]
    [[if eq .Name "active" -]]
        [[$active = 1]]
    [[end -]]
[[end -]]

[[ if (and $hackTheBox $active)]]
[[- /* Check if it is a windows machine */ -]]
[[$windows := 0]]
[[range .Tags -]]
    [[if eq .Name "windows" -]]
        [[$windows = 1]]
    [[end -]]
[[end -]]
{{% center %}}
This machine is currently **active**. Please enter the [[if $windows]]Administrator[[else]]root[[end]] hash, not the `root.txt`.
{{% /center %}}

{{% hugo-encryptor "[[ rich .Properties.Password.RichText ]]" %}}
[[ .Content ]]
{{% /hugo-encryptor %}}
[[ else]]
[[ .Content ]]
[[ end ]]