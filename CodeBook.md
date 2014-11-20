
Data Dictionary


SUBJECT_ID		2
	Subject Identifier. Used to identify the 30 volunteers who participated in the experiment
		1..30 .Integer

DOMAIN_SIGNAL_TYPE	9
	Domain Signal Type
		Time: Time Domain Signal
		Frequency: Frequency Domain Signal

MOTION_COMPONENT	19
	Body and Gravitational Motion Components
		BodyAcc: Linear Acceleration of the Body
		BodyAccJerk: Linear Acceleration of the Body with Jerk Signals
		BodyGyro: Horizontal, Lateral and Vertical Body Movements
		BodyGyroJerk: Horizontal, Lateral and Vertical Body Movements with Jerk Signals
		GravityAcc: Gravity Acceleration 
		BodyAccMag: Magnitude of Linear Acceleration of the Body
		BodyBodyAccJerkMag: Magnitude of Linear Acceleration of the Body-to-Body with Jerk Signals 
		BodyBodyGyroJerkMag: Magnitude of Horizontal, Lateral and Vertical Body-to-Body Movements With Jerk Signals
		BodyBodyGyroMag: Magnitude of Horizontal, Lateral and Vertical Body-to-Body Movements
		BodyAccJerkMag: Magnitude of Linear Acceleration of the Body with Jerk Signals
		BodyGyroJerkMag: Magnitude of Linear Acceleration of the Body With Jerk Signals
		BodyGyroMag: Magnitude of Horizontal, Lateral and Vertical Body Movements
		GravityAccMag: Magnitude of Gravity Acceleration 

THREE_AXIAL_DIRECTION	1
	Axial Direction of the Raw Signal
		X: Signal in the X direction
		Y: Signal in the Y direction
		Z: Signal in the Z direction

MEAN			14
	Average for Each Measurement
		-1..1 Decimal

ST_DEV			14
	Standard Deviation for Each Measurement
		-1..1 Decimal	

ACTIVITY		18
	Activity Label. "Activity" is the response variable
		WALKING: Subject is walking normally
		WALKING_UPSTAIRS: Subject is walking upstairs
		WALKING_DOWNSTAIRS:
 Subject is walking downstairs
		SITTING
: Subject is sitting
		STANDING: Subject is standing
		LAYING
: Subject is laying