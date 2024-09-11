# About this Report

About the dataset -
This dataset contains the fuel economy in miles per gallon (mpg) for 398 cars sold in the US in the 1970s and 1980s. The data includes vehicle characteristics including horsepower, acceleration, country of origin, and more.

Problem statements for the analysis -
1. Yearly fuel efficient leaders :
Problem Statement:
Which car models were the most fuel-efficient each year from 1970 to 1982?

Objective:
Identify the top-performing car models in terms of fuel economy for each year and analyze the characteristics that made them efficient.

**** Approach****
For analyzing the yearly fuel efficient leaders, I've formulated the following DAX measures :

    CompanyWithMaxMPG = 
    CALCULATE(
        FIRSTNONBLANK('auto-mpg'[company name], 1),
        FILTER(
            'auto-mpg',
            'auto-mpg'[mpg] = [Max Milage] && 'auto-mpg'[model year] = MAX('auto-mpg'[model year])
        )
    )
This will give us the top fuel efficient companies from each year.

Then for visualizing our results I've select a 'Line and clustered column chart'. The x-axis of the chart contains the DAX and Y-axis contains the average MPG.

The trend line shows the average MPG for each year.

![Screenshot 2024-07-24 205915](https://github.com/user-attachments/assets/ea22230a-1a3f-47de-9f0a-c01820424b34)


Also, I've created a DAX measures which selects the car with the highest MPG in each year. For visualizing this I've shown it in the tooltip of the chart.

![Screenshot 2024-07-24 215057](https://github.com/user-attachments/assets/18b32769-3eb3-467b-aeed-9e212b3b6d9e)


Additionally I've created a a button for visualizing the least fuel efficient cars. Clicking onto it will the chart visuals, showing the car & company name for 
each year having the least MPG. To achieve this I've used book marks. The DAX formula remains same except for the MAX() function I've used the MIN() function.


2. Impact of Vehicle Weight on Fuel Economy:
Problem Statement:
What is the relationship between vehicle weight and fuel economy? Are heavier cars less fuel-efficient than lighter ones?

Objective:
Analyze the correlation between vehicle weight and MPG to understand how weight affects fuel consumption.

**** Approach****
For analyzing the yearly fuel efficient leaders, I've formulated the following DAX measures :

Average Weight = AVERAGE('auto-mpg'[weight])

Then for visualizing our results I've select a 'Scatter Plot'. The x-axis of the chart contains the DAX and Y-axis contains the average MPG.

<img width="606" alt="PB-2" src="https://github.com/user-attachments/assets/563b5e6f-c3f4-4b68-80a9-0d60209743ad">


The trend line shows that with increase in weight our milage decrease thus the relationship is inversely proportional.

Additionally I've also created a visualization showing the relationship of MPG with displacement and horse power of the car.

3. Changes in Car Attributes Over Time:
Problem Statement:
How have car attributes such as weight, horsepower, and acceleration changed over the years covered by the dataset?

Objective:
Analyze trends in various car attributes over time to understand how car designs and performance have evolved.

**** Approach****
For analyzing the regional variation in fuel economy the various parameters I've considered are 'Milage', 'Displacement', ' Weight' , 'Horse Power', 'No. of cylinders'.

DAX measures used :

Average HP = AVERAGE('auto-mpg'[horsepower])
Average Milage = AVERAGE('auto-mpg'[mpg])

Average displacment = AVERAGE('auto-mpg'[displacement])

Average Weight = AVERAGE('auto-mpg'[weight])

Average Cylinder Used = AVERAGE('auto-mpg'[cylinders])
All these measure are plotted on a line chart against year for visualizing the trend.

![Screenshot 2024-07-24 205812](https://github.com/user-attachments/assets/3b1cd125-4e2f-4abb-a96c-6284fd64fffd)


<img width="574" alt="pw-3" src="https://github.com/user-attachments/assets/b45c685a-886b-4aa6-8484-9ea7dfdf7f02">


4. Identifying Outliers in Fuel Economy:
Problem Statement:
Which cars are outliers in terms of fuel economy, and what characteristics do they share?

Objective:
Identify cars that significantly deviate from the average MPG and investigate the features that make them outliers.

**** Approach****
Here I've used a 'Line Chart' where Company names are plotted on x-axis against average milage on y-axis. The reference line shows the significant derivation of milage of cars from the average milage. Additionally the visualization can be filtered based on the country.

![Screenshot 2024-07-24 234526](https://github.com/user-attachments/assets/d7a7d237-ccf4-4b2f-bf70-1cdaa913fcf0)

