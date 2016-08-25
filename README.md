# Rtextrankr
TextRank for Korean in R lang by [@mikigom](https://twitter.com/MikiBear_)

R version package for [textrankr](https://github.com/theeluwin/textrankr) python package

Reorder sentences for Korean text using TextRank algorithm.

## Enviroment & Dependency
```
Depends:
    R (>= 3.0.2)
Imports:
    KoNLP (>= 0.76.9),
    igraph (>= 1.0.1),
    sets (>= 1.0-16),
    foreach (>= 1.4.3),
    stringi (>= 1.1.0)
Collate:
    'Rtextrankkr.R'
```

## Example
```R
> example_text = "18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다. 
취미론에 속하는 이론가들은 상이한 개념이나 취지로 다양한 주장들을 전개했지만, 이것들로부터 다음과 같은 몇 가지 공통 요소들을 도출할 수 있다.
먼저 취미론자들은 ‘미의 감관’의 존재, 즉 감각적인 성질로서의 미를 파악하는 감관(sense)인 ‘취미(taste)’가 존재함을 주장한다.
하지만 취미는 시각과 청각과 같은 외적 감관이 아니라 내적인 감관이다. 맹인이 빛을 보지 못하듯, 사람들 중에는 뛰어난 시각 능력을 지니고 있으면서도 자연 풍경이나 그림에서 아무런 즐거움을 얻지 못하거나, 혹은 뛰어난 청각 능력에도 불구하고 음악에서 아무런 감흥을 느끼지 못하는 경우가 있다. 
이들은 취미를 결여한 사람들이다. 
이렇듯 비록 대상을 지각하는 외적인 감관과 더불어 작동하더라도 취미는 외적 감관인 오감의 능력과는 구별되는 능력이며, 그러한 의미에서 ‘내감’ 혹은 ‘제6감’이라고도 할 수 있다.
한편 미가 취미에 의해 지각된 것이라면, 취미론자들에게 미는 주관적인 것이 된다. 
취미론자의 한 사람인 허치슨은 미란 마음속에 일어난 하나의 관념이라고 주장했다. 
이는 곧 미가 그것을 지각하는 마음과 어떠한 관계도 없이 그 자체로 아름다운 성질, 곧 대상 속에 들어 있다고 생각되는 성질을 뜻하는 것이 아니라는 말이다. 
미의 관념이란 대상의 어떤 특수한 성질을 지각할 때 그 지각으로부터 환기되는 특수한 즐거움을 뜻한다고 이해할 수 있다.
취미론자들은 ‘이 꽃은 아름답다’와 같은 취미 판단을 할 때 ‘이 꽃’은 분명 외부 세계의 대상들을 지시하고 있지만, ‘아름답다’는 외적인 자극의 성질을 지시하는 것이 아니고 그러한 자극에 의해 우리의 마음속에 환기된 즐거움을 지시하고 있는 것으로 파악했다.
물론 고전적 미론에서도 주관의 즐거움이 거론된 경우는 있었으나, ‘아름다운 사물은 우리를 즐겁게 한다’와 같은 식의 파생적인 요소로 거론된 것이었고, 미의 본질에 대한 대답은 아니었다. 
이 변화가 바로 스톨니츠에 의해 ‘미학에서 일어난 코페르니쿠스적 혁명’이라 명명된 것으로, 취미론으로부터 비롯된 근대 미론과 그 이전의 고전적 미론을 구분하는 분수령이 된다."

> example_sentence = "미의 관념이란 대상의 어떤 특수한 성질을 지각할 때 그 지각으로부터 환기되는 특수한 즐거움을 뜻한다고 이해할 수 있다."
```
### xplit(text)
```R
> xplit(example_text)
 [1] "18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다"                                             
 [2] " "                                                                                                                                                                                                                                                    
 [3] "취미론에 속하는 이론가들은 상이한 개념이나 취지로 다양한 주장들을 전개했지만, 이것들로부터 다음과 같은 몇 가지 공통 요소들을 도출할 수 있다"                                                                                                          
 [4] ""                                                                                                                                                                                                                                                     
 [5] "먼저 취미론자들은 ‘미의 감관’의 존재, 즉 감각적인 성질로서의 미를 파악하는 감관(sense)인 ‘취미(taste)’가 존재함을 주장한다"                                                                                                                           
 [6] ""                                                                                                                                                                                                                                                     
 [7] "하지만 취미는 시각과 청각과 같은 외적 감관이 아니라 내적인 감관이다"                                                                                                                                                                                  
 [8] " 맹인이 빛을 보지 못하듯, 사람들 중에는 뛰어난 시각 능력을 지니고 있으면서도 자연 풍경이나 그림에서 아무런 즐거움을 얻지 못하거나, 혹은 뛰어난 청각 능력에도 불구하고 음악에서 아무런 감흥을 느끼지 못하는 경우가 있다"                               
 [9] " "                                                                                                                                                                                                                                                    
[10] "이들은 취미를 결여한 사람들이다"                                                                                                                                                                                                                      
[11] " "                                                                                                                                                                                                                                                    
[12] "이렇듯 비록 대상을 지각하는 외적인 감관과 더불어 작동하더라도 취미는 외적 감관인 오감의 능력과는 구별되는 능력이며, 그러한 의미에서 ‘내감’ 혹은 ‘제6감’이라고도 할 수 있다"                                                                           
[13] ""                                                                                                                                                                                                                                                     
[14] "한편 미가 취미에 의해 지각된 것이라면, 취미론자들에게 미는 주관적인 것이 된다"                                                                                                                                                                        
[15] " "                                                                                                                                                                                                                                                    
[16] "취미론자의 한 사람인 허치슨은 미란 마음속에 일어난 하나의 관념이라고 주장했다"                                                                                                                                                                        
[17] " "                                                                                                                                                                                                                                                    
[18] "이는 곧 미가 그것을 지각하는 마음과 어떠한 관계도 없이 그 자체로 아름다운 성질, 곧 대상 속에 들어 있다고 생각되는 성질을 뜻하는 것이 아니라는 말이다"                                                                                                 
[19] " "                                                                                                                                                                                                                                                    
[20] "미의 관념이란 대상의 어떤 특수한 성질을 지각할 때 그 지각으로부터 환기되는 특수한 즐거움을 뜻한다고 이해할 수 있다"                                                                                                                                   
[21] ""                                                                                                                                                                                                                                                     
[22] "취미론자들은 ‘이 꽃은 아름답다’와 같은 취미 판단을 할 때 ‘이 꽃’은 분명 외부 세계의 대상들을 지시하고 있지만, ‘아름답다’는 외적인 자극의 성질을 지시하는 것이 아니고 그러한 자극에 의해 우리의 마음속에 환기된 즐거움을 지시하고 있는 것으로 파악했다"
[23] ""                                                                                                                                                                                                                                                     
[24] "물론 고전적 미론에서도 주관의 즐거움이 거론된 경우는 있었으나, ‘아름다운 사물은 우리를 즐겁게 한다’와 같은 식의 파생적인 요소로 거론된 것이었고, 미의 본질에 대한 대답은 아니었다"                                                                    
[25] " "                                                                                                                                                                                                                                                    
[26] "이 변화가 바로 스톨니츠에 의해 ‘미학에서 일어난 코페르니쿠스적 혁명’이라 명명된 것으로, 취미론으로부터 비롯된 근대 미론과 그 이전의 고전적 미론을 구분하는 분수령이 된다"
```

### get_sentences(text)
```R
> get_sentences(example_text)
 [1] "18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다."                                             
 [2] "취미론에 속하는 이론가들은 상이한 개념이나 취지로 다양한 주장들을 전개했지만, 이것들로부터 다음과 같은 몇 가지 공통 요소들을 도출할 수 있다."                                                                                                          
 [3] "먼저 취미론자들은 ‘미의 감관’의 존재, 즉 감각적인 성질로서의 미를 파악하는 감관(sense)인 ‘취미(taste)’가 존재함을 주장한다."                                                                                                                           
 [4] "하지만 취미는 시각과 청각과 같은 외적 감관이 아니라 내적인 감관이다."                                                                                                                                                                                  
 [5] "맹인이 빛을 보지 못하듯, 사람들 중에는 뛰어난 시각 능력을 지니고 있으면서도 자연 풍경이나 그림에서 아무런 즐거움을 얻지 못하거나, 혹은 뛰어난 청각 능력에도 불구하고 음악에서 아무런 감흥을 느끼지 못하는 경우가 있다."                                
 [6] "이들은 취미를 결여한 사람들이다."                                                                                                                                                                                                                      
 [7] "이렇듯 비록 대상을 지각하는 외적인 감관과 더불어 작동하더라도 취미는 외적 감관인 오감의 능력과는 구별되는 능력이며, 그러한 의미에서 ‘내감’ 혹은 ‘제6감’이라고도 할 수 있다."                                                                           
 [8] "한편 미가 취미에 의해 지각된 것이라면, 취미론자들에게 미는 주관적인 것이 된다."                                                                                                                                                                        
 [9] "취미론자의 한 사람인 허치슨은 미란 마음속에 일어난 하나의 관념이라고 주장했다."                                                                                                                                                                        
[10] "이는 곧 미가 그것을 지각하는 마음과 어떠한 관계도 없이 그 자체로 아름다운 성질, 곧 대상 속에 들어 있다고 생각되는 성질을 뜻하는 것이 아니라는 말이다."                                                                                                 
[11] "미의 관념이란 대상의 어떤 특수한 성질을 지각할 때 그 지각으로부터 환기되는 특수한 즐거움을 뜻한다고 이해할 수 있다."                                                                                                                                   
[12] "취미론자들은 ‘이 꽃은 아름답다’와 같은 취미 판단을 할 때 ‘이 꽃’은 분명 외부 세계의 대상들을 지시하고 있지만, ‘아름답다’는 외적인 자극의 성질을 지시하는 것이 아니고 그러한 자극에 의해 우리의 마음속에 환기된 즐거움을 지시하고 있는 것으로 파악했다."
[13] "물론 고전적 미론에서도 주관의 즐거움이 거론된 경우는 있었으나, ‘아름다운 사물은 우리를 즐겁게 한다’와 같은 식의 파생적인 요소로 거론된 것이었고, 미의 본질에 대한 대답은 아니었다."                                                                    
[14] "이 변화가 바로 스톨니츠에 의해 ‘미학에서 일어난 코페르니쿠스적 혁명’이라 명명된 것으로, 취미론으로부터 비롯된 근대 미론과 그 이전의 고전적 미론을 구분하는 분수령이 된다."
```

### sentence2table(sentence)
```R
> sentence2table(example_sentence)

    한      때     뜻     수    미의   관념   대상   특수   성질   지각   환기   이해  즐거움 
     2      1      1      1      1      1      1      2      1      2      1      1      1 
```

### table2gset(table)
```R
> table2gset(sentence2table(example_sentence))
{"관념" [1], "대상" [1], "때" [1], "뜻" [1], "미의" [1], "성질" [1], "수" [1], "이해" [1], "즐거움" [1],
 "지각" [2], "특수" [2], "한" [2], "환기" [1]}
````

### co_occurence(sentence1, sentence2)
```R
> co_occurence(get_sentences(example_text)[1], get_sentences(example_text)[2])
[1] 0.05882353
```

### build_graph(sentences)
```R
> build_graph(get_sentences(example_text))
IGRAPH DNW- 14 182 -- 
+ attr: name (v/c), weight (e/n)
+ edges (vertex names):
[1] 18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다.->취미론에 속하는 이론가들은 상이한 개념이나 취지로 다양한 주장들을 전개했지만, 이것들로부터 다음과 같은 몇 가지 공통 요소들을 도출할 수 있다.                                                             
[2] 취미론에 속하는 이론가들은 상이한 개념이나 취지로 다양한 주장들을 전개했지만, 이것들로부터 다음과 같은 몇 가지 공통 요소들을 도출할 수 있다.                                                             ->18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다.
[3] 18세기 초부터 약 한 세기 동안 영국의 경험주의 철학자들이 발전시킨 미의 이론인 취미론은 미를 객관적이고 형식적인 성질, 예를 들어 비례와 같은 것으로 이해하였던 전통적인 미론과는 근본적으로 다른 것이었다.->먼저 취미론자들은 ‘미의 감관’의 존재, 즉 감각적인 성질로서의 미를 파악하는 감관(sense)인 ‘취미(taste)’가 존재함을 주장한다.                                                                              
+ ... omitted several edges
```

### summarize(text, count)
```R
> summarize(example_text, 2)
[1] "한편 미가 취미에 의해 지각된 것이라면, 취미론자들에게 미는 주관적인 것이 된다."                                     
[2] "미의 관념이란 대상의 어떤 특수한 성질을 지각할 때 그 지각으로부터 환기되는 특수한 즐거움을 뜻한다고 이해할 수 있다."
```
