# Calculating the Average Expression Profile From a scRNA-seq Reference Dataset
Because niche-DE compares observed gene expression against the average expression for a cell type, making an average expression profile matrix is critical. 

# From Raw Data
If you have raw data matrices, the expression profile matrix can be creaeted using the function 'CreateLibraryMatrix'. his function takes in 2 arguments 

<details>
  <summary>Arguments</summary>
  
  + seurat data: Single cell rna-seq counts matrix. Dimension should be #cells/spots by #genes
  + cell type: Cell type assignment matrix. First column is cell names and second column is cell type assignment.
  
 </details>
 
   ```
 #read in data
 data('liver_met_data')
 data('liver_met_CT')
 #create library matrix
 CreateLibraryMatrix(liver_met_data,liver_met_CT)
 ```
 

# From Seurat object
If your reference dataset is a seurat object, you can use the function 'CreateLibrarymatrixFromSeurat'. This function takes in 2 arguments 

<details>
  <summary>Arguments</summary>
  
  + seurat object: A seurat object
  + assay: The assay from which to extract the counts matrix to calculate the average expression profile
  Note that the cell types of the seurat object are assumed to be available via the command 'Idents(seurat object)'
  
 </details>
  
 ```
 #read in data
 data('liver_met_ref')
 #create library matrix
 CreateLibraryMatrixFromSeurat(liver_met_ref,assay = 'RNA')
 ```

