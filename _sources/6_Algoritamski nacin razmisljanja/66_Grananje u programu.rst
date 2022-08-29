
Гранање у програму
==================

Вратимо се опет на одлазак у продавницу. Неке од корака можеш унапред да предвидиш, знаш да се неће променити. 
Као што смо већ рекли, неке од њих не можеш унапред да предвидиш.

Oсновни је ред да се јавиш ако сретнеш неког познатог на улици. Да ли можеш унапред да предвидиш колико ћеш другова, 
другарица, рођака или кућних пријатеља срести? Да ли би било довољно да ти родитељи кажу „Јави се пет пута“? 
Како би, у овом случају, гласило добро, исправно упутство?

„**Ако** сретнеш неког познатог, поздрави га“.

На раскрсници може да буде постављен семафор. Упутство би гласило: 

„**Ако** је на семафору зелено светло за пешаке, пређи улицу. И у случају да је постављен семафор и да није – провери да ли наилази неко возило са леве или десне стране. **Ако** нема возила, пређи улицу.“

Слично је и кад састављаш програм.

.. infonote::

 Када се у програму проверава неки услов и раде различите ствари у зависности да ли је он испуњен и не, говоримо о **гранању**. 

За сваки од претходних случајева било је потребно да јасно кажеш шта треба да се уради *ако* је испуњен неки услов. 
У програму за овакве ситуације користиш блокове из групе ``Гранање``.

Превуци горњи блок у простор за слагање. 

Ови блокови се комбинују са различитим условима.
 
Као што је код условних петљи већ поменуто, **услови** су **изрази који могу бити тачни или нетачни**. 
Да би боље разумео како се користи гранање у програму, и овде смо убацили групу блокова ``Питај робота``.


Пример
------

**Карел треба да стигне на поље (7, 1). Ако на путу наиђе на лопту, треба да је узме. Састави решење тако да важи и ако је другачији распоред лоптица.**


.. blockly-karel:: karel_p8
  :categories: KarelCommands, Loops, Branching, KarelBrain
  
  {
      setup: function() {

           var world = new World(7, 7);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           world.putBall(2, 1);
		   world.putBall(4, 1);
		   world.putBall(6, 1);
		   world.putBall(7, 1);
		   
           var robot = new Robot();
           return {world: world, robot: robot};
      },
	  
	  isSuccess: function(robot, world) {
          for (var i = 1; i <= world.getAvenues(); i++)
              for (var j = 1; j <= world.getStreets(); j++)
                 if (world.getBalls(i, j) != 0)
                    return false;
          return true;
      }           
   }
 
Када би састављао блокове корак по корак, изгубио би много времена. Замисли да је испред Карела стотинак лоптица различито
распоређених. Универзално упутство било би следеће: 

„Направи корак. Ако се на пољу налази лоптица, узми је.“ 

Превуци горњи блок из групе ``Гранање``, а затим блок ``постоји лоптица`` из групе ``Питај робота``. Ако постоји лоптица, Карел треба да је узме.
Додај блок ``узми`` из групе ``Наредбе роботу`` (повежи га поред речи ``изврши``).

Пре тога, да би ишао даље, Карел треба да направи корак напред. Повежи и овај блок изнад блока са гранањем.

Колико пута Карел треба ово да понови?

У овом случају можемо да избројимо да је то шест пута. Из групе ``Петље`` превуци блок за бројачку петљу, укуцај број 6 уместо 10
и претходно састављене блокове превуци у простор планиран за наредбе, поред речи ``изврши`` (како би истовремено превукао све блокове који су повезани, 
миша држи на горњем блоку). Покрени програм!

Шта да радимо ако не знамо колика је дужина пута којим се Карел креће?
Наше решење је састављено применом бројачке петље. Сигурно је још универзалније ако кажеш „док Карел може напред“. 

Измени решење и тестирај тако састављен програм!
   
Задатак 17
----------

**Мирко је покушао да реши претходни пример тако што ће да примени условну петљу. Међутим, програм му стално одговара да је решење нетачно. Пронађи грешку!**

.. blockly-karel:: karel_z17
  :categories: KarelCommands, Loops, Branching, KarelBrain
  
  
  {
      setup: function() {

           var world = new World(7, 7);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           world.putBall(2, 1);
		   world.putBall(4, 1);
		   world.putBall(6, 1);
		   world.putBall(7, 1);
		   
           var robot = new Robot();
		   var domXml = '<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="controls_whileUntil" id="1)rOW#a/hEpZ/_Lv@b:U" x="131" y="109">\n    <value name="BOOL">\n      <block type="can_move" id="#.HC]U_!uKz|}Rk!JW{8"></block>\n    </value>\n    <statement name="DO">\n      <block type="controls_if" id="D=_vw:+~Le{?W1XM8KgJ">\n        <value name="IF0">\n          <block type="balls_present" id="eLjl8G|6y.qzS@9;sw;="></block>\n        </value>\n        <statement name="DO0">\n          <block type="pick_up" id="qelo*@4{EL*7{WQfR1Ju"></block>\n        </statement>\n        <next>\n          <block type="move" id="*YYtqewNAE4HTI72M-0`"></block>\n        </next>\n      </block>\n    </statement>\n  </block>\n</xml>';
           return {world: world, robot: robot, domXml:domXml};
      },
	  
	  isSuccess: function(robot, world) {
          for (var i = 1; i <= world.getAvenues(); i++)
              for (var j = 1; j <= world.getStreets(); j++)
                 if (world.getBalls(i, j) != 0)
                    return false;
          return true;
      }           
   } 
  
**Помоћ**: Провери редослед извршавања корака и, по потреби, измени!  


Када је реч о гранању, постоје два различита случаја: 

Први је када треба само да кажеш шта да се уради ако је испуњен неки услов (поздрављање ако сретнеш неког познатог). 

Други случај је када је потребно да објасниш и шта треба да се уради ако није испуњен услов, „иначе”. 

Ако је црвено светло на семафору, не треба да направиш ниједан даљи корак. Али, ако у продавници нема кифли, потребно 
је да знаш шта треба да урадиш уместо тога. На пример, да ли да купиш погачице, одеш у другу радњу или да само изађеш 
из радње и вратиш се кући.

Први блок у групи гранање предвиђен је за случај да није потребно ништа да се уради ако није испуњен услов 
(иако и овај блок може да се прошири кликом на зупчаник у његовом горњем левом углу)

Блок испод њега користиш када (у случају да није испуњен услов) треба да се изврши и нека друга наредба, односно неки други корак.

Пример
------

**Испред Карела се налазе рупе и лопте. Ако стане на поље на ком се налази лопта, треба да је узме. Иначе, треба да је остави у рупу.**

Превуци доњи блок из групе ``Гранање`` у простор за слагање блокова и погледај како изгледа. Осим ``ако`` и ``изврши``, појавило се и ``иначе``.
Поред ове речи повезујеш блок или групу блокова са наредбама које треба да се изврше ако услов није испуњен.

.. blockly-karel:: karel_p9
  :categories: KarelCommands, Branching, KarelBrain, Loops
  
  {
      setup: function() {
           var world = new World(7, 5);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
		   world.addEWWall(1, 1, 7)
           world.putBall(2, 1);
		   world.putBall(3, 1);
		   world.putBall(5, 1);
		   world.putHole(4, 1);
		   world.putHole(6, 1);
		   world.putHole(7, 1);
           var robot = new Robot();
           return {world: world, robot: robot};
      },
	  
	  isSuccess: function(robot, world) {
          for (var i = 1; i <= world.getAvenues(); i++)
              for (var j = 1; j <= world.getStreets(); j++)
                 if (world.getBalls(i, j) != 0)
                    return false;
          return true;           
      }
   }
 
У овом примеру: Карел направи корак напред. Ако на пољу постоји лоптица - треба да је узме, иначе - остави.

Овај блок треба да се понавља све док робот може да иде напред. Из групе ``Петље`` превуци одговарајући блок и убаци блок који је претходно састављен.
   
.. reveal::  Пример9
   :showtitle: Предлог решења   
   :hidetitle: Затвори
	
   Предлог решења
 
   .. image:: ../../_images/primer9_blokovi.png
     :width: 780
     :align: center   
   
   
Задатак 18
----------

**Карел не зна колико има лопти код себе. Јана je саставила мало сложенији програм. Шта је Јана рекла Карелу да треба да уради? Колико ће лоптица Карел имати код себе када изврши овај задатак?**

Покушај да одговориш пратећи корак по корак, односно блок по блок који је Јана поставила. 

Већ се назире да постоје два различита случаја. Шта ће Карел да уради у првом, а шта у другом? 
До када ће све то да ради? Објасни својим речима! 

Покушај да се крећеш по датим инструкцијама, да правиш исте кораке као Карел! 
У крајњем случају, покрени Јанин програм и одговори на питање!

(сваки пут кад покренеш програм, Карел ће имати  код себе различит број лопти, али ће на крају увек имати исти)

.. blockly-karel:: karel_z18
  :categories: KarelCommands, Loops, Branching, KarelBrain, Logic, Arithmetic
  
  
  {
      setup: function() {
	  
	  function random(n) {
            return Math.floor(n * Math.random());
        }
           var world = new World(5, 5);
           world.setRobotStartAvenue(3);
           world.setRobotStartStreet(1);
		   
           world.setRobotStartDirection("S");
           world.putBalls(4, 1, 10);
		   world.putHoles(2, 1, 10);
           var robot = new Robot();
		   var domXml = '<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="controls_whileUntil" id="|A1Ni,?T.k|=1l6t%{v4" x="46" y="43">\n    <value name="BOOL">\n      <block type="logic_compare" id="luDddc9w]PSm?cMd9Z@[">\n        <field name="OP">NEQ</field>\n        <value name="A">\n          <block type="count_balls_on_hand" id="yfMESb/z206!0`LuyKyJ"></block>\n        </value>\n        <value name="B">\n          <block type="math_number" id="u46aX~Dwh=VJiPh[ElTE">\n            <field name="NUM">5</field>\n          </block>\n        </value>\n      </block>\n    </value>\n    <statement name="DO">\n      <block type="controls_ifelse" id="3|s0)y.L/rVIKg=Z7+GD">\n        <value name="IF0">\n          <block type="logic_compare" id="CDwSJ_+83NW.#kk2H.0N">\n            <field name="OP">GT</field>\n            <value name="A">\n              <block type="count_balls_on_hand" id="wFEzmOY2QD.)b5J.kNi/"></block>\n            </value>\n            <value name="B">\n              <block type="math_number" id="cc}fSormHlH733(49^e$">\n                <field name="NUM">5</field>\n              </block>\n            </value>\n          </block>\n        </value>\n        <statement name="DO0">\n          <block type="turn_right" id="1^o!cNWs3xj}34SJ!$v:">\n            <next>\n              <block type="move" id="V%k:Os3w893Od.Qx?uUE">\n                <next>\n                  <block type="drop_off" id="F7S/{P*vv39]|XzRPb)}">\n                    <next>\n                      <block type="turn_around" id="s_4}H8C{laZfE`^{hlS(">\n                        <next>\n                          <block type="move" id="F%Ja}V4(fO}]GuUK$Gec">\n                            <next>\n                              <block type="turn_right" id="8JmC15I9{,s6j4(MGGUb"></block>\n                            </next>\n                          </block>\n                        </next>\n                      </block>\n                    </next>\n                  </block>\n                </next>\n              </block>\n            </next>\n          </block>\n        </statement>\n        <statement name="ELSE">\n          <block type="turn_left" id="*aVk_.+GHQW`[LMCO[;%">\n            <next>\n              <block type="move" id="E(Bp#ke8j-x6,.+UV:sd">\n                <next>\n                  <block type="pick_up" id="3Yi#br-`Y]4KYQ{[mMZe">\n                    <next>\n                      <block type="turn_around" id="R,cQ).OT*r/m%_EE6oz~">\n                        <next>\n                          <block type="move" id="{I__^jNv_XD!Q$ZZqt;@">\n                            <next>\n                              <block type="turn_left" id="f8n{dcd{]qNWvKG1BDe["></block>\n                            </next>\n                          </block>\n                        </next>\n                      </block>\n                    </next>\n                  </block>\n                </next>\n              </block>\n            </next>\n          </block>\n        </statement>\n      </block>\n    </statement>\n  </block>\n</xml>';
		   var n = random(10)
           robot.setBalls(n);
		   
           return {world: world, robot: robot, domXml:domXml};
      },
	  
      isSuccess: function(robot, world) {
          return robot.getBalls() == 5;                   
      }
   }
   
До сада су програми које си састављао били једноставни и нису се састојали из великог броја блокова. Током времена постаће сложенији.

И у овом окружењу постоји могућност да вратиш корак уназад ако случајно нешто погрешиш.

.. suggestionnote::

 Када кликнеш десним тастером миша било где на простор за слагање блокова добићеш следеће опције:
 
 - ``Опозови`` служи да се вратиш један корак уназад
 - ``Понови`` ће се појавити када се вратиш бар један корак уназад, моћи ћеш тада да идеш и корак унапред
 - ``Скупи блокове`` се користи када имаш пуно блокова, па хоћеш да се неки не виде, да програм буде прегледнији
 - ``Обриши блокове`` служи да избришеш све блокове одједном.
 
 