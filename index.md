# Hello Sailor
Welcome to my STATS 220 assignment 1 website. 

## House of Crocs
![House_of_Crocs_Meme](https://github.com/laura-read/stats220/blob/main/House_of_Crocs_meme.png?raw=true)

## About my meme
I created this meme with `R` code in RStudio using the `Magick` package. I adapted an existing and popular meme format of two stacked images with accompanying text beside the images. Three main elements inspired it:

1. My love of sailing
2. The fact that crocs have come back into fashion
3. Lady Gaga's iconic line in the 2022 film *House of Gucci*


**Crocs and Sailing**

Crocs were designed for boaties back in 2002 and are often used by sailors as they are a tremendous waterproof shoe. However, the brand is slightly controversial as it was considered ugly for many years. However, 2020 saw a rise in sales, and in the first half of 2021, Crocs brought in $1.1 billion in revenue. Which was more than the entirety of 2020. Check out this [GQ article](https://www.gq.com/story/crocs-comeback) for more information on the comeback of Crocs.

![Sailing and Doctors](https://img-9gag-fun.9cache.com/photo/av5Vd3M_460s.jpg)

My own experience with the brand is their classic clog becoming fashionable in 2005 very briefly, followed by a long period where owning a pair made you subject to ridicule. I am happy to feel confident to sing the praises of Crocs once again. So, my meme celebrates a sailor’s love for Crocs.

**Lady Gaga, an icon**

Lady Gaga played Patrizia Reggiani in the *House of Gucci* (2022) film. Where she improvised the line:
> [Father, son, and House of Gucci](https://www.youtube.com/watch?v=aLZYR03aLI0&ab_channel=LadyGagaReactions). 

Which was adored by:
* fans,
* critics, 
* and turned into many memes


![One does not simply be Lady Gaga](https://imageproxy.ifunny.co/crop:x-20,resize:640x,quality:90x75/images/658cce63b161bd45fdea985c9dac635b50d32c693bad8a2ad18349c70b5f3a75_1.jpg)



### The R code used to create my House of Crocs meme:
```r

library(magick)

# crocs meme

# square one
friends_text <- image_blank(width = 500, 
                          height = 317.5, 
                          color = "#ffffff") %>%
               image_annotate(text = "My friends:",
                              color = "#666666",
                              size = 50,
                              font = "Impact",
                              gravity = "center")

# square two
house_of_paolo <- image_read("https://www.nme.com/wp-content/uploads/2021/11/Jared-Leto-in-House-Of-Gucci.jpg") %>%
  image_scale(500) %>%
  image_annotate(text = "Don't say it again",
                 color = "#fff700",
                 size = 30,
                 font = "Impact",
                 gravity = "south")


# square three
me_text <- image_blank(width = 500, 
                       height = 375.2, 
                       color = "#ffffff") %>%
                image_annotate(text = "Me, a sailor:",
                               color = "#666666",
                               size = 50,
                               font = "Impact",
                               gravity = "center")


# square four
house_of_crocs <- image_read("https://headtopics.com/images/2021/7/30/britishvogue/britishvogue-1421037437367857153.webp") %>%
  image_scale(500) %>%
  image_annotate(text = "Father, son, and House of CROCS",
                 color = "#fff700",
                 size = 30,
                 font = "Impact",
                 gravity = "south")

# combining the top row
paolo_vector <- c(friends_text, house_of_paolo)
top_row <- image_append(paolo_vector)

# combining the bottom row
crocs_vector <- c(me_text, house_of_crocs)
bottom_row <- image_append(crocs_vector)

#final meme combined
c(top_row, bottom_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(800)
  
```



