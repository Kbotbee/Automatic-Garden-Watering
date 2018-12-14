# Automatic-Garden-Watering
A device that waters my house plants and displays data to keep track of the health of the plants using the Arduino
I am refrencing sevral tutorals:
1.Build This DIY Moisture Monitor and Never Kill Another House Plant, from Popular Mechanics by Alexandra Chang
2.Automatic Plant Watering System With Arduino, from Instructables by robotgeek_official
3.Simple Water Level Indicator with Alarm (Tested Circuits), from Electronics Hub by Administrator
4.Arduino Plant Watering System, from Instructables by benrbill

I used:
an arduino
Bucket
6V water pump
Tubing
6 Screw, 2 Nuts, and 2 Ring terminals
Red, Yellow, and green LED
3 BC547 
Resistors 1-10K ohms, 3-2.2K ohms, and 3-100 ohms
A plant
Solder
Adapter to 5V
(If you don't have good sunlight)
Plant friendly light bulb
Plug-in pendant
Plug-in timer

tools:
Hot glue gun
Soldering iron




Growing plants has been a passion of mine since I was a little girl and I helped my mom in the family garden. Over time we got busier and busier, and slowly the garden became less of a priority. Then it abruptly ended when we moved into my grandma’s basement and had no windows.  Living in a basement, the plants I had, some vegetables but mainly herbs, needed to go elsewhere. Relying on others with a lack of green thumb to care for them, and repeatedly killing them became a problem. The two main problems were that they were over watering my plants, resulting in mold problems (then not treating the problem, causing it to spread), and a lack of time for me to check on/ treat them. I wanted to create a watering system using the arduino that could monitor the moisture of the soil and pump water from a reservoir when needed. This would let save me time and help save my plants.
There were several Do it yourself projects that I found on Pinterest. One is a Arduino plant watering system by Benrbill found on the Instructables platform. It is a very simple watering system that uses a mason jar, a Arduino, a moisture sensor and a pump in order to water a small house plant, that could fit on a desk table. The size is convenient for small spaces but my plants are a lot bigger and I have more than this. I would like a larger system but certainly works for a single small plant and is a good starting point. The second project I was looking at was the automatic plant watering system with Arduino by robotgeek_official also on the instructables platform. This system is a lot more complicated than the previous one and it has three plants, it has lights on a timer and it also uses a bucket as it’s water reservoir. The lights are separate from the rest of the system and it has a simple plug-in wall timer to create a day and night shift. The system is considerably bigger and can do multiple plants; it is certainly good for my future goal of automatically caring for my plants. The third project I looked into was “Build this DIY moisture monitor and never kill another house plant” by Alexandra Chang on the platform Popular Mechanics. The system uses an Arduino, Photoresistor, a LCD screen, nuts, bolts, and ring terminals to make up the system. It does not automatically water the plants but has a self made moisture sensor and a light that shines when it needs water. The author references another project called potted plant protector by Luke Iseman which is a very similar system. They also offer even simpler version of the system without an LCD. The final page that I referenced was a water level indicator using simple transistors by Administrator on the like Tronics hub site. This is the only project that does not use the Arduino and is not a watering system. This project is meant it to have a indicator when a cup is beginning to overflow with water. I would, however, like to use the project in reverse to indicate when the bucket is becoming empty. This project uses a BC548 transistor, three LED (red, green, and yellow), metal contacts, and a bunch of resistors. It is very simple and if need be could be a completely external system that is still interactive.
Setting up an area for the system was interesting I needed to have a space with power , a not carpeted floor, and waterworks with plumbing. I found a spot in the corner of the basement because of the lack of natural light I went to the store to get a chord with a plant growth light bulb and a plug-in timer to simulate daytime and night time. Then I had to choose which of my plants would be my guinea pig. The cardinal basil got the choice I repotted him, put in a stick of tomato fertilizer and created and pesticide to take care of the whitefly that was on it and then was ready to go. I started with the system that I felt more confident with which was the bucket. In the bucket I drilled for holes for the four screws that I was going to put in as my metal contacts and soldering wires to each of them. I then used silicon grout sound of the screws to prevent leaking and attached a breadboard to the side. In the breadboard I put in a BC547 along with the three LEDs, Resisters, and wired them all up together. After that I worked on the moisture sensor. Soldered on a couple of wires to two ring terminals (I could only find terminals that were too big), then slipped them onto the two screws and screwed on the nuts. I cut out a rectangle of plastic and poked the screws through. I then hot glue the entire thing to make sure it was secure. This allows to prong of the moisture sensor to be spaced out evenly. For the water pump I made a box for it to sit in and glued it to the side the Bucket. I solder two wires to the prongs on the bottom of the motor. I then added some mini airline tubing (It was the right size) into two of the two water ports and then I figure out which one sucks in the water and which one pushes out the water by plugging it in with tubes in some water. I then marked which way the water flowed on the tubes. I also have a single relay board meant for the pump however I’m not entirely sure how it works and I wasn’t able to figure out the programming for the water pump so this will become a future project. The pump I am using is a 6V well my examples were 12V so it is possible that I do not need the relay; the pump runs on 5V with the Arduino fine.  Then all of the wires can be plugged into the circuit and adrenal ports. Sensors should be plugged into the analog in ports. The entire project would then run off of a Mode electronics adapter that could be plugged into the wall.
When I came to programming Arduino I ran into a bit of a brick wall with the moisture sensor I created. When using a soil sample that I increasingly added water, I noticed the readings was having weirdly fluctuating results. I am not sure if this is because I made it in a way that didn’t work properly or if it was something with how about with programming but the readings fluctuate wildly. The reading was in the end too unsteady for me to make an if statement for. As a result I could not really do the programming for the water pump properly because it needed to react and according to the moisture sensor.
System is mainly a plug in use. Fill the bucket up with water. Put the marked intake tube into the bucket and the marked outtake tube to the plant. Plug the Arduino in and let it run. Check on your plant every now and then. When the bucket is low on water to the point that the indicator light is on read refill.


//initialize variables for sensor pins
int moistPin = A0;
int lightPin = A2;

//initialize variables to store readings from sensors
int moistVal = 0;
int lightVal = 0;

void setup()
{
  //initialize the serial port
  Serial.begin(9600);
}

void loop()
{
  //read values from the sensors
  moistVal = analogRead(moistPin);
  lightVal = analogRead(lightPin);
  
  //display the readings on the serial monitor in a coherent way
  Serial.print("moisture reads ");
  Serial.println(moistVal);
  Serial.print("light reads ");
  Serial.println(lightVal);
  
  //wait one second before continuing. we're doing this so that we don't just see readings fly by the screen
  delay(1000);
}

Iseman, L. (2013, November 21). Potted Plant Protector | Make:. Retrieved December 13, 2018, from https://makezine.com/projects/potted-plant-protector/
