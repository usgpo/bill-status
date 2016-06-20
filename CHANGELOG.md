__Completed June 2016__
* Adjust formatting of the actionTime element - Change THIS value <actionTime>03:36PM</actionTime> 
to this value <actionTime>15:36:00</actionTime>. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hjres/BILLSTATUS-114hjres88.xml 
* Adjust values used for <billType> - <billType>SCONRES</billType> values replace <type>S.Con.Res.</type> values for related bills. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hr/BILLSTATUS-114hr5471.xml
* Adjust CBO child node attribute names. Change these attribute names within cboCostEstimates: rptPubDate to pubDate; rptTitle to title; rptUrl to url. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hr/BILLSTATUS-114hr3209.xml
* Remove <isReserved>. There is only one possible value: False. See https://www.congress.gov/help/legislative-glossary#glossary_reservedbillnumbers for background.

__Completed August 2015__
* Populate <isByRequest> element with primary source data. Expect values: Single Sponsor by request, Two Sponsors by request, and Multiple Sponsors by request. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/113/hr/BILLSTATUS-113hr4435.xml

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/113/s/BILLSTATUS-113s1237.xml
* <sourceSystem> name and code Expect values: House committee actions (1); House floor actions (2); Senate (0); Library of Congress (9) 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/s/BILLSTATUS-114s178.xml 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/s/BILLSTATUS-114s178.xml 
* Sponsors and cosponsors endpoints include <bioguide> as a separate field in addition to the URL. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hr/BILLSTATUS-114hr61.xml
* Add legislative calendar data in <calendarNumbers>. 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/s/BILLSTATUS-114s625.xml 

EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/113/hr/BILLSTATUS-113hr4435.xml 


