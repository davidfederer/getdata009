#Set Work Directory
setwd("C:\\Users\\david.federer\\Documents\\Data Science Library\\Coursera\\Getting and Cleaning Data\\UCI HAR Dataset\\")

#Step 1: Merge Test and Training Datasets
#Test and Train datasets are consolidated into one dataset, based on the X_train, X_test, y_test and y_train files

#Step 1a: Read Datasets and Columnbind the Independent and the Response Variables 
X_train <- read.table("train\\X_train.txt")
y_train <- read.table("train\\y_train.txt")
subject_train <- read.table("train\\subject_train.txt")

dat_train <- cbind(X_train, y_train, subject_train)

X_test <- read.table("test\\X_test.txt")
y_test <- read.table("test\\y_test.txt")
subject_test <- read.table("test\\subject_test.txt")

dat_test <- cbind(X_test, y_test, subject_test)

#Step 1b: Consolidate Datasets
dat_all <- rbind(dat_train, dat_test)

#Step 1c: Assign Column Names. Column names are assigned to the columns of the consolidated dataset based on the features text file
features <- read.table("features.txt")
features <- as.character(features[,2])
colnames(dat_all) <- c(features, "ACTIVITY", "SUBJECT_ID") 

#Step 1d: Recode Values in Activity Field. The values in the "ACTIVITY" column (sourced from y_train and y_test files) are recoded into more intuitive values based on the "activity_labels"

activity_labels <- read.table("activity_labels.txt")
dat_all$ACTIVITY <- activity_labels[dat_all$ACTIVITY,2]


#Step 2: Extract Measurements on Mean and Standard Deviation. The full dataset is subsetted to contain only the measurements on the mean and standard deviation for each measurement

index_cols_retained <- c(1,2,3,4,5,6,41,42,43,44,45,46,81,82,83,84,85,86,121,122,123,124,125,126,161,162,163,164,165,166,201,202,214,215,227,240,241,253,254,266,267,268,269,270,271,345,346,347,348,349,350,424,425,426,427,428,429,503,504,516,517,529,530,542,543,562,563)
dat_mean_stdev <- dat_all[, index_cols_retained]

#Step 3. The substrings of the column names of the remaining columns are converted into more intuititive descriptions

new_col_names <- c('Time-BodyAcc-MEAN-X',
                   'Time-BodyAcc-MEAN-Y',
                   'Time-BodyAcc-MEAN-Z',
                   'Time-BodyAcc-ST_DEV-X',
                   'Time-BodyAcc-ST_DEV-Y',
                   'Time-BodyAcc-ST_DEV-Z',
                   'Time-GravityAcc-MEAN-X',
                   'Time-GravityAcc-MEAN-Y',
                   'Time-GravityAcc-MEAN-Z',
                   'Time-GravityAcc-ST_DEV-X',
                   'Time-GravityAcc-ST_DEV-Y',
                   'Time-GravityAcc-ST_DEV-Z',
                   'Time-BodyAccJerk-MEAN-X',
                   'Time-BodyAccJerk-MEAN-Y',
                   'Time-BodyAccJerk-MEAN-Z',
                   'Time-BodyAccJerk-ST_DEV-X',
                   'Time-BodyAccJerk-ST_DEV-Y',
                   'Time-BodyAccJerk-ST_DEV-Z',
                   'Time-BodyGyro-MEAN-X',
                   'Time-BodyGyro-MEAN-Y',
                   'Time-BodyGyro-MEAN-Z',
                   'Time-BodyGyro-ST_DEV-X',
                   'Time-BodyGyro-ST_DEV-Y',
                   'Time-BodyGyro-ST_DEV-Z',
                   'Time-BodyGyroJerk-MEAN-X',
                   'Time-BodyGyroJerk-MEAN-Y',
                   'Time-BodyGyroJerk-MEAN-Z',
                   'Time-BodyGyroJerk-ST_DEV-X',
                   'Time-BodyGyroJerk-ST_DEV-Y',
                   'Time-BodyGyroJerk-ST_DEV-Z',
                   'Time-BodyAccMag-MEAN',
                   'Time-BodyAccMag-ST_DEV',
                   'Time-GravityAccMag-MEAN',
                   'Time-GravityAccMag-ST_DEV',
                   'Time-BodyAccJerkMag-MEAN',
                   'Time-BodyGyroMag-MEAN',
                   'Time-BodyGyroMag-ST_DEV',
                   'Time-BodyGyroJerkMag-MEAN',
                   'Time-BodyGyroJerkMag-ST_DEV',
                   'Frequency-BodyAcc-MEAN-X',
                   'Frequency-BodyAcc-MEAN-Y',
                   'Frequency-BodyAcc-MEAN-Z',
                   'Frequency-BodyAcc-ST_DEV-X',
                   'Frequency-BodyAcc-ST_DEV-Y',
                   'Frequency-BodyAcc-ST_DEV-Z',
                   'Frequency-BodyAccJerk-MEAN-X',
                   'Frequency-BodyAccJerk-MEAN-Y',
                   'Frequency-BodyAccJerk-MEAN-Z',
                   'Frequency-BodyAccJerk-ST_DEV-X',
                   'Frequency-BodyAccJerk-ST_DEV-Y',
                   'Frequency-BodyAccJerk-ST_DEV-Z',
                   'Frequency-BodyGyro-MEAN-X',
                   'Frequency-BodyGyro-MEAN-Y',
                   'Frequency-BodyGyro-MEAN-Z',
                   'Frequency-BodyGyro-ST_DEV-X',
                   'Frequency-BodyGyro-ST_DEV-Y',
                   'Frequency-BodyGyro-ST_DEV-Z',
                   'Frequency-BodyAccMag-MEAN',
                   'Frequency-BodyAccMag-ST_DEV',
                   'Frequency-BodyBodyAccJerkMag-MEAN',
                   'Frequency-BodyBodyAccJerkMag-ST_DEV',
                   'Frequency-BodyBodyGyroMag-MEAN',
                   'Frequency-BodyBodyGyroMag-ST_DEV',
                   'Frequency-BodyBodyGyroJerkMag-MEAN',
                   'Frequency-BodyBodyGyroJerkMag-ST_DEV',
                   'ACTIVITY',
                   'SUBJECT_ID')

colnames(dat_mean_stdev) <- new_col_names
dat_mean_stdev$ID <- 1:nrow(dat_mean_stdev)



#Step 4: Create Independent a Tidy Dataset
#Step 4a: The full dataset is split into two datasets, one containing all triaxial signals and one without the triaxial signals

dat_ind_1 <- dat_mean_stdev[, c(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,66,67,68)]
dat_ind_2 <- dat_mean_stdev[, c(31,32,33,34,35,36,37,38,39,58,59,60,61,62,63,64,65,66,67,68)]

library(tidyr)
library(dplyr)


#Step5. All columns in the datasets mentioned in the previous step, are collapsed into key-value pairs whilst retaining "ACTIVITY" and "SUBJECT_ID" as separate columns. Susequently, a "key" is generated and split into "DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric", "TRIAXIAL_DIRECTION" for the dataset with triaxial signals and "DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric" for the dataset without measurements on triaxial signals.For both aforementioned datasets the "metric" field contains values for the metric type, i.e. "mean" or "standard deviation". The values of this field are spread across two columns, i.e. "MEAN" and "ST_DEV"

dat_ind_cleaned_1 <- dat_ind_1 %>% 
                     gather(mt, value, -c(ID, SUBJECT_ID, ACTIVITY)) %>% 
                     separate(mt, c("DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric", "TRIAXIAL_DIRECTION"), sep="-") %>%
                     spread(metric, value)

dat_ind_cleaned_2 <- dat_ind_2 %>%
                     gather(mt, value, -c(ID, SUBJECT_ID, ACTIVITY)) %>%
                     separate(mt, c("DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "metric"), sep="-") %>%
                     spread(metric, value)



#Step6. The two intermediate datasets are merged superfluous fields created in the process, e.g. "metric" are removed. 

library(gtools)
dat_cleaned <- smartbind(dat_ind_cleaned_1, dat_ind_cleaned_2)
dat_cleaned <- dat_cleaned[,c("SUBJECT_ID", "DOMAIN_SIGNAL_TYPE", "MOTION_COMPONENT", "TRIAXIAL_DIRECTION", "MEAN", "ST_DEV", "ACTIVITY")]

head(dat_cleaned)