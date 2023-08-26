<h1 style="text-align: left;">DSTA Challenge of Wits 2023 Round 2</h1><div>Huge pity I did not attempt round 1 because I was busy with finishing up my Data Science Bootcamp and also due to my Paris trip. I was mindlessly scrolling social media when I saw the ad again and thought I should try it out.</div>
<div><br /></div><h2 style="text-align: left;">Task:</h2><div>Millions of stolen cash was stashed away by terror organisation APOCALYPSE in their
safe. A thumb drive Logs.zip with log files was recovered when they were captured.
Handed to you, your team’s mission is to find the secret key from the “Logs.zip” files that
will unlock the safe to recover the stolen cash.
Armed with programming expertise and knowledge of text processing, you know how best
to represent insights from data to answer mission requirements. You are told
APOCALYPSE used a 2D shape as their secret key.
Can you find the secret key to unlock the safe?&nbsp;</div><div><br /></div><div>Hint 1: Download Logs.zip from the challenge website.&nbsp;</div><div>Hint 2: Write a script to solve the challenge.&nbsp;</div><div><br /></div><h2 style="text-align: left;">Solution:</h2><div>The "Logs.zip" archive contains more than 2000 XML files, named from "Log_0.xml" to "Log2254.xml".</div><div><br /></div><div>First, I written a code to load one of the xml file to see what is in it. Here's an excerpt from "log_0.xml":</div><div><br /></div><div><div class="line" style="font-family: monospace; font-size: 13px;"><span class="html-tag">&lt;data&gt;</span></div><div class="opened" style="font-family: monospace; font-size: 13px; margin-left: 1em;"><div class="line"><span class="html-tag">&lt;location&gt;</span>285,88<span class="html-tag">&lt;/location&gt;</span></div><div class="line"><span class="html-tag">&lt;convo&gt;</span>the holes in this film remain agape -- holes punched through by an inconsistent , meandering , and sometimes dry plot .<span class="html-tag">&lt;/convo&gt;</span></div><div class="line"><span class="html-tag">&lt;class&gt;</span>casual<span class="html-tag">&lt;/class&gt;</span></div></div><div class="line" style="font-family: monospace; font-size: 13px;"><span class="html-tag">&lt;/data&gt;</span></div></div><div class="line" style="font-family: monospace; font-size: 13px;"><span class="html-tag"><br /></span></div><p style="text-align: left;">The XML elements include "location," "convo," and "class." I proceeded to consolidate the data into a Pandas dataframe, utilizing a for loop to create individual columns for each XML tag. During the loading process, I encountered errors with two files: "log_317.xml" and "log_1768.xml." Upon investigation, I found these two files to be nearly identical except for their "location" values. More details can be found in the ".txt" file within the Misc folder.</p><p style="text-align: left;">Interestingly, these files seemed to contain hints for decoding, which led me to mistakenly invest a significant amount of time searching for non-English characters within the "convo" column. This approach was misguided. After nearly giving up, a moment of insight occurred when I recognized that certain entries in the "convo" column resembled international news.</p><p style="text-align: left;">I realized that the two problematic files contained content about a foreign language that I couldn't process in Python. This revelation motivated a creative idea: filtering conversations mentioning countries or related entities. I achieved this by utilizing SpaCy, resulting in over 700 filtered rows. While not flawless, this filtering method provided a workable solution for the challenge.</p><p style="text-align: left;">Beforehand, I had attempted to dissect the data by splitting and identifying unique elements in the location column. The numerical values were consistently integers, ranging from two digits to over 200. My intuition suggested they might be coordinates, but my initial attempts at plotting them while filtering by class yielded inconclusive results. Even when I used only the coordinates using the over 700 rows of filtered data, the plotted data still appeared random.</p><p style="text-align: left;">Frustration led me to narrow down the data to conversations related to Bangladesh (the language of the two problematic files). This reduced the dataset to just 5 rows. Plotting these values surprisingly resulted in a straight line, revealing my oversight:&nbsp;</p><p style="text-align: left;"><b></b></p><blockquote><b>I had neglected to convert the "location" values from strings to integers.</b></blockquote><p></p><p></p><p style="text-align: left;">After rectifying this oversight and replotting with the filtered data, the solution became evident. For a visual representation of the plot and the final solution, please refer to the solution Jupyter notebook.</p><p style="text-align: left;">---</p><p style="text-align: left;">Whole challenge took me just one or two hours to figure out, and half the time I was lying on the bed scrolling social media because ideas always comes to me while relaxed. Not difficult at all but at least it is fun. 😎 Looking forward to trying other kind of challenges.</p><p style="text-align: left;">~Althea🤍</p>
