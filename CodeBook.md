Work performed to clean the data
Step:
#1. Test and Train datasets were consolidated into one dataset, based on the X_train, X_test, y_test and y_train files
#2. Column names were assigned to the columns of the consolidated dataset based on the features text file
#3. The values in the "ACTIVITY" column (sourced from y_train and y_test files) were recoded into more intuitive values based on the "activity_labels" file
#4. The full dataset were subsetted to contain only the measurements on the mean and standard deviation for each measurement
#5. The substrings of the column names of the remaining columns were converted into more intuititive descriptions
#6. The full dataset was split into two datasets, one containing all triaxial signals and one without the triaxial signals
#7. All columns in the datasets mentioned in the previous step, were collapsed into key-value pairs whilst retaining "ACTIVITY" and "SUBJECT_ID" as separate columns
#8a. The "key" generated in the previous step was split into "DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric", "TRIAXIAL_DIRECTION" for the dataset with triaxial signals
#8b. ...and "DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric" for the dataset without measurements on triaxial signals
#9. For both aforementioned datasets the "metric" field contains values for the metric type, i.e. "mean" or "standard deviation". The values of this field where spread across
two columns, i.e. "MEAN" and "ST_DEV"
#10. The two intermediate datasets were merged superfluous fields created in the process, e.g. "metric" were removed. 


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