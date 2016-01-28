---
layout: post
title:  "Analyzing a Confession"
date:   2016-01-27 23:33:0
description: A computational look at the Brendan Dassey confession made famous by Making a Murderer
categories:
- blog
permalink: confession
---

**Warning:** this blog post contains spoilers for the Netflix documentary series Making a Murderer

### Brendan Dassey's confession
If you haven't seen the true crime documentary series Making a Murderer yet, go watch it! The Netflix series gives a fascinating insight in the  American justice system and how it seems to fail to adhere to the principle of guilty beyond reasonable doubt. It has caused quite a buzz. On Reddit amateur sleuths are obsessing over the case.

One of the cringe worthy things we see in the documentary is the confession of Steven's nephew, Brendan Dassey. Brendan is a boy with learning disabilities and is interrogated without any help present by two trained policemen for 6 hours. In this interrogation Brendan confesses helping Steven Avery rape and murder Theresa Halbach. This confession alone leads to his conviction for life. We see some small parts of the interview in the documentary, such as the part below.

> FASSBENDER: Did he say why he wanted you to do that?

> BRENDAN: No. (shakes head “no”)

> WIEGERT: Which knife did you use?

> BRENDAN: The same one he stabbed her with.

> FASASBENDER: And how many times did he stab her again?

> BRENDAN: Once.

> FASSBENDER: Are you sure about that? (Brendan nods “yes”)

> WIEGERT: So Steve stabs her first and then you cut her neck? (Brendan nods “yes”) What else happens to her in her head?

> FASSBENDER: It’s extremely, extremely important you tell us this, for us to believe you.

> WIEGERT: Come on Brendan, what else?

> (pause)

> FASSBENDER: We know, we just need you to tell us.

> BRENDAN: That’s all I can remember.

> WIEGERT: All right, I’m just gonna come out and ask you. Who shot her in the head?

> BRENDAN: He did.

> FASSBENDER: Then why didn’t you tell us that?

> BRENDAN: Cuz I couldn’t think of it.

4 hours of the interview can be seen [here](https://www.youtube.com/watch?v=65sr1ZjrQi0).

As it is kind of hard to analyze 4+ hours of video, I wanted to see if I could do some automatic analysis of the interview. The goal is  to gain a little insight in this particular interview.

### Getting the data
Luckily, a PDF transcipt of the interview is available [here](https://www.docdroid.net/ZSo3Oc1/01mar2006transcript.pdf.html).
I downloaded the PDF and performed OCR (using Google Docs) to extract the text. I then did some very simple computational analyses of the text using Python.

###Word clouds
Analyzing the most frequently used words by all parties, it becomes clear that Brendan acknowledges a lot of the questions asked to him.

[brendan]
[brendan]
[brendan]

###Words uttered during the interview

[nwords]
Next, we can have a look at the total words that are uttered during the interview. Interesting is that both Fassbender and Wieger talk more than Brendan in the beginning of the interview, and that Fassbender seems to get be more prominent nearing the end. Brendan is very consistent, reaffirming his role as acknowledging. We can see that the interrogators together have uttered around 22.000 words while Brendan has only uttered 10.000.

###Unique words uttered during the interview
[nunique]
More interesting are the unique words uttered during the interrogation. Basically, repeating a word probably doesn't bring new information into the conversation, so only looking at new words that haven't been uttered by any of the parties before might also give some insight.

As we see here, the difference becomes only bigger. Both detectives utter more new words than Brendan, roughly 1100 versus 450. Interesting is the beginning of the conversation, where both detectives are uttering a lot of new words and Brendan is not really adding anything. 

###Unique bigrams uttered during the interview
[nbigrams]
Words can take us only so far. There are a limited number of words that we can use, but we can use them to convey information in lots of ways: 'Mary slaps John' and 'John slaps Mary' contain the same words but have different meanings. So. let's look at combination of words, so-called *n-grams*. Let's look at all the unique pairs of consecutive words, called bigrams. Now we really see where the information comes from: it's mainly Fassbender who brings new information to the table.



###Concluding
I did some very simple visualization of the Brendan Dassey interrogation. A lot more analyses could be performed on the data: measuring perplexity of the speakers (how predictable are their utterances?), topic modelling (who talks about what), etc.





[brendan]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/brendan.png
[fassbender]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/fassbender.png
[wiegert]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/wiegert.png
[nwords]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/nbwords.png
[nunique]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/nunique.png
[nbigrams]: https://github.com/swubb/swubb.github.io/blob/master/assets/images/nbigrams.png

