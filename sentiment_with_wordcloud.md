
# Visualizing Movie Reviews in Word Cloud

Samrat Halder and Hariz Johnson


## IMDB Reviews
We first scrape all the movie reviews from IMDB 

```r
library(rvest)
library(xml2)
library(plyr)
result <- c()
ID <- 4154796
movie_IMDb <- read_html(paste0("https://www.imdb.com/title/tt",ID,"/reviews?ref_=tt_urv"))
reviews <- movie_IMDb %>% html_nodes("#pagecontent") %>% html_nodes("div.content") %>% html_text()
#perfrom data cleaning on user reviews
reviews <- gsub("\r?\n|\r", " ", reviews) 
reviews <- tolower(gsub("[^[:alnum:] ]", " ", reviews))
write.csv(reviews, paste0(getwd(),"/resources/wordcloud_sentiment/reviews.csv"))
head(reviews)
```

```
## [1] "                 there is no way that i could describe my emotions for this movie  i m totally speechless  i haven t laughed  even cried  this much in marvel movie or even in any movie  i m fully on my emotion  there are so many tears of joy and loss  amazing story  the acting is outstanding  epic action  great cgi  the best storytelling ever told in a superhero movie  amazing performance  i love it more than 3000 happiness  sadness  pure joy  excitement    i m gonna miss this moment in my whole life because let s face it  it s been awhile movies can bring such a big enthusiasm like this it is such an experience you ll gonna remember it forever  people are clapping  laughing  crying  full of a state emotion  it s 3 hours long but it went by like a finger snapping by thanos  and now i m thinking i m actually in quantum realm because it felt like 5 seconds  even though you know where the story is gonna bring you because it s still a  superhero movie  but it left me speechless  it s not just a superhero movie  it s more than that   spoiler alert  even some characters that you didn t like before  you will love them in this movie  like captain marvel  i didn t like her before in her own movie but in endgame they showed how powerful  how strong and how capable she really is  and now i kinda love her  but marvel should really be careful of her line though  i didn t like some of her line like  i m the strongest  and  you didn t win because before you didn t have me  duh  also not gonna forget hawkeye  to be honest  in avengers i really didn t like hawkeye because he s just a  guy  with an arrow and just randomly showed up in any scene but actually he s character is so badass  everything that we need  what we want is here also i don t get it why some people can not accept that thor is fat or treat him like a joke  i mean  this movie might be trying to give us a message about no matter what  shape  are you  you can be a hero and save the world  to be honest  i like what they did to thor  that man is depressed and taking the most responsible after he missed the shot to kill thanos in infinity war  even though he already did killed him but it s not gonna bring back his people of asgard  also he s god of thunder for god sake  he could slap his stomach with thunder and got his abs back i m so happy too for captain america  finally he could do his dance with peggy and i didn t expected that we could see the fight between captain america with his own self  also when tony met his father really warm my heart  and we can see the  real life  jarvis   i didn t expected that too when the whole superhero arrived it is so epic  the whole person in theater are screaming and shocked  gives me a goosebumps and still left me speechless this movie is absolute perfection  the ending of this movie is we and the characters deserved  it gives a perfect balance for all these past 10 years  epic and perfect ending  i was not disappointed at all  this movie was completely emotional and visually stunning  now i get it why the russo brothers told us to do a marvel movie marathon before watching endgame because this movie had everything to accomplish what left behind before all of this ready or not  whatever it takes go watch it for yourself                                       4 207 out of 6 378 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
## [2] "                 can t ignore the truth that this is a super hero film  while except the last several minute  other plots can attract any attention  can t even compare with avengers  infinity war  narrative thread and music disordered throughout 3 hour movie                                       15 out of 19 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              
## [3] "                 after avengers infinity war  we waited for the avengers endgame  we wondered how the story would go on  how our heroes would turn back  what would be the end of thanos  many theories related to this have been put forward  avengers endgame was undoubtedly the most anticipated film of recent years  normally  the higher the expectation  the higher the probability of disappointment  but this is not the case for endgame  whatever you re expecting  you find much more in the film  this means that the biggest concern about the film has disappeared on the other hand  another comparison comes up  is endgame more successful than infinity war  we can comfortably say it avengers infinity war is just the beginning of the story  endgame was the finale of the story  so we shouldn t think of these two films as two separate stories  there is only one story divided into two parts avengers endgame is  above all  a great homage to the ten year history of the marvel cinematic universe  the story highlights the original avengers team  iron man  captain america  thor  hulk  black widow and hawkeye are at the center of events  no character comes in front of them  of course there are many characters that play an important role in the story outside the original avengers team  everyone s concern was that captain marvel  who was included in the marvel world  overshadowed other heroes  we can say that this certainly did not happen  what is important in this struggle is not how strong you are  but how good you are  this comes to the fore in all areas  it gives good message about being a hero and a family of course  avengers endgame has some critical aspects  for example  is the three hour period necessary in terms of the story  it can be discussed  the head of the story moves much slower than the rest  it also drags the heroes into an emotional predicament  then the tempo is rising and the heavy scenes we are watching are getting more meaningful  the last 45 minutes of the movie is fully action packed  but the last 45 minutes goes so fast that you don t even realize it  action and battle scenes are really successful  there is not even a slight distress about visual effects  there are also slight logic errors in the film  but in general the story is so successful that these details become meaningless and insignificant after a certain point lastly  avengers endgame doesn t have a movie end scene  because after the film s final  there is no need for another scene  the marvel legend stan lee appears with a small stage  but this is the last surprise scene in the marvel cinematic universe  moreover  there is no clue about marvel s future  this makes us wonder more about spider man  far from home  10 10                                      1 927 out of 3 341 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
## [4] "                 i have to say  my first reaction walking out of the cinema was that it was great  probably an 8 10  you know there s so much fan service in this movie and i particularly loved the  i can do this all day  ca line from one ca to another  it was almost toy story 2  enlightened buzz to naive buzz banter i loved clever hulk  found thor hilarious  though a bit annoying at times  and loved the references to past movies  cap swinging mjollnir around was beautiful the deaths in this movie were also pretty surprising but i agree with some of the more balanced reviews in here that it was bizarre that so much time was spent on hawkeye   does anyone really care about him  not really killing off black widow was a surprising touch  but i  like many others  probably felt more of an emotional reaction to banner s relationship with her and not hawkeye  because no one actually cares about him   renner  as an actor  just doesn t cut it much  unfortunately the real problem with end game  is the time travel  i don t know why any movie franchise would ever want to deal with time travel knowing how much grief it creates  sure they try to explain everything with their hilarious conversation about movies  but in the end  there are just too many questions left at the end of the day  particularly when they already try to explain it through the ancient one the most glaring one of these is  if they change the past  they re changing another timeline  so how selfish is that  if tony stark snaps his fingers and kills thanos  what happens to that original timeline  if he sent thanos and everyone back  how does he magically know not to send gamora back who is now stuck in 2023   and so does that mean 2014 quill never meets gamora    what the hell  essentially erasing the entire 2014 gotg franchise in that universe  if captain america goes back in time  he will inevitably change history in some way or another  so that is another timeline  right  so while everyone else s timeline is meant to stay the same in the present  as said by stark  how does cap end up sitting by the same lake as everyone else there are also way too many questions about new timelines created   but perhaps that is intentional  such as the loki tv show  but this is why i hate it when they bring time travel into any movie and just add stuff to it to make it wrap up nicely in their own universe also  don t get me started on how impossibly strong thanos suddenly is without an infinity gauntlet  even with the ig he couldn t stop thor s stormbringer  but now without the ig can easily defeat thor with stormbringer and mjollnir  iron man and cap    how convenient i also think marvel made a serious mistake creating captain marvel  how is she brought in as a convenient deus ex machina and yet doesn t really stick around to show off all her abilities  and she can t even defeat thanos single handedly  pfft  that was rich  she can barely prevent thanos from snapping his fingers  yet in infinity war  cap was able to actually hold off his hand too  bizarre parallels so okay  sure  it was enjoyable to watch  but i just feel that there are too many plot inconsistencies creeping into end game  there should have been better ways to get the infinity stones back  and i think someone stupid just thought time travel was the best way to do it                                        2 676 out of 4 679 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
## [5] "                 i want to start out saying i love all the marvel movies leading up to endgame  i loved infinity war because it seemed to be setting up a terrific conclusion to the original 6 avengers story arc s  i was very wrong  let s start with tony s arc  in ironman 1 tony is told you are a man who has everything and nothing  in ironman 2 we find out his dad was distant and cold to him  and in ironman 3 he is getting panic attacks because he thinks it s up to him to save the world from all threats  so in endgame he finally gets everything that s important  he becomes a dad and husband and    was proven right by having to die saving the universe himself  why  because we are supposed to believe tony can t retire  of course he can  didn t he say to steve in aou  isn t that why we fight so we can end the fight  so we can go home   tony wanted to retire  tony s arc should have been about being a good dad like his father never was and finally becoming the man who has everything important  he should have learned that he doesn t have to do it all on his own  team work should have won the final battle  what s the point of finally getting all the avengers together if it s left to one man to sacrifice himself to save everyone  tony s ending was not satisfying and it was not the end they have been building towards from the beginning  now let s talk about the real tragedy in this movie  steve rogers character  we know he is a good man who always does what he believes is right  he calls home the avengers facility and says he can t ignore a situation that s headed south  he loved peggy but found out she had gotten married and had a happy life and he tried moving on with her niece  this storyline was ignored which was ok because most of steves storyline in the mcu has been about saving bucky  you remember him right  steve didn t seem to for the entire movie  instead of thinking about sam and bucky and all the people they are going to save if their plan works when they find thanos in the beginning of endgame steve s just looking at the peggy compass that he hasn t looked at in at least 3 movies  why  so we can all forget about his actual character development and think it s a great ending when he goes back in time to be with peggy  i m just going to ignore all the plot holes associated with steve going back in time and just focus on the character assasination this commits  this means the same guy who says he can t ignore a situation headed south  who never ran away from a fight  who said i m with you till the end of the line  to bucky is just going to live out his life in the past never saving his friend from being a brain washed assassin  never saving his other friends parents from being killed by his best friend  never stopping any of the thousands of bad things he would know are going to happen  that s not steve  the writers never let steve get a personal life  he never found someone after peggy and he never had anything except the avengers  he was the one that was set up to die  the final battle starts with what is probably the most epic scene in comic book movie history but fizzles our soon after  doctor stranges plan makes no sense  how was this the only way they could win  why couldn t captain marvel snap  why couldn t captain marvel just fly the gauntlet to another galaxy  why couldn t doctor strange open a portal and drop the gauntlet on some random planet  in infinity war why didn t doctor strange use his portal to go to wakanda and tell thor to aim for the head  the characters powers were very inconsistent for the first time in the mcu  why was thanos with no infinity stones able to fight mjolnir and storm breaker but thanos with all 6 stones would have lost to storm breaker if thor would have just aimed for the head  why can captain marvel fly through a huge spaceship 10 times but she gets knocked out after one punch from thanos  why does no one attack thanos at the same time as someone else  where s the big team up  you would think getting everyone together for the first time would have been the only way to defeat thanos  but you d be wrong because it s all about tony stark  even steve picking up mjolnir means nothing really because it has no affect on the end of the battle  thor and steve could be taken out of this movie and nothing would change  they do nothing of importance  this movie seems so disconnected from infinity war that it s boggles my mind how this movie has the same writers and directors as infinity war and it was filmed at the same time as infinity war  how can you get one so wrong and the other so right  it seems clear to me that the writers and directors decided that tony was dying and steve was going back to the past no matter how much their story suffered from doing it  it s like they had a check list of things to put in the movie without actually making a good story that fit in with the rest of their movies  this is by far the most dissapointing ending to anything i ve ever looked forward to                                       326 out of 550 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "
## [6] "                 3 hours out of my life i will never get back  not worth the hype  you think the soap opera is done by the ultimate battle  think again  let us milk it and release another spider man  geez a lou                                       197 out of 326 found this helpful                                                       was this review helpful   sign in to vote                                                   permalink                              "
```
## Cleaning the data!
In this part first we clean the data using standard text mining techniques eg. removing redundant characters, stop words, stemming etc


```r
library(tm)
library(plyr)
library(stringr)
library(wordcloud)
library(RColorBrewer)

removeURL <- function(x) {
  gsub("http[[:alnum:]]*", "", x)
}
removelongWORDS <- function(x) {
  gsub("\\b[[:alpha:]]{15,}\\b", "", x, perl=FALSE)
}
removeCharacters <-function (x, characters)  {
  gsub(sprintf("(*UCP)(%s)", paste(characters, collapse = "|")), "", x, perl = FALSE)
}
reviews <- read.csv(paste0(getwd(),"/resources/wordcloud_sentiment/reviews.csv"), row.names = NULL)
dataset <- reviews$x
dataset <- str_replace_all(dataset, "[^[:alnum:]]", " ")
CorpusObj<- VectorSource(dataset)
CorpusObj<- Corpus(CorpusObj)
CorpusObj <- tm_map(CorpusObj, removelongWORDS)
CorpusObj <- tm_map(CorpusObj, removeURL)
CorpusObj <- tm_map(CorpusObj, removePunctuation)
CorpusObj <- tm_map(CorpusObj, removeNumbers) 
CorpusObj <- tm_map(CorpusObj, removeCharacters, c("\uf0b7","\uf0a0"))
CorpusObj <- tm_map(CorpusObj, tolower)
CorpusObj <- tm_map(CorpusObj, stemDocument, language = "english") 
CorpusObj <- tm_map(CorpusObj, removeWords, 
                    c(stopwords("english"), "text show-more__control", "movi",
                      "like","vote", "also","review", "permalink", "help", "stori","charact")) 
CorpusObj<-tm_map(CorpusObj,stripWhitespace)
CorpusObj.tdm <- TermDocumentMatrix(CorpusObj, control = list(minWordLength = 3)) 
freqr <- rowSums(as.matrix(CorpusObj.tdm))
CorpusObj.tdm.sp <- removeSparseTerms(CorpusObj.tdm, sparse=0.90) 
```

We make a term document matrix


```r
mTDM <- as.matrix(CorpusObj.tdm)
v <- sort(rowSums(mTDM),decreasing=TRUE)
d <- data.frame(word = names(v),freq=v)
head(d, 10)
```

```
##          word freq
## can       can   41
## thano   thano   38
## just     just   37
## film     film   30
## time     time   30
## aveng   aveng   29
## endgam endgam   29
## found   found   29
## even     even   28
## infin   infin   25
```

## Word Cloud

Finally we create the word cloud from the corpus object that we created in the last part.


```r
pal <- brewer.pal(9, "BuGn")
pal <- pal[-(1:2)]
png(paste0(getwd(),"/resources/wordcloud_sentiment/wordcloud.png"), width=1280,height=900)
wordcloud(d$word,d$freq, min.freq=300, scale=c(7,0.5),
          colors=brewer.pal(8, "Dark2"),  random.color= TRUE, random.order = FALSE)
dev.off()
```

```
## png 
##   2
```

Please note to see the word cloud check the png file. It is not the best practice to plot word cloud from a huge corpus on R console because of the limited resolution