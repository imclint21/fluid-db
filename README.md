# fluid-db

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
