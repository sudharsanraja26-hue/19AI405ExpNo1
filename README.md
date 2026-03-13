<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: SUDHARSAN RAJA</h3>
<h3>Register Number :212224080056 </h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

<h3>Program:</h3>

```
import random

class MedicinePrescribingAgent:
    def __init__(self):
        self.performance = 0
        self.rooms = ["Room 1", "Room 2"]
        self.current_room = self.rooms[0]
        self.environment = {}

    def sense_environment(self):
        temperature = round(random.uniform(97, 102), 1)
        self.environment[self.current_room] = temperature
        return temperature

    def prescribe_medicine(self, temperature):
        print(f"Checking {self.current_room}... Patient temperature: {temperature}°F")
        if temperature > 98.5:
            print(f"Treatment given in {self.current_room}.")
            self.performance += 10
        else:
            print(f"No treatment needed in {self.current_room}.")

    def move_to_other_room(self):
        self.current_room = (
            "Room 2" if self.current_room == "Room 1" else "Room 1"
        )
        print(f"\nMoving from {'Room 1' if self.current_room == 'Room 2' else 'Room 2'} to {self.current_room}...")
        self.performance -= 1

    def run_agent(self, cycles=2):
        print("Medicine Prescribing Agent Simulation Started\n")
        for _ in range(cycles):
            temp = self.sense_environment()
            self.prescribe_medicine(temp)
            self.move_to_other_room()

        print("\nSimulation Complete!")
        print("Final Performance Score:", self.performance)
        print("Environment State:", self.environment)


agent = MedicinePrescribingAgent()
agent.run_agent(cycles=2)
```

<h3>Output:</h3>

Medicine Prescribing Agent Simulation Started

Checking Room 1... Patient temperature: 100.8°F
Treatment given in Room 1.

Moving from Room 1 to Room 2...
Checking Room 2... Patient temperature: 100.1°F
Treatment given in Room 2.

Moving from Room 2 to Room 1...

Simulation Complete!
Final Performance Score: 18
Environment State: {'Room 1': 100.8, 'Room 2': 100.1}

<h3>Result:</h3>

The AI medicine prescribing agent was successfully implemented.
