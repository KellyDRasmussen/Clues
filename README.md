# Salsa20 Decryption Example

This repository chronicles my journey to decrypt a message using the Salsa20 stream cipher with a SHA256 hash as the key.

## Background

This time last year, there was a social media challenge to decrypt a bunch of clues as part of a promotion for open positions at FE.

I got stuck in and used ChatGPT to bring me up to speed on things like what a SHA256 hash is and what a nonce is.

I found someone else who was stuck on LinkedIn, and with his Python skills and my ... desire to solve the puzzle, we got there together. We must have pored over every detail in the campaign but we didn't know HOW it was encrypted. Eventually, we both clicked at the same time and realised it was weird that they had employees talking about how much they loved their Salsa class that some people had attended for 20 years.

He coded it himself, I asked ChatGPT but it just wouldn't work whatever I did.

## This Year

This year, I wanted to see if the new ChatGPT model could make a dent. I still had all the clues in my GitHub, so my prompt was:

"help me decrypt something
It's salsa 20
the cypher is: d7a7e396df976cf6c59adce5d1381ea020a35af126efd0d5d380e4ccb74758e0f05e86a0bed61ac75d5a1dfd029c8792ced99c5abf33354505e288f0b9bda280c9099506be3c3ee818b5e405e1fbf45903708cd067cafa34aa5f5b88958ae6603b4a427ab2
the SHA256 hash of key: 7980a97a11e2b99636133b9baf922de286d3cf893843537f255ab0af56982985
the nonce is zero"

and then I needed an extra prompt of

"you don't need the key, just use the hash"

and boooooom: here it is, no python required.
## Official Solution

Here's their official solution: [FE's Write-up on the Kryptokampagne 2023](https://www.fe-ddis.dk/globalassets/fe/dokumenter/2024/andet/-write-up-kryptokampagne-2023-.pdf)



# Clues
Ymzj ul yri silx wfi yarvcg jrr yri Alczv efxcv yzekj 
Hvis du har brug for hjaelp saa har Julie nogle hints


c = 
d7a7e396df976cf6c59adce5d1381ea020a35af126efd0d5d380e4ccb74758e0f05e86a0bed61ac75d5a1dfd029c8792ced99c5abf33354505e288f0b9bda280c9099506be3c3ee818b5e405e1fbf45903708cd067cafa34aa5f5b88958ae6603b4a427ab2


m=
208871578055264008815784987206014433070334523545419810972640958947509377585338691597595297032174177294081762119296537944087440098006610423063209828598869266969090367569156350784559124967654965549514873876699171511374496034782850275906009358469730618151266793026118362845377720818091597450493462610299709872282554185731540110

m=
0420bad53b6bf9f24ae66ef88fce42b4e549722adfadddae1eeb8d275e6e97dfd4684c2a6574ae0cca639db1af9f55fc1904e91f62d129c313d0e497a3d439ba2c6a2ce2a13712321211db8fb0c1613d3d65e7150137bab3dec7b0c35e8093456d006a01bda97ae8a370b10f3930c0ece7eac89124a3811296e06840ceb1e65db4a6ca0714048e



m=
b"\x04 \xba\xd5;k\xf9\xf2J\xe6n\xf8\x8f\xceB\xb4\xe5Ir*\xdf\xad\xdd\xae\x1e\xeb\x8d'^n\x97\xdf\xd4hL*et\xae\x0c\xcac\x9d\xb1\xaf\x9fU\xfc\x19\x04\xe9\x1fb\xd1)\xc3\x13\xd0\xe4\x97\xa3\xd49\xba,j,\xe2\xa17\x122\x12\x11\xdb\x8f\xb0\xc1a==e\xe7\x15\x017\xba\xb3\xde\xc7\xb0\xc3^\x80\x93Em\x00j\x01\xbd\xa9z\xe8\xa3p\xb1\x0f90\xc0\xec\xe7\xea\xc8\x91$\xa3\x81\x12\x96\xe0h@\xce\xb1\xe6]\xb4\xa6\xca\x07\x14\x04\x8e"




m=
 ºÕ;kùòJænøÎB´åIr*ß­Ý®ë'^nßÔhL*et®Êc±¯UüébÑ)ÃÐä£Ô9º,j,â¡72Û°Áa==eç7º³ÞÇ°Ã^Emj½©zè£p±90ÀìçêÈ$£àh@Î±æ]´¦Ê




*** SHZpcyBkdSBzZXIgdGFsbGV0IHNvbSBldCBwb2x5bm9taXVtIGthbiBmb3JtbGVuIHheMTI5ICsgeV4xNSA9ICh4XjQzICsgeV41KSh4Xjg2IC0geV41ICogeF40MyArIHleMTApIG3lc2tlIGJydWdlcz8=

Hvis du ser tallet som et polynomium kan formlen x^129 + y^15 = (x^43 + y^5)(x^86 - y^5 * x^43 + y^10) måske bruges?
***

***
From graphic 

Key = 1337^d modN

key = 227857446649348275215647624464987241545636391362023478013040699386815734626065451408037899136441568883745828351958633840245091058087960398324909397690679101231208181603855993607345719742780245362918121267992945532766628775198487738065139866725489690423370740983880047037716138970499389202696990105294543663986620847650920138

decrypt(sha256("%d" % key), c)

SHA256 hash of key:
7980a97a11e2b99636133b9baf922de286d3cf893843537f255ab0af56982985



E=2^16+1

E=65537

 x^129 + y^15 = (x^43 + y^5)(x^86 - y^5 * x^43 + y^10) 

N=322^129 + 1333^15 = (322^43 + 1333^5)(322^86 - 1333^5 * 322^43 + 1333^10)

N= 326142539696924869207354354349525777354625893486653622189395488570919279428474475992466593327327880467240974364754407340514146702151463752178592812454871297201622111046567101468602407404235288039149988688165646020710444604497246278100132958510436252439567842298341241387495508297137724774387730729252380126287935310548246749

p = 688339168571559064510890633409023118072556068415553307947521668819820261272348172120258590996493624996917541
q = 473810810989785206183249335304084394309924019877922194181460660379414549164923233586166841085016532206298905214099916489998878755064839730080183959658954277362706718659083359101267500159088948862882849028267625721689

d=
23277411682444513415588140935195489930516542056911703584095967129872818858456892464634671869151413108404712687106347131094414136703918485984415116584342547166936602844775908149714421497854425141640979857547117113977459236442246273533023260245463744374793214467886003966178024315906202636394177453536585323508848265290553873

***
KD9D 84 S9JJ && D8372 S LK951
W9403 SJ829 SK! SID93 DI993 ADDA KF9400 ALS93
&CHD84 KLN11 D9403 DDW 48392 AS

19245
48392
98238
90238


***
Block size: 135 (for N)
block size: 135(for m)

