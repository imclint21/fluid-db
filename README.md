<p align="center">
  <p align="center">
    <img src="https://raw.githubusercontent.com/thisisclint21/fluid-db/master/logo.svg" height="100" alt="FluidDB" />
  </p>
  <h3 align="center">
    About FluidDB
  </h3>
  <p align="center">
    FluidDB is a dynamic object storage database. 🦀
  </p>
  <p align="center">
    <a href="https://github.com/thisisclint21/fluid-db/actions?workflow=Build"><img src="https://github.com/thisisclint21/fluid-db/workflows/Build/badge.svg" /></a>
    <a href="https://www.rust-lang.org/"><img src="https://img.shields.io/badge/Made%20With-Rust-dea584" /></a>
    <a href="https://github.com/thisisclint21/fluid-db/blob/master/LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-lightgrey.svg" /></a>
    <a href="https://discord.gg/mZz67M6"><img src="https://img.shields.io/badge/Discord-Server-7289DA" /></a>
  </p>
</p>

## Introduction

Lucid is a high performance, secure and distributed key-value store accessible through an HTTP API, that is built around a modular configuration to enable features on the fly, like persistence, encryption SSE, compression, replication, and more.

[Read the complete Medium article →](https://medium.com/@clint21/lucid-an-http-key-value-store-c0e734586e26)

## Getting Started

Get the latest binary from the [releases](https://github.com/lucid-kv/lucid/releases) page and run these commands:

```
$ ./lucid init
$ ./lucid server
```


This is a simple proof-of-concept written in c#:

```csharp
// This is the PoC of FluidDB — Written by clint21.eth on February, 4th 2023

// ReSharper disable All

using System.Text.RegularExpressions;

var client = new FluidDbClient();

// 230204222038.948 3290 00000 user1 51.158.154.391:49024 104.18.7.129:443 2115 76835 0 CONNECT www.google.fr:443 HTTP/1.1

var logModel = DatabaseModel.FromRegex(@"\d{2}-\d{2} \d{2}:\d{2}:\d{2},\d{3}|\Z)");

var logsCollection = client.CreateCollection("logs", logModel);
logsCollection.Push("230204222038.948 7427 00000 hp_b09d66e3 51.158.154.191:49024 104.18.7.94:443 2115 76835 0 CONNECT www.carrefour.fr:443 HTTP/1.1");
logsCollection.Find(""); // Nothing for now

// Example with binary files

var rihanna = File.ReadAllBytes("~/sounds/rihanna-unfaithful.mp3");

var mp3Model = new DatabaseModel();

var soundsCollection = client.CreateCollection("mp3s", CollectionTypes.Binary);
soundsCollection.Push(rihanna);
```
