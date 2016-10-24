#RC Painter

## Challenge 1:

Paint a kitchen wall Imagine that you have an RC car that is able to roll on walls.
You attach a painting roll and a little reservoir of paint on the car to paint the wall of your kitchen. How would you automate the painting process?

### General assumptions:

You can pick where you initially place the car - There is enough paint in the reservoir to paint the whole wall without refill

### Deliverable:

Think about the type of sensors and processing you would want onboard, as well as an overall idea of your algorithms architecture. No need for actual code at this time. We’re just trying to kick-start a conversation.

## Assumptions:

1. The wall is rectangular.
2. The paint roller is equal to the width of the car.
3. The paint roller is attached to the back of the car.
4. The car should end near the bottom of the wall so that it can be retrieved.
5. We know the size of the wall and the height and width are greater than 2 times the size of the car.

## Considerations:

1. The car turns around a radius, causing a circular stroke of paint.
2. Any wet paint the car drives over should be repainted.
3. The amount of paint used should be minimized.

## Setup:

The care will have 5 sensors:
* 1 sensor on the front to detect how far from the edge of the wall the car is.
* 2 sensors on either side of the car to measure it's distance from the bottom edge.
* 2 sensors on either side of the car to detect whether paint along it's edge is dry.

## Approach:

### From the perspective of facing the wall.
### 1 unit = width and height of car + paint roller

* We initially place the car starting at the top left-hand corner of the wall, 1 unit right of the edge facing the right.

* The car begins by backing up and painting the very top left-hand corner of the wall.

* The car continues by driving right and turns downward upon getting near the right edge(using a proximity sensor).

* Every time the car makes a 90 degree turn, it should back up(1 unit) in order to completely paint the unit of wall it used to make the turn.

* The car then continues another 90 degrees until it is facing the left edge -- once again backs up to completely fill the unit of wall that was used for the turn.

* As every turn is made, proximity sensors on either side of the vehicle will alert the vehicle upon reaching a distance of less than 2 units from the bottom of the wall.

..* It begins with the proximity sensor on the right of the car measuring the distance and the sensor on it's left to check for dryness of paint, upon turning the sensors switch and the left sensor measures distance and the right measures dryness.

..* If this is the case, the next turn made by the car should result in the car being (distance from wall - 1 unit) from the bottom. This is to ensure that the final path the car takes is the width of the car.

* Once the car is against the bottom edge of the wall it should stop within one 1 of reaching either the left or right edge depending on which direction the car results in.

* At this point a sensor should alert the car whether the paint on the wall above the car is dry.
..* Once that paint it dry the car can make it's final maneuver of turning, backing into the corner, then moving forward.

* The wall is now painted and the car can be retrieved.

## Demo:
Here is a video demonstrating the cars travel path (apologies for the low quality): [Pathing demo](https://www.youtube.com/watch?v=VKIs81gYPeo)
