# Arduino-Radar
Arduino Radar

Arduino radar project made with a servo motor and ultrasonic sensor. Demonstration can be found at https://drive.google.com/open?id=1UHdlioWGUSu0HkprwKKyJVCmZePkeGMc

The foundation of the program is an object array of size 180 that stores a line for every degree in the semicircle (although only half of the objects in the array are used). 

![image](https://user-images.githubusercontent.com/62212652/81449771-f4472000-914e-11ea-8f93-ad5cf18164bc.png)
![image](https://user-images.githubusercontent.com/62212652/81453698-417bbf80-9158-11ea-8808-eeaa6cdda525.png)

Once an object is detected by the ultrasonic sensor (HC-SR04), the member variable for the red colour value of the detected object associated with the degree at which an object is detected, is set to 250 so that it will appear on the screen. Its x and y coordinates are also set, using the angle ('i' in my code) and distance at which the object is detected. You will notice that each coordinate is multiplied by 15, which is the ratio between pixels on the radar screen and centimetres in the real world. 

![image](https://user-images.githubusercontent.com/62212652/81452132-12634f00-9154-11ea-85ad-e1f61cca976e.png)

The ultrasonic sensor operates by sending out sound waves, and recording how long it takes for them to return. After that, it's simple kinematics to determine how far away the objects are.

![image](https://user-images.githubusercontent.com/62212652/81457275-704b6300-9163-11ea-902e-bbbc0df75a3b.png)

The blurred trail effect on both the radar lines and the red dots happens by simply decreasing the colour values with each increment in degree. The if(i%4==0) ensures that lines will only be drawn at every fourth degree for a more spaced out, cleaner look. 
![image](https://user-images.githubusercontent.com/62212652/81453460-95d26f80-9157-11ea-962e-9e1483911495.png)

The following is the arduino code used to write three pieces of information to the serial monitor, which is then read by processing: the distance of the current object detected, the angle of the servo motor, and whether the servo is going forward or backward.  
![image](https://user-images.githubusercontent.com/62212652/81453944-e72f2e80-9158-11ea-83e1-4dc1f11438d1.png)

We then parse the information into a float array called 'vals.'
![image](https://user-images.githubusercontent.com/62212652/81453980-01690c80-9159-11ea-94d1-3d5377ce72cf.png)

![image](https://user-images.githubusercontent.com/62212652/81454003-104fbf00-9159-11ea-99ba-ca56447bc89b.png)

The following code is included in the setup function to declare the port that we're reading from, and states that the serialEvent function will execute every time there is a line break in the serial monitor. 
![image](https://user-images.githubusercontent.com/62212652/81456712-67599200-9161-11ea-8b92-77773d0f3778.png)

These are the main components of the program. Contact me at d352wang@uwaterloo.ca if you have further questions!
