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
setup_logging() # output fo the simulation
rng = make_rng_time_seed() # random number generator used for the robot brain
body = make_body() # Creation of a robot body, make_body() shoudl return a BodyV2 object
brain = BrainCpgNetworkNeighborRandom(body=body, rng=rng) # Creation of a robot brain, there are different "brains", here a CPG brain was chosen
robot = ModularRobot(body, brain) # Combine the brain and body into a modular robot
scene = ModularRobotScene(terrain=terrains.flat()) # Creation of modular robot scene
scene.add_robot(robot) # robot is added to the created scene
scene.add_interactive_object(Ball(radius=0.1, mass=0.1, pose=Pose(Vector3([-0.5, 0.5, 0])))) # Additionally to robots you can also add interactive objects to the scene.
simulator = LocalSimulator(viewer_type="native") # What type of mujoco viewer, "native" and "custom"
batch_parameters = make_standard_batch_parameters() # Important parameters for simulation
batch_parameters.simulation_time = 120 #60  # Here we update our simulation time.
simulate_scenes(simulator=simulator, batch_parameters=batch_parameters, scenes=scene)
```
