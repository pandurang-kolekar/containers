# Containers for Bioinformatics Workflows

Usage guidelines

## 1. cutadapt

[cutadapt documentation](https://cutadapt.readthedocs.io/)

```
docker run --entrypoint cutadapt -v <path to data folder>:/data pskolekar/cutadapt:2.9 -u 17 -o /data/test_trimmed_R1.fastq.gz /data/test_R1.fastq.gz
```
