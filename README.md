# Region matrix
is a tool for writing the matrix of areas-under-the-curve (AUCs) of indexed BAMs in regions specified by a BED file. An AUC is the sum of the number of reads aligning across every base of the region. Only primary alignments in each BAM file are considered. When specifying regions in the BED file, remember that its coordinates are 0-based and half-open: the start coordinate is included in the region, while the end coordinate is excluded from the region.

Requires Python 2.x and https://github.com/Ensembl/WiggleTools.

## Usage

```
python region_matrix.py --regions <3-column COORDINATE-SORTED BED file specifying regions> \
                        [--bams <space-separated list of BAM files> OR --bam-manifest <path to BAM manifest file] \
                        --wiggletools <path to wiggletools executable> \
                        -p <max number of wiggletools processes to run at once>
```

## Specifying BAMs

BAMs may be specified as a space-separated list of paths after `--bams` or as the path to a BAM manifest file as the argument of `--bam-manifest`. Each line of the BAM manifest file takes the form
```
<path to indexed BAM><TAB><sample name>
```
. If BAMs are specified as the argument of `--bams`, sample names are taken to be their paths.

## Output

Table whose `(i, j)`th entry is the AUC of the `i`th sample in the `j`th region. Output is written to stdout; rows are labeled by sample, and columns are labeled by region.

## License

MIT. See `LICENSE` for details.
