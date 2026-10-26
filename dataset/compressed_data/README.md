# compressed_data

These three files are too big for GitHub (over 100 MB each), so they are stored compressed with gzip. Uncompress them before running `code/exploration.ipynb`.

| Compressed file | Uncompress to |
|---|---|
| `nvd_cves.csv.gz` | `dataset/nvd_cves.csv` |
| `cves.csv.gz` | `dataset/uckg/cves.csv` |
| `edges_cve_cpe.csv.gz` | `dataset/uckg/edges_cve_cpe.csv` |

## Option 1: Python (any operating system)

Open a terminal in the `dataset` folder, start `python`, and paste:

```python
import gzip, shutil

files = {
    "compressed_data/nvd_cves.csv.gz": "nvd_cves.csv",
    "compressed_data/cves.csv.gz": "uckg/cves.csv",
    "compressed_data/edges_cve_cpe.csv.gz": "uckg/edges_cve_cpe.csv",
}
for src, dst in files.items():
    with gzip.open(src, "rb") as f_in, open(dst, "wb") as f_out:
        shutil.copyfileobj(f_in, f_out)
```

## Option 2: Terminal (macOS, Linux, or Git Bash on Windows)

From the `dataset` folder:

```bash
gunzip -c compressed_data/nvd_cves.csv.gz > nvd_cves.csv
gunzip -c compressed_data/cves.csv.gz > uckg/cves.csv
gunzip -c compressed_data/edges_cve_cpe.csv.gz > uckg/edges_cve_cpe.csv
```

The compressed files stay in this folder, and the uncompressed CSVs are ignored by git, so nothing extra gets committed.
