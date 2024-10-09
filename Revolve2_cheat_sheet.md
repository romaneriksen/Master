# Create a robot body
- A modular robot follows a tree structure, with a "center core" as the parent node
```
body = BodyV2() # Creates the center core
```
- There are two different parts that one can attach to the core, a hinge and a brick, and these can also be attached to each other.
- These modules can also be attatched in a rotated fashion
```
body.core_v2.left_face.bottom = ActiveHingeV2(RightAngles.DEG_0) # Attatches a hinge to the core on the left?
body.core_v2.left_face.bottom = BrickV2(RightAngles.DEG_0) # Attatches a brick to the core on the left?
```
# main() method to run the simulation
```
# output for the simulation
setup_logging()

# random number generator used for the robot brain
rng = make_rng_time_seed()

# Creation of a robot body, make_body() shoudl return a BodyV2 object
body = make_body()

# Creation of a robot brain, there are different "brains", here a CPG brain was chosen
brain = BrainCpgNetworkNeighborRandom(body=body, rng=rng)

# Combine the brain and body into a modular robot
robot = ModularRobot(body, brain)

# Creation of modular robot scene
scene = ModularRobotScene(terrain=terrains.flat()) 
scene.add_robot(robot) # robot is added to the created scene

# Additionally to robots you can also add interactive objects to the scene.
scene.add_interactive_object(Ball(radius=0.1, mass=0.1, pose=Pose(Vector3([-0.5, 0.5, 0]))))

# What type of mujoco viewer, "native" and "custom"
simulator = LocalSimulator(viewer_type="native")

batch_parameters = make_standard_batch_parameters() # Important parameters for simulation
batch_parameters.simulation_time = 120 #60  # Here we update our simulation time.

# Simulate the scene
simulate_scenes(simulator=simulator, batch_parameters=batch_parameters, scenes=scene)
```
