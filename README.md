# Madison Courses Extractor
> [!NOTE]
> Active development and maintenance of this project is now done under the [Madgrades extractor](https://github.com/Madgrades/madgrades-extractor)! This repository is now read-only.

This tool extracts data from the University of Wisconsin–Madison's [Percentage Distribution of Grades Reports (PDGR)](https://registrar.wisc.edu/grade-reports/#:~:text=Course%20Grade%2DDistribution%20Reports) and [Departmental Instructional Reports (DIR)](https://registrar.wisc.edu/curricular-build/#dir:~:text=The%20Departmental%20Instructional%20Report%20%28DIR%29%20contains%20every%20scheduled%20course%20section%20for%20every%20department%2E), interprets the data as a human would, converts them to tabular form, and outputs them as CSV files.

* **Accurate:** Having high accuracy is this tool's first priority. Though verifying 100% accuracy would be a monumental task, this tool's output has been compared with other extractors' outputs to improve the accuracy of all extractors involved. It was designed and built with accuracy as its most important feature from its conception. As of August 2026, this tool extracts 1,940,159 PDF lines with 1,272,804 rows of actual data, while having only 6 known inaccuracies, resulting in an estimated 99.9995% accuracy.
* **Fast:** Built with [tabula-java](https://github.com/tabulapdf/tabula-java), this tool is dramatically faster than comparable tools built on other PDF parsing libraries that I have seen. Additionally, this tool can take advantage of multithreading.
* **Maintainable:** Despite the inherent headaches that come with extracting data from PDFs, this tool was intended to be maintainable. It was built with the mindset that there are more new PDF formats to come, and they may even look wildly different from existing ones.
* **Unopinionated:** This tool makes as few decisions about the data for you as possible. It delivers them presented as closely as possible to how they are interpreted from the reports.

## Getting Started

1. Ensure you have a Java 8 Runtime Environment.

2. Build from source with Maven: clone this repository and build with `mvn clean install`.

3. Obtain the report PDFs you want to extract data from. The recommended source is [this archive](https://github.com/Madgrades/madgrades-pdf-archive).

4. Run with `java -jar Madison-Courses-Extractor.jar` and the usage instructions.

## Usage

```bash
> java -jar Madison-Courses-Extractor.jar --help
Usage: madison-courses-extractor [-ehvV] [-o=<outputDirectory>]
                                 [-t=<threadCount>] INPUT...
Extracts tabular data from UW-Madison report PDFs.
      INPUT...     PDF files and/or directories to process.
  -e, --excluded   Also write excluded rows output files.
  -h, --help       Show this help message and exit.
  -o, --output-dir=<outputDirectory>
                   Directory where output files will be written.
  -t, --threads=<threadCount>
                   Number of extraction threads.
  -v, --verbose    Print abnormal-row warnings.
  -V, --version    Print version information and exit.
```

> [!WARNING]
> Due to Tabula not being thread-safe, as you increase the number of threads, memory requirements go up.

## Documentation

To learn more about the design philosophy for this extractor, known limitations, and implementation details, read [docs.md](./docs.md)

*This project is unaffiliated with UW–Madison* 
