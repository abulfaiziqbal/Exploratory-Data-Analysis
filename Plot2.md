# Exploratory-Data-Analysis

# Inserting complete data set
data1 <- read.csv("D:/Coursera/Data Science John Hopkins University/EDA/household_power_consumption.txt", 
                  header=T, sep=';', na.strings="?")
data1$Date <- as.Date(data1$Date, format="%d/%m/%Y")

# Now Subsetting the data
dataActual <- subset(data1, subset=(Date >= "2007-02-01" & Date <= "2007-02-02"))

# Removing the first data set
rm(data1)

# Converion of Dates
datetime <- paste(as.Date(dataActual$Date), dataActual$Time)
dataActual$Datetime <- as.POSIXct(datetime)

# Plotting the graph Plot2
plot(dataActual$Global_active_power~dataActual$Datetime, type="l",
     ylab="Global Active Power (kilowatts)", xlab="")
dev.copy(png, file="D:/Coursera/Data Science John Hopkins University/EDA/plot2.png", height=480, width=480)
dev.off()
