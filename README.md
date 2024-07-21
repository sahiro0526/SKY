from spike import PrimeHub, DistanceSensor, Motor
motor1 = Motor('D')
motor2 = Motor('E')
distance_sensor1 = DistanceSensor('A')
distance_sensor2 = DistanceSensor('F')
def CLOCK():
 X=1
 while True:
  motor1.start(speed=-90)
  distance_sensor1.wait_for_distance_closer_than(distance=35,unit='cm')
  motor1.stop()
  motor2.run_to_position(29)
  motor1.run_for_seconds(1.98,speed=-100) 
  motor2.run_to_position(0)
  motor1.start(speed=90)
  distance_sensor1.wait_for_distance_farther_than(distance=50,unit='cm')
  motor1.stop()
  X=X+1
  if X==13:
    motor1.stop()
    break
def UNCLOCK():
 X=1
 while True: 
  motor1.start(speed=-90)
  distance_sensor1.wait_for_distance_closer_than(distance=40,unit='cm')
  motor1.stop()
  motor2.run_to_position(332)
  motor1.run_for_seconds(1.21,speed=-100)
  motor2.run_to_position(0)
  motor1.start(speed=90)
  distance_sensor1.wait_for_distance_farther_than(distance=40,unit='cm')
  motor1.stop()
  X=X+1
  if X==13:
    motor1.stop()
    break
dist2_cm=distance_sensor2.get_distance_cm()
print(dist2_cm)
motor2.run_to_position(0)
if dist2_cm<30:
 CLOCK()
else:
  UNCLOCK()
