---
layout: post
title:  "How To Use R Markdown in Jekyll"
date:   2022-09-27
author: Zayne Kirkham
description: A short how-to on an important data science blogging skill
image: /assets/images/hex-rmarkdown.png
---
## Introduction

   Jekyll blogs allow their owners to have a massive amount of control
in how their websites are presented by sourcing individual posts from
Markdown files. While it seems good at first, this restriction to
Markdown files cuts off one of a data scientist’s greatest tools: R
Markdown.

   R Markdown have a pivotal place in the field of data
science. Data science is a discipline that heavily relies upon
reproducibility. The code used to analyze data should be accessible for
those seeking to reproduce the analysis so that they may verify your
results.

   While it is possible to simply copy and paste your code into your
reports and blogs, R Markdown provides a much cleaner and
simpler alternative by letting you perform your analysis directly in the
report file. When these documents are rendered, the code is evaluated
and included in the report, according to the parameters you set in the
document.

   This evaluation is not performed when the post page is rendered in
Jekyll; in fact, Jekyll does not even recognize any file type other than
.md as a blog post. This can be extremely frustrating to someone seeking
to make their code. Luckily, there is a way to get around this.

## How to

   The solution is deceptively simple. When you create an R Markdown in Posit (R-Studio), you are only offered three selections for
which file types your file can be rendered into. These three options are
HTML, PDF and Word. In reality, there are additional types, each with
their own uses. The one we will focus on today is gfm, or Github
Flavored Markdown. This is a special type of markdown that seamlessly
integrates itself into Github-based Jekyll blogs.

   To render your document into gfm, replace the top output option in
the YAML code at the top of your file with the following code.

    output:
      md_document:
        variant: gfm
        preserve_yaml: False

   After you render your converted markdown file, add the YAML needed at
the top of the file to publish the blog. Next, make sure the file is in
the correct folder—usually designated as `_posts`—and you are good to
go!

## A Comment on Images

   There is a small caveat to be aware of while using this method:
images. When you render your R Markdown file to one of the
three standard options, your images are embedded in the file. When you
render to a markdown file, however, the images are placed in a separate
folder and only referenced in the markdown. When you push your post to
your github repository, these images must be pushed as well. The
markdown reference to the image must be updated to point to the raw link
of the image in your repository.

   I suggest simplifying this by designating the folder in which your
images will be stored at the beginning of your R Markdown file with the
code below. You can push this folder with your blog post.

    knitr::opts_chunk$set(fig.path = "images/")

   Here is a simple plot to demonstrate how to include images.

``` r
library(ggplot2)
ggplot(data = diamonds) +
  geom_violin(aes(y=price, x=cut, fill = cut), show.legend = FALSE)
```
![Figure](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/_posts/Images/unnamed-chunk-1-1.png)

Image markdown before alteration:
```
![](images/unnamed-chunk-1-1.png)
```
Image markdown after alteration:
```
![Figure](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/_posts/Images/unnamed-chunk-1-1.png)
```

## Conclusion

   While researching for this post, I was astonished by how little
discussion there was about it. I was eventually able to find one place
that discussed it: this blog post
[here](https://jchellmuth.com/news/jekyll/website/code/2020/01/04/Rmarkdown-posts-to-Jekyll.html).
While some of the things the author discusses are depreciated, his post
was instrumental in helping me to figure out how to work out how to
place R Markdown files in Jekyll. I encourage you to check out his blog!

   If you need additional help getting this process to work, feel free
to dig through the documentation for this very blog post at the links
below: 
* [R Markdown
File](https://github.com/zayne-kirkham/stat386-projects/blob/main/assets/Reference%20Files/2022-08-04-How-To-Use-R-Markdown-in-Jekyll-RMD-File.rmd)
* [Edited Markdown
File](https://github.com/zayne-kirkham/stat386-projects/blob/main/_posts/2022-08-04-How-To-Use-R-Markdown-in-Jekyll.md?plain=1)
* [\_posts
Folder](https://github.com/zayne-kirkham/stat386-projects/tree/main/_posts)

Good luck with all your statistical adventures!

![Figure](https://raw.githubusercontent.com/zayne-kirkham/stat386-projects/main/assets/images/pexels-alex-knight-2599244.jpg)
