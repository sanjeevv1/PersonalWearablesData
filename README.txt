README file

This file takes as input the data and codebooks supplied from the Samsung wearables project provided as a zip
file. Files in the zip file were extracted and stored in the directory "UCI HAR Dataset" which is a sub directory of 
my working directory. This directory has the codebook and other descriptive files and has two further sub directories "test" 
and "train" which contain the test and the training data from the project.

This code was written to read the data from the "test" and "train" subdirectories. But the code that I am submitting assumes that
the ALL the data (both for test and train, as well as the descriptive "activity labels" file is in the working directory itself as
specified in the rubric for the project.

1. This code reads the test data as well as the training data measurements (please see the codebooks that come with the supplied data), as well
as the non-measurement data pertaining to the Activity and Subject. The Activity and Subject data is merged with the test and traiing data. Then
the test and training data are merged together to yield one data set. The test and training data have 561 variables/columns, Activity and Subject have
one column each, so the total mergd dataset has 563 columns.

2. From these 563 columns I have extracted the data pertaining to the mean and standard deviation only. There were 53 columns for mean and 33 columns
for standard deviation in the measurement data of 561 columns. So from the dataset yielded in Step 1, 86 columns of measurement data as well
as one column of Subject and activity data were extracted for a total 88 columns. To figure which of the 561 columns in Step 1 had to be
extracted, I loaded the features.txt file which contained the column names into Excel and looked up all the columns that had "mean"(mean)
and standard deviation (std) in the column names. I also used global find and replace to clean up the column names by removing all commas,dashes
parenthesis etc. from the names and fave them some English names and made them conform to Pascal case notation to make it easier to read
the column names and know what they signify. Then I imported the column numbers to be extracted and their cleaned up names from Excel
into R by cutting and pasting. Once this was done, I did the relevant extraction in R.

3. From the dataset created in step 2, I calculated the mean of the column measurements by activity and subject. There are 6 activity types
and 30 subjects in the data. This makes for 6x30 rows that the dataset contains. Each element in the row represents the mean for that measurement
in the data in step 2, broken by activity and subject. There are 86 measurement columns in Step 2. So there are 180 rows and 86 measurement columns
along with one columns denoting the subject and activity type for the row for a total of 180 rows and 87 columns.

4. The data created in step 3 was written out to the output file as the final result.
