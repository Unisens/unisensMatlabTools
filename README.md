# unisensMatlabTools

This library provides some useful tools to work with the unisens data format in Matlab

It makes use of [unisens4java library](https://github.com/Unisens/unisens4java), [unisesn2excelLibs](https://github.com/Unisens/unisens2excel) and [Apache POI](https://poi.apache.org/).

## License

The unisensMatlabTools library is licensed under the LGPL.
<br />
<br />

## Descriptions of the matlab functions

| Matlab function | Description |
|-----------------|-------------|
|addUnisensJar.m|Add unisens.jar to java path|
|batchExamples.m|shows some simple examples of how to use the unisensMatlabTools|
|batchUnisens2Exel.m|add Results.xlsx file to all unisens datasets|
|batchUnisensBin2Csv.m|convert all unisens datasets in basePath from bin to csv|
|batchUnisensCsv2Bin.m|convert all unisens datasets in basePath from csv to bin|
|copyEntry.m|copy a unisens entry from one to another dataset|
|exel2UnisensHeaders.m|reintegrate previously extracted unisens header data from Excel back into unisens datasets|
|fixUnisensXmlNs.m|fix unisens namespace in unisens.xml|
|getAllUnisensPaths.m|get a list of paths of all unisens datasets inside basepath|
|importMovisensEcg.m|import movisens ecg from unisens dataset|
|injectMarker.m|inject marker from a marker dataset into a measurement dataset|
|rdir.m|returns the basepath|
|removeEntriesOtherThan.m|remove all entries from a unisens dataset but the ones given in entryNames|
|removeEntry.m|remove an entry from a unisens dataset|
|renameArtifactMarker.m|renames artifact.csv entry to newName and changes samplerate to 1Hz|
|renameEntry.m|rename an entry in a unisens dataset|
|unisens2xls.m|convert unisens dataset to excel (only entries with the same given sample rate)|
|unisensAddZerosEnd.m|adds zeros to the end of a unisens dataset|
|unisensAdjustSamplerate.m|adjuses the sample rate of the entryTest signal in srcPathTest to the sample rate of entryRef signal in srcPathRef|
|unisensBin2Csv.m|convert unisens dataset with bin entries to dataset with csv entries|
|unisenCrop.m|crop a unisens dataset to a specified region|
|unisensCsv2Bin.m|convert unisens dataset with csv entries to dataset with bin entries|
|unisensCutEnd.m|cut off the end of a unisens dataset|
|unisensCutStart.m|cut off a region at the beginning of a unisens dataset|
|unisensEcg2Csv4Kubios.m|convert unisens dataset with an ecg entry to a csv file that can be imported by Kubios HRV|
|unisensHeaders2Exel.m|extract unisens header data from unisens datasets to Excel for checking or editing|
|unisensMerge.m|merges two datasets|
|unisensReadSignal.m|read a single signal from a unisens dataset|
|unisensSynchronize.m|synchronizes two unisens datasets|
|unitPrefix2Factor.m|get factor from unit prefix|

## Detailed descriptions

### # unisens2xls

This Matlab Skript converts unisens timeseries with a specific samplerate (usually 1/60s) to Excel Results.xlsx files. In addition markers and other non equdistand event data, stored in unisens event entries, are converted.

The standard format for marker is:

  ```text
  (2018-07-24T18:12:03.851; M; Maker 1)
   ```

The underlying java library (<https://github.com/Unisens/unisens2excel>) also supports JSON format:

  ```json
  [{"date":"2018-07-24T18:12:03.851","type":"M","comment":"Maker 1"}]
  ```

#### Convert single unisens dataset

```matlab

unisens2xls(unisensPath);

unisens2xls(unisensPath, sampleRate);

unisens2xls(unisensPath, sampleRate, excelPathAndFile);

```

When no samplerate is given 1/60s is assumed.
When no excelPathAndFile is give, ```unisensPath\Results.xslx``` i used.

#### Batch convert datasets

```matlab

batchUnisens2Excel (basePath, sampleRate);

```
