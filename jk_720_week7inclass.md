    read_1 <- "CGCGCAGTAGGGCACATGCCAGGTGTCCGCCACTTGGTGGGCACACAGCCGATGACGAACGGGCTCCTTGACTATAATCTGACCCGTTTGCGTTTGGGTGACCAGGGAGAACTGGTGCTCCTGC"
    reads <- c("CGCGCAGTAGGGCACATGCCAGGTGTCCGCCACTTGGTGGGCACACAGCCGATGACGAACGGGCTCCTTGACTATAATCTGACCCGTTTGCGTTTGGGTGACCAGGGAGAACTGGTGCTCCTGC", "AAAAAGCCAACCGAGAAATCCGCCAAGCCTGGCGACAAGAAGCCAGAGCAGAAGAAGACTGCTGCGGCTCCCGCTGCCGGCAAGAAGGAGGCTGCTCCCTCGGCTGCCAAGCCAGCTGCCGCTG", "CAGCACGGACTGGGGCTTCTTGCCGGCGAGGACCTTCTTCTTGGCATCCTTGCTCTTGGCCTTGGCGGCCGCGGTCGTCTTTACGGCCGCGGGCTTCTTGGCAGCAGCACCGGCGGTCGCTGGC")

1.  Drosophila melanogaster
2.  The class is character. length(reads) returns 3, the length of the
    vector. nchar(reads) returns 124.
3.  

<!-- -->

    read_1split <- strsplit(read_1, split = '')
    for (i in read_1split) {
      print(i)
    }

    ##   [1] "C" "G" "C" "G" "C" "A" "G" "T" "A" "G" "G" "G" "C" "A" "C" "A" "T"
    ##  [18] "G" "C" "C" "A" "G" "G" "T" "G" "T" "C" "C" "G" "C" "C" "A" "C" "T"
    ##  [35] "T" "G" "G" "T" "G" "G" "G" "C" "A" "C" "A" "C" "A" "G" "C" "C" "G"
    ##  [52] "A" "T" "G" "A" "C" "G" "A" "A" "C" "G" "G" "G" "C" "T" "C" "C" "T"
    ##  [69] "T" "G" "A" "C" "T" "A" "T" "A" "A" "T" "C" "T" "G" "A" "C" "C" "C"
    ##  [86] "G" "T" "T" "T" "G" "C" "G" "T" "T" "T" "G" "G" "G" "T" "G" "A" "C"
    ## [103] "C" "A" "G" "G" "G" "A" "G" "A" "A" "C" "T" "G" "G" "T" "G" "C" "T"
    ## [120] "C" "C" "T" "G" "C"

1.  It is a list.

<!-- -->

    read_1splitvec <- unlist(read_1split)
    str(read_1splitvec)

    ##  chr [1:124] "C" "G" "C" "G" "C" "A" "G" "T" "A" "G" "G" "G" "C" "A" ...

1.  

<!-- -->

    tabler1s <- table(read_1split)
    tabler1s / sum(tabler1s)

    ## read_1split
    ##         A         C         G         T 
    ## 0.1854839 0.2822581 0.3225806 0.2096774

1.  

<!-- -->

    basefreq <- function(x) {
      y <- table(x)
      return(y / sum(y))
    }
    basefreq(read_1split)

    ## x
    ##         A         C         G         T 
    ## 0.1854839 0.2822581 0.3225806 0.2096774

This works for both lists and vectors.

2.1 In the first case x is returned because it was defined outside the
loop. In the second case x is merely an internal variable within the
function and R is unable to call these.

2.2

    x <- c()

    system.time(for (i in 1:10000) {
      x <- c(x, i^2)
    })

    ##    user  system elapsed 
    ##    0.11    0.03    0.15

2.3

    y <- vector(mode = "integer", length = 10000)

    system.time(for (i in 1:10000) {
      y[i] <- i^2
    })

    ##    user  system elapsed 
    ##       0       0       0

2.4 Presumably using the apply function with an anonymous function to
square the elements of 1:10000. I forget how to do this.
