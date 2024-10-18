## AW-Checker

Maude is required to execute AW-Checker. It can be downloaded from here: https://maude.cs.illinois.edu/wiki/Maude_download_and_installation.

After installing, we can try checking properties by the following commands:

```
maude AW-Checker/propositions.maude
Maude> load Traces/lidar/cutin/cutin20-10-1.maude .
Maude> load AW-Checker/metacom.maude .
Maude> load Traces/lidar/cutin/properties-checking.maude .
```