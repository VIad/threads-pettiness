# Pettiness
_noun_
1. undue concern with trivial matters, especially of a small-minded or spiteful nature.
   
    "the sheer pettiness of the officials was quite startling"
   
    - lack of importance or worth; triviality.
      
        "these awesome moments lift us above the pettiness of the world"
-----
### Стъпка 1:
Отвори developer tools на твоя браузър (Обикновенно F12 бутона)
 * При Chrome: десен бутон -> Inspect
 * При друг browser -> Google: How to open developer tools in [browser-name]
Стигни то таб "Console"

**NOTE: Browser-a ще се пробва да те стресне с това, но ти не си путка, и знаеш, че няма проблеми.**
(Реално абсолютно нищо не "хакваме", това е просто clientside код, който автоматизира кликване на бутончета за 'unfollow' и нищо повече)
![alt text for screen readers](https://i.imgur.com/V1jtfxs.png)

--------
### Стъпка 2:
Влез в списъка с **твоите последователи.** 

**СКРОЛНИ ДО ДОЛУ (не работи ако не стигнеш до долу)**

Изчисти конзолата и copy-paste-ни следния код вътре:
```javascript
const parentDivClassName = "xb5mbof x78zum5 x1q0g3np xyamay9 x1ypdohk x1swvt13"
const childElementClassName = "x1i10hfl xjbqb8w x1ejq31n xd10rxx x1sy0etr x17r0tee x972fbf xcfux6l x1qhh985 xm0m39n x9f619 x1ypdohk xt0psk2 xe8uvvx xdj266r x11i5rnm xat24cr x1mh8g0r xexx8yu x4uap5 x18d9i69 xkhd6sd x16tdsg8 x1hl2dhg xggy1nq x1a2a7pz xp07o12 xzmqwrg x1citr7e x1kdxza xt0b8zv"

const followedListParents = document.getElementsByClassName(parentDivClassName)


const arrayFollowed = Array.prototype.slice.call(followedListParents)
const listFollowed = arrayFollowed.map((el => el.getElementsByClassName(childElementClassName)[0])).map((el => el.getAttribute("href"))).map((el => el.substring(2)))
```

след това Enter за да го изпълниш

Трябва да изпише: undefined.. this is good

--------
### Стъпка 3:
Влез в списъка с хората **които следваш.** СКРОЛНИ ДО ДОЛУ (не работи ако не стигнеш до долу)

copy-paste-ни този код в конзолата
```javascript
const followingListUnfollowButtonClassName = "x1i10hfl xjbqb8w x1ypdohk xdl72j9 x2lah0s xe8uvvx xdj266r x11i5rnm xat24cr x1mh8g0r x2lwn1j xexx8yu x18d9i69 x1n2onr6 x16tdsg8 x1hl2dhg xggy1nq x1ja2u2z x1t137rt x1q0g3np x1lku1pv x1a2a7pz x6s0dn4 x1a2cdl4 xnhgr82 x1qt0ttw xgk8upj x9f619 x3nfvp2 x1s688f x90ne7k xl56j7k x193iq5w x1g2r6go x11xpdln xz4gly6 x87ps6o xuxw1ft x19kf12q x12w9bfk x6bh95i x1re03b8 x1hvtcl2 x3ug3ww x13fuv20 xu3j5b3 x1q0q8m5 x26u7qi x178xt8z xm81vs4 xso031l xy80clv xu0ddkp xwsj4vy x1e558r4 x150jy0e"


const followingListParents = document.getElementsByClassName(parentDivClassName)


const arrayFollowing = Array.prototype.slice.call(followingListParents)
const listFollowing = arrayFollowing.map((el => el.getElementsByClassName(childElementClassName)[0])).map((el => el.getAttribute("href"))).map((el => el.substring(2)))

const difference = listFollowing.filter((el => !listFollowed.includes(el)))

console.log('ne te sledvat '+ difference.length+ ' choveka, koito ti sledvash. Dosta pedalsko ot tqhna strana')

const unfollowButtons = arrayFollowing.filter((el => difference.includes(el.getElementsByClassName(childElementClassName)[0].getAttribute("href").substring(2)))).map((el => el.getElementsByClassName(followingListUnfollowButtonClassName)[0]))
```
Отново Enter за да изпълниш кода

Ако всичко е правилно, програмата ще ти каже колко хора не те следват обратно

### Стъпка 4
copy paste-ни този код в конзолата:
```javascript
unfollowButtons.forEach((el => el.click()))
```
Enter, и трябва да е готово.

Refresh-ни страницата след като си изпълнил тези стъпки.

