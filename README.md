# NINTH-CLASS

## TOPIC
- bluetooth connection
### CODE
1. #include <SoftwareSerial.h> //
2. SoftwareSerial BTSerial(12, 13);   //12-TX    IMPORTANT!! TX of BTS serial is connected to RX of Serial, RX of BTS serial is connected to TX of Serial (RX is received, T of TX is transmit)
3. int motor1PinA  = 2 ;              //connect to pin2
4. int motor1PinB =3 ;                 //connect to pin3
5. int enableRPin=  11 ; // RIGHT, the motor 1 Pin is the motor on the right
6. int motor2PinA  = 4 ;                 //connect to pin4
7. int motor2PinB =5;                    //connect to pin5
8. int enableLPin=  10 ; //left, the motor 2pin is the motor on the left
9. char in;                                 //Specify a variable 
10. void setup() {   
11. pinMode(motor1PinA, OUTPUT);     //use motor1PinA as an output (result)
12. pinMode(motor1PinB, OUTPUT);     //use motor1PinB as an output (result)
13. pinMode(enableLPin, OUTPUT);     //use enableLPin as output (result)
14. pinMode(motor2PinA, OUTPUT);    //use motor2PinA as an output (result)
15. pinMode(motor2PinB, OUTPUT);     //use motor2PinB as an output (result)
16. pinMode(enableRPin, OUTPUT ;      //use enableRPin as output (result)
17. analogWrite(enableRPin, 100);//set the speed of the motor(maximum is 255)
18. analogWrite(enableLPin, 100);//set the speed of the motor(maximum is 255)
19. Serial.begin(9600);
20. BTSerial.begin(9600); //Initialize Bluetooth data rate 
21. }
22. void loop() {
23. if (BTSerial.available()) //if you receive data through Bluetooth,
24. Serial.write(BTSerial.read()); //send data from Bluetooth to the RX pin on the serial port, and output the received data to the PC serial window
25. if (Serial.available())//If you enter the data that came into the serial monitor window and send it, 
26. BTSerial.write(Serial.read());// output data sent via Bluetooth to your smartphone
27. if (BTSerial.available())
28. { in =BTSerial.read();
29. Serial.write(in);
30. }
31. if (Serial.available()) 
32. {  BTSerial.write(Serial.read());
33. Serial.print("data =");
34. Serial.println(in);
35. }
36. switch(in){
37. case 'F':Forward(); break;
38. case 'R': Right(); break; 
39. case 'S': Stop(); break;
40. case 'L': Left(); break;
41. case 'B': Back(); break;
42. case 'G': FowardLeft(); break;
43. case 'I': FowardRight(); break;
44. case 'H': BackLeft(); break;
45. case 'J':BackRight();break;
46. } 
47. }  
48. void Forward(){  //  FRONT
49. analogWrite(enableRPin, 255);
50. analogWrite(enableLPin, 255);
51. digitalWrite(motor1PinA, HIGH);
52. digitalWrite(motor1PinB,LOW);
53. digitalWrite(motor2PinA,HIGH);
54. digitalWrite(motor2PinB,LOW);
55. }
56. void Right(){ //  RIGHT
57. analogWrite(enableRPin, 255);
58. analogWrite(enableLPin, 255);
59. digitalWrite(motor1PinA, LOW);
60. digitalWrite(motor1PinB,LOW);
61. digitalWrite(motor2PinA,HIGH);
62. digitalWrite(motor2PinB,LOW);
63. }
64. void Left(){ //  LEFT
65. analogWrite(enableRPin, 255);
66. analogWrite(enableLPin, 255);
67. digitalWrite(motor1PinA, HIGH);
68. digitalWrite(motor1PinB,LOW);
69. digitalWrite(motor2PinA,LOW);
70. digitalWrite(motor2PinB,LOW);
71. }
72. void Stop(){  //  STOP
73. analogWrite(enableRPin, 255);
74. analogWrite(enableLPin, 255);
75. digitalWrite(motor1PinA, LOW);
76. digitalWrite(motor1PinB,LOW);
77. digitalWrite(motor2PinA,LOW);
78. digitalWrite(motor2PinB,LOW);
79. }
80. void Back(){  //  BACK
81. analogWrite(enableRPin, 255);
82. analogWrite(enableLPin, 255);
83. digitalWrite(motor1PinA, LOW);
84. digitalWrite(motor1PinB,HIGH);
85. digitalWrite(motor2PinA,LOW);
86. digitalWrite(motor2PinB,HIGH);
87. }
88. void FowardRight(){  //  RIGHT 45 ANGLE
89. analogWrite(enableRPin,100);
90. analogWrite(enableLPin, 255);
91. digitalWrite(motor1PinA, HIGH);
92. digitalWrite(motor1PinB,LOW);
93. digitalWrite(motor2PinA,HIGH);
94. digitalWrite(motor2PinB,LOW);
95. }
96. void FowardLeft(){  //  LEFT 45 ANGLE
97. analogWrite(enableRPin, 255);
98. analogWrite(enableLPin, 100);
99. digitalWrite(motor1PinA, HIGH);
100. digitalWrite(motor1PinB,LOW);
101. digitalWrite(motor2PinA,HIGH);
102. digitalWrite(motor2PinB,LOW);
103. }
104. void BackLeft(){// LEFT BACK 45 ANGLE
105. analogWrite(enableRPin, 255);
106. analogWrite(enableLPin, 100);
107. digitalWrite(motor1PinA,LOW);
108. digitalWrite(motor1PinB,HIGH);
109. digitalWrite(motor2PinA,LOW);
110. digitalWrite(motor2PinB,HIGH);
111. }
112. void BackRight(){// RIGHT BACK 45 ANGLE
113. analogWrite(enableRPin,100);
114. analogWrite(enableLPin, 255);
115. digitalWrite(motor1PinA,LOW);
116. digitalWrite(motor1PinB,HIGH);    
117. digitalWrite(motor2PinA,LOW);
118. digitalWrite(motor2PinB,HIGH);
119. }
