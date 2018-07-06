

```python
import pandas as pd

# Load CSVs
service_requests_df = pd.read_csv('311_service_requests.csv', low_memory=False)
food_inspections_df = pd.read_csv('food_establishment_inspections.csv')

#test = food_inspections.groupby(['zipcode']).size()
#sample = service_requests_df.groupby(['complaint_type']).size()
#sample = sample[sample['complaint_type'] == 'Food Establishment']
#sample = sample.groupby(['descriptor']).size()
```


```python
food_inspections_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>facility</th>
      <th>address</th>
      <th>inspection_date</th>
      <th>violation_item</th>
      <th>violation_description</th>
      <th>critical_violation</th>
      <th>num_critical</th>
      <th>num_critical_not_corrected</th>
      <th>num_noncritical</th>
      <th>local_health_department</th>
      <th>...</th>
      <th>permit_expiration_date</th>
      <th>food_service_type</th>
      <th>food_service_description</th>
      <th>nys_inspection_id</th>
      <th>inspection_type</th>
      <th>inspection_comments</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>Unnamed: 23</th>
      <th>Unnamed: 24</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>STEVIE V'S - LA ROSA PIZZERIA</td>
      <td>6318 ROBINSON ROAD,  LOCKPORT</td>
      <td>10/3/17</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Niagara County</td>
      <td>...</td>
      <td>10/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant/Catering Operation</td>
      <td>286815</td>
      <td>Inspection</td>
      <td>Restrooms: OK\r\nFood Testing Thermometers: OK...</td>
      <td>43.124090</td>
      <td>-78.736710</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>SCOOPS-N-MORE</td>
      <td>90 GLENEIDA AVENUE,  CARMEL</td>
      <td>9/9/15</td>
      <td>10B</td>
      <td>Non-food contact surfaces and equipment are im...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Putnam County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>299840</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.429351</td>
      <td>-73.679427</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>J &amp; B LUNCHEONETTE</td>
      <td>189 ROUTE 9W,  HAVERSTRAW</td>
      <td>4/15/10</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Rockland County</td>
      <td>...</td>
      <td>4/30/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>303561</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.198585</td>
      <td>-73.981861</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>STOLTZFUS PASTRIES</td>
      <td>2325  McCULLOCH ROAD,  ROMULUS</td>
      <td>7/12/12</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Seneca  County</td>
      <td>...</td>
      <td>7/30/18</td>
      <td>Food Service Establishment</td>
      <td>Bakery</td>
      <td>308241</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.786649</td>
      <td>-76.809727</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>BOATYARD GRILL</td>
      <td>525 TAUGHANNOCK BOULEVARD,  ITHACA</td>
      <td>8/26/11</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Tompkins County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant/Catering Operation</td>
      <td>313774</td>
      <td>Re-Inspection</td>
      <td>NaN</td>
      <td>42.442929</td>
      <td>-76.513121</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>DUNKIN DONUTS</td>
      <td>571-577 BROADWAY,  KINGSTON</td>
      <td>1/26/17</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Ulster County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>316462</td>
      <td>Inspection</td>
      <td>Walk in freezer at 0 degrees F.  Handwash stat...</td>
      <td>41.928899</td>
      <td>-74.002976</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>WOODSTOCK CUCINA, LLC</td>
      <td>109 MILL HILL ROAD,  WOODSTOCK</td>
      <td>4/27/15</td>
      <td>11C</td>
      <td>Food contact surfaces not washed, rinsed and s...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>9.0</td>
      <td>Ulster County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>317327</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.037124</td>
      <td>-74.110615</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>BREAD ALONE BAKERY</td>
      <td>22 MILL HILL ROAD,  WOODSTOCK</td>
      <td>1/11/12</td>
      <td>8B</td>
      <td>In use food dispensing utensils improperly stored</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Ulster County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>316695</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.040633</td>
      <td>-74.117516</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>BEAR CAFE, THE</td>
      <td>295 TINKER STREET,  BEARSVILLE</td>
      <td>2/14/13</td>
      <td>14A</td>
      <td>Insects, rodents present</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>20.0</td>
      <td>Ulster County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>316696</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>TOUCH OF CLASS</td>
      <td>426 NORTH MAIN  STREET,  CANANDAIGUA</td>
      <td>1/24/06</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Geneva District Office</td>
      <td>...</td>
      <td>4/30/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>420878</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.900890</td>
      <td>-77.290872</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>UNION HALL INN</td>
      <td>2 UNION Place,  JOHNSTOWN</td>
      <td>11/3/10</td>
      <td>14C</td>
      <td>Pesticide application not supervised by a cert...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Herkimer District Office</td>
      <td>...</td>
      <td>12/31/17</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>337822</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.006234</td>
      <td>-74.367175</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>GRANDVIEW FARMS GOLF COURSE</td>
      <td>400 HARTWELL  ROAD,  BERKSHIRE</td>
      <td>4/12/11</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Tioga County</td>
      <td>...</td>
      <td>9/30/17</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>430604</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.317652</td>
      <td>-76.112406</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>DUNKIN DONUTS</td>
      <td>5 GOLDENS BRIDGE SHOPPING CENTER,  GOLDENS BRIDGE</td>
      <td>9/20/17</td>
      <td>11D</td>
      <td>Non food contact surfaces of equipment not clean</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>7/31/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>553825</td>
      <td>Inspection</td>
      <td>Measured cold holding temperatures adequate at...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>ICE CREAM WORKS</td>
      <td>14  GEORGE  STREET,  OWEGO</td>
      <td>5/6/13</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Tioga County</td>
      <td>...</td>
      <td>10/31/16</td>
      <td>Food Service Establishment</td>
      <td>Frozen Desserts</td>
      <td>831532</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Fabius Fire Department</td>
      <td>7825 Main STREET,  Fabius</td>
      <td>10/9/12</td>
      <td>11D</td>
      <td>Non food contact surfaces of equipment not clean</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/19</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>541950</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>SCARSDALE PIZZA STATION</td>
      <td>844 SCARSDALE AVENUE,  SCARSDALE</td>
      <td>4/27/12</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>1/31/19</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>536234</td>
      <td>Re-Inspection</td>
      <td>NaN</td>
      <td>40.986091</td>
      <td>-73.808930</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>GOTTA GETTA BAGEL</td>
      <td>1039 BROADWAY,  WOODMERE</td>
      <td>9/18/13</td>
      <td>4A</td>
      <td>Toxic chemicals are improperly labeled, stored...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>10/31/17</td>
      <td>Food Service Establishment</td>
      <td>Delicatessen</td>
      <td>573770</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.631449</td>
      <td>-73.707302</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>ZEN'S CHINESE FOOD</td>
      <td>2695 MERRICK ROAD,  BELLMORE</td>
      <td>2/26/15</td>
      <td>4A</td>
      <td>Toxic chemicals are improperly labeled, stored...</td>
      <td>Critical Violation</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>7.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>4/30/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>816465</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.662857</td>
      <td>-73.529327</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>HOTEL ADAMS &amp; HOMETOWN PIZZERIA</td>
      <td>4 WEST CHURCH STREET,  ADAMS</td>
      <td>7/18/14</td>
      <td>4A</td>
      <td>Toxic chemicals are improperly labeled, stored...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>9.0</td>
      <td>Watertown District Office</td>
      <td>...</td>
      <td>12/31/19</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>546279</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.809303</td>
      <td>-76.024607</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>DRYDEN COMMUNITY CENTER CAFE</td>
      <td>1 WEST  MAIN STREET,  DRYDEN</td>
      <td>7/29/15</td>
      <td>5A</td>
      <td>Potentially hazardous foods are not kept at or...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Tompkins County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant/Catering Operation</td>
      <td>599284</td>
      <td>Inspection</td>
      <td>Part I Critical Item Violation 5A\r\nPart II B...</td>
      <td>42.490502</td>
      <td>-76.297760</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>DRYDEN COMMUNITY CENTER CAFE</td>
      <td>1 WEST  MAIN STREET,  DRYDEN</td>
      <td>7/28/17</td>
      <td>5A</td>
      <td>Potentially hazardous foods are not kept at or...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Tompkins County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant/Catering Operation</td>
      <td>599284</td>
      <td>Inspection</td>
      <td>Part I Critical Item Violation 5A\r\nNo Part I...</td>
      <td>42.490502</td>
      <td>-76.297760</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>DAVENPORT GRILLE</td>
      <td>125 TUCKAHOE ROAD,  YONKERS</td>
      <td>4/18/13</td>
      <td>5A</td>
      <td>Potentially hazardous foods are not kept at or...</td>
      <td>Critical Violation</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>795419</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.954637</td>
      <td>-73.864613</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>SHADOWS ON THE HUDSON</td>
      <td>176 RINALDI BOULEVARD,  POUGHKEEPSIE</td>
      <td>11/4/11</td>
      <td>5B</td>
      <td>Potentially hazardous foods are not cooled by ...</td>
      <td>Critical Violation</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>558512</td>
      <td>Inspection</td>
      <td>6A/6B-hot holding, food below 140 degs F.  Tem...</td>
      <td>41.697787</td>
      <td>-73.938826</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>SUCO-PATHFINDER DINING</td>
      <td>7060 STATE ROUTE 104,  OSWEGO</td>
      <td>11/8/17</td>
      <td>5B</td>
      <td>Potentially hazardous foods are not cooled by ...</td>
      <td>Critical Violation</td>
      <td>5.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Oswego County</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Institutional Food Service</td>
      <td>College Food Service</td>
      <td>297007</td>
      <td>Inspection</td>
      <td>Discussed methods of keeping salad line cold t...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>AVITABILE DELI</td>
      <td>1016 MCLEAN AVENUE,  YONKERS</td>
      <td>8/12/14</td>
      <td>5C</td>
      <td>Potentially hazardous foods are not stored und...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>9.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>7/31/18</td>
      <td>Food Service Establishment</td>
      <td>Delicatessen</td>
      <td>879268</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>No. 1 Chinese Restaurant</td>
      <td>334 Cornelia STREET,  Plattsburgh</td>
      <td>3/18/10</td>
      <td>9A</td>
      <td>Inadequate personal cleanliness</td>
      <td>Not Critical Violation</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>9.0</td>
      <td>Clinton County</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>268663</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>44.697257</td>
      <td>-73.480932</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>NICOLINO'S RESTAURANT</td>
      <td>4515 STATE HWY 30,  AMSTERDAM</td>
      <td>4/6/16</td>
      <td>5C</td>
      <td>Potentially hazardous foods are not stored und...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Herkimer District Office</td>
      <td>...</td>
      <td>11/30/19</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>337977</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>STADIUM PLAZA GREEN GARDEN</td>
      <td>1485 ROUTE 9D B3,  WAPPINGERS FALLS</td>
      <td>4/6/10</td>
      <td>5E</td>
      <td>Enough refrigerated storage equipment is not p...</td>
      <td>Critical Violation</td>
      <td>8.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>11/30/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>554131</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Log Cabin (The)</td>
      <td>2813 Route 11,  Lafayette</td>
      <td>8/8/07</td>
      <td>5E</td>
      <td>Enough refrigerated storage equipment is not p...</td>
      <td>Critical Violation</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>541813</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Chili's Grill &amp; Bar</td>
      <td>3954 State Route 31,  Liverpool</td>
      <td>5/20/11</td>
      <td>8A</td>
      <td>Food not protected during storage, preparation...</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>16.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>583739</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1012846</th>
      <td>BATTLE ISLAND CLUBHOUSE CAFE</td>
      <td>2150 STATE ROUTE 48,  FULTON</td>
      <td>6/1/16</td>
      <td>8A</td>
      <td>Food not protected during storage, preparation...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Oswego County</td>
      <td>...</td>
      <td>1/18/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>296177</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.359864</td>
      <td>-76.439347</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012847</th>
      <td>Oriental Buffet</td>
      <td>1000 Linden Street,  Ogdensburg</td>
      <td>4/13/17</td>
      <td>13B</td>
      <td>Garbage storage areas not properly constructed...</td>
      <td>Not Critical Violation</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>25.0</td>
      <td>Canton District Office</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>852456</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012848</th>
      <td>WATERHOUSE RESTAURANT, INC.</td>
      <td>85 LAKE AVENUE,  LAKE LUZERNE</td>
      <td>5/11/07</td>
      <td>13B</td>
      <td>Garbage storage areas not properly constructed...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Glens Falls District Office</td>
      <td>...</td>
      <td>9/30/19</td>
      <td>Food Service Establishment</td>
      <td>Catering Operation</td>
      <td>333436</td>
      <td>Re-Inspection</td>
      <td>NaN</td>
      <td>43.310574</td>
      <td>-73.834078</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012849</th>
      <td>CHI</td>
      <td>103  POST  AVENUE,  WESTBURY</td>
      <td>11/4/10</td>
      <td>14A</td>
      <td>Insects, rodents present</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>10/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>684307</td>
      <td>Re-Inspection</td>
      <td>NaN</td>
      <td>40.751950</td>
      <td>-73.587832</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012850</th>
      <td>CHI</td>
      <td>103  POST  AVENUE,  WESTBURY</td>
      <td>11/9/15</td>
      <td>14A</td>
      <td>Insects, rodents present</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>10/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>684307</td>
      <td>Inspection</td>
      <td>Michael Landesberg  exp. December 2016\r\n80 s...</td>
      <td>40.751950</td>
      <td>-73.587832</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012851</th>
      <td>Asian Cafe</td>
      <td>701 SOUTH Crouse AVENUE,  Syracuse</td>
      <td>9/29/16</td>
      <td>14A</td>
      <td>Insects, rodents present</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>888408</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012852</th>
      <td>LOGAN'S BAR &amp; GRILL</td>
      <td>NY STATE ROUTE 8,  SPECULATOR</td>
      <td>8/23/11</td>
      <td>9C</td>
      <td>Hair is improperly restrained</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>Saranac Lake District Office</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant/Catering Operation</td>
      <td>359927</td>
      <td>Re-Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012853</th>
      <td>FAMILY QUICK STOP</td>
      <td>8 WEST MAIN STREET,  PAWLING</td>
      <td>10/13/10</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Delicatessen</td>
      <td>273915</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.561949</td>
      <td>-73.602084</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012854</th>
      <td>MAIN MOON CHINESE RESTAURANT</td>
      <td>190 INNIS AVENUE,  POUGHKEEPSIE</td>
      <td>1/10/12</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>274977</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.709212</td>
      <td>-73.902991</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012855</th>
      <td>PEARL EAST</td>
      <td>1191 NORTHERN  BOULEVARD,  MANHASSET</td>
      <td>10/9/09</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>12.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>570275</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.791110</td>
      <td>-73.702007</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012856</th>
      <td>PAT'S PIZZA</td>
      <td>3527 HEMPSTEAD TURNPIKE,  LEVITTOWN</td>
      <td>9/12/14</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>8.0</td>
      <td>Nassau  County</td>
      <td>...</td>
      <td>5/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>708866</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.725671</td>
      <td>-73.503203</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012857</th>
      <td>CLANCY'S BAR &amp; RESTAURANT</td>
      <td>7001 PACKARD ROAD,  NIAGARA FALLS</td>
      <td>5/29/14</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Niagara County</td>
      <td>...</td>
      <td>11/30/17</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>851497</td>
      <td>Inspection</td>
      <td>8A--Product in walk-in cooler found on the flo...</td>
      <td>43.108995</td>
      <td>-78.984691</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012858</th>
      <td>MAIN MOON</td>
      <td>480 EXCHANGE  STREET,  GENEVA</td>
      <td>12/16/15</td>
      <td>14B</td>
      <td>Effective measures not used to control entranc...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Geneva District Office</td>
      <td>...</td>
      <td>5/31/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>327228</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.867501</td>
      <td>-76.981709</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012859</th>
      <td>PIZZA CENTRAL</td>
      <td>1123 CENTRAL  AVENUE,  ALBANY</td>
      <td>1/30/12</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Albany County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>738894</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.690276</td>
      <td>-73.801627</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012860</th>
      <td>PIZZA CENTRAL</td>
      <td>1123 CENTRAL  AVENUE,  ALBANY</td>
      <td>1/5/15</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Albany County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>738894</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.690276</td>
      <td>-73.801627</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012861</th>
      <td>KFC/TACO BELL</td>
      <td>270 EAST Fairmount AVENUE,  Lakewood</td>
      <td>1/22/16</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Chautauqua County</td>
      <td>...</td>
      <td>6/30/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>264521</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.097931</td>
      <td>-79.308788</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012862</th>
      <td>Highland Grill</td>
      <td>208 Highland AVENUE,  East Syracuse</td>
      <td>10/9/09</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Tavern</td>
      <td>292801</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.065939</td>
      <td>-76.078986</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012863</th>
      <td>TRAILS END INN</td>
      <td>62 TRAILS END WAY,  KEENE VALLEY</td>
      <td>8/5/16</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Saranac Lake District Office</td>
      <td>...</td>
      <td>11/30/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>357641</td>
      <td>Inspection</td>
      <td>No violations observed.  All food observed to ...</td>
      <td>44.187500</td>
      <td>-73.789105</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012864</th>
      <td>TRAILS END INN</td>
      <td>62 TRAILS END WAY,  KEENE VALLEY</td>
      <td>9/12/08</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>Saranac Lake District Office</td>
      <td>...</td>
      <td>11/30/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>357641</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>44.187500</td>
      <td>-73.789105</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012865</th>
      <td>RED LOBSTER #0654</td>
      <td>20831 STATE ROUTE 3,  WATERTOWN</td>
      <td>6/16/10</td>
      <td>11D</td>
      <td>Non food contact surfaces of equipment not clean</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Watertown District Office</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>363710</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012866</th>
      <td>EAGLE'S AERIE #782</td>
      <td>19260 US ROUTE 11,  WATERTOWN</td>
      <td>8/18/10</td>
      <td>1H</td>
      <td>Food from unapproved source, spoiled, adultera...</td>
      <td>Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>Watertown District Office</td>
      <td>...</td>
      <td>12/31/17</td>
      <td>Institutional Food Service</td>
      <td>Religious, Charitable, Fraternal Organization</td>
      <td>362519</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.946058</td>
      <td>-75.915373</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012867</th>
      <td>RANI MAHAL FINE INDIAN CUISINE</td>
      <td>327 MAMARONECK AVENUE,  MAMARONECK</td>
      <td>11/16/09</td>
      <td>10B</td>
      <td>Non-food contact surfaces and equipment are im...</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>9/30/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>557048</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>40.951349</td>
      <td>-73.735134</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012868</th>
      <td>WALTER PANAS H.S.</td>
      <td>300 CROTON AVENUE,  CORTLANDT MANOR</td>
      <td>12/3/10</td>
      <td>8A</td>
      <td>Food not protected during storage, preparation...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Institutional Food Service</td>
      <td>School K-12 Food Service</td>
      <td>455388</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.277555</td>
      <td>-73.859162</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012869</th>
      <td>Mama Nancy's</td>
      <td>512 State Fair BOULEVARD,  Syracuse</td>
      <td>1/5/06</td>
      <td>15A</td>
      <td>Floors, walls, ceilings, not smooth, properly ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>1/31/18</td>
      <td>Food Service Establishment</td>
      <td>Restaurant</td>
      <td>539422</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.059365</td>
      <td>-76.181807</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012870</th>
      <td>Fabius-Pompey High School</td>
      <td>1211 MILL STREET,  FABIUS</td>
      <td>5/25/07</td>
      <td>8E</td>
      <td>Accurate thermometers not available or used to...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Institutional Food Service</td>
      <td>School K-12 Food Service</td>
      <td>467310</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>42.830331</td>
      <td>-75.984893</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012871</th>
      <td>Fayetteville-Manlius H.S.-House I</td>
      <td>8201 EAST SENECA TURNPIKE,  MANLIUS</td>
      <td>1/9/09</td>
      <td>14A</td>
      <td>Insects, rodents present</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.0</td>
      <td>Onondaga County</td>
      <td>...</td>
      <td>12/31/18</td>
      <td>Institutional Food Service</td>
      <td>School K-12 Food Service</td>
      <td>466874</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>43.007392</td>
      <td>-75.959716</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012872</th>
      <td>DUTCHESS MANOR</td>
      <td>263 ROUTE 9D,  BEACON</td>
      <td>10/30/14</td>
      <td>8A</td>
      <td>Food not protected during storage, preparation...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>2/28/18</td>
      <td>Food Service Establishment</td>
      <td>Catering Operation</td>
      <td>273815</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.460090</td>
      <td>-73.980870</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012873</th>
      <td>ST MARY'S SCHOOL-WAPPINGERS</td>
      <td>2 CONVENT  AVENUE,  WAPPINGERS FALLS</td>
      <td>10/31/06</td>
      <td>None</td>
      <td>NaN</td>
      <td>Not Critical Violation</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Dutchess County</td>
      <td>...</td>
      <td>3/31/18</td>
      <td>Institutional Food Service</td>
      <td>School K-12 Food Service</td>
      <td>498508</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.604242</td>
      <td>-73.921903</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012874</th>
      <td>SKYVIEW REHABILITATION &amp; HEALTHCARE</td>
      <td>1280 ALBANY POST ROAD,  CROTON-ON-HUDSON</td>
      <td>11/29/16</td>
      <td>15B</td>
      <td>Lighting and ventilation inadequate, fixtures ...</td>
      <td>Not Critical Violation</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>Westchester County</td>
      <td>...</td>
      <td>4/30/18</td>
      <td>Food Service Establishment</td>
      <td>Commissary</td>
      <td>580046</td>
      <td>Re-Inspection</td>
      <td>Discussed: Remaining violations must be comple...</td>
      <td>41.224770</td>
      <td>-73.908280</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1012875</th>
      <td>LIMONCELLO</td>
      <td>159-167  MAIN STREET,  GOSHEN</td>
      <td>11/6/08</td>
      <td>8C</td>
      <td>Improper use and storage of clean, sanitized e...</td>
      <td>Not Critical Violation</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>6.0</td>
      <td>Orange County</td>
      <td>...</td>
      <td>9/30/18</td>
      <td>Food Service Establishment</td>
      <td>Food Service Establishment</td>
      <td>601490</td>
      <td>Inspection</td>
      <td>NaN</td>
      <td>41.403220</td>
      <td>-74.320562</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1012876 rows × 25 columns</p>
</div>




```python
# SERVICE REQUESTS
service_requests = service_requests_df[['incident_zip', 'complaint_type']]
service_requests = service_requests[service_requests['complaint_type'].isin(['Food Poisoning','Food Establishment'])]

# Grouby
service_requests = service_requests.drop(['complaint_type'], axis=1)
food_poison = service_requests.groupby(['incident_zip']).size()

food_poison = food_poison.to_frame()
food_poison = food_poison.rename(columns={'incident_zip': 'zipcode',0:'total_services_requests'})

# FOOD INSPECTIONS
food_inspections = food_inspections_df[['zipcode','num_critical']]#, 'num_critical_not_corrected', 'num_noncritical']]

# Clean data
food_inspections['zipcode'] = food_inspections['zipcode'].astype(str)
food_inspections = food_inspections.groupby(['zipcode']).sum().reset_index()

food_inspections = food_inspections[food_inspections['zipcode'].apply(lambda x: len(x)==5)]
food_inspections = food_inspections.rename(columns={'num_critical':'total_inspections'})
food_inspections = food_inspections.set_index('zipcode')
#food_inspections = food_inspections.to_frame()
#food_inspections = food_inspections.rename(columns={0:'total_inspections'})

```

    /anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:16: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      app.launch_new_instance()



```python
import matplotlib.pyplot as plt

# Inner join 
joined = food_poison.join(food_inspections, how='inner')

requests = joined['total_services_requests'].values
violations = joined['total_inspections'].values


plt.figure(figsize=(15,7))
plt.scatter(requests, violations,s=20,color='b')

# Format
plt.title('Contamination Complaints vs Inspection Violations by Zipcode', fontsize=15)
plt.tick_params(top='off', bottom='off', left='off', right='off', labelleft='on', labelbottom='on')
plt.xlabel('Complaints')
plt.ylabel('Inspections')

ax = plt.gca()
ax.spines['right'].set_visible(False)
ax.spines['top'].set_visible(False)

plt.show()


```


![png](test1_files/test1_3_0.png)



```python
joined.to_csv('table1.csv')
```
