# Coursework1_200315522
For Time series coursework 1
#---
  title: "Coursework1_200315522"
author: "Daniella Concessio"
date: "2024-03"
output: html_document
#---


> df<-read.csv("C:/Users/danie/OneDrive - Queen Mary, University of London/ log_payton_manning.txt")

>View(df)

#load the library(prophet) here, if not then install before if not done so
#We call the prophet function that now fits our model. 

>m <- prophet(df)

#we are now going to make a dataframe with a column ds that has the dates for the preictions to be made. 

#I will be using the make_future_dataframe function this forecasts the period numbers and also a suitable dataframe

>future <- make_future_dataframe(m, periods=365)
>tail(future)

#It will then print out in the console a few of the data.

#we will then use the forecast function to get our forecast. 

>forecast <- predict(m,future)
>tail(forecast[c('ds','yhat','yhat_lower','yhat_upper')])

#from the above, the yhat is the column that has the forecast. 
#Whereas, the other columns are for uncertainty and other components like seasonal components.


#I will now be using 3 ways to plot this model. The first one is the most basic use which is just by using 'plot'

>plot(m,forecast)

#Analysis of the basic plot:-There are a few anomalies in this plot. Some of the points are placed far away, which could suggest abnormality or errors in the data,etc.
#-There seems to be a pattern that is recurring which suggests seasonality. The plots portray higher than 8 every 2 years, which is like a every 2 year cycle.

#The second type of plot used is where I will now be breaking down the model to calculate several other components like trends, weekly seasonality and yearly seasonality.

>prophet_plot_components(m,forecast)

#Analysis: -In this plot you can see quite frankly clear how it is easily broken down into different components. 
#- In the weekly data shown in the plot, there are higher observations during certain days and then lowers down when reaching the weekend, which suggests that seasonal factors like holidays or weather can explain this. 

##Upon research, I will insert another plot that I came across called the Dygraphs

>dyplot.prophet(m,forecast)

#The plot that displays from above is such a cool plot. 
#Analysis: - By using the dygraph, we can easily visualise the trendlines, which help in identifying the trends in the data. However, to cancel or reduce noise one can use smoothing techniques. 
#-we can easily see that when we hoover over the data, it displays detailed information whcih can be used for results into mutliple series or comparing with other series. 
#-As stated in the basic plot analysis as well, there are a few anomalies here as well. However, we can easily just hoover over the data and that point and it gives us a reference of the date,actual and predicted data. 
