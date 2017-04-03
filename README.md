長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(xml2)
library(rvest) 
frame = data.frame(Title=character(),
                      Author=character(),
                      PushNum=character())
for(i in 5294:5299){
PTTURL<-paste0("https://www.ptt.cc/bbs/movie/index",i,".html") 
PTTContent <- read_html(PTTURL)
post_title <- PTTContent %>% html_nodes(".title") %>% html_text() 
post_title <- gsub("\n",replacement="",post_title)
post_title <- gsub("\t",replacement="",post_title)
post_author<- PTTContent %>% html_nodes(".author") %>% html_text()
post_pushnum <- PTTContent %>% html_nodes(".nrec") %>% html_text()
PTTframe <- data.frame(Title = post_title, Author = post_author, PushNum = post_pushnum)
frame <- rbind(frame,PTTframe)
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(frame)
```

| Title                                                            | Author       | PushNum |
|:-----------------------------------------------------------------|:-------------|:--------|
| \[普雷\] 點評《漫漫回家路》/微雷                                 | KACIRIE      |         |
| \[普好雷\] 目擊者 好但不會看第二次                               | cappa        | 21      |
| \[普雷\] 點評《絕境之南》：想贖罪，就留下來                      | KACIRIE      |         |
| \[ 算好雷\] 攻殼機動隊                                           | cw56983      | 19      |
| \[ 問片\] 眼前的壞人不是壞人                                     | a1322313     | 2       |
| \[新聞\] 最強老爸喪妻8年「聽見她說話」　如戲人                   | huanglove    |         |
| Re: \[討論\] 玩命關頭紅在哪                                      | Kobe2630     | 16      |
| \[問片\] 提到校園霸凌的同志電影                                  | itwitb       | 16      |
| ［LIVE］CINEMAX 太陽帝國                                         | HellKitty    | 3       |
| \[討論\] 【安娜貝爾：造孽】中文官方預告 釋出                     | MyAll        | 31      |
| \[請益\] 本能寺大飯店vs生日卡片                                  | baozi0329    | 13      |
| \[普雷\] 雙生姊魅 Let Her Out                                    | mysmalllamb  |         |
| (本文已被刪除) \[vincentgotu\]                                   | -            |         |
| \[普雷\] 描寫生動的寶貝老闆                                      | blacktooth   | 5       |
| \[選片\] 攻殼vs金剛vs異星智慧                                    | AE35         | 36      |
| \[新聞\] 蘇有朋 《嫌疑人》打趴好萊塢片 一夜捲2.                  | huanglove    | 12      |
| \[好雷\] 目擊者                                                  | innocent8675 | 20      |
| \[普雷\]《生日卡片》，做自己人生中的主角。                       | a122239      | 2       |
| \[好雷\] 我和我的冠軍女兒 Dangal                                 | BMay         | 31      |
| \[普雷\] 嫌疑犯X的獻身(中國版)                                   | kmwace       | 14      |
| \[贈票\] 玩命關頭8 4/11特映會                                    | ck980417     | 4       |
| \[老雷\] 《鋼琴教師》真神作也                                    | Leika        | 24      |
| \[討論\] Angelababy                                              | kiradu       | 21      |
| \[普無雷\] 愛有來世 The Doscovery                                | biboga       | 2       |
| \[贈票\] 東京影展最佳影片《昨日盛開的花朵》贈票                  | pelicula     | 44      |
| \[請益\] 請問瘋狂麥斯是cyberpunk嗎？                             | pketam       | 11      |
| \[影展\] 4/5(三) 怪奇地下電影大賞【粉紅色水仙】                  | victorway    |         |
| \[新聞\] 那些年我們放棄的角色！12位婉拒演知名                    | go190214     | 52      |
| \[討論\]關於絕命鈴聲這部片                                       | gyfatz       | 6       |
| \[好雷\] 虎父無犬女———冠軍女兒 tak                               | umixnobu 10  |         |
| Re: \[請益\] 請問瘋狂麥斯是cyberpunk嗎？                         | LOLI5566     | 94      |
| \[好雷\] 目擊者觀後感－意義深刻的笑話(有雷)                      | freeeedoom   | 17      |
| \[普雷\] 聲之形                                                  | kirktyler    | 6       |
| (本文已被刪除) <huanglove>                                       | -            |         |
| \[超好雷\] 低調的好動畫 聲之形                                   | dakkk        | 4       |
| Re: \[討論\]關於絕命鈴聲這部片                                   | gyfatz       |         |
| \[好雷\]《目擊者》- 兩好三壞安全上壘                             | jk10134      | 10      |
| \[請益\] 《聲之形》一個細節求解(有電影+漫畫雷)                   | larrybear    | 7       |
| \[新聞\] 凱文費吉談《復仇者聯盟》的沙威瑪片段                    | qn123456     | 8       |
| \[好雷\] 當他們認真編織時-超渡煩惱                               | immad        | 1       |
| \[好雷\] 我和我的冠軍女兒 這片必看                               | stock5566    | 17      |
| \[LIVE\] X戰警天啟Apocalypse 猩猩台手剝21:00                     | pttnowash    | 爆      |
| \[新聞\] 周星馳太孤獨…找林允聊天 j                               | ay5566 6     |         |
| \[普好雷\] 攻殼機動隊                                            | m19871006    | 3       |
| \[問片\] 今天狂新聞裡的電影片段                                  | archvalkyrie | 2       |
| \[問片\] 今天出來狂新聞開計程車                                  | a4839821     | 9       |
| \[好雷\] 單身動物園 The Lobster                                  | ownr         | 34      |
| (本文已被刪除) \[jay5566\]                                       | -            |         |
| \[請益\] 想請教魔女嘉莉原著和電影有差很多嗎                      | qwer04230423 | 26      |
| \[討論\] 孫儷加盟張藝謀三國新片擔任女主角！！！                  | jay5566      | 31      |
| \[好雷\] 目擊者-時間暫停的意義？                                 | zzz499       | 2       |
| \[好雷\] 聲之形～無法傳達的內心吶喊                              | paulyear     |         |
| \[片單\] 聰明縝密的犯罪者有好結果                                | NTUlosers    | 42      |
| \[ 好雷\] 另人耳目一新的目擊者                                   | a3696786     | 18      |
| \[討論\] 想聊聊蓋皮爾斯Guy Pearce這個演員                        | SpkSpawn     | 59      |
| \[不算有雷的雷\] The Quiet Passion 寂靜的激情                    | Ruthcat      |         |
| \[片單\] 無神論者被排擠的片?                                     | kyouya       | 6       |
| \[請益\] \[有雷\] 冠軍女兒的真實故事                             | endurant     | 4       |
| \[情報\] 《神鬼傳奇》最新預告 震撼登場                           | SKnight      | 64      |
| \[好雷\] 冥中注定我愛你 - 黃姵嘉好漂亮                           | SuperSg      | 4       |
| \[討論\] 景甜真的很雷嗎？                                        | jimmy9991    | 23      |
| \[討論\] 明天我要和昨天的妳約會聖地巡禮                          | thjyrsj      | 17      |
| \[新聞\] 北美週末:寶貝老闆稱霸, 美女野獸居次                     | lovemelissa  | 20      |
| \[好雷\] 目擊者-流暢的國片!!(買電影票要小心!!)                   | stoneJ       | 18      |
| \[情報\]【4/1(六) 台北單日電影票房粗估 】                        | ss30066      | 20      |
| \[問片\] 一部俄羅斯兄弟到美國發展的電影                          | Ga1axyNote7  | 5       |
| Re: \[新聞\] 北美週末:寶貝老闆稱霸, 美女野獸居次                 | senria       | 3       |
| Re: \[討論\] 景甜真的很雷嗎？                                    | bill1478963  | 2       |
| \[普雷\]目擊者                                                   | nothing188   | 3       |
| \[普雷\]攻殼機動隊 have no ghost in the shell                    | brioche      | 11      |
| \[ 好雷\] 寶貝老闆 出乎意料的好看！                              | TCPai        | 5       |
| \[好雷\] 明天，我要跟昨天的妳約會                                | QoHyacinthoQ | 2       |
| \[ 超好雷\] 目擊者 誰殺了XX                                      | lingary      | 4       |
| \[好雷\] 攻敵必救                                                | emip         | 12      |
| (本文已被刪除) <h2030625>                                        | -            | 56      |
| (本文已被刪除) \[LD0123\]                                        | -            |         |
| \[情報\]越南景甜破尺度主演【嚇女的誘惑】HD高畫質中文電影預告     | jas1123kimo  | 4       |
| \[好雷\] 目擊者的疑問與想法                                      | green741s    | 6       |
| \[微好雷\] 救殭清道夫                                            | flowgo       |         |
| \[吐雷\] 不吐不快之攻殼機動隊2017                                | lordyamato   | 11      |
| \[好雷\] 最後一頁，最恐怖－目擊者                                | ueiwei       | 2       |
| \[請益\] 自己一個人適合看這片嗎QQ?                               | NiNiHOT      |         |
| \[好雷\] 白雪公主殺人事件                                        | kurama1984   | 15      |
| \[新聞\] 好消息！以後電影上映45天網路上就看得到                  | jay5566      | 5       |
| \[討論\] marvel是不是沒                                          | justempty    |         |
| \[情報\] 《異形：聖約》片段預告                                  | Tristan0918  | 2       |
| \[片單\] 請推薦不限種類好看電影，我也推薦一下                    | koisppq      | 9       |
| (本文已被刪除) \[jay5566\]                                       | -            |         |
| \[請益\] 療養怨的小問題                                          | alista       | 3       |
| \[輕微雷\]攻殼機動隊腦粉簡短觀影心得                             | ahhway       | 6       |
| \[好雷\] 聲之形                                                  | nerv3890     | 1       |
| \[討論\] 《玩命鎗火》導演欲拍攝殭屍版漫威電影！                  | jay5566      |         |
| \[微好雷\]金剛戰士Power Rangers勾起滿滿回憶!                     | fullmetalyao | 1       |
| Re: \[討論\] marvel是不是沒                                      | LOLI5566     | 5       |
| \[普好雷\] 她們的顫慄故事(陸譯:女劫)-XX                          | LF25166234   |         |
| \[討論\] 最喜歡的「西遊」電影？                                  | kiradu       | 10      |
| \[問片\] 嬰兒殺父母的恐怖片                                      | amx2131      | 7       |
| \[新聞\] 湯姆克魯斯5月訪台　四度來台破紀錄！                     | jay5566      | 19      |
| \[情報\]《銀魂》真人電影片場劇照                                 | jay5566      | 34      |
| \[普雷\] 目擊者故事好但不算好的懸疑片                            | signm        | 4       |
| \[情報\] 2017 北美4~6月上映電影列表                              | ooic         | 9       |
| \[好雷\] 我和我的冠軍女兒-以父威對抗體制                         | nosweating   | 4       |
| \[多部雷\]那些有血有肉的超級英雄們                               | LIPOYI       | 6       |
| \[選片\] 攻殼機動隊VS美女與野獸                                  | a85405       | 13      |
| \[問片\] 好朋友相約結婚                                          | purist       |         |
| Re: \[情報\]越南景甜破尺度主演【嚇女的誘惑】HD高畫質中文電影預告 | andey        |         |
| (本文已被刪除) <t4937054>                                        | -            | 3       |
| \[普雷\]一路順風－天亮了，我們繼續走。                           | guangpiano   |         |
| (本文已被刪除) <t4937054>                                        | -            |         |
| \[負雷\] 攻殼機動隊                                              | arrakis      | 1       |
| \[討論\] (Cinefix)十大不靠對話的電影                             | peter220     | 1       |
| \[公告\]《各式疑難雜症FAQ》                                      | yunyun85106  | 23      |
| \[公告\] 板規！必看！｜好文推薦‧惡文檢舉 e                       | ricf129 爆   |         |
| \[贈票\] 恐怖驚悚【逃出絕命鎮】北中南搶先看                      | ChloeD       | 爆      |
| \[贈票\] 東京影展最佳影片《昨日盛開的花朵》贈票                  | pelicula     | 53      |

解釋爬蟲結果
------------

``` r
str(frame)
```

    ## 'data.frame':    115 obs. of  3 variables:
    ##  $ Title  : Factor w/ 112 levels "(本文已被刪除) [vincentgotu]",..: 8 6 7 2 3 17 20 15 19 14 ...
    ##  $ Author : Factor w/ 97 levels "-","a122239",..: 14 8 14 9 3 11 16 13 10 17 ...
    ##  $ PushNum: Factor w/ 37 levels "","12","13","14",..: 1 9 1 6 7 1 5 5 10 11 ...

``` r
#共爬出115個電影標題
table(frame$Author)
```

    ## 
    ##            -      a122239     a1322313         AE35    baozi0329 
    ##            8            1            1            1            1 
    ##   blacktooth         BMay        cappa      cw56983    HellKitty 
    ##            1            1            1            1            1 
    ##    huanglove innocent8675       itwitb      KACIRIE       kmwace 
    ##            2            1            1            2            1 
    ##     Kobe2630        MyAll  mysmalllamb       biboga     ck980417 
    ##            1            1            1            1            1 
    ##        dakkk   freeeedoom     go190214       gyfatz        immad 
    ##            1            1            1            2            1 
    ##      jk10134       kiradu    kirktyler    larrybear        Leika 
    ##            1            2            1            1            1 
    ##     LOLI5566     pelicula       pketam     qn123456  takumixnobu 
    ##            2            2            1            1            1 
    ##    victorway     a3696786     a4839821 archvalkyrie     endurant 
    ##            1            1            1            1            1 
    ##      jay5566       kyouya    m19871006    NTUlosers         ownr 
    ##            6            1            1            1            1 
    ##     paulyear    pttnowash qwer04230423      Ruthcat      SKnight 
    ##            1            1            1            1            1 
    ##     SpkSpawn    stock5566      SuperSg       zzz499  bill1478963 
    ##            1            1            1            1            1 
    ##      brioche         emip       flowgo  Ga1axyNote7    green741s 
    ##            1            1            1            1            1 
    ##  jas1123kimo    jimmy9991      lingary   lordyamato  lovemelissa 
    ##            1            1            1            1            1 
    ##   nothing188 QoHyacinthoQ       senria      ss30066       stoneJ 
    ##            1            1            1            1            1 
    ##        TCPai      thjyrsj       ahhway       alista      amx2131 
    ##            1            1            1            1            1 
    ## fullmetalyao    justempty      koisppq   kurama1984   LF25166234 
    ##            1            1            1            1            1 
    ##     nerv3890      NiNiHOT        signm  Tristan0918       ueiwei 
    ##            1            1            1            1            1 
    ##       a85405        andey      arrakis       ChloeD     ericf129 
    ##            1            1            1            1            1 
    ##   guangpiano       LIPOYI   nosweating         ooic     peter220 
    ##            1            1            1            1            1 
    ##       purist  yunyun85106 
    ##            1            1

``` r
#如下所示：「-」作者為最多貼文數，不過在ppt中，作者名稱被標示為「-」，都是被管理員所刪除的貼文，故不予計算，最多貼文的作者應為「jay5566」。
```

1.共爬出115個電影標題

2.如下所示：「-」作者為最多貼文數，不過在ppt中，作者名稱被標示為「-」，都是被管理員所刪除的貼文，故不予計算，最多貼文的作者應為「jay5566」。

``` r
#在這次爬蟲中，就標題來看發覺，鄉民們取的標題，有如新聞媒體般，充斥著誇飾、搞笑、一刀見血，對不常使用的我覺得很新鮮、有趣，和許多佛心的贈票資訊，與電影內容，讓我確實地發現這就是ptt歷久不衰的原因，因為充滿著熱心的鄉民。
```

在這次爬蟲中，就標題來看發覺，鄉民們取的標題，有如新聞媒體般，充斥著誇飾、搞笑、一刀見血，對不常使用的我覺得很新鮮、有趣，和許多佛心的贈票資訊，與電影內容，讓我確實地發現這就是ptt歷久不衰的原因，因為充滿著熱心的鄉民。
