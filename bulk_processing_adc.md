Bulk processing on ADC
================

My collection of useful code snippets for bulk processing data on the Arctic Data Center:

Updating file types
-------------------

In this example, I needed to change the file types of a bunch of zip files in different packages submitted by the same PI.

``` r
library(tidyverse)
library(dataone)

cn <- CNode('PROD')
mn <- getMNode(cn,'urn:node:ARCTIC')

results <- query(mn, list(q = 'submitter:*0000-XXXX-XXXX-XXXX',
                               fq = "formatType:DATA",
                               fl = '*',
                               sort = 'dateUploaded+desc',
                               rows='100'),
                      as = "data.frame")

zip_files <- results %>% 
  as_tibble() %>% 
  filter(str_detect(fileName, "zip"),
         formatId == "application/octet-stream") %>% 
  select(fileName, formatId, id)

for(pid in zip_files$id){
  sysmeta <- dataone::getSystemMetadata(mn, pid)
  sysmeta@formatId <- "application/zip"
  updateSystemMetadata(mn, pid, sysmeta)
  cat(pid, "has been updated \n")
}
```

*Note:* The same trick can be used for `set_file_name` and other processes.
