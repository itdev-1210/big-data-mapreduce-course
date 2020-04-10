# Telecom Example

This is an example of a MapReduce program on Hadoop.
In this example we are going to solve a very useful 
problem called Call Data Record (CDR) Analytics.

## Problem

Here is a problem statement

A Telecom company keeps records for its subscribers in 
specific format. Consider following format

````
FromPhoneNumber|ToPhoneNumber|CallStartTime|CallEndTime|STDFlag
````

Now we have to write a MapReduce program to find out all phone 
numbers who are making more than 60 mins of STD calls. Here 
if STD Flag is 1 that means it was as STD Call. STD is call 
is call which is made outside of your state or long distance 
calls. By indentifying such subscribers, telcom company wants 
to offer them STD (Long Distance) Pack which would efficient 
for them instead spending more money without that package.

## Input Example

The data is coming in log files and looks like as shown below.

````
FromPhoneNumber|ToPhoneNumber|CallStartTime|CallEndTime|STDFlag
9665128505|8983006310|2015-03-01 09:08:10|2015-03-01 10:12:15|1
9665128505|8983006310|2015-03-01 07:08:10|2015-03-01 08:12:15|0
9665128505|8983006310|2015-03-01 09:08:10|2015-03-01 09:12:15|1
9665128505|8983006310|2015-03-01 09:08:10|2015-03-01 10:12:15|0
9665128506|8983006310|2015-03-01 09:08:10|2015-03-01 10:12:15|1
9665128507|8983006310|2015-03-01 09:08:10|2015-03-01 10:12:15|1
````

First of all we need to understand the data, depending upon the 
output we are expecting, we need to write a mapper class which 
would emit `FromPhoneNumber` and `Duration` of STD Call intermediate 
key value pairs.
