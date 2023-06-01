# Fuel delivery network optimization for Gazpromneft company
This project is dedicated to optimizing transportations between oil bases and petrol stations, thus minimizing OPEX costs and reducing time spent.
The project was implemented using methods of linear programming through Python libraries. Three main libraries were considered and compared in terms of accuracy and efficiency: PuLP, CVXPY and PYOMO.

The overall idea of the technical implementation was to minimize the cost function, 
which states the sum volumes transported between oil bases and petrol stations, multiplied by the cost of each transportation.
There are several restrictions, that need to be satisfied:
- The demand of each petrol station should be satisfied
- The supply of each oil base should not bee exceeded
- All products delivered for one petrol station should be taken from one oil base
- For some oil bases there should be a percent loading threshold which should be overcome


This directory contains source data in excel format 'opt_data_gen (1).xlsb', which contains data on petrol volume required for petrol stations, 
volume of petrol available on the oil bases, and information on connections between oil bases and petrol stations (in terms of distances, costs).
Secondly, there is a configuration file with constants that can be entered by user. It includes file name, month for which the model will calculate costs, set of regions to choose,
types of upper and lower bounds for supply restrictions (which can be calculated for products or for group of products, such as diesel/petrol),
the list of oil bases on which user wants to set the lower bound at all, and the percentage of this loading.
There are also two files which contain data exploration and the visualization of the solution for better understanding.
Finally, there are three files, each on the mentioned libraries, which can be considered as the separate solution.

The most optimal solutions are obtained on CVXPY and PuLP libraries, both working on CBC solver. 

In order to interact with the model, the user should fill the configuration file, and launch the file.
The output of the model will be the distribution of the volumes of each product delivered for each petrol stations from oilbases and the final cost of solution.

As a result the lowest cost (84 million rubles) obtained on PuLP CBC is significantly lower than the proposed baseline (267 million rubles), and works approximately 30 minutes.
