=====
Увод
=====

.. blockly-karel:: Карел_на_поље_33

   {
        setup:function() {
            var world = new World(5,5);
            world.setRobotStartAvenue(1);
            world.setRobotStartStreet(1);
            world.setRobotStartDirection("E");
            world.putBall(3, 3);
            world.addEWWall(1, 1, 2);
            world.addNSWall(2, 2, 2);
            world.addEWWall(2, 3, 3);
            world.addNSWall(3, 1, 2);
            world.addNSWall(3, 4, 1);
            world.addNSWall(1, 5, 1);
            world.addEWWall(4, 1, 1);

            var robot = new Robot();

            var code = ["from karel import *",
                                        "napred()      # idi napred",
                                        "napred()      # idi napred",
                                        "levo()        # okreni se nalevo",
                                        "napred()      # idi napred",
                                        "napred()      # idi napred",
                                        "uzmi()        # uzmi lopticu"];
            return {robot:robot, world:world, code:code};
        },

        isSuccess: function(robot, world) {
           return robot.getStreet() === 3 &&
           robot.getAvenue() === 3 &&
           robot.getBalls() === 1;
        },
   }


.. blockly-karel:: Карел_на_поље_33_грешке
  :categories: KarelCommands, Values

  {
      setup: function() {
           function random(n) {
              return Math.floor(n * Math.random());
           }

           var N = 3 + random(3);
           var world = new World(N, 1);
           world.setRobotStartAvenue(1);
           world.setRobotStartStreet(1);
           world.setRobotStartDirection("E");
           world.putBall(N, 1);
           var robot = new Robot();
           var code = ["from karel import *",
                       "while mozeNapred():",
                       "    napred()",
                       "uzmi()"]
           return {world: world, robot: robot, code: code};
      },

      isSuccess: function(robot, world) {
           var lastAvenue = world.getAvenues();
           return robot.getStreet() === 1 &&
           robot.getAvenue() === lastAvenue &&
           world.getBalls(lastAvenue, 1) == 0;
      }
   }
