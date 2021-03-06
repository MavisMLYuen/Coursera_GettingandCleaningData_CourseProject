Code Book

The script "run_analysis.R" performs the 5 steps required for the course project.

Step 1 - Merge the training and test sets to create one data set.
Step 2 - Extract only the measurements on the mean and standard deviation for each measurement.
Step 3 - Use descriptive activity names to name the activities in the data set.
Step 4 - Appropriately label the data set with descriptive variable names.
Step 5 - From Step 4, create a second independent tidy data set with the average of each variable for each activity and each subject.

* Firstly, all the similar data (files with the same number of columns and referring to the same entities) is merged using the rbind() function. 
* Then, only those columns with the mean and standard deviation measures are taken from the whole dataset. After extracting these columns, they are given the correct names, taken from "features.txt".
* As activity data is addressed with values 1:6, the names and IDs from "activity_labels.txt" are taken and substituted in the dataset. 
* On the whole dataset, those columns with vague column names are corrected. 
* Finally, a new dataset is generated with all the average measures for each subject and activity type (30 subjects * 6 activities = 180 rows). The output file of this average data is called "TidyData.txt", and uploaded to this repository.

Variables

* x_train, y_train, x_test, y_test, subject_train and subject_test contain the data from the downloaded files.
* x_data, y_data and subject_data merge the previous datasets to further analysis.
* features contains the correct names for the x_data dataset, which are applied to the column names stored in mean_and_std_features, a numeric vector used to extract the desired data.
* A similar approach is taken with activity names through the activities variable.
* all_data merges x_data, y_data and subject_data in a big dataset.
* averages_data contains the relevant averages which will be later stored in a .txt file. ddply() from the plyr package is used to apply colMeans() and ease the development.
