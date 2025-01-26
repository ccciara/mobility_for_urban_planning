# Mobility Data for Urban Planning Project
### UCL GEOG0051 Mining Social and Geographic Datasets

Within this project, two mobility datasets are analysed to determine the best method for deciding the location of a new kindergarten in Cambridge, UK. 
This process requires consideration of mobility patterns within the city; 
ideally, the kindergarten will be placed somewhere with high walkable accessibility for residents, but low exposure to car traffic, 
so that children can walk to school without having to cross dangerous busy roads and do not receive excessive exposure to car pollution at school.

## Part 1
Data: Gowalla locational check ins
A dataset composed of userid's, check in coordinates, and check in times is analysed to predict route choice and travel mode. 
Functions and data pipelines are constructed to smoothly predict and visualize mobility patterns from input data.
First, the shortest path is plotted between two sequential points, then the travel speed is found through path distance and time elapsed. 
Travel mode is estimated from travel speed, though this is vulnerable to error as data on when users began their journeys is not available. 
Finally, daily journeys for single users or the entire userbase are visualized with different colors representing different travel modes.

<img width="388" alt="Screenshot 2025-01-26 at 11 21 41 AM" src="https://github.com/user-attachments/assets/5a70690b-d6fd-4dbf-ab29-212cd7437d47" />

Example of daily travel output for one user.


<img width="1149" alt="Screenshot 2025-01-26 at 11 23 46 AM" src="https://github.com/user-attachments/assets/39105795-910f-4b26-b6f8-d10b61bc11f9" />
Predicted walking and cycling journeys vs predicted car journeys for all users.

Though this dataset highlights some potential areas of high pedestrian activity and low car presence, particularly around Mill Road Cemetery,
this is probably not the best data to make decisions from as it captures only a small and likely biased proportion of Cambridge mobility.
Let's try another method!

## Part 2
Data: Street network graph + land use analysis
This second method of analysis focuses on qualities of the street networks for pedestrians and drivers in order to discover areas which should naturally draw more pedestrians and fewer drivers.
This is achieved through analysis of centrality measures. 
Two centrality measures are used here; degree centrality, or how many connections a street has to surrounding streets, 
and betweeness centrality, which calculates the shortest paths between all streets in the city and gives each street a score depending on how many shortest paths pass through it.
Degree centrality is calculated for the walking street network in order to locate areas with the most interconnection for pedestrians, 
and betweeness centrality is calculated for the driving street network to find the streets likely to hold the most car traffic.

The high pedestrian opportunity and high car risk streets were then plotted on top of a land use map, in order to also locate an area that is close to both residential zones and green spaces, 
as schools near green spaces have been found to have beneficial effects on children's mental and physical health. 
Examining this shows an area in the north side of Cambridge near Orchard Park, where there is high pedestrian potential, low car traffic, and access to both residential areas and green space.
<img width="802" alt="Screenshot 2025-01-26 at 11 36 02 AM" src="https://github.com/user-attachments/assets/af6ec4d3-d703-49f0-8bd2-7bd41a33fcf6" />

