# Summary of Metanodes and Metaedges

| metanode            | abbreviation | metaedges | nodes | unconnected_nodes |
|:--------------------|--------------|-----------|-------|-------------------|
| Anatomy             | A            | 1         | 652   | 115               |
| Biological Process  | BP           | 1         | 12322 | 0                 |
| Cellular Component  | CC           | 1         | 1695  | 0                 |
| Compound            | C            | 2         | 2778  | 535               |
| Disease             | D            | 3         | 137   | 16                |
| Gene                | G            | 4         | 20608 | 3232              |
| Molecular Function  | MF           | 1         | 3460  | 0                 |
| Pharmacologic Class | PC           | 1         | 478   | 0                 |
| Symptom             | S            | 1         | 505   | 35                |

| metaedge                                  | abbreviation | edges  | source_nodes | target_nodes |
|:------------------------------------------|--------------|--------|--------------|--------------|
| Compound - binds - Gene                   | CbG          | 25733  | 2167         | 2705         |
| Disease - localizes - Anatomy             | DlA          | 4335   | 121          | 537          |
| Disease - presents - Symptom              | DpS          | 3758   | 121          | 470          |
| Disease - resembles - Disease             | DrD          | 250    | 87           | 81           |
| Gene - participates - Biological Process  | GpBP         | 548342 | 16061        | 12322        |
| Gene - participates - Cellular Component  | GpCC         | 88885  | 12241        | 1695         |
| Gene - participates - Molecular Function  | GpMF         | 104777 | 14213        | 3460         |
| Pharmacologic Class - includes - Compound | PCiC         | 1948   | 478          | 1202         |
