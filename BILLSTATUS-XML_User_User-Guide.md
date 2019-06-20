
# Bill Status XML Bulk Data
# User Guide 

# Contents

[1. Introduction](#1.-Introduction)
[2. XML Descriptions](#2.-XML-Descriptions)
[3. Action Code Element Possible Values](#3.-Action-Code-Element-Possible-Values)
[4. Actions Type Element Possible Values](#4.-Actions-Type-Element-Possible-Values)
[5. Mapping of LOC Summaries Version Codes and Action Description Text](#5.-Mapping-of-LOC-Summaries-Version-Codes-and-Action-Description-Text)
[6. Title Type Possible Values](#6.-Title-Type-Possible-Values)
[7. Data Set](#7.-Data-Set)
[8. Resources Directory](#8-Resources-Directory)

# 1. Introduction

At the direction of the U.S. House of Representatives Appropriations Committee, in support of the Legislative Branch Bulk Data Task Force ([footnote](#footnote)), the Government Publishing Office (GPO), the Library of Congress (LOC), the Clerk of the House, and the Secretary of the Senate are making Bill Statuses in XML format available through the GPO's govinfo Bulk Data repository starting with the 113th Congress. The govinfo Bulk Data repository for Bill Status information is available at [https://www.govinfo.gov/bulkdata/BILLSTATUS/resources](https://www.govinfo.gov/bulkdata/BILLSTATUS/resources).

Please see [https://www.govinfo.gov](https://www.govinfo.gov/) or [https://www.congress.gov](https://www.congress.gov/) for access to individual House and Senate Congressional Bills in PDF, XML, and HTML formats.

## 1.1. Bill Types

### Bills

- House Bill (HR)
- Senate Bill (S)

A bill is a legislative proposal before Congress. Bills from each house are assigned a number in the order in which they are introduced, starting at the beginning of each Congress (first and second sessions). Public bills pertain to matters that affect the general public or classes of citizens, while private bills pertain to individual matters that affect individuals and organizations.

### Joint Resolutions

- House Joint Resolution (HJRES)
- Senate Joint Resolution (SJRES)

Like a bill, a joint resolution is a legislative proposal that requires the approval of both houses and the signature of the President. It has the force of law, if approved. Resolutions from each house are assigned a number in the order in which they are introduced, starting at the beginning of each Congress (first and second sessions). Joint resolutions generally are used for limited matters, such as a single appropriation for a specific purpose. They are also used to propose amendments to the Constitution. These types of joint resolutions do not require the President's signature if three-quarters of the states have ratified them.

### Concurrent Resolutions

- House Concurrent Resolution (HCONRES)
- Senate Concurrent Resolution (SCONRES)

A concurrent resolution is a legislative proposal that requires the approval of both houses but does not require the signature of the President and does not have the force of law. Concurrent resolutions generally are used to make or amend rules that apply to both houses. They are also used to express the sentiments of both of the houses. For example, a concurrent resolution is used to set the time of Congress' adjournment. It may also be used by Congress to convey congratulations to another country on the anniversary of its independence.

### Simple Resolutions

- House Simple Resolution (HRES)
- Senate Simple Resolution (SRES)

A simple resolution is a legislative proposal that addresses matters entirely within the prerogative of one house or the other. It requires neither the approval of the other house nor the signature of the President, and it does not have the force of law. Most simple resolutions concern the rules of one house. They are also used to express the sentiments of a single house. For example, a simple resolution may offer condolences to the family of a deceased member of Congress, or it may express the sense of the Senate or House on foreign policy or other executive business.

Additional information about bill types can be found at [http://www.gpo.gov/help/index.html#about\_congressional\_bills.htm](http://www.gpo.gov/help/index.html#about_congressional_bills.htm).

## 1.2. Scope of Bulk Data

The Bill Status bulk data collection on govinfo includes XML bills statuses from 2013 (113th Congress) forward.

## 1.3. Bulk Data Downloads

The Bulk Data repository is organized by Congress and bill type. A ZIP file is available for each bill type and contains Bill Status XML files for that bill type within a specific Congress. Each Bill Status XML file contains information about legislation under consideration for a specific measure.

# 2. XML Descriptions

The following conventions are used in this document:

- Top-level XML element names are denoted with angled brackets and in courier. For example, `<title>` is an XML element. Any children of the elements are described within the table and are not denoted with angle brackets or courier.

## 2.1.Elements
This section provides available element names and their descriptions

### `<billStatus>` 
Root element. 
### `<bill>`
 Parent container for a single legislative measure.   |
### `<actions>` 
Parent container for actions. The "Actions" element may include the following children:  

- actionByCounts _See Note_.  
    - houseOfRepresentatives  
    - senate  
    - bothChambers
    
- actionTypeCounts _See Note_.
     - Various children such as:
	     - actionStageOverride
	    - becamePublicLaw
    - committeeReportOfABill
    - generalDebate,
    - passedAgreedToInHouse
    - passedSenate
  
- actions
  - item
    - actionCode – _See table 3 (below) for Action Code Element Possible Values_
    - actionDate (e.g., 2014-02-11)
    - actionTime (e.g., 18:16:46; _Note: Only present for House floor actions_ ONLY process timestamps when sourceSystem code value=2)
    - committee
      - name
      - systemCode (e.g., ssju00). _See_ [_https://www.congress.gov/help/field-values/current-committees_](https://www.congress.gov/help/field-values/current-committees).
    - links
      - link
        - name (e.g.,  Roll no. 60)
        - url (e.g., http://clerk.house.gov/evs/2014/roll060.xml; https://www.congress.gov/congressional-record/2015/senate-section/page/S2613-2625)
    - sourceSystem
      - code (Possible values are 0, 1, 2, and 9.)
      - name (Possible values are House, House committee actions, Senate, and Library of Congress.)
    - text (e.g., Motion to table the veto message to accompany S. J. Res. 8 agreed to in Senate by Yea-Nay Vote. 96 - 3. Record Vote Number: 172. (consideration: CR S2644))
    - type _See table 4 (below) for Action Type Element Possible Values Note: `<actionbyCounts>`, `<actionTypeCounts>`, and `<type>` elements support Congress.gov facets and data processing; they do not represent House or Senate legislative process activities._
Note: `<sourceSystem>` and `<type>` are often required to disambiguate Action Codes._Note: Content in the Type element will be changed in 2016 to match this documentation._

### `<amendments>`
Parent container for amendments. The Amendments element may include the following children:

- amendment
  - congress (e.g., 114)
  - description
  - latestAction
    - actionDate (e.g., 2015-03-24)
    - text (e.g., Amendment SA 498 agreed to in Senate by Yea-Nay Vote. 75 - 24. Record Vote Number: 83.)
  - number (e.g., 498)
  - purpose (e.g., To establish a deficit-neutral reserve fund relating to legislation submitted to Congress by President Obama to protect and strengthen Social Security.)
  - type (e.g. HAMDT, SAMDT)
  - actions
    - count
    - actionByCounts
    - actionTypeCounts
    - item
      - actionCode – _See table 3 (below) for Action Code Element Possible Values_
      - actionDate (e.g., 2016-01-06)
      - actionTime _(e.g., 08:22PM; Note: Only present for House floor actions)_
      - committee
	    - name
	    - systemCode (e.g., ssju00). _See https://www.congress.gov/help/field-values/current-committees._
	- links
	  - link
	    - name (e.g., Roll no. 17)
		- url (e.g., http://clerk.house.gov/evs2016/roll017.xml; https://www.congress.gov/congressional-record/2015/senate-section/page/S2613-2625)
	- sourceSystem
	  - code (Possible values are 0, 1, 2, and 9)
	  - name (Possible values are House, House committee actions, Senate, and Library of Congress.)
	- text (e.g., By unanimous consent, the Murphy (FL) amendment was withdrawn. (consideration: CR H87))
- amendedAmendment
- amendedBill
  - congress
  - number
  - originChamber
  - originChamberCode
  - title
  - type
  
Note: Amendments to Amendments are now available.
  

### `<billNumber>` 
Numerical bill number.  _Note: See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for information about "reserved bill numbers."_
### `<billType>`
Bill type (Possible values are H, S, HRES, SRES, HJRES, SJRES, HCONRES, and SCONRES). 
### `<calendarNumbers>`
Parent container for House or Senate calendar numbers. The "Calendar Numbers" element may include the following children:
- item
  - calendar (e.g., Senate Calendar of Business, Senate Executive Calendar)
  - number (e.g., 0192, U00134, H00002, P00021,D00001)
_Note: House calendar codes are U=Union, H=House, P=Private, and D=Discharge._ 

### `<cboCostEstimates>`

Parent container for Congressional Budget Office cost estimates. The "Congressional Budget Office Cost Estimates" element may include the following children:
- item
  - rptPubDate (e.g., 2015-10-08T19:37:56Z)
  - rptTitle (e.g., S. 1300, Adoptive Family Relief Act)
  - rptUrl (e.g., http://www.cbo.gov/publication/50883)

### `<constitutionalAuthorityStatementText>`

Constitutional authority statement about the legislative measure

Example:
``<![CDATA[<pre>From the Congressional Record Online through the Government Publishing Office [<a href='http://www.gpo.gov'>www.gpo.gov</a>]By Mr. FRANKS of Arizona: H.J. Res. 45. Congress has the power to enact this legislation pursuant to the following: Article V of the U.S. Constitution: ``The Congress, whenever two thirds of both Houses shall deem it necessary, shall propose Amendments to this Constitution . . .''\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_[Page H2310]</pre>]]>

_Note: Value is enclosed in CDATA._ 

### `<committeeReports>`
 Parent container for committee reports. The "Committee Reports" element may include the following children:
 
- committeeReport
  -  citation (e.g., H. Rept. 114-182)

_Note: This element will be empty unless a measure has associated reports._ |

### `<committees>`
Parent container for committees. Committees, subcommittees, and references to reports associated with a legislative measure are included here, as well as the nature and date of [committee-related activity](https://www.congress.gov/help/legislative-glossary/#glossary_committeeactivity) and [Congressional report](https://www.congress.gov/help/legislative-glossary/#glossary_congressionalreport) number. The "Committees" element may include the following children:

- billCommittees
  - item
    - activities
      - item
        - date (e.g., 2015-03-27T08:20:51Z)
        - name (e.g., Discharged from)
        - reports
          - item
            - citation (e.g., S. Rept. 114-123)
    - chamber (e.g., House)
    - name (e.g., Energy and Commerce Committee)
    - subcommittees
      - item
        - activities
          - item
            - date (e.g., 2013-07-11T20:29:02Z)
            - name (e.g., reporting)
        - name (e.g., Energy and Power Subcommittee)
        - systemCode (e.g., hsif03)
    - systemCode (e.g., hsif00)
    - type (e.g., standing)

_Note: The `<committees>` element will be empty unless a measure has received committee-related action._ 

### `<congress>`

The number of the Congress (e.g., 114).

### `<cosponsors>` 

Parent container for cosponsors. The "Cosponsors" element may include the following children:

- item
  - firstName (e.g., Pedro)
  - middleName (e.g., Lee)
  - lastName (e.g., Zinke)
  - isOriginalCosponsor (e.g., True)
  - sponsorshipDate (e.g. 2013-01-03)
  - sponsorshipWithdrawnDate
  - identifiers
    - bioguideId (e.g., P000596)
    - gpoId (e.g., 8138)
    - lisID (e.g., 1953)

_Note: This element will be empty unless a measure has cosponsors. 
__Note: Values contained in <sponsorshipWithdrawnDate> include House cosponsor deleted dates and Senate cosponsor withdrawn dates__._ 
_Note:__See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about cosponsors__.
_Note: Name elements will be changed in 2016 to match this documentation._   

### `<createDate>`
The date the record was created for Congress.gov.   |

### `<introducedDate>`

The date the legislative measure was introduced, submitted, offered, or proposed (e.g., 2013-01-03). This element corresponds with the first action date element in the XML file for an introduced measure. 

### `<isByRequest>`

A designation on a measure indicating that the member has introduced the measure on behalf of someone else (e.g., the President or an executive branch agency), or pursuant to statutory requirements, and may not necessarily support its provisions. Possible values are: Single Sponsor by request, Two Sponsors by request, and Multiple Sponsors by request. 

_Note: Please see the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about the designation "by request"__._ |

### `<isReserved>`

_Note: This element will be removed in 2016._

### `<lastAction>`

Parent container for the last action. The "Last Action" element may include the following children:

- actionDate (e.g., 2015-10-16)
- links
  - link
    - name (e.g., Public Law No: 114-70)
    - url (e.g., https://www.congress.gov/114th-congress/senate-bill/261/text/pl)
- text (e.g., Became Public Law No: 114-270.)

_Note: Data from this element also appears within `<actions>` element._ 

### `<laws>`
Parent container for the public or private law citation. The "Laws" element may include the following children:

- item
  - number (e.g., 113-235)
  - type (Possible values are Public Law and Private Law.)

_Note: This element will be empty unless a measure has been enacted into law and the public law number has been assigned._

### `<recordedVotes>`
Parent container for recorded votes. The "Recorded Votes" element may include the following children:

- recordedVote
  - chamber (e.g., Senate, House)
  - congress (e.g., 114)
  - date (e.g., 2015-05-05T22:33:54Z)
  - fullActionName (e.g., MOTION TO CONSIDER)
  - rollNumber (e.g., 66, 563)
  - sessionNumber (e.g., 1, 2)
  - url (e.g., http://www.senate.gov/legislative/LIS/roll\_call\_lists/roll\_call\_vote\_cfm.cfm?&congress=114&session=1&vote=00066)

_Note: When constructing links to Senate roll call votes, the formatting of_ _the ampersand may need to be transformed._

### `<notes>` 
Parent container for notes. The "Notes" element may include the following children:

- Item
  - links
    - link
      - name (e.g., H.Res.776)
      - url (e.g., https://www.congress.gov/bill/113th-congress/house-resolution/776/)
    - text 
       -Example: ``<![CDATA On 7/30/2013, a motion was filed to discharge the Committee on Rules from the consideration of H.Res.306 a resolution providing for consideration of H.Res.36. A discharge petition requires 218 signatures for further action. (Discharge Petition No. <a href="http://clerk.house.gov/113/lrc/pd/petitions/DisPet0004.xml">113-4</a>: text with signatures.]]) The “Text” element is enclosed in CDATA.``
  The "Text" element is enclosed in CDATA.

    - links
      - link
        - name (e.g., H.Res.776)
      - url (e.g., [https://www.congress.gov/bill/113th-congress/house-resolution/776](https://www.congress.gov/bill/113th-congress/house-resolution/306))
      
_Note: See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information._ 

### `<originChamber>`

The chamber in which the measure originated. Possible values are House and Senate.

### `<primarySubject>`

Parent container for primary subjects. There are 33 policy area terms which span across all legislation from 1973 to the present.Legislative analysts at the Library of Congress closely examine each bill and resolution to assign a  [policy area term](https://www.congress.gov/help/legislative-glossary/#glossary_policyareaterm) that best describes the entire legislative measure. This policy area term can be found in the `<name>` element (e.g., Economics and Public Finance)

- parentSubject

_Note: See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about policy area terms._ |

### `<relatedBills>` 

Parent container for related bills. A related bill may be a [companion measure](https://www.congress.gov/help/legislative-glossary/#glossary_companionmeasure), an [identical bill](https://www.congress.gov/help/legislative-glossary/#glossary_identicalbill), a [procedurally-related measure](https://www.congress.gov/help/legislative-glossary/#glossary_procedurallyrelatedmeasure), or one with [substantive similarities](https://www.congress.gov/help/legislative-glossary#glossary_reservedbillnumbershttps://www.congress.gov/help/legislative-glossary/). Legislative analysts at the Library of Congress closely examine bills and resolutions to assign bill relationships. Bill relationships may also be identified by the House or Senate. Bill relationships refer only to same-Congress measures. The "Related Bills" element may include the following children:

- item
  - congress (e.g., 113)
  - latestAction
    - actionDate (e.g., 2014-12-19)
    - text (e.g., Referred to the Subcommittee on Energy and Power.)
  - latestTitle (e.g., Omnibus Territories Act of 2013)
  - number (e.g., 1237)
  - relationshipDetails
    - item
      - identifiedBy (e.g., CRS)
      - type (e.g., Related Bill)
  - type (e.g., S.)

 _Note: The following resources provide information about how to build links to related bills._ 
 
 govinfo
 - https://www.govinfo.gov/link-docs/
 
Congress.gov
-  https://www.congress.gov/bill/`<congress>`/`<type>`/`<number>`
-  [https://www.congress.gov/bill/113/hr/83](https://www.congress.gov/bill/113/hr/83)

_Note: See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about related bills._ 

### `<sponsors>` 

Parent container for sponsors. The "Sponsors" element may include the following children:
- item
  - firstName (e.g., Charles)
  - middleName (e.g., B.)
  - lastName (e.g., Rangel)
  - identifiers
    - bioguideId (e.g. R000053)
    - gpoId (e.g. 9803)
    - lisID (e.g. 944)
_Note: Name elements will be changed in 2016 to match this documentation_

### `<subjects>`

Parent container for subjects. [Legislative subject terms](https://www.congress.gov/help/legislative-glossary/#glossary_legislativesubjectterm) like those found in <otherSubjects> describe a measure's substance and effects. There are approximately 1,000 issue-oriented, entity, and geographic terms. The "Subjects" element may include the following children:

- billSubjects
  - otherSubjects
    - item
      - name (e.g. Alternative and renewable resources)
        - parentSubject
          - name (e.g. Energy)
  - primarySubjects
    - name (e.g. Economics and Public Finance)
      - parentSubject
        - name
_Note:  __See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about legislative subject terms.  _

### `<summaries>` 
Parent container for summaries. Upon introduction of a bill or resolution in the House or Senate, legislative analysts in the [Congressional Research Service](https://www.congress.gov/help/legislative-glossary#glossary_crs)of the Library of Congress write a short summary that objectively describes the measure's significant provisions. Introduced version summaries are subject to length limitations as a matter of policy.

When a measure receives action (e.g. it is reported from a committee or passed by the House or Senate), the analysts then write an expanded summary detailing the measure's effect upon programs and current law. Bill summaries are written as a result of a Congressional action and may not always correspond to a document published by the [Government Publishing Office](https://www.congress.gov/help/legislative-glossary#glossary_gpo). A final public law summary is prepared upon enactment into law. 

Each summary description identifies the date and version of the measure and indicates whether there have been amendments: e.g. Passed House amended (07/19/2013).

See table 5 (below) for Mapping of LOC Action Codes for Summaries, Action Description Text, and Version Codes. The "Summaries" element may include the following children:

- billSummaries
  - item
    - actionDate (e.g. 2013-01-03
    - actionDesc (e.g. Introduced in House)
    - text 
       - Example: ```<![CDATA[<p>Requires the Secretary of the Interior to establish a team of technical, policy, and financial experts to: (1) develop an energy action plan addressing the energy needs of each of the insular areas (American Samoa, the Northern Mariana Islands, Puerto Rico, Guam, and the Virgin Islands) and Freely Associated States (the Federated States of Micronesia, the Republic of the Marshall Islands, and the Republic of Palau); and (2) assist each of the insular areas and Freely Associated States in implementing such plan.<br> </p> <p>Requires such plan to include: (1) recommendations to reduce reliance and expenditures on imported fossil fuels, to develop indigenous, nonfossil fuel energy sources, and to improve performance of energy infrastructure and overall energy efficiency; (2) a schedule for implementation of such recommendations and identification and prioritization of specific projects; (3) a financial and engineering plan for implementing and sustaining projects; and (4) benchmarks for measuring progress toward implementation.</p>]]>``` The "Text" element is enclosed in CDATA.
    - lastSummaryUpdateDate (e.g. 2013-06-24T21:11:48Z)
    - name (e.g. Introduced in House)
    - updateDate (e.g. 2013-01-03T05:00:00Z)
    - versionCode (e.g. 00)
    
 _Note: Bill Summaries are also available as a separate collection on the govinfo Bulk Data repository._ 
 
 _Note: updateDate applies to the item under billSummaries while lastSummaryUpdateDate applies to the summary itself._

### `<textVersions>` 
Parent container for links to bills on govinfo. The "Text Versions" element may include the following children:

- item
  - date (e.g. 2018-09-26T04:00:00Z)
  - type (e.g. Engrossed in Senate)
  - formats
    - item
      - url (e.g. https://www.govinfo.gov/content/pkg/BILLS-115hr302eah/xml/BILLS-115hr302eah.xml) 

### `<title>`

Parent container for titles.

### `<titles>`

Parent container for additional titles. In addition to an official title, a bill may be assigned one or more short titles upon introduction, committee or chamber action, or enactment. Titles may apply to all or portions of a measure's content. Titles may change as a measure moves through the legislative process. The "Titles" element may include the following children:

- item
  - chamberCode (e.g. H)
  - chamberName (e.g. House)
  - parentTitleType (e.g. Official Titles - House of Representatives, Short Title)
  - title (e.g. To require the Secretary of the Interior to assemble a team of technical, policy, and financial experts to address the energy needs of the insular areas of the United States and the Freely Associated States through the development of energy action plans aimed at promoting access to affordable, reliable energy, including increasing use of indigenous clean-energy resources, and for other purposes.)
  - titleType (e.g. Official Titles as Amended by House, Short Titles on Other Versions for portions of this bill) - see ([6. Title Type Possible Values](#6.-Title-Type-Possible-Values))

_Note: Popular Titles are informal, unofficial names for legislation that may be assigned by the House, Senate, or CRS to improve access. Popular titles are usually not found within official legislative texts (e.g. the Patient Protection and Affordable Care Act is commonly known as the health care reform bill).__Note:_ _See the_ [_Congress.gov Glossary_](https://www.congress.gov/help/legislative-glossary) _for more information about titles._  

### `<updateDate>`
The date the record metadata was updated for Congress.gov.

### `<version>`
Version number is provided to GPO by the Library of Congresss, and it is passed through to files on the bulk data repository. Plan is to increment value when data format changes.

### `<dublinCore>` ```xmlns:dc="http://purl.org/dc/elements/1.1/"``` 
Parent container for Dublin Core metadata.  The "Dublin Core" element may include the following children:

- dc:format (value is text/xml)
- dc:language (value is EN)
- dc:rights (value is Pursuant to Title 17 Section 105 of the United States Code, this file is not subject to copyright protection and is in the public domain.)
- dcLcontributor (value is Congressional Research Service, Library of Congress)
- dc:description (value is This file contains bill summaries and statuses for federal legislation. A bill summary describes the most significant provisions of a piece of legislation and details the effects the legislative text may have on current law and federal programs. Bill summaries are authored by the Congressional Research Service (CRS) of the Library of Congress. As stated in Public Law 91-510 (2 USC 166 (d)(6)), one of the duties of CRS is "to prepare summaries and digests of bills and resolutions of a public general nature introduced in the Senate or House of Representatives". For more information, refer to the User Guide that accompanies this file.)


# 3. Action Code Element Possible Values

This table provides codes and descriptions for possible values in the `<actionCode>` child of the `<actions>` element listed in the Elements section 2.1.

Codes in this table are representational of the codes that map actions with action texts related to a measure. It is provided as a courtesy; a complete, authoritative list of action codes does not exist. In general, expect action codes when source system is 2 (House floor) or 9 (Library of Congress).

Various code sets are used by multiple systems in the House, Senate, and Library of Congress by legislative clerks and data editors for functions independent of this bulk data set. As new codes and systems were developed, there was no coordinated effort to retroactively apply new codes to old records. Many codes are concatenated with other codes or elements or utilize free text. Codes in one set may be redundant with a different code in another code set.  Additionally, some codes may have been used and re-used over the years for different purposes further complicating the ability to create an authoritative list.

The original code set can be found at [http://www.loc.gov/pictures/resource/ppmsca.33996/](http://www.loc.gov/pictures/resource/ppmsca.33996/).

| Code | Text in the `<actionCode>` Element |
| --- | --- |
| **B00100** | Sponsor introductory remarks on measure |
| **E20000** | Presented to President |
| **E30000** | Signed by President |
| **E40000** | Became Public Law No: 114-47 |
| **H11100** | Referred to the Committee |
| **H11200** | Sequential committee referral   |
| **H12100** | Committee report of an original measure |
| **H12200** | Committee reported |
| **H12300** | Committee discharged |
| **H12410** | Union Calendar assignment |
| **H14000** | Received in the House |
| **H15000** | Held at the desk |
| **H17000** | Motion to Discharge Committee |
| **H1L210** | Rule provides for consideration of |
| **H1L220** | Rule passed/agreed in House |
| **H25200** | Conference report [free text] filed   |
| **H37300** | Final Passage Under Suspension of the Rules Results |
| **H38310** | Motion To Reconsider Results |
| **H30000** | Consideration by House |
| **H8D000** | DEBATE |
| **H81000** | Point of order against a motion |
| **1000** | Introduced in House |
| **2000** | Referred to House committee |
| **5000** | Reported to House |
| **8000** | Passed/agreed to in House |
| **10000** | Introduced in Senate |
| **11000** | Referred to Senate committee |
| **13100** | Senate committee/subcommittee hearings |
| **13200** | Senate committee/subcommittee markups |
| **14000** | Reported to Senate |
| **14500** | Senate committee discharged |
| **14900** | Senate committee report filed after reporting |
| **17000** | Passed/agreed to in Senate |
| **28000** | Presented to President. |
| **36000** | Became Public Law |

# 4. Actions Type Element Possible Values

This table provides codes and descriptions for possible values in the `<type>` child of the `<actions>` element listed in the Elements section 2.1.

Action types primarily represents legislative process stages or categories of more detailed actions. Most types condense actions into sets. Some types are used for data processing and do not represent House or Senate legislative process activities.

| Text in the `<type>` Element|
| --- |
| Actions by the President |
| Actions Related to President |
| Actions Related to Veto |
| Amending Actions |
| BecameLaw |
| Calendars |
| Chamber Actions |
| Chamber Consideration Actions |
| Committee |
| Committee Actions |
| Conference Actions |
| Discharge |
| Floor |
| ForwardY-N |
| House Actions |
| Introduced in House |
| Introduced in Senate |
| IntroReferral |
| NotUsed |
| President |
| Procedural |
| ResolvingDifferences |
| Senate Actions |
| Significant Actions |
| Unknown |
| VARIES |

# 5. Mapping of LOC Summaries Version Codes and  Action Description Text

This table provides codes and descriptions for possible values in the `<actionDesc>` and `<versionCode>` children of the `<summaries>` element listed in the Elements section 2.1.  This list maps internal LOC summary and bill text version types.

| LOC Summaries `<versionCode>` | Chamber |Text in the `<actionDesc>` Element |
| --- | --- | --- |
| **00** | HOUSE | Introduced in House |
| **00** | SENATE | Introduced in Senate |
| **01** | SENATE | Reported to Senate amended |
| **02** | SENATE | Reported to Senate amended, 1st committee reporting |
| **03** | SENATE | Reported to Senate amended, 2nd committee reporting |
| **04** | SENATE | Reported to Senate amended, 3rd committee reporting |
| **05** | SENATE | Reported to Senate amended, 4th committee reporting |
| **06** | SENATE | Reported to Senate amended, 5th committee reporting |
| **07** | SENATE | Reported to Senate amended, 6th committee reporting |
| **08** | SENATE | Reported to Senate amended, 7th committee reporting |
| **09** | SENATE | Reported to Senate amended, 8th committee reporting |
| **10** | SENATE | Reported to Senate amended, 9th committee reporting |
| **11** | SENATE | Reported to Senate amended, 10th committee reporting |
| **12** | SENATE | Reported to Senate without amendment, 1st committee reporting |
| **13** | SENATE | Reported to Senate without amendment, 2nd committee reporting |
| **14** | SENATE | Reported to Senate without amendment, 3rd committee reporting |
| **15** | SENATE | Reported to Senate without amendment, 4th committee reporting |
| **16** | SENATE | Reported to Senate without amendment, 5th committee reporting |
| **17** | HOUSE | Reported to House amended |
| **18** | HOUSE | Reported to House amended, Part I |
| **19** | HOUSE | Reported to House amended, Part II |
| **20** | HOUSE | Reported to House amended, Part III |
| **21** | HOUSE | Reported to House amended, Part IV |
| **22** | HOUSE | Reported to House amended, Part V |
| **23** | HOUSE | Reported to House amended, Part VI |
| **24** | HOUSE | Reported to House amended, Part VII |
| **25** | HOUSE | Reported to House amended, Part VIII |
| **26** | HOUSE | Reported to House amended, Part IX |
| **27** | HOUSE | Reported to House amended, Part X |
| **28** | HOUSE | Reported to House without amendment, Part I |
| **29** | HOUSE | Reported to House without amendment, Part II |
| **30** | HOUSE | Reported to House without amendment, Part III |
| **31** | HOUSE | Reported to House without amendment, Part IV |
| **32** | HOUSE | Reported to House without amendment, Part V |
| **33** | HOUSE | Laid on table in House |
| **34** | SENATE | Indefinitely postponed in Senate |
| **35** | SENATE | Passed Senate amended |
| **36** | HOUSE | Passed House amended |
| **37** | SENATE | Failed of passage in Senate |
| **38** | HOUSE | Failed of passage in House |
| **39** | HOUSE | Senate agreed to House amendment with amendment |
| **40** | SENATE | House agreed to Senate amendment with amendment |
| **41** | HOUSE | Senate disagreed to House amendment with amendment |
| **42** | SENATE | House disagreed to Senate amendment with amendment |
| **43** | HOUSE | Senate disagreed to House amendment |
| **44** | SENATE | House disagreed to Senate amendment |
| **45** | SENATE | Senate receded and concurred with amendment|
| **46** | HOUSE | House receded and concurred with amendment |
| **47** | SENATE | Conference report filed in Senate |
| **48** | HOUSE | Conference report filed in House |
| **49** | BOTH | Public Law |
| **50** | BOTH | Private Law |
| **51** | BOTH | Line item veto by President |
| **52** | SENATE | Passed Senate amended, 2nd occurrence |
| **53** | SENATE | Passed Senate amended, 3rd occurrence |
| **54** | HOUSE | Passed House amended, 2nd occurrence |
| **55** | HOUSE | Passed House amended, 3rd occurrence |
| **56** | SENATE | Senate vitiated passage of bill after amendment |
| **57** | HOUSE | House vitiated passage of bill after amendment |
| **58** | SENATE | Motion to recommit bill as amended in Senate |
| **59** | HOUSE | Motion to recommit bill as amended in House |
| **60** | SENATE | Senate agreed to House amendment with amendment, 2nd occurrence |
| **61** | SENATE | Senate agreed to House amendment with amendment, 3rd occurrence |
| **62** | HOUSE | House agreed to Senate amendment with amendment, 2nd occurrence |
| **63** | HOUSE | House agreed to Senate amendment with amendment, 3rd occurrence |
| **64** | SENATE | Senate receded and concurred with amendment, 2nd occurrence |
| **65** | SENATE | Senate receded and concurred with amendment, 3rd occurrence |
| **66** | HOUSE | House receded and concurred with amendment, 2nd occurrence |
| **67** | HOUSE | House receded and concurred with amendment, 3rd occurrence |
| **70** | HOUSE | Hearing scheduled in House |
| **71** | SENATE | Hearing scheduled in Senate |
| **72** | HOUSE | Hearing held in House |
| **73** | SENATE | Hearing held in Senate |
| **74** | HOUSE | Markup in House |
| **75** | SENATE | Markup in Senate |
| **76** | HOUSE | Rule reported to House |
| **77** | HOUSE | Discharged from House committee |
| **78** | SENATE | Discharged from Senate committee |
| **79** | HOUSE | Reported to House, without amendment |
| **80** | SENATE | Reported to Senate without amendment |
| **81** | HOUSE | Passed House, without amendment |
| **82** | SENATE | Passed Senate, without amendment |
| **83** | SENATE | Conference report filed in Senate, 2nd conference report |
| **84** | SENATE | Conference report filed in Senate, 3rd conference report |
| **85** | SENATE | Conference report filed in Senate, 4th conference report |
| **86** | HOUSE | Conference report filed in House, 2nd conference report |
| **87** | HOUSE | Conference report filed in House, 3rd conference report |
| **88** | HOUSE | Conference report filed in House, 4th conference report |

# 6. Title Type Possible Values

Below are the possible values in the <titleType> elements listed in the [Elements table 2.1](#2.1.Elements).  See the Congress.gov Glossary for information about "titles."

| Code | Text in the `<titleType>` Element |
| --- | --- |
| **01** | Official Title as Introduced |
| **02** | Official Title as Amended by House |
| **03** | Official Title as Amended by Senate   |
| **04** | Official Title as Agreed to by House and Senate |
| **05** | Official Title as Enacted |
| **10** | Display Title |
| **09** | Official Title on Other Bill Versions |
| **20** | Short Title as Introduced |
| **21** | Short Title as Reported to House |
| **22** | Short Title as Reported to Senate |
| **23** | Short Titles as Passed House |
| **24** | Short Titles as Passed Senate |
| **25** | Short Title as Enacted |
| **26** | Short Title on Conference report |
| **29** | Short Title on Other Versions |
| **30** | Short Title as Introduced for portions of this bill   |
| **31** | Short Title as Reported to House for portions of this bill |
| **32** | Short Title as Reported to Senate for portions of this bill |
| **33** | Short Title as Passed House for portions of this bill |
| **34** | Short Title as Passed Senate for portions of this bill |
| **35** | Short Title as Enacted for portions of this bill |
| **36** | Short Title on Conference report for portions of this bill |
| **39** | Short Titles on Other Versions for portions of this bill |
| **40** | Popular Title |



# 7. Data Set

Bill Status data is provided to GPO by the Library of Congress, and XML files are available for bulk data download on the govinfo Bulk Data repository starting with the 113th Congress (2013-2014). Bill Status XML files are not available through govinfo search or browse; they are only available in the govinfo Bulk Data repository.

In general, there are no restrictions on re-use of information in the Bill Status data set because U.S. Government works are not subject to copyright protection and are in the public domain. GPO and its legislative branch data partners do not restrict downstream uses of Bill Status data, except that independent providers should be aware that only GPO and its legislative branch data partners are entitled to represent that they are the providers of official Bill Status data.

Bill Status XML files can be manipulated and enriched to operate in the various applications that users may devise. GPO and its legislative branch data partners cannot vouch for the authenticity of data that is not under GPO's control. GPO is providing free access to Bill Status XML files for display in various applications and mash-ups outside the Fgovinfo domain. GPO does not endorse third party applications and does not evaluate how the original legal or legislative content is displayed on other sites. Consumers should form their own conclusions as to whether the downloaded data can be relied upon within an application or mash-up.

# 8. Resources Directory

The resources directory at [https://www.govinfo.gov/bulkdata/BILLSTATUS/resources](https://www.govinfo.gov/bulkdata/BILLSTATUS/resources) contains the _User Guide for Bill Status XML Bulk Data_.

### footnote
 House Report 113-417 that accompanies H.R.4487, the Legislative Branch Appropriations bill for FY2015
