# Region matrix
is a tool for writing the matrix of areas-under-the-curve (AUCs) of indexed BAMs in regions specified by a BED file. An AUC is the sum of the number of reads aligning across each base of the region. Only primary alignments in each BAM file are considered. When specifying regions in the BED file, remember that its coordinates are 0-based and half-open: the start coordinate is included in the region, and the end coordinate is excluded from the region.

Require Python 2.x and https://github.com/Ensembl/WiggleTools.

## Usage

```
python region_matrix.py --regions <3-column BED file specifying regions> \
                        --bams <space-separated list of BAM files> \
                        --wiggletools <path to wiggletools executable> \
                        -p <max number of wiggletools processes to run at once>
```

## Output

Matrix whose `(i, j)`th element is the AUC of the `i`th sample in the `j`th region. Output is written to stdout.

## License

MIT. See `LICENSE` for details.
