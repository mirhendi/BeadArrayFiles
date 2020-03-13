# IlluminaBeadArrayFiles
Library to parse file formats related to Illumina bead arrays. GTC files contain genotyping (and other) information encoded in a binary format. The IlluminaBeadArrayFiles library provides a parser to extract information from these binary files.

## Generating GTC files
If you have intensity data files (IDATs) for which GTC files are not currentty available, it is possible to generate these files with Illumina Array Analysis Platform (https://support.illumina.com/array/array_software/illumina-array-analysis-platform.html)

## Build instructions
The IlluminaBeadArrayFiles repository supports building a package with the python distutils module (https://docs.python.org/2/distutils/setupscript.html). To build a source distribution, run the included setup.py script supplying the "sdist" command

>python setup.py sdist

## Installation instructions
After unpacking the installation package, run the setup.py script supplying the "install" command

>python setup.py install

## Dependencies
The library depends on the availability of the numpy package in the python installation (http://www.numpy.org/)

## Example usage

> from IlluminaBeadArrayFiles import GenotypeCalls, BeadPoolManifest, code2genotype  
> import sys  
> gtc_file = "path_to_genotypes.gtc"  
> manifest_file = "path_to_manifest.bpm"  
> names = BeadPoolManifest( manifest_file ).names  
> genotypes = GenotypeCalls( gtc_file ).get_genotypes()     
> for (locus, genotype) in zip( names, genotypes ):  
> &nbsp;&nbsp;sys.stdout.write( locus + "," + code2genotype[genotype] + "\n" )

Also, see examples/gtc_final_report.py for an additional example of usage. 

## GTC File Format
The specification for the GTC file format is provided in docs/GTC_File_Format_v5.pdf

## Description of classes and objects in exposed in package
For further details on specific class methods, please consult the built-in docstring documentation

### code2genotype
Dictionary mapping from genotype byte code (see GTC file format specification) to a string representing the genotype (e.g., "AA")

### NC, AA, AB, and BB
Constants representing byte values for associated genotypes

### GenotypeCalls
Class to parse GTC files as produced by Illumina AutoConvert and AutoCall software.

### NormalizationTransform
Class to encapsulate a normalization transform for conversion of raw intensity data to normalized intensity data

### ScannerData
Class to encapsulate the meta-data collected in the GTC file for a scanner instrument

### BeadPoolManifest
Class for parsing a binary (BPM) manifest file. This class can be used to recover the in-order list of loci names in a given manifest, which is necessary to associate the genotype information present in the GTC file to a specific locus name. 

### RefStrand, SourceStrand
Represents different strand conventions in manifest

### BeadPoolManifest
Read information from a binary BPM file

### LocusAggregate
Aggregate information across many samples for a given loci

### ClusterFile
Read information from a binary EGT file

## Compatibility
This library is compatible with Python 3.7 and was tested with Python 3.7.6

## License

This is the upgraded version of https://github.com/Illumina/BeadArrayFiles to support Python 3



