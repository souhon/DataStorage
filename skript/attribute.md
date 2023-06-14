# Attribute
Example
 `{AttributeName:"",Name,"",Operation:0,Slot:"mainhand",Amount:0D,UUIDLeast:4325814L,UUIDMost:21456L}`

**AttributeName**には属性の名前を指定します  

|AttributeName|Base Value|Min|Max|
|:-|:-:|:-:|:-:|
|generic.maxHealth|20|1.4e-45f|1024|
|generic.followRange|32|0|2048|
|generic.knockbackResistance|0|0|1|
|generic.movementSpeed|0.699999988079071|0|1024|
|generic.flyingSpeed|0.4000000059604645|0|1024|
|generic.attackDamage|2|0|2048|
|generic.attackSpeed|4|0|1024|
|generic.armor|0|0|30|
|generic.armorToughness|0|0|20|
|generic.luck|0|-1024|1024|

**Name**には任意の文字列を指定します（空文字は不可）  
**Slot**には`mainhand offhand feet legs chest head`のいずれかを指定します  
**Operation**には0,1,2のいずれかを指定します  
<pre>
 0 -> BaseValue + Amount  
 1 -> BaseValue + BaseValue * Amount  
 2 -> BaseValue * (1 + Amount)
</pre>
**Amount**には任意の数値を指定します  
**UUIDLeast/Most**には適当な数値を入れます。これは属性の識別子として使用されます

## generic.attackSpeed

アイテムを使用・装着したときのモーションの計算
$$CP=\frac{20}{attackSpeed}$$
$$CAS=\frac{ticksSinceLastSwing+adjustTicks}{CP}$$
$$mainHandProgress = CAS^3\\{ 0\le CAS\le 1 \\}$$
$$offHandProgress = 1$$

モーションの時間をn tickと考えるとattackSpeedの値は
$$attackSpeed = 20 / n$$
ベース値を考慮してn tickのモーションの値は
$$attackSpeed = 20 / n - 4$$
