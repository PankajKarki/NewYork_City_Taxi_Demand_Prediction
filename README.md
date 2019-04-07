# NYC-Taxi-Demand-Prediction
# Business Problem/Problem Statement
For a given location in New York City, our goal is to predict the number of pickups in that given location. 
Some location require more taxis at a particular time than other locations owing to the presence schools, hospitals, offices etc. 
The prediction result can be transferred to the taxi drivers via Smartphone app, and they can subsequently move to the locations where predicted pickups are high.

## Objectives & Constraints 
__Objectives:__ Our objective is to predict the number of pickups as accurately as possible for each region in a 10min interval. We will break up the whole New York City into regions, that we will discuss later in the blog. Now, the 10min interval is chosen because in NYC one can commute 1 mile in approximately 10 minutes given the traffic is normal at that particular time.

__Constraints:__ 
* __Latency__ Given a location and current time of a taxi driver, as a taxi driver, he/she excepts to get the predicted pickups in his/her region and the adjoining regions in few seconds. Hence, there is a medium latency requirement.

* __Interpretability:__ As long as taxi driver gets good prediction result, he/she is not be much interested in the interpretability of the result. He/she is not much interested in why he/she is getting this result. Hence, there is a no interpretability required.

* __Relative Errors:__ Mean Absolute Percentage Error will be the relative error we will consider. Let say the predicted pickups for a particular location are 100, but actual pickups are 102, the percentage error will be 2% and Absolute error is 2. The taxi driver will be more interested in the percentage error than the absolute error. Let say in some region the predicted pickups are 250, and if taxi driver knows that the relative error is 10% then he/she will consider the predicted result to be in the range of 225 to 275, which is considerable.

# Data Information
<p>
Ge the data from : http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml (2016 data)
The data used in the attached datasets were collected and provided to the NYC Taxi and Limousine Commission (TLC) 
</p>

## Information on taxis:

<h5> Yellow Taxi: Yellow Medallion Taxicabs</h5>
<p> These are the famous NYC yellow taxis that provide transportation exclusively through street-hails. The number of taxicabs is limited by a finite number of medallions issued by the TLC. You access this mode of transportation by standing in the street and hailing an available taxi with your hand. The pickups are not pre-arranged.</p>

<h5> For Hire Vehicles (FHVs) </h5>
<p> FHV transportation is accessed by a pre-arrangement with a dispatcher or limo company. These FHVs are not permitted to pick up passengers via street hails, as those rides are not considered pre-arranged. </p>

<h5> Green Taxi: Street Hail Livery (SHL) </h5>
<p>  The SHL program will allow livery vehicle owners to license and outfit their vehicles with green borough taxi branding, meters, credit card machines, and ultimately the right to accept street hails in addition to pre-arranged rides. </p>
<p> Credits: Quora</p>

<h5>Footnote:</h5>
In the given notebook we are considering only the yellow taxis for the time period between Jan - Mar 2015 & Jan - Mar 2016

# Data Collection
We Have collected all yellow taxi trips data from jan-2015 to dec-2016(Will be using only 2015 data)
<table>
<tr>
<th> file name </th>
<th> file name size</th>
<th> number of records </th>
<th> number of features </th>
</tr>
<tr>
<td> yellow_tripdata_2016-01 </td>
<td> 1. 59G </td>
<td> 10906858 </td>
<td> 19 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-02 </td>
<td> 1. 66G </td>
<td> 11382049 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2016-03 </td>
<td> 1. 78G </td>
<td> 12210952 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2016-04 </td>
<td> 1. 74G </td>
<td> 11934338 </td>
<td> 19 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-05 </td>
<td> 1. 73G </td>
<td> 11836853 </td>
<td> 19 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-06 </td>
<td> 1. 62G </td>
<td> 11135470 </td>
<td> 19 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-07 </td>
<td> 884Mb </td>
<td> 10294080 </td>
<td> 17 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-08 </td>
<td> 854Mb </td>
<td> 9942263 </td>
<td> 17 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-09 </td>
<td> 870Mb </td>
<td> 10116018 </td>
<td> 17 </td>
</tr>

<tr>
<td> yellow_tripdata_2016-10 </td>
<td> 933Mb </td>
<td> 10854626 </td>
<td> 17 </td>
</tr>
<tr>
<td> yellow_tripdata_2016-11 </td>
<td> 868Mb </td>
<td> 10102128 </td>
<td> 17 </td>
</tr>
<tr>
<td> yellow_tripdata_2016-12 </td>
<td> 897Mb </td>
<td> 10449408 </td>
<td> 17 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-01 </td>
<td> 1.84Gb </td>
<td> 12748986 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-02 </td>
<td> 1.81Gb </td>
<td> 12450521 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-03 </td>
<td> 1.94Gb </td>
<td> 13351609 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-04 </td>
<td> 1.90Gb </td>
<td> 13071789 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-05 </td>
<td> 1.91Gb </td>
<td> 13158262 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-06 </td>
<td> 1.79Gb </td>
<td> 12324935 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-07 </td>
<td> 1.68Gb </td>
<td> 11562783 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-08 </td>
<td> 1.62Gb </td>
<td> 11130304 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-09 </td>
<td> 1.63Gb </td>
<td> 11225063 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-10 </td>
<td> 1.79Gb </td>
<td> 12315488 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-11 </td>
<td> 1.65Gb </td>
<td> 11312676 </td>
<td> 19 </td>
</tr>
<tr>
<td> yellow_tripdata_2015-12 </td>
<td> 1.67Gb </td>
<td> 11460573 </td>
<td> 19 </td>
</tr>
</table>

## Features in the dataset:
<html><head></head><body><table>
   <tbody><tr>
      <th>Field Name</th>
      <th>Description</th>
   </tr>
   <tr>
      <td>VendorID</td>
      <td>
         A code indicating the TPEP provider that provided the record.
         <ol>
            <li>Creative Mobile Technologies</li>
            <li>VeriFone Inc.</li>
         </ol>
      </td>
   </tr>
   <tr>
      <td>tpep_pickup_datetime</td>
      <td>The date and time when the meter was engaged.</td>
   </tr>
   <tr>
      <td>tpep_dropoff_datetime</td>
      <td>The date and time when the meter was disengaged.</td>
   </tr>
   <tr>
      <td>Passenger_count</td>
      <td>The number of passengers in the vehicle. This is a driver-entered value.</td>
   </tr>
   <tr>
      <td>Trip_distance</td>
      <td>The elapsed trip distance in miles reported by the taximeter.</td>
   </tr>
   <tr>
      <td>Pickup_longitude</td>
      <td>Longitude where the meter was engaged.</td>
   </tr>
   <tr>
      <td>Pickup_latitude</td>
      <td>Latitude where the meter was engaged.</td>
   </tr>
   <tr>
      <td>RateCodeID</td>
      <td>
         The final rate code in effect at the end of the trip.
         <ol>
            <li> Standard rate </li>
            <li> JFK </li>
            <li> Newark </li>
            <li> Nassau or Westchester</li>
            <li> Negotiated fare </li>
            <li> Group ride</li>
         </ol>
      </td>
   </tr>
   <tr>
      <td>Store_and_fwd_flag</td>
      <td>This flag indicates whether the trip record was held in vehicle memory before sending to the vendor,<br\> aka “store and forward,” because the vehicle did not have a connection to the server.
         <br\>Y= store and forward trip
         <br\>N= not a store and forward trip
      </br\></br\></br\></td>
   </tr>
   <tr>
      <td>Dropoff_longitude</td>
      <td>Longitude where the meter was disengaged.</td>
   </tr>
   <tr>
      <td>Dropoff_ latitude</td>
      <td>Latitude where the meter was disengaged.</td>
   </tr>
   <tr>
      <td>Payment_type</td>
      <td>
         A numeric code signifying how the passenger paid for the trip.
         <ol>
            <li> Credit card </li>
            <li> Cash </li>
            <li> No charge </li>
            <li> Dispute</li>
            <li> Unknown </li>
            <li> Voided trip</li>
         </ol>
      </td>
   </tr>
   <tr>
      <td>Fare_amount</td>
      <td>The time-and-distance fare calculated by the meter.</td>
   </tr>
   <tr>
      <td>Extra</td>
      <td>Miscellaneous extras and surcharges. Currently, this only includes. the $0.50 and $1 rush hour and overnight charges.</td>
   </tr>
   <tr>
      <td>MTA_tax</td>
      <td>0.50 MTA tax that is automatically triggered based on the metered rate in use.</td>
   </tr>
   <tr>
      <td>Improvement_surcharge</td>
      <td>0.30 improvement surcharge assessed trips at the flag drop. the improvement surcharge began being levied in 2015.</td>
   </tr>
   <tr>
      <td>Tip_amount</td>
      <td>Tip amount – This field is automatically populated for credit card tips.Cash tips are not included.</td>
   </tr>
   <tr>
      <td>Tolls_amount</td>
      <td>Total amount of all tolls paid in trip.</td>
   </tr>
   <tr>
      <td>Total_amount</td>
      <td>The total amount charged to passengers. Does not include cash tips.</td>
   </tr>
</tbody></table></body></html>

# ML Problem Formulation
<p><b> Time-series forecasting and Regression</b></p>
<br>
-<i> To find number of pickups, given location cordinates(latitude and longitude) and time, in the query reigion and surrounding regions.</i>
<p> 
To solve the above we would be using data collected in Jan - Mar 2015 to predict the pickups in Jan - Mar 2016.
</p>

# Performance metrics
1. Mean Absolute percentage error.
2. Mean Squared error.
