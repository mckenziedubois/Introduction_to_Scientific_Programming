{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<img src=\"https://comp116sp19.cs.unc.edu/images/COMP116Logo.png\" style=\"display:inline; width:200px\" />\n",
    "\n",
    "# Assignment 1\n",
    "\n",
    "**Remember** always start work at the top of the notebook.\n",
    "\n",
    "The data supplied to you in this assignment will be graded using different data.\n",
    "For example, if a problem asks you to determine the length of a string you\n",
    "could print the string, count the number of characters, and assign the count to the variable.\n",
    "**But the string used during grading will be different** so instead you should use the Python\n",
    "function that will compute the length of the string because that will work on this data \n",
    "and the data you will be graded with.\n",
    "\n",
    "## Introduction\n",
    "\n",
    "This assignment involves working with and plotting data in arrays. You will complete this assignment by working in this notebook. When you are finished you will submit your notebook using the button in the unlocker. \n",
    "\n",
    "I have completed several parts of the assignment for you. You should study these parts but do not modify them. You'll have to do similar things for yourself in future assignments. \n",
    "\n",
    "## Learning Objective\n",
    "\n",
    "In this assignment you will learn to use the powerful array operations that are provided by Numpy. Given real data you will answer questions of scientific interest. \n",
    "\n",
    "In order to maximize your learning about Numpy arrays you are prohibited from using any sort of looping constructs for solving these problems.\n",
    "\n",
    "## Setup\n",
    "\n",
    "This will setup the environment for the assignment.  \n",
    "\n",
    "In the cell that follows,\n",
    "you must assign the variable Author to have the string value of your onyen.\n",
    "You must acknowledge who your collaborators are."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "data": {
      "application/javascript": [
       "IPython.notebook.set_autosave_interval(15000)"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Autosaving every 15 seconds\n"
     ]
    }
   ],
   "source": [
    "%matplotlib inline\n",
    "%autosave 15\n",
    "\n",
    "# these next lines make the array and plotting modules available\n",
    "import numpy as np\n",
    "import pylab\n",
    "\n",
    "# we use checker to provide feedback, you wouldn't use it in a real application\n",
    "import comp116\n",
    "check, report = comp116.start('A1')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Author and Collaborators\n",
    "\n",
    "Enter your onyen in the variable Author.\n",
    "The variable Collaborators should be assigned a list of the onyens of the students who helped with with this assignment."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Put your onyen between the quotes\n",
    "Author = 'your onyen here'\n",
    "\n",
    "# If you have no collaborators then remove all the strings from this list\n",
    "# it should look like Collaborators = [ ]\n",
    "Collaborators = [ 'list', 'their', 'onyens', 'here' ]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "editable": false
   },
   "outputs": [],
   "source": [
    "check('Author', Author != 'your onyen here', points=1.25)\n",
    "check('Collaborators', Collaborators != [ 'list', 'their', 'onyens', 'here' ], points=1.25)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## The data\n",
    "\n",
    "First we will read several data sets from files. These datasets are:\n",
    "* `my_string` is a long string read from a UNC website.\n",
    "* Monthly Jordan and Falls Lake data (from Army Corps of Engineers)\n",
    "  * `monthly_depth`: a 240&Cross;2 array with depth in feet of Jordan and Falls lakes for each month from Jan 1985 to Dec 2004, which is 20 years.\n",
    "  So Jordan's monthly depth is in slice `monthly_depth[: 0]`.\n",
    "  * `monthly_rain`: a 240&Cross;2 array with total rainfall in inches for each month again starting in Jan 1985.\n",
    "* Daily Haw river and Jordan Lake data (from USGS)\n",
    "  * `hawgage`: a 365&Cross;4 array of daily average river or lake height in feet at Haw River, Bynum, and above & below the Jordan Lake Dam by Moncure. (These sites are listed upstream to downstream, but the gauges are not in that order.)\n",
    "  * `hawrain`: a 365&Cross;2 array of daily rainfall in inches measured at two rain gauges from 29 Aug 07 to 28 Aug 08."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "The first 50 characters of my_string are https://gradschool.unc.edu/funding/gradschool/weis\n",
      "\n",
      "The first 5 rows of depth are\n",
      " [[214.9  247.63]\n",
      " [216.4  250.25]\n",
      " [216.9  249.85]\n",
      " [215.95 249.97]\n",
      " [215.9  249.54]]\n",
      "\n",
      "The first 5 rows of rain are\n",
      " [[4.05 4.61]\n",
      " [5.12 5.37]\n",
      " [1.27 1.39]\n",
      " [0.66 0.46]\n",
      " [4.66 4.79]]\n",
      "\n",
      "The first 5 rows of hawgage are\n",
      " [[212.9    1.58   3.23   2.68]\n",
      " [212.84   1.64   3.23   2.65]\n",
      " [212.77   1.74   3.26   2.65]\n",
      " [212.7    1.66   3.33   2.85]\n",
      " [212.6    1.58   3.35   2.79]]\n",
      "\n",
      "The first 5 rows of hawrain are\n",
      " [[0.   0.  ]\n",
      " [0.01 0.38]\n",
      " [0.01 0.  ]\n",
      " [0.   0.  ]\n",
      " [0.01 0.  ]]\n"
     ]
    }
   ],
   "source": [
    "# These are the strings and arrays you should use in your code.\n",
    "\n",
    "# You should NOT assume these are the same arrays used during the grading of your code.\n",
    "# For example, you'll compute the length of my_string using Python functions.  If you\n",
    "# actually print out my_string here and physically count the number of characters, the\n",
    "# grader will figure this out because the my_string used to grade your work will be different.\n",
    "import pickle\n",
    "with open('A1data.pickle', 'rb') as f:\n",
    "    (my_string, monthly_depth, monthly_rain, hawgage, hawrain) = pickle.load(f)\n",
    "print('The first 50 characters of my_string are', my_string[:50])\n",
    "print()\n",
    "\n",
    "print('The first 5 rows of depth are\\n', monthly_depth[:5])\n",
    "print()\n",
    "\n",
    "print('The first 5 rows of rain are\\n', monthly_rain[:5])\n",
    "print()\n",
    "\n",
    "print('The first 5 rows of hawgage are\\n', hawgage[:5])\n",
    "print()\n",
    "\n",
    "print('The first 5 rows of hawrain are\\n', hawrain[:5])"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Fun with strings\n",
    "\n",
    "## Q1 Find the length of variable `my_string`\n",
    "\n",
    "Create a variable my_string_len and assign it the number of characters in my_string. You should not count the characters in my_string but use the Python function that computes the length of a string, list, or NumPy array."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "my_string_len = len(my_string)  # Update with your code"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q1 appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q1', my_string_len, points=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q2 Find `my_string`'s middle character\n",
    "\n",
    "Create a variable middle_character and assign it the\n",
    "character that appears at the mid-point (middle) of\n",
    "my_string.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "# HINT: You might want to use the my_string_len variable\n",
    "# computed in the previous cell\n",
    "middle_character = my_string[len(my_string)//2]  # Update with your code"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q2 appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q2', middle_character, points=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q3 Reverse a string\n",
    "\n",
    "Create a variable reverse that has the value of\n",
    "my_string but in the reverse order."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [],
   "source": [
    "reverse = my_string[::-1]  # Update with your code"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q3 appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q3', reverse, points=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q4 Even characters of a reversed string\n",
    "\n",
    "Create a variable even_string_reverse that has the all the\n",
    "even characters (the second character, fourth character, etc) in my_string then put them in **reverse order.**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Hint, you may want to do this in two steps\n",
    "my_string_even = my_string[1::2]\n",
    "even_string_reverse = my_string_even[::-1]  # UPDATE WITH YOUR CODE"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q4 appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q4', even_string_reverse, points=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Plotting data\n",
    "\n",
    "## Q5 Plot monthly Jordan and Falls Lake data\n",
    "\n",
    "<img src=\"files/plot1.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Plot a line graph of depths for both lakes. The graph you produce should look like the figure to the right.\n",
    "You won't have to put in the title or axis labels as\n",
    "they have been provided for you."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q5 appears correct\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Remember, the variable, monthly_depth, has a row for the depth of Jordan and Falls lake for each month.\n",
    "\n",
    "# put your code here to plot the line graph of depths over time.\n",
    "pylab.plot(monthly_depth)\n",
    "\n",
    "\n",
    "# these show how to label the figure\n",
    "# DO NOT UPDATE THE FOLLOWING LINES OF CODE!!!!\n",
    "pylab.title('Depth of Jordan and Falls lakes')\n",
    "pylab.ylabel('Depth (feet)')\n",
    "pylab.xlabel('Months starting with Jan 1985')\n",
    "check('Q5', pylab.gcf(), points=10)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q6 Compute monthly depth over target\n",
    "The target depths for Jordan and Falls lakes are 216 feet and 251.5 feet, respectively.  **For how many months was each lake over its target?**\n",
    "\n",
    "The variable JordanOverTarget should be the number of \n",
    "months Jordan lake was over the target set for it.  \n",
    "The variable FallsOverTarget should be the number of\n",
    "months where Falls lake was over the target set for it.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Months Jordan lake was over its target = 154\n",
      "Months Falls lake was over its target = 59\n"
     ]
    }
   ],
   "source": [
    "JordanOverTarget = np.count_nonzero((monthly_depth[:,0] > 216)) # replace this with some expression\n",
    "FallsOverTarget = np.count_nonzero((monthly_depth[:,1] > 251.5)) # replace this with some expression\n",
    "\n",
    "\n",
    "print('Months Jordan lake was over its target =', JordanOverTarget)\n",
    "print('Months Falls lake was over its target =', FallsOverTarget)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q6.Jordan appears correct\n",
      "Q6.Falls appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q6.Jordan', JordanOverTarget, points=2.5)\n",
    "check('Q6.Falls', FallsOverTarget, points=2.5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q7 Plot the August rainfall\n",
    "\n",
    "<img src=\"files/plot3.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Plot the rain in August as a line graph over years for both lakes. Set the title to 'Rain in August for Jordan and Falls lakes'. Label the x axis 'Years since 1985'. Label the y axis 'Inches'. It should look like the figure to the right.  \n",
    "\n",
    "In this plot, you will need to add the xlabel, ylabel, and title.\n",
    "You may want to model your code from the previous plot to create\n",
    "the title, x-axis label, and y-axis label.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q7 appears correct\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Hint: You may want to create a variable August_rain that is\n",
    "# an slice of variable rain that starts at the month 8, 20, \n",
    "# etc.  In other words, starts at element with index 7 and\n",
    "# all elements that follow in 12-month increments\n",
    "August_rain= monthly_rain[7::12]\n",
    "\n",
    "# Add title, x labels, and y labels\n",
    "pylab.plot(August_rain)\n",
    "pylab.title('Rain in August for Jordan and Falls lakes')\n",
    "pylab.xlabel('Years since 1985')\n",
    "pylab.ylabel('Inches')\n",
    "check('Q7', pylab.gcf(), points=10)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q8 Produce a bar and line graph\n",
    "\n",
    "<img src=\"files/plot4.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Compute the average height that Falls Lake is above its target for each month over the 20 years from 1985-2004, and display as bar chart with a bar for each month.  Plot the line for 2004 in red on top of this bar chart. Again, it should look like the sample to the right. Note there are two parts, computing a value and plotting the red line.\n",
    "\n",
    "Hint: You can reshape the 1-D array of monthly depths into a 2-D array with one row per year. Then, you can take the mean down the columns to get the monthly means."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 45,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q8 appears correct\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Assign variable Falls to be an array of only the depths of Falls lake\n",
    "Falls = monthly_depth[:,1]\n",
    "\n",
    "\n",
    "# Hint: You may want to reshape the one-dimensional array, Falls, and create\n",
    "# a two dimensional array where there are as many rows as needed (-1) and \n",
    "# twelve columns for each of the twelve months\n",
    "FallsByMonth = np.reshape(Falls, (-1,12))\n",
    "\n",
    "# Hint: You may want to compute FallsByMonthMeanOverTarget which is the mean \n",
    "# of FallsByMonth for each month minus the target of 251.5\n",
    "# Hint: FallsByMonthMeanOverTarget should be an array of shape (12,)\n",
    "\n",
    "FallsByMonthMeanOverTarget = (np.mean(FallsByMonth, axis =0))-251.5 # replace this with code to compute the value\n",
    "\n",
    "# then you can create a bar chart with X values of [1, 2, 3, ... 12 ] and \n",
    "# the Y values, bar height, of the FallsbyMonthMeanOverTarget\n",
    "pylab.bar(np.arange(1,13), FallsByMonthMeanOverTarget, align='center')\n",
    "\n",
    "# then plot a line in red on top of that has the same X values and has\n",
    "# the Y-values of the last year of rainfall that was over the target.  \n",
    "\n",
    "# Hint: You may want to create a varaible, FallsLastYear, that is \n",
    "# the rainfall for the last year (twelve months) of the Falls variable.\n",
    "# Then you might want to create another variable, FallsLastYearOverTarget,\n",
    "# that is the rainfall over the target of 251.5\n",
    "FallsLastYear = Falls[-12:]\n",
    "FallsLastYearOverTarget = FallsLastYear -251.5\n",
    "\n",
    "pylab.plot(np.arange(1,13), FallsLastYearOverTarget, 'r')\n",
    "\n",
    "pylab.title('Average Falls lake depth 85-04, and line for 2004')\n",
    "pylab.ylabel('Height above target(ft)')\n",
    "pylab.xlabel('Month')\n",
    "check('Q8', pylab.gcf(), points=12.5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q9 Daily rain data\n",
    "\n",
    "Determine how many days had more than 1 inch of precipitation at __either__ of the sites in hawrain, and how many days had less than 1/4 inch at __both__ sites.**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 69,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Days with more than 1 inch of rain at either = 10\n",
      "Days with less than 1/4 inch of rain at both = 314\n"
     ]
    }
   ],
   "source": [
    "# your code goes here\n",
    "DaysEitherHawrainOverOneInch = np.count_nonzero(np.any(hawrain>1, axis =1)) # replace this with some expression\n",
    "DaysBothHawrainUnderQuarterInch = np.count_nonzero(np.all(hawrain<.25, axis =1))# replace this with some expression\n",
    "\n",
    "# then we will print the results\n",
    "print('Days with more than 1 inch of rain at either =', DaysEitherHawrainOverOneInch)\n",
    "print('Days with less than 1/4 inch of rain at both =', DaysBothHawrainUnderQuarterInch)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 70,
   "metadata": {
    "editable": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Q9.1 appears correct\n",
      "Q9.2 appears correct\n"
     ]
    }
   ],
   "source": [
    "check('Q9.1', DaysEitherHawrainOverOneInch, points=5)\n",
    "check('Q9.2', DaysBothHawrainUnderQuarterInch, points=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q10 Relative height\n",
    "\n",
    "<img src=\"files/plot7.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Determine the lowest height for each gauge in hawgage, and create an array of adjusted heights by subtracting the corresponding lowest heights. Plot these adjusted heights as a line graph. Set the title to 'Adjusted gauge heights', x axis label 'Days since 28Aug07', and y axis label 'Height above min (ft)'."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 87,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "The adjuested heights for the four haw river gages are: [[2.67 0.12 0.17 0.13]\n",
      " [2.61 0.18 0.17 0.1 ]\n",
      " [2.54 0.28 0.2  0.1 ]\n",
      " ...\n",
      " [3.66 0.08 0.2  0.13]\n",
      " [3.62 0.12 0.2  0.14]\n",
      " [3.79 7.27 0.24 2.42]]\n",
      "Q10.1 appears correct\n",
      "Q10.2 appears correct\n"
     ]
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Hint: You might want to create a variable hawgage_min which is the\n",
    "# minimum of each row of hawgage.\n",
    "hawgage_min = np.min(hawgage, axis =0)\n",
    "\n",
    "# Then you can assign adjusted_heights to be the difference between\n",
    "# hawgage and hawgage_min\n",
    "adjusted_heights = hawgage - hawgage_min # replace this with your code to compute the answer\n",
    "\n",
    "pylab.plot(adjusted_heights)\n",
    "pylab.title('Adjusted gauge heights')\n",
    "pylab.xlabel('Days since 28Aug07')\n",
    "pylab.ylabel('Height above min (ft)')\n",
    "\n",
    "print('The adjuested heights for the four haw river gages are:', adjusted_heights)\n",
    "check('Q10.1', adjusted_heights, points=10)\n",
    "check('Q10.2', pylab.gcf(), points=10)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Q11 Maximum increase and decrease\n",
    "\n",
    "Determine the maximum increase and maximum decrease in height from one day to the next for each of the four gauges in hawgage. Print the most positive change (maximum increase) for the 4 gages and the most negative change (maximum decrease)."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 92,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Maximum one-day increase in height = 4.66\n",
      "Minimum one-day decrease in height = -217.66\n",
      "Q12.1 incorrect\n",
      "  expected 7.15\n",
      "Q12.2 incorrect\n",
      "  expected -6.22\n"
     ]
    }
   ],
   "source": [
    "# Hint: You might want to create delta_height which would be the\n",
    "# difference between each height in the rows of hawgage.\n",
    "# Then you can set max_increase to be the largest of these differences\n",
    "# and max_decrease the smallest of these differences.\n",
    "\n",
    "delta_height = np.diff(hawgage,axis =1)\n",
    "\n",
    "max_increase = np.max(delta_height) # replace this with your code to compute the answer\n",
    "max_decrease = np.min(delta_height)# replace this with your code to compute the answer\n",
    "\n",
    "\n",
    "print('Maximum one-day increase in height =', max_increase)\n",
    "print('Minimum one-day decrease in height =', max_decrease)\n",
    "\n",
    "check('Q12.1', max_increase, points=5)\n",
    "check('Q12.2', max_decrease, points=5)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Done!\n",
    "<img src=\"restartAndClearOutput.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Now go back, restart the kernel (menu <font color=\"green\">Kernel</font>-><font color=\"green\">Restart and Clear</font>), and then Shift-Enter your way through the notebook to run all the cells again so you an be sure all your code will work as you expect during grading."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Saving your work\n",
    "<img src=\"saveAndCheckpoint.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Now save your work by going to (menu <font color='green'>File</font>-><font color='green'>Save and Checkpoint</font>)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "editable": false
   },
   "outputs": [],
   "source": [
    "# This line will produce a summary report of your assignment\n",
    "report(Author, Collaborators)\n",
    "print('The submit button for the assignment is in the unlocker notebook')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Close this notebook and then go back to the AssignmentUnlocker\n",
    "<img src=\"closeAndHalt.png\" width=\"300\" style=\"float: right\" />\n",
    "\n",
    "Before going back to the AssignmentUnlocker and submit your work, you'll need to go close this\n",
    "notebook (menu <font color='green'>File</font>-><font color='green'>Close and Halt</font>.)\n",
    "\n",
    "\n",
    "Note that if you actually saved your work you should not see the leaving site message below.\n",
    "If you do see the `Leave Site` warning, cancel and save your work again.\n",
    "<br />\n",
    "<img src=\"leaveSite.png\" width=\"300\" style=\"float: left\" />"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 1
}
