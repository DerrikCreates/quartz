---
title: Hosting a quartz 4 site
draft: "false"
description: partial guide on how to build and host quartz 4
date: 2026-02-08
---
 read the official docs on this. this is going to be a very brief step by step to quickly get up and running.

# Creating project

```shell
git clone https://github.com/jackyzha0/quartz.git
cd quartz
npm i
npx quartz create
```

# Preview locally
```shell
npx quartz build --serve
```


# Config for self hosting

set base url in `quartz.config.js`


# Caddyfile

```caddyfile
docs.derrikcreates.com {
    root * /quartz/public
    try_files {path} {path}.html {path}/ =404
    file_server
    encode gzip
 
    handle_errors {
        rewrite * /{err.status_code}.html
        file_server
    }
}
```