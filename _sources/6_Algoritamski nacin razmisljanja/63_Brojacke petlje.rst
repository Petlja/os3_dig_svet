
Бројачке петље
==============

У примеру с почетка лекције о алгоритамском размишљању поменули смо упутство за куповину кифли. 
Размисли о следећем:

- претпоставимо да је растојање од твоје куће/стана до раскрснице 172 корака,
- правите прославу, па треба да купиш 35 кифли.

Колико би наредби, једну по једну, требало да задаш роботу попут Карела да то уради (у продавници сваку кифлу узимаш са пулта, 
спушташ је у корпу, узимаш из корпе, стављаш поред касе…)? Не, наравно, нема потребе да то стварно рачунаш!

Хтели смо само да ти укажемо на то да у скоро сваком од претходних примера постоје наредбе које се понављају тачно 
одређен број пута. Добра ствар је што нема потребе да их све пишеш, постоји једноставнији начин.

.. infonote::

 Када наредба (или група наредби) треба да се изврши више пута, у програму се користи **петља**. 
 Када се унапред тачно зна колико пута наредба треба да се понови, петља се назива **бројачка петља**.

Пример
------

Карел треба да сакупи осам лопти. Примени бројачку петљу у решењу!

.. blockly-karel:: karel_p3
  :flyouttoolbox:
  :categories: KarelCommands, Loops
  
  {
      setup: function() {
           var world = new World(5, 5);
           world.setRobotStartAvenue(3);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("W");
           world.putBalls(2, 1, 8);
           var robot = new Robot();
		   var domXml ='<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="move" id="P:A@rh-yEri6hB{xdg%*" x="48" y="144">\n    <next>\n      <block type="pick_up" id=";JAex_)98[eDGkpG(8P*">\n        <next>\n          <block type="pick_up" id="Y]9=zS.P$?.ulkeWZOna">\n            <next>\n              <block type="pick_up" id="Hl^WZ[JwN?W~qwLo$(i+">\n                <next>\n                  <block type="pick_up" id="PSrYQpfO1_:sYiU-Z74C">\n                    <next>\n                      <block type="pick_up" id="r,CU6Gij:uOB?Rs*x|h?">\n                        <next>\n                          <block type="pick_up" id="%+#=HW53tdzO/mL{FJFB">\n                            <next>\n                              <block type="pick_up" id="A/(WFPG.M25!%i7K*HkN">\n                                <next>\n                                  <block type="pick_up" id="j}6?R838*}OqcE%idBb."></block>\n                                </next>\n                              </block>\n                            </next>\n                          </block>\n                        </next>\n                      </block>\n                    </next>\n                  </block>\n                </next>\n              </block>\n            </next>\n          </block>\n        </next>\n      </block>\n    </next>\n  </block>\n  <block type="move" id="Bh,5mG1Hx_G4,[McyR:T" x="252" y="141">\n    <next>\n      <block type="controls_repeat" id="[3myH(#a:Mhy9XI0R1gw">\n        <field name="TIMES">8</field>\n        <statement name="DO">\n          <block type="pick_up" id="1oK]fLL/EC1g-+9YG#gL"></block>\n        </statement>\n      </block>\n    </next>\n  </block>\n</xml>';
		   return {world: world, robot: robot, domXml:domXml};
      },
	  
      isSuccess: function(robot, world) {
           return robot.getBalls()==8
      }
   }

Овог пута се на гомили налази осам лопти. Карел треба прво да направи један корак напред, 
а затим осам пута узме лопту. 

На десну страну смо превукли блокове за два решења овог проблема. За које је потребно мање блокова? 
Избриши дуже решење и покрени програм!

Много је брже да поставиш један блок и изабереш колико пута треба да се понови неки корак него да сваки пут исписујеш наредбу за корак који се понавља. 

.. questionnote::

 Замисли колико би ти времена требало да саставиш програм без петље када би Карел требало да узме 200 лопти!

Овог пута смо у решењу употребили блок зелене боје који представља **бројачку петљу**. 

И њега превлачиш као и претходне. Међутим, овај блок сам за себе ништа не ради. Потребно је да у њега "увучеш" блок 
или више блокова са корацима који треба да се понове више пута.

.. suggestionnote::

 Са десне стране сада постоји већ више блокова са наредбама и постају непрегледне. Да би биле прегледније, од следећег 
 задатка ће бити подељене у групе (``Наредбе роботу`` и ``Петље``). Када кликнеш на назив групе, појавиће се блокови који се 
 у њој налазе!

Задатак 6
---------

Задатак је исти као и **Задатак 4**. Овог пута у решењу користи бројачку петљу!

.. blockly-karel:: karel_z6
  :categories: KarelCommands, Loops
  
  {
      setup: function() {
           var world = new World(5, 5);
		   world.addEWWall(1, 1, 4)
		   world.addNSWall(4, 2, 4)
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           world.putBall(5, 1);
		   world.putBall(5, 5);
           var robot = new Robot();
          
           return {world: world, robot: robot};
      },
	  
      isSuccess: function(robot, world) {
           return robot.getBalls() == 2;
      }
   }

**Помоћ**: да би узео прву лоптицу, Карел треба четири пута да направи корак, па да је узме. Затим треба да се окрене у 
леву страну и  понови исти поступак за другу лоптицу. 

Једно од решења може бити следеће: 

.. reveal::  Задатак6
   :showtitle: Предлог решења   
   :hidetitle: Затвори
	
   Предлог решења
 
   .. image:: ../../_images/zadatak6_blokovi.png
     :width: 780
     :align: center
	 
Да ли видиш још неку могућност да употребиш блок за бројачку петљу?

Задатак 7
---------
На гомили се налази пет лоптица које Карел треба да убаци у рупу. Реши задатак применом бројачких петљи!

.. suggestionnote::
 Изнад Карелове главе можеш да пратиш број лоптица које тренутно има код себе!

 
.. blockly-karel:: karel_z7
  :categories: KarelCommands, Loops
  
  {
      setup: function() {
           var world = new World(5, 5);
           world.setRobotStartAvenue(5);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("W");
           world.putBalls(3, 1, 5);
		   world.putHoles(1, 1, 5);
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

**Помоћ**: Карел треба да направи два корака, пет пута да узме лоптицу, опет да направи два корака и пет пута да 
остави лоптицу. Користи бројачку петљу кад год је могуће!

Задатак 8
---------

Помози Карелу да стигне до поља (6, 6)! Изабери пут који ти највише одговара! (користи бројачку петљу у решењу!)

.. blockly-karel:: karel_z8
  :categories: KarelCommands, Loops
  
  {
      setup: function() {
           var world = new World(6, 6);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("N");
		   for (var i = 1; i <= world.getAvenues()-1; i++)
		       world.addEWWall(i+1, i, 1)
		   for (var i = 1; i <= world.getAvenues()-1; i++)
		       world.addNSWall(i, i, 1)
			   
           var robot = new Robot();
           return {world: world, robot: robot};
      },
	  
      isSuccess: function(robot, world) {
	        return robot.getAvenue() == 6 && robot.getStreet() == 6
      }
   }
 
**Помоћ**: Добро размисли да ли постоји више решења за овај проблем? Можда на први поглед пут уз цикцак 
зид делује краћи, али да ли је стварно тако? Како ћеш најједноставније да објасниш Карелу пут до циља?
 
Задатак 9
----------

Да би успешно завршио задатак, Карел треба да сакупи пет лоптица које се налазе на крају овог необичног пута. 
Примени петље у програму и помози му! 
 
.. blockly-karel:: karel_z9
  :categories: KarelCommands, Loops
  
  {
      setup: function() {
           var world = new World(6, 6);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
		   world.putBalls(6, 6, 5)
		   for (var i = 1; i <= world.getAvenues()-1; i++)
		       world.addEWWall(i+1, i, 1)
		   for (var i = 1; i <= world.getAvenues()-1; i++)
		       world.addNSWall(i, i, 1)
		   for (var i = 1; i <= world.getAvenues()-1; i++)
		       world.addEWWall(i, i+1, 1)
		   for (var i = 1; i <= world.getAvenues()-2; i++)
		       world.addNSWall(i, i+2, 1)
 
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

**Помоћ**: Испиши сваку наредбу коју треба да изврши и уочи које се од њих понављају. Колико пута? 
У овом решењу можеш да употребиш две различите петље – за кретање уз зид и за сакупљање лоптица. 

   

