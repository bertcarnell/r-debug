FROM wch1/r-debug

RUN apt-get update && apt-get upgrade -y

RUN apt-get -y install libgmp-dev qpdf

# Rcpp, testthat, and rmarkdown should already be installed
RUN RDvalgrind -e 'if (!all(c("Rcpp", "testthat", "rmarkdown") %in% installed.packages()[,"Package"])) install.packages(c("Rcpp", "testthat", "rmarkdown"))'
# assertthat, DoE.base, and knitr are not installed already
RUN RDvalgrind -e 'install.packages(c("assertthat", "DoE.base", "knitr"))'

RUN RDsan -e 'if (!all(c("Rcpp", "testthat", "rmarkdown") %in% installed.packages()[,"Package"])) install.packages(c("Rcpp", "testthat", "rmarkdown"))'
RUN RDsan -e 'install.packages(c("assertthat", "DoE.base", "knitr"))'

RUN RDcsan -e 'if (!all(c("Rcpp", "testthat", "rmarkdown") %in% installed.packages()[,"Package"])) install.packages(c("Rcpp", "testthat", "rmarkdown"))'
RUN RDcsan -e 'install.packages(c("assertthat", "DoE.base", "knitr"))'

