# hashcode
```python
# Remove hard coded constants (for intersection.number)
class Car():
	# start = ''
	# destination = ''
	street_counter = 1
	pos = 0
	current_street = ''
	streets = [] #street a car wants to pass
	travel_time = 0

	def __init__(self, street_to_travel):
		# self.start = street_to_travel[0]
		self.pos = street_to_travel[0].time
		self.current_street = street_to_travel[0]
		self.streets = street_to_travel

	# def startDrive(self):
	# 	for s in self.streets:
	# 		self.travel_time +=s.time
	# 	print("car travelled and takes time:", self.travel_time)

	
	# for normal condition 
	def startDrive(self):
		self.travel_time +=1
		
		print(self.streets[-1:][0].name)
		if(self.current_street ==self.streets[-1:][0]):
			print("wohoo")
			self.travelTime()
			return 
		
		if(self.pos ==0):
			if(self.current_street.traffic_light):#check if street have light
				if(self.current_street.traffic_light.color):
					self.current_street = self.streets[self.street_counter]
					self.street_counter+=1
					self.pos = self.current_street.time-1	
			else:
				self.current_street = self.streets[self.street_counter]
				self.street_counter+=1
				self.pos = self.current_street.time-1
				
		else:
			self.pos-=1

	def travelTime(self):
		print("car travelled and takes time:", self.travel_time)


class TrafficLight():
	color = True
	time = 0.0

	curr_iter = 0
	def changeColor(self):
		# self.curr_iter +=1
		# if(curr_iter%time==0):
		
		# 	if self.color == False:
		# 		self.color = True
		# 	else:
		# 		self.color = True
		pass
		

class Intersection():
	intersection_number =0
	incoming_streets = []
	
	def updateLights(self):
		for i in incoming_streets:
			i.traffic_light.time +=1

	# outgoing_streets = []

class Street():
	name = ""
	time = 0

	beginig = 0
	ending = 0
	traffic_light = 0

	def __init__(self, b, e, name, time):
		self.beginig = b
		self.ending = e
		self.name = name
		self.time = time

	def associateLight(self, time):
		pass


# class City():
# 	street_intersection = [[0,"a",1],[2,"b",1],[1,"c",3]]



# Functions
def cityBuilder(b, e, name, l):
	s = Street(b,e,name, l)
	city.append(s)


def traficLightBuilder(city):
	count_b = []
	count_e = []
	count = 0

	dick = {}
	for index, i in enumerate(city):
		for indexj, j in enumerate(city):
			if i.ending == j.ending and index !=indexj:
				if i.name in dick:
					print("if main aya")
					dick[i.name]+=1
				else:
					t_light = TrafficLight()
					t_light.time = 1
					i.traffic_light = t_light
					intersection = Intersection()
					intersection.intersection_number =1 
					intersection.incoming_streets.append(i)
					dick[i.name] = 1
					
	for i in count_b:
		count +=1

	print(dick)
	print(intersection.incoming_streets)
	return city




# Driver code
if __name__ == "__main__":
	city = []

	# first line generic inputs==========================
	ip_arr = [int(x) for x in input().split(" ")]

	# mapping inputs
	d = ip_arr[0]
	i = ip_arr[1]
	s = ip_arr[2]
	v = ip_arr[3]
	f = ip_arr[4]


	# S line inputs=======================================
	for i in range(0, s):
		s_inputs = [x for x in input().split(" ")]
		b = int(s_inputs[0])
		e = int(s_inputs[1])
		street_name = str(s_inputs[2])
		l = int(s_inputs[3])
		cityBuilder(b, e, street_name, l)

	city = traficLightBuilder(city)


	# Inputs for street to travel for car===================
	ip = input().split(" ")
	street_to_travel = []
	for i in city:
		for j in ip:
			if i.name == j:
				street_to_travel.append(i)
	
	for i in street_to_travel:
		print(i.name, i.traffic_light)
	# Let's drive the car and simulation=====================
	ferrari = Car(street_to_travel)
	

	I = Intersection()
	time = 0
	while(time <9):
		# I.updateLights()
		ferrari.startDrive()
		time+=1
	ferrari.travelTime()

# SAMPLE INPUTS
'''
6 4 5 2 1000
2 0 rue-de-londres 1
0 1 rue-d-amsterdam 1
3 1 rue-d-athenes 1
2 3 rue-de-rome 2


1 2 rue-de-moscou 3
4 rue-de-londres rue-d-amsterdam rue-de-moscou rue-de-rome
3 rue-d-athenes rue-de-moscou rue-de-londres
'''
print(city[1].traffic_light, city[1].name)
```
