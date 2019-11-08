# Estimating the Business Impact of Wildfires According to FEMA's Seven Lifelines

---

## Executive Summary
More than 80 natural disasters strike the United States every year, causing extensive property destruction and loss of life. The Federal Emergency Management Agency, or FEMA, works with first responders to support citizens in the preparedness for, response to, protection from , and recovery from all natural disaster hazards. Some of their primary challenges as an organization are their ability and efficiency in responding to disasters as they first occur, as well as how to manage ongoing disasters. 

As a disaster first occurs and is ongoing, FEMA officials must determine the businesses and organizations that must receive priority assistance in order to best help citizens during a time of crisis. FEMA developed a framework to better respond to disasters. Utilizing the Lifelines framework, FEMA officials can prioritize and focus response efforts, utilize a common lexicon, facilitate unity of purpose and better communication, and clarify which components of the disaster require cross-sector coordination. The seven lifelines identified are as follows:
1. Safety & Security
2. Food, Water, Sheltering
3. Health & Medical
4. Energy (Power & Fuel)
5. Communications
6. Transportation
7. Hazardous Material

In recent years, the frequency and impact of wildfires in the United States has exponentially increased, with California being one of the main states impacted. In 2018, there were 8,054 fires in California that burned 1,823,152 acres, compared to in 2010, when 6,502 fires burned 108,742 acres. Additionally, there are significant financial and human losses as a result of these fires. In 2018 alone, there were 85 lives lost and a $400 billion impact to the state. San Diego and its surrounding communities in particular have been affected by some of the largest impacting fires in the last two decades. The Cedar fire in October 2003 claimed 273,246 acres, 2,820 structures, and 15 lives from San Diego County. Also in San Diego County, the Witch fire claimed 197,990 acres, 1,650 structures, and 2 lives in October 2007. Both the Cedar and Witch fires are among top 10 most destructive fires in California's recorded wildfire history. 

---

## Problem Statement

The challenge that we set out to address was how we can help FEMA to identify businesses that may have been impacted in a disaster zone, and which Lifeline those businesses may align to. Utilizing this information, we aimed to create an interactive map for visualizing these Lifeline locations in relation to areas that have historically been affected by disasters and areas that are at risk to be affected in the future. We applied this technique to San Diego County, however the idea was to create a method and results that could be carried out for any other location in the United States.

---

## Table of Contents

* Included in this repository:
    * [01-Code](./01-Code): scraping, cleaning, combining datasets 
    * [02-Data](./02-Data): Yelp, Google, historical fire disaster perimeters, current high risk fire areas
    * [03-Webapp-Images](./03-Webapp-Images): screenshots taken from ARCGIS webapp
* Tools
* Data Description
* Problem Approach
    * Collecting Data
    * Aligning the Lifelines
    * Mapping
* Conclusions
* Improvements and Next Steps
* Authors
* Resources
* Additional Resources for Wildfire Information

Additionally, we created a static site with this information: https://sites.google.com/view/fema-lifeline-business-lines/home

---

## Tools
The tools we used in preparing this analysis and technical report include the following: 
* Google API 
* Yelp API 
* Python
* ArcGIS
* Tableau
* Google Sites

---

## Data Description
The following data sources are included in our analysis:
* **Google Places:** Businesses and organizations, the category or type of business, latitude, longitude, and formatted address found using Google Places API. 
* **Yelp:** Businesses and organizations, the category or type of business, latitude, longitude, and formatted address found using Yelp API. 
* **San Diego County Disasters:** Historical data on type and dates of disasters that have occurred in San Diego County from FEMA's website. 
* **Fire Perimeters:** Perimeters of areas affected by wildfire disasters.
* **Wildfire Risk:** Current area in San Diego County at high risk of fire danger.
* **Lifeline Information:** Lifelines descriptions and categories for classifying businesses and organizations, as defined by FEMA.

---

## Problem Approach
In addressing this problem for FEMA and New Light Technologies, we used the following approach:
1. Collection and Cleaning of data 
2. Align the Lifelines
3. Mapping
4. Conclusions and Next Steps

### Collection and Cleaning of Data 
Our original prompt suggested using Yelp API data, which we set out to do. We quickly learned, both from looking at the data we received and consulting previous GA students' projects, that this data is not very robust and did not include enough information to solely rely on Yelp. We decided to also incorporate data from Google Places utilizing their API. In addition to the location data, we had to use definitions and descriptions of what the actual FEMA lifelines are from FEMA's website. This formed the basis of the data we used for mapping.

In order to add context to the map, we collected data on historical disasters affecting the San Diego County area. We found specific perimeteres of the areas in the county affected by some of the historically most damaging fires. We also found data from USDA that shows the current wildfire high risk zones, which was also added to our map.

### Align the Lifelines
What kind of businesses or organizations align to each FEMA Lifeline? See below for a breakdown of the search terms and categories/types we used to determine this. We used the following alignment to align each business on our map to a FEMA Lifeline.

| # | Lifeline | Components | Google 'types' | Google Search Terms | Yelp Categories |
| --- | --- | --- | --- | --- | --- |
| 1 | Safety and Security | Law Enforcement/Security<br>Search and Rescue<br>Fire Services<br>Government Service<br>Responder Safety<br>Imminent Hazard Mitigation | police<br>fire_station<br>local_government_office | police department<br>police organization<br>emergency management<br>fire department<br>government services | fire departments <br>police departments<br>municipality<br>jailsandprisons<br>post offices<br>courthouses |
| 2 | Food, Water, Sheltering | Evacuations<br>Food/Potable Water<br>Shelter<br>Durable Goods<br>Water Infrastructure<br>Agriculture | stadium<br>store<br>supermarket<br>grocery<br>grocery_or_supermarket<br>lodging | animal shelters <br>community centers<br>homeless shelters<br>stadiums arenas<br>water purification<br>food delivery services<br>food banks<br>water delivery<br>water stores<br>water suppliers | food banks<br>animal shelters<br>homeless shelters<br>community centers<br>water purification <br>food delivery services<br>food banks<br>water delivery<br>water stores<br>water suppliers<br>stadium<br>store<br>supermarket<br>grocery<br>grocery_or_supermarket |
| 3 | Health and Medical | Medical Care<br>Patient Movement<br>Public Health<br>Fatality Management<br>Health Care Supply Chain | doctor<br>hospital<br>veterinary_care | counciling and mental health<br>med centers<br>hospitals<br>emergency rooms<br>urgent_care<br>cremation services | emergency medicine<br>emergency rooms<br>hospitals<br>med centers<br>urgent_care<br>assisted living |
| 4 | Energy | Power (Grid)<br>Temporary Power<br>Fuel | gas_station | Fuel supplier<br>pipeline<br>gas company<br>Electrical equipment supplier<br>Electrical substation<br>power plant<br>nuclear power plant | fuel docks<br>service stations<br>utilities<br> electricity suppliers<br>ev charging stations<br>natural gas suppliers |
| 5 | Communications | Infrastructure<br>Alerts, Warnings, Messages<br>911 and Dispatch<br>Responder Communications<br>Financial Services | bank<br>atm<br>city_hall<br>post_office | cell towers<br>radio stations<br>television stations<br>banks | telecommunications<br>printmedia<br>radio stations<br>television stations<br>isps |
| 6 | Transportation | Highway/Roadway<br>Mass Transit<br>Railway<br>Aviation<br>Maritime<br>Pipeline | airport<br>bus_station<br>subway_station<br>train_station<br>transit_station<br>light_rail_station | roadside assist<br>towing<br>buses<br>metro station<br>public transport<br>metro stations<br>bus stations<br>train stations<br>airport<br>port<br>pipeline | transport all |
| 7 | Hazardous Material | Facilities<br>Hazardous Debris<br>Pollutants<br>Contaminants | NA | hazardous waste<br>nuclear power plant | biohazard cleanup<br>hazardous waste disposal<br>recycling center |

---

### Mapping
Once our data was collected and aligned with a FEMA lifeline, we mapped those locations out along with the historical disaster-affected areas and the current high risk zones. We wanted to provide a map that was intuitive and provided the most value, so we tested a few different options before deciding on a final option.

**Google Earth**

While this was easy to map, the image was not very clear and was not very interactive. It was also not possible to map the Lifeline businesses and then add layers of fire perimeters or current fire risk zones.

**BIOS**


**ArcGIS**

Ultimately, we decided ArcGIS provided the best usability, interactiveness, and visuals. We could apply many layers to this map and update those layers simply and efficiently. We included layers of all businesses color-coded by Lifeline, the perimeters of historical wildfire disasters, and current high risk fire zones.

[starting map](./03-Webapp-Images/Starting-Map.png)

---

## Conclusions
Using data from Google, Yelp, FEMA, and the USDA, we were able to create a map that shows the businesses in San Diego county and to which FEMA Lifeline those businesses align. Addtionally, we were able to add layers to the map of the perimeters of areas that were previously affected by a wildfire disaster or are in a high risk area that could be affected in the future. This information can help FEMA decision-makers to mobilize and anticipate resource needs during a disaster. 

The map is a tool that can be used as a starting point to determine evacuation plans, or estimate potential or actual impact from a disaster. Knowing locations and which lifeline they map to can help disaster response teams more quickly help those locations or provide aid to those who need it during a disaster.

---

## Improvements and Next Steps

We recommend to New Light Technologies and FEMA to invest in public and private technology partnerships. With the valuable tools we found to complete this analysis, we were able to paint a picture of how businesses and access to Lifelines could be impacted by a disaster. With less barriers (scrape limits/delays, software costs), our process could be reproduced in minimal time for any location in the United States. Technology partnerships would greatly increase the efficiency of identifying and mapping a disaster to assess its impact.

Additionally, if a partnership was established with platforms like Yelp or Google, they could add new features to better help FEMA in their response. Adding visible fields on their sites that note if the business is in an area affected by a disaster and whether or not that business is open as a result of the disaster could streamline our method even further.

The ArcGIS map that was used to create our map was built through a free trial. For next steps, we recommend investing in this type of software to enhance this map and apply it to other areas affected by disasters. It has a software usage fee of $500 per year.

The map is an example of what could be used for any area in the US that might be affected by a disaster. To make this process easier for FEMA and its contractors, we recommend investing in and acquiring new technologies that help to efficiently and effectively map out the information that we mapped out in this analysis. Additionally, partnering with a tech company like Google to provide businesses an opportunity to put their open status on Google after a disaster can benefit response teams to more quickly assess the status of a disaster. Currently, one of the well-known ways that FEMA assesses the damage is through the [Waffle House Index](https://www.fema.gov/blog/2011-07-07/news-day-what-do-waffle-houses-have-do-risk-management). Implementing a tech partnership to make it easier for all businesses to communicate their status can paint a better picture of the status after a disaster. 

---

## Authors
* **Brenda Hali**
* **Jessie Owens**
* **John Kirby**
* **Larry Curran**

---

## Resources
* Many GA students before us have worked on this problem, and we would not have been able to get as far without referring to their work:
    * [ATL](https://github.com/awharmon/FEMA-Lifelines-Categorization-for-Disaster-Response)
    * [ATX](https://github.com/adriancampos1/GA_DSI8_FEMA_Lifelines)
    * [DEN](https://github.com/meldev00/FEMA_disaster_tool)
* [FEMA Lifelines Framework](https://www.fema.gov/media-library-data/1544469177002-251a503b3717f0d6d483bae6169f4106/Revised_Community_Lifelines_Information_Sheet.pdf)
* [FEMA Lifelines Response Toolkit](https://www.fema.gov/media-library-data/1550596598262-99b1671f270c18c934294a449bcca3ce/Tab1b.CommunityLifelinesResponseToolkit_508.pdf)
* [Insurance Information Institute Facts & Statistics: Wildfires](https://www.iii.org/fact-statistic/facts-statistics-wildfires#Wildfires%20by%20year)
* [USDA Probabilistic Wildfire Risk](https://apps.fs.usda.gov/arcx/rest/services/RDW_Wildfire/ProbabilisticWildfireRisk/MapServer)
* [FEMA Historical Disaster Declarations](https://www.fema.gov/openfema-dataset-disaster-declarations-summaries-v1)
* [California Government Data on Fire Perimeters](https://map.dfg.ca.gov/metadata/ds0396.html)
* [Yelp Fusion API](https://www.yelp.com/fusion)
* [Google Places API](https://cloud.google.com/maps-platform/places/?utm_source=google&utm_medium=cpc&utm_campaign=FY18-Q2-global-demandgen-paidsearchonnetworkhouseads-cs-maps_contactsal_saf&utm_content=text-ad-none-none-DEV_c-CRE_315916117679-ADGP_Hybrid+%7C+AW+SEM+%7C+BKWS+~+Google+Maps+Places+API-KWID_43700039136946201-aud-543033638149:kwd-301485308762-userloc_9061285&utm_term=KW_%2Bgoogle%20%2Bplaces%20%2Bapi-ST_%2Bgoogle+%2Bplaces+%2Bapi&gclid=Cj0KCQiAtf_tBRDtARIsAIbAKe2R2vm_LUh1w7EmpAMzDouKnI7fKGonY279Baz_lOh0LnA5Gd9M1rsaAooVEALw_wcB)
* [Estimated economic impact of 2018 wildfires](https://www.accuweather.com/en/weather-news/accuweather-predicts-2018-wildfires-will-cost-california-total-economic-losses-of-400-billion/70006691)

---

## Additional Resources for Wildfire Information:
There are many resources to learn about the impact of preparedness for wildfires as they are occuring and how to prepare for them. The following are some of the valuable tools and information resources that we found throughout the process of preparing our technical report and analysis but did not reference in our work:
* An interactive real-time map produced by the LA Times showing all current active wildfires, when it started burning, and how much of it has been contained: https://www.latimes.com/wildfires-map/
* The "Know Your Hazards" interactive map from ArcGIS that upon entering a street address, informs you what types of natural disasters and hazards you might be affected by: http://www.arcgis.com/apps/webappviewer/index.html?id=1f35f94756bc45f9960717cbd15488a8 or in Spanish: https://www.readysandiego.org/es-us/
* Alert San Diego is a regional notification system to alert those that have been impacted by or are in danger of being impacted by emergencies or disasters in the area. This was created by the County of San Diego in partnership with Blackboard Connect Inc. Individuals can enroll through https://www.readysandiego.org/alertsandiego/ or in Spanish at https://www.readysandiego.org/content/oesready/es/alertsandiego.html
* San Diego county local government has made great efforts to prepare for any type of disaster, including their emergency website: https://www.sdcountyemergency.com/content/oesemergency/en-us/resources/law-enforcement-fire-agencies-government-agencies.html
* The San Diego Supercomputer Center are trying to predict where active wildfires will spread next: https://www.nytimes.com/2019/06/24/us/wildfires-big-data-california.html
* Map of disaster losses per zip code: https://www.nytimes.com/interactive/2018/05/24/us/disasters-hurricanes-wildfires-storms.html?hp&amp;action=click&amp;pgtype=Homepage&amp;clickSource=story-heading&amp;module=second-column-region&amp;region=top-news&amp;WT.nav=top-news
* San Diego Fire Safety Review https://www.fs.usda.gov/Internet/FSE_DOCUMENTS/stelprdb5297014.pdf
https://www.thebalance.com/wildfires-economic-impact-4160764
* Stanford estimated cost of wildfires https://searchworks.stanford.edu/view/xj043rd8767
* Impact of climate change on wildfires in the western United States https://www.pnas.org/content/113/42/11770
* Study from National Bureau of Economic Research on impact of disasters https://www.documentcloud.org/documents/4941265-2017-NBER-the-Effect-of-Natural-Disasters-on.html
