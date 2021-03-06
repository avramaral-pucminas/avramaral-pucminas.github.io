---
layout: post
title: R Notebook
tags: [test, sample]
---

Caros amigos, a execução dos pontos do programa ainda não demonstrou convincentemente que vai participar na mudança das posturas dos órgãos dirigentes com relação às suas atribuições. Acima de tudo, é fundamental ressaltar que a hegemonia do ambiente político aponta para a melhoria das diversas correntes de pensamento. Todas estas questões, devidamente ponderadas, levantam dúvidas sobre se a contínua expansão de nossa atividade exige a precisão e a definição dos índices pretendidos. É claro que o fenômeno da Internet auxilia a preparação e a composição do sistema de participação geral.

$$
y = x + 2
$$


```R
x <- rnorm(10000000)
hist(x, col="blue", breaks=1000)
```


![png]({{ site.baseurl }}/assets/img/R-example_0_0.png)



```R
print(sample(1:3))
print(sample(1:3, size=3, replace=FALSE))  # same as previous line
print(sample(c(2,5,3), size=4, replace=TRUE))
print(sample(1:2, size=10, prob=c(1,3), replace=TRUE))
```

    [1] 3 1 2
    [1] 3 2 1
    [1] 2 5 2 5
     [1] 2 1 2 2 1 2 2 2 1 2



```R
readinteger <- function()
{
  n <- readline(prompt="Enter an integer: ")
  return(as.integer(n))
}

print(readinteger())
```

    Enter an integer: 5
    [1] 5



```R
x = matrix(1:6,3,2)
x= cbind(1,x)
y = matrix(c(1,-1,1),dim(x)[1],1)
iter = 100
alpha = 0.01
m = nrow(y)
tat = matrix(c(rep(0,ncol(x))),1,ncol(x))
cost = matrix(c(0),iter,1)
for(i in 1:iter)
{
  predict = 1 / (1 + exp(-x %*% t(tat)))
  for(j in 1:ncol(x))
  {
    errors = (predict - y) * x[,j]
    tat[,j] = tat[,j] - alpha * (1.0 / m) * sum(errors)
  }
  predict = 1 / (1 + exp(-x %*% t(tat)))
  cost[i,] = sum(-y*log(predict) - (1-y)*log(1-predict))/m
  if (i > 1) {
    if (cost[i] > cost[i-1]) {
      break
    }
  }
}
t(tat)
plot(cost)
```


<table>
<tbody>
	<tr><td>-0.02703496</td></tr>
	<tr><td>-0.03414864</td></tr>
	<tr><td>-0.11525352</td></tr>
</tbody>
</table>




![png]({{ site.baseurl }}/assets/img/R-example_3_1.png)



```R
smokerData <- read.csv(file='http://bit.ly/imdbratings',sep=',',header=T)
summary(smokerData)
```


      star_rating                               title       content_rating
     Min.   :7.40   Dracula                        :  2   R        :460   
     1st Qu.:7.60   Les Miserables                 :  2   PG-13    :189   
     Median :7.80   The Girl with the Dragon Tattoo:  2   PG       :123   
     Mean   :7.89   True Grit                      :  2   NOT RATED: 65   
     3rd Qu.:8.10   (500) Days of Summer           :  1   APPROVED : 47   
     Max.   :9.30   [Rec]                          :  1   UNRATED  : 38   
                    (Other)                        :969   (Other)  : 57   
           genre        duration  
     Drama    :278   Min.   : 64  
     Comedy   :156   1st Qu.:102  
     Action   :136   Median :117  
     Crime    :124   Mean   :121  
     Biography: 77   3rd Qu.:134  
     Adventure: 75   Max.   :242  
     (Other)  :133                
                                                         actors_list
     [u'Daniel Radcliffe', u'Emma Watson', u'Rupert Grint']    :  6  
     [u'Mark Hamill', u'Harrison Ford', u'Carrie Fisher']      :  3  
     [u'Ian McKellen', u'Martin Freeman', u'Richard Armitage'] :  2  
     [u'Michael J. Fox', u'Christopher Lloyd', u'Lea Thompson']:  2  
     [u'Tom Hanks', u'Tim Allen', u'Joan Cusack']              :  2  
     [u'Aamir Khan', u'Gracy Singh', u'Rachel Shelley']        :  1  
     (Other)                                                   :963  



```R
smokerData
```


<table>
<thead>
  <tr>
    <th>star_rating</th>
    <th>title</th>
    <th>content_rating</th>
    <th>genre</th>
    <th>duration</th>
    <th>actors_list</th>
  </tr>
</thead>
<tbody>
	<tr><td>9.3                                                                  </td><td>The Shawshank Redemption                                             </td><td>R                                                                    </td><td>Crime                                                                </td><td>142                                                                  </td><td>[u'Tim Robbins', u'Morgan Freeman', u'Bob Gunton']                   </td></tr>
	<tr><td>9.2                                                                  </td><td>The Godfather                                                        </td><td>R                                                                    </td><td>Crime                                                                </td><td>175                                                                  </td><td>[u'Marlon Brando', u'Al Pacino', u'James Caan']                      </td></tr>
	<tr><td>9.1                                                                  </td><td>The Godfather: Part II                                               </td><td>R                                                                    </td><td>Crime                                                                </td><td>200                                                                  </td><td>[u'Al Pacino', u'Robert De Niro', u'Robert Duvall']                  </td></tr>
	<tr><td>9.0                                                                  </td><td>The Dark Knight                                                      </td><td>PG-13                                                                </td><td>Action                                                               </td><td>152                                                                  </td><td>[u'Christian Bale', u'Heath Ledger', u'Aaron Eckhart']               </td></tr>
	<tr><td>8.9                                                                  </td><td>Pulp Fiction                                                         </td><td>R                                                                    </td><td>Crime                                                                </td><td>154                                                                  </td><td>[u'John Travolta', u'Uma Thurman', u'Samuel L. Jackson']             </td></tr>
	<tr><td>8.9                                                                  </td><td>12 Angry Men                                                         </td><td>NOT RATED                                                            </td><td>Drama                                                                </td><td> 96                                                                  </td><td>[u'Henry Fonda', u'Lee J. Cobb', u'Martin Balsam']                   </td></tr>
	<tr><td>8.9                                                                  </td><td>The Good, the Bad and the Ugly                                       </td><td>NOT RATED                                                            </td><td>Western                                                              </td><td>161                                                                  </td><td>[u'Clint Eastwood', u'Eli Wallach', u'Lee Van Cleef']                </td></tr>
	<tr><td>8.9                                                                  </td><td>The Lord of the Rings: The Return of the King                        </td><td>PG-13                                                                </td><td>Adventure                                                            </td><td>201                                                                  </td><td>[u'Elijah Wood', u'Viggo Mortensen', u'Ian McKellen']                </td></tr>
	<tr><td>8.9                                                                  </td><td>Schindler's List                                                     </td><td>R                                                                    </td><td>Biography                                                            </td><td>195                                                                  </td><td>[u'Liam Neeson', u'Ralph Fiennes', u'Ben Kingsley']                  </td></tr>
	<tr><td>8.9                                                                  </td><td>Fight Club                                                           </td><td>R                                                                    </td><td>Drama                                                                </td><td>139                                                                  </td><td>[u'Brad Pitt', u'Edward Norton', u'Helena Bonham Carter']            </td></tr>
	<tr><td>8.8                                                                  </td><td>The Lord of the Rings: The Fellowship of the Ring                    </td><td>PG-13                                                                </td><td>Adventure                                                            </td><td>178                                                                  </td><td>[u'Elijah Wood', u'Ian McKellen', u'Orlando Bloom']                  </td></tr>
	<tr><td>8.8                                                                  </td><td>Inception                                                            </td><td>PG-13                                                                </td><td>Action                                                               </td><td>148                                                                  </td><td>[u'Leonardo DiCaprio', u'Joseph Gordon-Levitt', u'Ellen Page']       </td></tr>
	<tr><td>8.8                                                                  </td><td>Star Wars: Episode V - The Empire Strikes Back                       </td><td>PG                                                                   </td><td>Action                                                               </td><td>124                                                                  </td><td>[u'Mark Hamill', u'Harrison Ford', u'Carrie Fisher']                 </td></tr>
	<tr><td>8.8                                                                  </td><td>Forrest Gump                                                         </td><td>PG-13                                                                </td><td>Drama                                                                </td><td>142                                                                  </td><td>[u'Tom Hanks', u'Robin Wright', u'Gary Sinise']                      </td></tr>
	<tr><td>8.8                                                                  </td><td>The Lord of the Rings: The Two Towers                                </td><td>PG-13                                                                </td><td>Adventure                                                            </td><td>179                                                                  </td><td>[u'Elijah Wood', u'Ian McKellen', u'Viggo Mortensen']                </td></tr>
	<tr><td>8.7                                                                  </td><td>Interstellar                                                         </td><td>PG-13                                                                </td><td>Adventure                                                            </td><td>169                                                                  </td><td>[u'Matthew McConaughey', u'Anne Hathaway', u'Jessica Chastain']      </td></tr>
	<tr><td>8.7                                                                  </td><td>One Flew Over the Cuckoo's Nest                                      </td><td>R                                                                    </td><td>Drama                                                                </td><td>133                                                                  </td><td>[u'Jack Nicholson', u'Louise Fletcher', u'Michael Berryman']         </td></tr>
	<tr><td>8.7                                                                  </td><td>Seven Samurai                                                        </td><td>UNRATED                                                              </td><td>Drama                                                                </td><td>207                                                                  </td><td>[u'Toshir\xf4 Mifune', u'Takashi Shimura', u'Keiko Tsushima']       </td></tr>
	<tr><td>8.7                                                                  </td><td>Goodfellas                                                           </td><td>R                                                                    </td><td>Biography                                                            </td><td>146                                                                  </td><td>[u'Robert De Niro', u'Ray Liotta', u'Joe Pesci']                     </td></tr>
	<tr><td>8.7                                                                  </td><td>Star Wars                                                            </td><td>PG                                                                   </td><td>Action                                                               </td><td>121                                                                  </td><td>[u'Mark Hamill', u'Harrison Ford', u'Carrie Fisher']                 </td></tr>
	<tr><td>8.7                                                                  </td><td>The Matrix                                                           </td><td>R                                                                    </td><td>Action                                                               </td><td>136                                                                  </td><td>[u'Keanu Reeves', u'Laurence Fishburne', u'Carrie-Anne Moss']        </td></tr>
	<tr><td>8.7                                                                  </td><td>City of God                                                          </td><td>R                                                                    </td><td>Crime                                                                </td><td>130                                                                  </td><td>[u'Alexandre Rodrigues', u'Matheus Nachtergaele', u'Leandro Firmino']</td></tr>
	<tr><td>8.7                                                                  </td><td>It's a Wonderful Life                                                </td><td>APPROVED                                                             </td><td>Drama                                                                </td><td>130                                                                  </td><td>[u'James Stewart', u'Donna Reed', u'Lionel Barrymore']               </td></tr>
	<tr><td>8.7                                                                  </td><td>The Usual Suspects                                                   </td><td>R                                                                    </td><td>Crime                                                                </td><td>106                                                                  </td><td>[u'Kevin Spacey', u'Gabriel Byrne', u'Chazz Palminteri']             </td></tr>
	<tr><td>8.7                                                                  </td><td>Se7en                                                                </td><td>R                                                                    </td><td>Drama                                                                </td><td>127                                                                  </td><td>[u'Morgan Freeman', u'Brad Pitt', u'Kevin Spacey']                   </td></tr>
	<tr><td>8.6                                                                  </td><td>Life Is Beautiful                                                    </td><td>PG-13                                                                </td><td>Comedy                                                               </td><td>116                                                                  </td><td>[u'Roberto Benigni', u'Nicoletta Braschi', u'Giorgio Cantarini']     </td></tr>
	<tr><td>8.6                                                                  </td><td>Once Upon a Time in the West                                         </td><td>PG-13                                                                </td><td>Western                                                              </td><td>175                                                                  </td><td>[u'Henry Fonda', u'Charles Bronson', u'Claudia Cardinale']           </td></tr>
	<tr><td>8.6                                                                  </td><td>The Silence of the Lambs                                             </td><td>R                                                                    </td><td>Drama                                                                </td><td>118                                                                  </td><td>[u'Jodie Foster', u'Anthony Hopkins', u'Lawrence A. Bonney']         </td></tr>
	<tr><td>8.6                                                                  </td><td>Leon: The Professional                                               </td><td>R                                                                    </td><td>Crime                                                                </td><td>110                                                                  </td><td>[u'Jean Reno', u'Gary Oldman', u'Natalie Portman']                   </td></tr>
	<tr><td>8.6                                                                  </td><td>City Lights                                                          </td><td>PASSED                                                               </td><td>Comedy                                                               </td><td> 87                                                                  </td><td>[u'Charles Chaplin', u'Virginia Cherrill', u'Florence Lee']          </td></tr>
	<tr><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td><td>⋮</td></tr>
	<tr><td>7.4                                                                     </td><td>Home Alone                                                              </td><td>PG                                                                      </td><td>Comedy                                                                  </td><td>103                                                                     </td><td>[u'Macaulay Culkin', u'Joe Pesci', u'Daniel Stern']                     </td></tr>
	<tr><td>7.4                                                                     </td><td>Bound                                                                   </td><td>R                                                                       </td><td>Crime                                                                   </td><td>108                                                                     </td><td>[u'Jennifer Tilly', u'Gina Gershon', u'Joe Pantoliano']                 </td></tr>
	<tr><td>7.4                                                                     </td><td>Sleepy Hollow                                                           </td><td>R                                                                       </td><td>Drama                                                                   </td><td>105                                                                     </td><td>[u'Johnny Depp', u'Christina Ricci', u'Miranda Richardson']             </td></tr>
	<tr><td>7.4                                                                     </td><td>Pirate Radio                                                            </td><td>R                                                                       </td><td>Comedy                                                                  </td><td>117                                                                     </td><td>[u'Philip Seymour Hoffman', u'Bill Nighy', u'Nick Frost']               </td></tr>
	<tr><td>7.4                                                                     </td><td>The NeverEnding Story                                                   </td><td>PG                                                                      </td><td>Adventure                                                               </td><td>102                                                                     </td><td>[u'Noah Hathaway', u'Barret Oliver', u'Tami Stronach']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>X-Men                                                                   </td><td>PG-13                                                                   </td><td>Action                                                                  </td><td>104                                                                     </td><td>[u'Patrick Stewart', u'Hugh Jackman', u'Ian McKellen']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>Zero Dark Thirty                                                        </td><td>R                                                                       </td><td>Drama                                                                   </td><td>157                                                                     </td><td>[u'Jessica Chastain', u'Joel Edgerton', u'Chris Pratt']                 </td></tr>
	<tr><td>7.4                                                                     </td><td>Manhattan Murder Mystery                                                </td><td>PG                                                                      </td><td>Comedy                                                                  </td><td>104                                                                     </td><td>[u'Woody Allen', u'Diane Keaton', u'Jerry Adler']                       </td></tr>
	<tr><td>7.4                                                                     </td><td>National Lampoon's Vacation                                             </td><td>R                                                                       </td><td>Comedy                                                                  </td><td> 98                                                                     </td><td>[u'Chevy Chase', u"Beverly D'Angelo", u'Imogene Coca']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>My Sister's Keeper                                                      </td><td>PG-13                                                                   </td><td>Drama                                                                   </td><td>109                                                                     </td><td>[u'Cameron Diaz', u'Abigail Breslin', u'Alec Baldwin']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>Deconstructing Harry                                                    </td><td>R                                                                       </td><td>Comedy                                                                  </td><td> 96                                                                     </td><td>[u'Woody Allen', u'Judy Davis', u'Julia Louis-Dreyfus']                 </td></tr>
	<tr><td>7.4                                                                     </td><td>The Way Way Back                                                        </td><td>PG-13                                                                   </td><td>Comedy                                                                  </td><td>103                                                                     </td><td>[u'Steve Carell', u'Toni Collette', u'Allison Janney']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>Capote                                                                  </td><td>R                                                                       </td><td>Biography                                                               </td><td>114                                                                     </td><td>[u'Philip Seymour Hoffman', u'Clifton Collins Jr.', u'Catherine Keener']</td></tr>
	<tr><td>7.4                                                                     </td><td>Driving Miss Daisy                                                      </td><td>PG                                                                      </td><td>Comedy                                                                  </td><td> 99                                                                     </td><td>[u'Morgan Freeman', u'Jessica Tandy', u'Dan Aykroyd']                   </td></tr>
	<tr><td>7.4                                                                     </td><td>La Femme Nikita                                                         </td><td>R                                                                       </td><td>Action                                                                  </td><td>118                                                                     </td><td>[u'Anne Parillaud', u'Marc Duret', u'Patrick Fontana']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>Lincoln                                                                 </td><td>PG-13                                                                   </td><td>Biography                                                               </td><td>150                                                                     </td><td>[u'Daniel Day-Lewis', u'Sally Field', u'David Strathairn']              </td></tr>
	<tr><td>7.4                                                                     </td><td>Limitless                                                               </td><td>PG-13                                                                   </td><td>Mystery                                                                 </td><td>105                                                                     </td><td>[u'Bradley Cooper', u'Anna Friel', u'Abbie Cornish']                    </td></tr>
	<tr><td>7.4                                                                     </td><td>The Simpsons Movie                                                      </td><td>PG-13                                                                   </td><td>Animation                                                               </td><td> 87                                                                     </td><td>[u'Dan Castellaneta', u'Julie Kavner', u'Nancy Cartwright']             </td></tr>
	<tr><td>7.4                                                                     </td><td>The Rock                                                                </td><td>R                                                                       </td><td>Action                                                                  </td><td>136                                                                     </td><td>[u'Sean Connery', u'Nicolas Cage', u'Ed Harris']                        </td></tr>
	<tr><td>7.4                                                                     </td><td>The English Patient                                                     </td><td>R                                                                       </td><td>Drama                                                                   </td><td>162                                                                     </td><td>[u'Ralph Fiennes', u'Juliette Binoche', u'Willem Dafoe']                </td></tr>
	<tr><td>7.4                                                                     </td><td>Law Abiding Citizen                                                     </td><td>R                                                                       </td><td>Crime                                                                   </td><td>109                                                                     </td><td>[u'Gerard Butler', u'Jamie Foxx', u'Leslie Bibb']                       </td></tr>
	<tr><td>7.4                                                                     </td><td>Wonder Boys                                                             </td><td>R                                                                       </td><td>Drama                                                                   </td><td>107                                                                     </td><td>[u'Michael Douglas', u'Tobey Maguire', u'Frances McDormand']            </td></tr>
	<tr><td>7.4                                                                     </td><td>Death at a Funeral                                                      </td><td>R                                                                       </td><td>Comedy                                                                  </td><td> 90                                                                     </td><td>[u'Matthew Macfadyen', u'Peter Dinklage', u'Ewen Bremner']              </td></tr>
	<tr><td>7.4                                                                     </td><td>Blue Valentine                                                          </td><td>NC-17                                                                   </td><td>Drama                                                                   </td><td>112                                                                     </td><td>[u'Ryan Gosling', u'Michelle Williams', u'John Doman']                  </td></tr>
	<tr><td>7.4                                                                     </td><td>The Cider House Rules                                                   </td><td>PG-13                                                                   </td><td>Drama                                                                   </td><td>126                                                                     </td><td>[u'Tobey Maguire', u'Charlize Theron', u'Michael Caine']                </td></tr>
	<tr><td>7.4                                                                     </td><td>Tootsie                                                                 </td><td>PG                                                                      </td><td>Comedy                                                                  </td><td>116                                                                     </td><td>[u'Dustin Hoffman', u'Jessica Lange', u'Teri Garr']                     </td></tr>
	<tr><td>7.4                                                                     </td><td>Back to the Future Part III                                             </td><td>PG                                                                      </td><td>Adventure                                                               </td><td>118                                                                     </td><td>[u'Michael J. Fox', u'Christopher Lloyd', u'Mary Steenburgen']          </td></tr>
	<tr><td>7.4                                                                     </td><td>Master and Commander: The Far Side of the World                         </td><td>PG-13                                                                   </td><td>Action                                                                  </td><td>138                                                                     </td><td>[u'Russell Crowe', u'Paul Bettany', u'Billy Boyd']                      </td></tr>
	<tr><td>7.4                                                                     </td><td>Poltergeist                                                             </td><td>PG                                                                      </td><td>Horror                                                                  </td><td>114                                                                     </td><td>[u'JoBeth Williams', u"Heather O'Rourke", u'Craig T. Nelson']           </td></tr>
	<tr><td>7.4                                                                     </td><td>Wall Street                                                             </td><td>R                                                                       </td><td>Crime                                                                   </td><td>126                                                                     </td><td>[u'Charlie Sheen', u'Michael Douglas', u'Tamara Tunie']                 </td></tr>
</tbody>
</table>
