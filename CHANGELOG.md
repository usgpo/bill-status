Completed June 2016
* Adjust formatting of the actionTime element - Change THIS value <actionTime>03:36PM</actionTime> 
to this value <actionTime>15:36:00</actionTime>. EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hjres/BILLSTATUS-114hjres88.xml 
* Adjust values used for <billType> - <billType>SCONRES</billType> values replace <type>S.Con.Res.</type> values for related bills. EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hr/BILLSTATUS-114hr5471.xml
* Adjust CBO child node attribute names. Change these attribute names within cboCostEstimates: rptPubDate to pubDate; rptTitle to title; rptUrl to url. EXAMPLE: https://www.gpo.gov/fdsys/bulkdata/BILLSTATUS/114/hr/BILLSTATUS-114hr3209.xml
* Remove <isReserved> from API. There is only one possible value: False. See https://www.congress.gov/help/legislative-glossary#glossary_reservedbillnumbers for background.




