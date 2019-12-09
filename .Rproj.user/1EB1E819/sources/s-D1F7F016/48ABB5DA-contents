#' @title userstats
#' @description userstats() allows for easy Twitter analysis of user-specified
#' Twitter accounts. See details for more information.
#' @param user username of a real Twitter account that the user wishes to analyze
#' @param n number of tweets to analyze from that account, Default: 1000
#' @param bg_col background color of output tables, Default: 'white'
#' @param txt_col text color of output tables, Default: '#1A5276'
#' @param year year during which tweets are to be analyzed and displayed in
#' output, Default: 2019
#' @param x number of recent tweets to display from that account in the output,
#' Default: 10
#' @return an HTML output containing summary information of the specified
#' account(s) using input username(s) as well as the specified number of recent
#' tweets from that account(s)
#' @details userstats() allows Twitter users to search the website by username,
#' allowing the user to search multiple usernames at one time, specify which year
#' they would like summary information for, specify the number of tweets they
#' would like to analyze (with a maximum output allowed of 3,200 tweets),
#' customize the background color of output tables, and customize the text color
#' of the output with the assumption of knowledge of HTML color codes.
#' @examples
#' \dontrun{
#' if(interactive()){
#' userstats(c("taylorswift13","katyperry"), 1000, year = 2019, x=5)
#' userstats("taylorswift13", 1000, x=5)
#' userstats(c("taylorswift13","21savage","trvisxx","katyperry"), 1000, year=2019, x = 3)
#' }
#' @rdname userstats
#' @export

userstats <- function(user, n=1000, bg_col = "white", txt_col = "#1A5276", year=2019, x=10){
  if(!is.numeric(n))
    stop("n must be numeric number no more than 3200", call. = FALSE)
  if(n>3200)
    stop("n should not exceed 3200", call. = FALSE)
  user <- deparse(substitute(user))
  n <- deparse(substitute(n))
  year <- deparse(substitute(year))
  x <- deparse(substitute(x))
  # read in the template and modify it
  report <- readLines("inst/userstatsTemplate.txt")
  report <- gsub("xxxbg", bg_col, report, fixed = TRUE)
  report <- gsub("xxxnum", n, report, fixed = TRUE)
  report <- gsub("xxxusers", user, report, fixed = TRUE)
  report <- gsub("xxxcol", txt_col, report, fixed = TRUE)
  report <- gsub("xxxyr", year, report, fixed = TRUE)
  report <- gsub("xxxtwt", x, report, fixed = TRUE)
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
