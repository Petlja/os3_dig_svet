
Аритметичке и логичке операције
===============================

.. questionnote::

 Које су основне аритметичке операције? Које су ознаке за њих у математици? 
 Како су ове операције означене на калкулатору?

Осим што сакупља и преноси лопте, Карел је и одличан математичар и може да ти помогне да провериш своја решења. 
Овако изгледа када он то ради. Покрени следећи програм!

.. blockly-karel:: karel_p5  
  :categories: KarelSays, Arithmetic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();

				var domXml ='<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="text_print" id="@OqW3Km%2aBKWZj4[DE9" x="112" y="109">\n    <value name="TEXT">\n      <block type="math_arithmetic" id="s70^]$T8j[/nMz3bk;QD">\n        <field name="OP">MINUS</field>\n        <value name="A">\n          <block type="math_number" id="D`*QH`zjCV5[|FhHsdN+">\n            <field name="NUM">112</field>\n          </block>\n        </value>\n        <value name="B">\n          <block type="math_number" id="0!~!tXZ=waR!_e.dW-|3">\n            <field name="NUM">13</field>\n          </block>\n        </value>\n      </block>\n    </value>\n  </block>\n</xml>';
                
				return {robot:robot, world:world, domXml:domXml};
            },
            isSuccess: function(robot, world) {
               return robot.getLastMessage() == 99 
            },
  }

.. suggestionnote:

 Ако добијеш нетачан или нелогичан резултат, блокови нису добро сложени или нису постављене вредности/операције које су тражене у задатку!

Пример:
-------

**Састави блокове за израчунавање производа бројева 78 и 9**

.. blockly-karel:: karel_p6  
  :exportmode:
  :categories: KarelSays, Arithmetic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
   
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == 702
            },
  }

Када треба да провери неки рачун, Карел користи блокове из групе ``Аритметика``. 

У овој групи се налазе два блока – блок помоћу којег уносиш вредности (операнде, бројеве са којима рачунаш) и блок 
за операцију. 

Превуци блок за операцију (доњи блок) у простор за слагање! 

Када кликнеш на стрелицу поред знака плус, 
појавиће се и остале операције које можеш да изабереш. Ознаке за сабирање и одузимање су у овом окружењу 
исте као у математици, x je ознака за множење, ÷ за дељење, а последња ознака је за степеновање 
(то ћеш учити у старијим разредима).

Изнад овог блока налази се блок за унос вредности (тренутно стоји вредност нула). 
Превуци два оваква блока у простор за слагање и убаци их у отворе са 
леве и десне стране знака операције (претходно превученог блока).

Сада у простору за слагање блокова стоји израз ``0 + 0``.

Измени вредности као што је речено у тексту задатка (кликни на прву нулу и укуцај број 78, другу нулу на исти начин замени бројем 9) и промени знак
``+`` у ``x``. 

Да би Карел исписао резултат, потребно је да му то и кажемо. У групи ``Поруке роботу`` налази се наредба ``испиши``. 

Повежи блок испред претходно сложеног израза.

Покрени програм! 

Појавиле су се две поруке - прва је резултат математичког израза који је састављен, а друга потврђује да је резултат који смо очекивали исправан. 


.. questionnote::

 Поред аритметичких операција, у математици се користе и операције поређења. Које су то операције?
 
Операције поређења се у Кареловом свету налазе у групи ``Логичке операције``. Помоћу њих се праве логички изрази, 
који као вредност могу да врате ``Тачно`` или ``Нетачно``.

Кликни на групу ``Логички оператори`` и превуци први блок (са ознаком ``=`` у средини) у простор за слагање. Кликни на 
стрелицу поред знака једнако и погледај које све операције можеш да користиш. Означене су исто као и у математици. 
(знак ``≠`` користиш када провераваш да ли је вредност са леве стране различита од вредности са десне стране овог знака). 

Са леве и десне стране знака поређења можеш да убацујеш вредности или целе изразе (као из претходног примера) и да их међусобно поредиш.

.. suggestionnote::

 Када желиш да упоредиш два израза, прво са стране састави блокове за њих, па их тек онда убаци у блок за поређење, у отворе са 
 леве и десне стране знака. Рачунар ће прво израчунати једну вредност, затим другу и тек онда ће да упореди њихове резултате.

Погледај следећи пример, покрени га и по узору на њега уради задатке који следе.

Пример
------

**Провери да ли је 325 веће од збира бројева 48 и 286**


.. blockly-karel:: karel_p7 
  :categories: KarelSays, Arithmetic, Logic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                var domXml = '<xml xmlns="https://developers.google.com/blockly/xml">\n  <block type="text_print" id="./k=Op.P-]Of^K6^PNYn" x="33" y="141">\n    <value name="TEXT">\n      <block type="logic_compare" id="Az;KBd4,{p*H?.vtu)|Z">\n        <field name="OP">GT</field>\n        <value name="A">\n          <block type="math_number" id="l^X,KI,q+D5yU5bRR;Yt">\n            <field name="NUM">325</field>\n          </block>\n        </value>\n        <value name="B">\n          <block type="math_arithmetic" id="pOeI*XBU3FOq*ljILsOD">\n            <field name="OP">ADD</field>\n            <value name="A">\n              <block type="math_number" id="GsZc9wXC|w;|8+Uy[23y">\n                <field name="NUM">48</field>\n              </block>\n            </value>\n            <value name="B">\n              <block type="math_number" id="V7c,kPAKH=aQYCa?12_+">\n                <field name="NUM">286</field>\n              </block>\n            </value>\n          </block>\n        </value>\n      </block>\n    </value>\n  </block>\n</xml>';
                return {robot:robot, world:world, domXml:domXml};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == false
            },
  }


Прва порука ``нетачно`` даје резултат (325 није веће од 48 + 286), а друга друга значи да је добијени резултат у складу са текстом овог примера, да су блокови добро сложени.

Задатак 12
----------

**Састави блокове за решавање следећег задатка:  140 : 10 - 2** 

.. blockly-karel:: karel_z12 
  :categories: KarelSays, Arithmetic, Logic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == 12
            },
  }
  

**Помоћ**: Обрати пажњу на приоритет операција. Прво стави у један блок 140 : 2. Затим узми нови блок и подеси операцију одузимање.
Са леве стране убаци 140:2, а са десне 2


Задатак 13
----------

**Састави блокове за решавање следећег задатка:  140 : (10 - 3)** 

.. blockly-karel:: karel_z13 
  :categories: KarelSays, Arithmetic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == 20
            },
  }
  
**Помоћ**: Задатак је врло сличан претходном, али сада имаш заграду. У блоку за дељење са 
једне стране треба да стоји 140, а са друге израз који је написан у загради (састави га прво негде са стране).

Задатак 14
----------

**Састави блокове за решавање следећег задатка: Од збира бројева 47 и 93 одузми производ бројева 30 и 3.**

.. blockly-karel:: karel_z14 
  :categories: KarelSays, Arithmetic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == 50
            },
  }
  
Задатак 15
----------

**Састави блокове за решавање следећег задатка: Маја има 75 сличица, а Мирко за 19 више. Колико сличица заједно имају Маја и Мирко?**

.. blockly-karel:: karel_z15 
  :categories: KarelSays, Arithmetic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == 169
            },
  }
  
Задатак 16
----------

**Марко је за домаћи задатак требало да провери да ли је тачан следећи израз: (125 + 5) + 270 > 363. Марко је рекао да јесте. Састави програм за овај израз и питај Карела да ли је Марко у праву.**

.. blockly-karel:: karel_z16   
  :categories: KarelSays, Arithmetic, Logic

  {
            setup:function() {
                var world = new World(3,3);
                world.setRobotStartAvenue(2);
                world.setRobotStartStreet(2);
                world.setRobotStartDirection("S");;
                var robot = new Robot();
                return {robot:robot, world:world};
            },
			
            isSuccess: function(robot, world) {
              return robot.getLastMessage() == true
            },
  }