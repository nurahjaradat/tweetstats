#' @title keystats
#' @description keystats() allows for easy Twitter analysis of user-specified
#' Twitter keywords and hashtags. See details for more information.
#' @param key keyword or hashtag that the user wishes to analyze
#' @param n number of tweets to analyze relating to key, maximum tweets to
#' analyze is 18,000, Default: 10000
#' @param top_num number of top words/hashtags/locations displayed in output,
#' Default: 10
#' @param graph_col color of output graphs, Default: 'dodgerblue3'
#' @return an HTML output containing summary information and graphics of the
#' specified keyword(s) using input keyword(s). See details for specifics.
#' @details keystats() allows Twitter users to search the website by keyword or
#' hashtag,returning multiple graphics and statistical summaries such as a
#' bar plot of related unique words, a word cloud, a radar chart, and two
#' bar plots of location statistics.
#' @examples
#' \dontrun{
#' if(interactive()){
#'  #keystats("data science", n=1000, top_num = 20)
#'  }
#' }
#' @rdname keystats
#' @export

keystats <- function(key,n=10000,top_num=10, graph_col = "dodgerblue3"){
  if(!is.numeric(n))
    stop("n must be numeric number no more than 18000", call. = FALSE)
  if(n>18000)
    stop("n should not exceed 18000", call. = FALSE)
  if(!is.numeric(top_num))
    stop("top_num must be numeric")
  key <- deparse(substitute(key))
  n <- deparse(substitute(n))
  top_num <- deparse(substitute(top_num))
  graph_col <- deparse(substitute(graph_col))

  # read in the template and modify it
  report <- readLines("inst/keystatsTemplate.txt")
  report <- gsub("xxxnum", n, report, fixed = TRUE)
  report <- gsub("xxxkeyword", key, report, fixed = TRUE)
  report <- gsub("xxxtop_num", top_num, report, fixed = TRUE)
  report <- gsub("xxxfill", graph_col, report, fixed = TRUE)

  # write out template
  tf <- tempfile(fileext = ".Rmd")
  to <- tempfile(fileext = ".Html")
  writeLines(report, tf)

  # render R markdown and display
  library(rmarkdown)
  render(input = tf,
         output_format = "html_document",
         output_file = to)
  file.show(to)

  invisible(to)
}
