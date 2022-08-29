
Линијски програми
=================

Пре него што наставимо, покушај самостално да решиш следећи задатак. Овог пута у лавиринту се налази једна лоптица више!

Задатак 1
---------

Помози Карелу да сакупи обе лоптице!

.. blockly-karel:: karel_z1
  :flyouttoolbox:
  :categories: BeginnerKarelCommands
  
  {
      setup: function() {
           var world = new World(5, 5);
		   world.addNSWall(1, 1, 4)
		   world.addNSWall(2, 1, 3)
		   world.addEWWall(2, 4, 4)
		   world.addEWWall(3, 3, 3)
           world.setRobotStartAvenue(2);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("N");
           world.putBall(2, 3);
		   world.putBall(5, 4);
           var robot = new Robot();
           return {world: world, robot: robot};
      },
	  
      isSuccess: function(robot, world) {
        return robot.getBalls() == 2;   
      }
   }
   
У претходна два програма блокови били поређани један испод другог, као да продужаваш линију док их слажеш. Овакви програми називају се **линијски**.

.. infonote::

 **Линијски програми** су програми код којих су све наредбе написане једна испод друге.

 
Задатак 2
---------

Карел жели да сакупи лоптице које се налазе у два реда лавиринта. Обрати пажњу, на гомили у другом реду налазе 
се две лоптице (потребно је да два пута узастопно поновиш наредбу ``узми`` када дођеш до те гомиле).

.. blockly-karel:: karel_z2
  :flyouttoolbox:
  :categories: BeginnerKarelCommands
  
  {
      setup: function() {
           var world = new World(5, 5);
		   world.addEWWall(1, 1, 4)
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           world.putBall(3, 1);
		   world.putBall(4, 1);
		   world.putBalls(2, 2, 2);
           var robot = new Robot();
           return {world: world, robot: robot};
      },
	  
	  isSuccess: function(robot, world) {
        return robot.getBalls() == 4;   
           
      }
   }
   
.. reveal::  Задатак2
   :showtitle: Предлог решења   
   :hidetitle: Затвори
	
   Предлог решења
 
   .. image:: ../../_images/zadatak2_blokovi.png
     :width: 780
     :align: center


Током превлачења блокова може да се деси да их погрешно поставиш. 

.. infonote::

 Када кликнеш на било који (већ превучен) блок десним тастером миша, добићеш две опције: ``Дуплирај`` и ``Избриши блок``. 
 Прва опција ће направити још један такав блок, а друга ће га избрисати.
 
Постоји још један начин да избришеш блок:
 
Кликни на блок који желиш да избришеш. Постаће уоквирен жутом линијом. Када притиснеш тастер *Delete* на тастатури, 
изабрани блок ће нестати.


Задатак 3
--------- 

Марко је хтео да помогне Карелу, превукао је неколико блокова, али је морао да крене у школу! Сложи припремљене блокове и провери да ли ће 
Карел успети да дође до лопте и узме је. Ако је потребно, избриши блок који је вишак или додај неки ако недостаје!

.. blockly-karel:: karel_z3
  :flyouttoolbox:
  :categories: BeginnerKarelCommands

   {
        setup:function() {
            var world = new World(5,5);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(1, 3);
            world.addEWWall(1, 1, 2);
            world.addEWWall(2, 3, 3);
            world.addNSWall(3, 1, 2);
            world.addNSWall(3, 4, 1);
            world.addNSWall(1, 5, 1);
            var robot = new Robot();
            var domXml = '<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="move" id="^c,s6?}@%hfN~%l{L^4]" x="437" y="88"></block>\n  <block type="move" id="v((;N^?~/DPk?PtcD!rH" x="63" y="123"></block>\n  <block type="turn_left" id="8ot[uBd,stAEC4|/E7}o" x="298" y="147"></block>\n  <block type="pick_up" id="u;=%D4uiqat3FDWes#=P" x="42" y="189"></block>\n  <block type="move" id="8jzM+{4K7b6%3,D_tpyl" x="181" y="203"></block>\n  <block type="turn_right" id="3QvO+QuL$beiAIhQN/Qg" x="479" y="198"></block>\n  <block type="move" id="[;1x]bR043wC(UJQ:[$6" x="283" y="299"></block>\n  <block type="turn_left" id="s3fOMprumtO,.x/?fyNO" x="61" y="313"></block>\n  <block type="move" id=":.jI_,|BH6syiWlrrUNe" x="393" y="375"></block>\n  <block type="move" id="=fvSp9pM2-te1KdOu3Rd" x="201" y="433"></block>\n</xml>';
            return {robot:robot, world:world, domXml:domXml};
        },

        isSuccess: function(robot, world) {
           return robot.getAvenue() == 1 &&
		   robot.getStreet() == 3 &&
           robot.getBalls() == 1;
        }
   }

.. questionnote:: 

 Присети се и комбинација које си учио у Ворду (*Ctrl+C*, *Ctrl+X*, *Ctrl+V*), Кликни на неки блок и тако га селектуј. 
 Притисни на тастатури ове комбинације. Да ли можеш да их употребиш и у овом окружењу?
 
Задатак 4
---------  

На овај задатак ћемо се вратити нешто касније. За сада само помози Карелу да узме обе лоптице!
 
.. blockly-karel:: karel_z4
  :flyouttoolbox:
  :categories: BeginnerKarelCommands
  
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
           return robot.getAvenue() == 5 && 
		   robot.getStreet() == 5 &&
           robot.getBalls() == 2;
      }
   }
 
 
У лавиринту се налазе и рупе у које Карел оставља своје лопте када му нису потребне. 
Осим корака напред, скретања лево и десно и узимања лопте, наш робот зна и како да спусти (остави) лопту.

Карел је повезао још једну ствар: када се два пута узастопно окрене за по 90 степени, укупно ће се окренути за 180 степени.

.. questionnote::
 
 Колико степени има цео круг? А полукруг? 
 
.. infonote::

 Када Карел прими наредбу ``остави``, спустиће лопту. Наредба ``окрени полукружно`` значи да треба да се окрене за 180 степени.


Пример
------ 

.. blockly-karel:: karel_p2
  :flyouttoolbox:
  :categories: KarelCommands
  
  {
      setup: function() {
           var world = new World(5, 5);
           world.setRobotStartAvenue(3);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("S");
           world.putBall(5, 1);
		   world.putHole(1, 1);
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
 
.. reveal::  Пример2
   :showtitle: Предлог решења   
   :hidetitle: Затвори
	
   Предлог решења
 
   .. image:: ../../_images/primer2_blokovi.png
     :width: 780
     :align: center
	 
.. questionnote::

 Из Природе и друштва учио си стране света. Које су основне стране света и како се одређују? Где се на географској карти 
 налази север, а где југ?

Задатак 5
---------

Карел треба да убаци у рупу лоптицу која се налази западно од њега. Која је то рупа? Састави програм!

.. blockly-karel:: karel_z5
  :flyouttoolbox:
  :categories: KarelCommands
  
  {
      setup: function() {
           var world = new World(5, 5);
           world.setRobotStartAvenue(3);
           world.setRobotStartStreet(3);
           world.setRobotStartDirection("N");
           world.putHole(4, 3);
		   world.putBall(3, 1);
		   world.putBall(1, 3);
		   world.putBall(5, 3);
           var robot = new Robot();
          
           return {world: world, robot: robot};
      },
	  
        isSuccess: function(robot, world) {
           for (var i = 1; i <= world.getAvenues(); i++)
              for (var j = 1; j <= world.getStreets(); j++)
                 if (!(world.getBalls(i, j) == 2 || world.getBalls(1, 3) == 0))
                    return false;
          return true;
      }
   }