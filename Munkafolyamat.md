A munka kultúráról egy remek videót tett közzé a Spotify, [megtekinthető itt](https://labs.spotify.com/2014/03/27/spotify-engineering-culture-part-1/).

A munkafolyamat alapvetően egyéni munkára van kitalálva, de legkevésbé sem tilos a [pair programming](https://en.wikipedia.org/wiki/Pair_programming) sem. Társszerzők megjelöléséről [itt lehet olvasni](https://github.com/SzFMV2018-Osz/documentation/Git-anyagok#t%C3%A1rsszerz%C5%91k).

A konkrét feladatmegoldáshoz az alábbi folyamat az elvárt:

![](https://raw.githubusercontent.com/SzFMV2018-Osz/documentation/master/images/proc1.png)

* User Story:
    * high level description of sprint goal by customer not complete! Never detailed enough!
* Component Design:
    * what will realize the functions in the user story You have to recognize the (hidden?) functionality!
* Requirement Specification:
    * what makes the component work as expected basically the Definition of Done for the component
* Task Definition:
    * add milestone (there is one for every sprint) to issue
    * add assignee to issue
    * add Definition of Done list to issue
    * add project (there is one for every team) to issue

![](https://raw.githubusercontent.com/SzFMV2018-Osz/documentation/master/images/proc2.png)

* Dod: Definition of Done

## Code Review in details

![](https://raw.githubusercontent.com/SzFMV2018-Osz/documentation/master/images/proc3.png)

* Clean Code:
    * no magic numbers
    * no abbreviations
    * no extreme unit lengths
    * talkative names
    * unambiguous code
* in short:
    * Easy to understand and maintain
    * Reads like well written prose