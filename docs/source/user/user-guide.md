PDS4 Magellan Mission Dictionary User's Guide  
2023-10-06 Jennifer Ward  
2024-11-27 Ethan I. Schaefer  
# Introduction  
   1. Purpose of this User's Guide  
   - This User's Guide provides an overview of the Magellan Mission Data Dictionary. It details how to include the dictionary in a PDS4 label, describes the organization of classes and attributes, provides definitions of the classes and attributes, and lists examples of labels that use it.  
   2. Audience  
   - This User's Guide should be useful to data providers intending to archive Magellan data with PDS as well as PDS Nodes who are working with these data providers.  
  
# Overview of the Magellan Mission Data Dictionary  
  
The Magellan Mission Data Dictionary contains classes and attributes specific to the Magellan mission and its instruments.  
Steward: Jennifer Ward, PDS Geosciences Node, geosci@wunder.wustl.edu  
  
# How to Include the Magellan Mission Data Dictionary in a PDS4 Label  
  
The dictionary consists of a set of files with names in the form PDS4_MGN_xxxx_yyyy.ext, where  
- xxxx = the PDS4 Information Model version, e.g. 1M00  
- yyyy = the MGN Mission Dictionary version, e.g. 1100  
  
and the file extensions are  
  
- .csv = A comma-separated value table of dictionary attributes  
- .JSON = The dictionary contents in JSON format  
- .sch = The dictionary "rules" as an XML Schematron file  
- .txt = The report generated when the dictionary was built  
- .xml = The PDS4 label that describes this set of files  
- .xsd = The dictionary contents as an XML schema file  
  
Only the schema and Schematron files are needed for validating a PDS4 label.  
  
The latest version of this dictionary may be found on the PDS web site at https://pds.nasa.gov/datastandards/dictionaries/index-missions.shtml#mgn.  
  
The following is an example showing the use of this dictionary in a PDS4 label.  
  
```
   <?xml version="1.0" encoding="UTF-8"?>
   <?xml-model href="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1M00.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
   <?xml-model href="https://pds.nasa.gov/pds4/mission/mgn/v1/PDS4_MGN_1K00_1000.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>    
   <Product_Observational xmlns="http://pds.nasa.gov/pds4/pds/v1"
       xmlns:mgn="http://pds.nasa.gov/pds4/mission/mgn/v1"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://pds.nasa.gov/pds4/pds/v1           https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1M00.xsd
                           http://pds.nasa.gov/pds4/mission/mgn/v1   https://pds.nasa.gov/pds4/mission/mgn/v1/PDS4_MGN_1K00_1000.xsd">
```  
  
The following is an example showing the location of the Magellan dictionary classes and attributes in a PDS4 label.  
  
```
<Observation_Area>
  ...
  <Mission_Area>
    <mgn:Magellan_Parameters>
      <mgnband_name>
      <mgndsn_station_number>
      <mgnorganization_id>
      <mgnreceived_polarization_type>
      <mgnproduct_type>
      <mgnproduct_version_id>
      <mgnmapping_cycle>
      <mgnorbit_number>
      <mgnstart_orbit_number>
      <mgnstop_orbit_number>
      <mgnmission_phase_name>
      <mgnradar_look_direction>
      <mgnspacecraft_clock_count_partition>
      <mgnspacecraft_clock_start_count>
      <mgnspacecraft_clock_stop_count>
      <mgnproducer_institution_name>
      <mgnoriginal_pds_volume_id>
    </mgn:Magellan_Parameters>
  </Mission_Area>
  ...
</Observation_Area>
```  
  
The namespace for the Magellan Mission Dictionary is http://pds.nasa.gov/pds4/mission/mgn/v1, abbreviated "mgn:".  
  
# Organization of Classes and Attributes  
  
See the [schematic](../../MGN_LDD_diagram.png) for a visual representation of the classes and attributes (not yet available).  
  
Below is a list showing the hierarchy of classes in order of appearance in the PDS4 label.  
See the Definitions section for complete definitions.  
  
- [Magellan_Parameters](#magellan_parameters-attributes)  
  
Below are lists showing the hierarchy of class attributes in order of appearance in the PDS4 label.  
See the Definitions section for complete definitions.  
  
## [Magellan_Parameters](#magellan_parameters) (attributes)  
  
- product_type  
- product_version_id  
- [mapping_cycle](#*mapping-cycle*)  
- orbit_number  
- start_orbit_number  
- stop_orbit_number  
- mission_phase_name  
- radar_look_direction  
- spacecraft_clock_count_partition  
- spacecraft_clock_start_count  
- spacecraft_clock_stop_count  
- producer_institution_name  
- original_pds3_volume_id  
  
# Definitions  
## Classes (in alphabetical order)  
  
### Magellan_Parameters  
The Magellan_Parameters class is the container for mission-specific metadata elements.  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
  
## Attributes (in alphabetical order)  
### *band_name*  
 The name of the radio band in which the signal was received.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - S  
    - S band  
  - X  
    - X band  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
### *dsn_station_number*  
 The number of the DSN antenna used to collect the data.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum value: 0  
- Maximum value: 99  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
### *mapping_cycle*  
The mapping cycle in which the data were acquired. Should be 1 to 6.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum value: 1  
- Maximum value: 6  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*mission_phase_name*  
 The mission_phase_name attribute provides the mission-defined name of a time period within the mission.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - Mapping Cycle 1  
    - The first mapping cycle extended from completion of the orbit  
                    trim and checkout phase until completion of one cycle of radar  
                    mapping (approximately 243 days). Started 1990-09-15 and ended  
                    1991-05-15.  
  - Mapping Cycle 2  
    - The second mapping cycle extended from completion of the first  
                    mapping cycle through an additional cycle of mapping.  
                    Acquisition of 'right-looking' SAR data was emphasized. Radio  
                    occultation measurements were carried out on orbits 3212-3214.  
                    A period of battery reconditioning followed completion of  
                    Cycle 2. Started 1991-05-16 and ended 1992-01-17.  
  - Mapping Cycle 3  
    - The third mapping cycle extended from completion of battery  
                    reconditioning through an additional cycle of mapping  
                    (approximately 243 days). Acquisition of 'stereo' SAR data  
                    was emphasized. The last orbit in the third cycle was orbit  
                    5747. Started 1992-01-24 and ended 1992-09-14.  
  - Mapping Cycle 4  
    - The fourth mapping cycle extended from completion of the third  
                    mapping cycle through an additional cycle of mapping.  
                    Acquisition of radio tracking data for gravity studies was  
                    emphasized. Radio occultation measurements were carried out  
                    on orbits 6369, 6370, 6471, and 6472. Because of poor  
                    observing geometry for gravity data collection at the  
                    beginning of the cycle, this cycle was extended 10 days beyond  
                    the nominal 243 days. Orbits included within the fourth cycle  
                    were 5748 through 7626. Periapsis was lowered on orbit 5752  
                    to improve sensitivity to gravity features in Cycle 4.  
                    Started 1992-09-14 and ended 1993-05-25.  
  - Aerobraking  
    - The aerobraking phase extended from completion of the fourth  
                    mapping cycle through achievement of a near-circular orbit.  
                    Circularization was achieved more quickly than expected; the  
                    first gravity data collection in the circular orbit was not  
                    scheduled until 11 days later. Orbits included within the  
                    aerobraking phase were 7627 through 8392. Started 1993-05-26  
                    and ended on 1993-08-05.  
  - Mapping Cycle 5  
    - The fifth mapping cycle extended from completion of the  
                    aerobraking phase through an additional cycle of mapping  
                    (approximately 243 days). Acquisition of radio tracking data  
                    for gravity studies was emphasized. The first orbit in the  
                    fifth cycle was orbit 8393. Started on 1993-08-16 and ended on  
                    1994-04-15.  
  - Mapping Cycle 6  
    - The sixth mapping cycle extended from completion of the fifth  
                    mapping cycle through an additional cycle of mapping  
                    (approximately 243 days). Acquisition of radio tracking data  
                    for gravity studies was emphasized. The first orbit in the  
                    sixth cycle was orbit 12249. Started on 1994-04-16.  
  - Primary Mission  
    - The prime science phase of the mission. This value occurs  
                    in the original PDS labels of the MIDR products.  
- Minimum occurrences: 0  
- Maximum occurrences: unbounded  
- Nillable: No  
  
*orbit_number*  
The orbit_number attribute identifies the number of the orbital revolution around a target body.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum value: 1  
- Maximum value: 20000  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*organization_id*  
 The organization that produced the data.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - SUE  
    - Stanford University Element of the Venus Express Radio Science  
                    Team  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*original_pds_volume_id*  
The original PDS volume_id of where the Magellan data are located.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*producer_institution_name*  
The producer_institution_name attribute identifies a university, research center, NASA center, or other institution associated with the production of a data product.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*product_type*  
The product_type attribute indicates the type of data for an individual data product. The values are based on the values used by the Magellan project for their delivery to PDS.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - F-MIDR  
    - Full resolution Mosaicked Image Data Record  
  - C1-MIDR  
    - Compressed one time Mosaicked Image Data Record  
  - C2-MIDR  
    - Compressed two times Mosaicked Image Data Record  
  - C3-MIDR  
    - Compressed three times Mosaicked Image Data Record  
  - P-MIDR  
    - Polar projected Mosaicked Image Data Record  
  - F-BIDR  
    - Full resolution Basic Image Data Record  
  - C-BIDR  
    - Compressed Basic Image Data Record  
  - ARCDR  
    - Altimetry and Radiometry Composite Data Record  
  - GTDR  
    - Global topography map data record  
  - GEDR  
    - Global emissivity map data record  
  - GREDR  
    - Global reflectivity map data record  
  - GSDR  
    - Global slope map data record  
  - GXDR  
    - Global map image Data Record with maps for  
                    topography, emissivity, slope and reflectivity  
  - SCVDR  
    - Surface Characteristics Vector Data Record  
  - GVDR  
    - Global Vector Data Record  
  - BSR  
    - Bistatic Radar  
  - LOSAPDR  
    - Line Of Sight Acceleration Profile Data Record  
  - SHXDR  
    - Spherical Harmonic Data Record for topography and gravity models  
- Minimum occurrences: 1  
- Maximum occurrences: 1  
- Nillable: No  
  
*product_version_id*  
The product_version_id attribute identifies the version of an individual data product.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*radar_look_direction*  
 The radar_look_direction attribute provides the direction the radar antenna was pointing relative to the spacecraft ground track along a given orbit. Most cases were Left or Right. Stereo indicates left looking with an incidence angle for stereo measurements. Maxwell is a special case for observing the Maxwell feature.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - Left  
    - Left looking observation  
  - Right  
    - Right looking observation  
  - Mixed  
    - Mixed looking observation (both left and right)  
  - Stereo  
    - Stereo observation  
  - Maxwell  
    - Maxwell observation  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*received_polarization_type*  
 The radio polarization of the receiving antenna and feed.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values:  
  - right circular  
    - Right circular polarization  
  - left circular  
    - Left circular polarization  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*spacecraft_clock_count_partition*  
The spacecraft_clock_count_partition attribute indicates the clock partition active for the spacecraft_clock_start_count and spacecraft_clock_stop_count attributes.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*spacecraft_clock_start_count*  
The spacecraft_clock_start_count attribute provides the value of the spacecraft clock at the beginning of a time period of interest.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: Yes  
  
*spacecraft_clock_stop_count*  
The spacecraft_clock_stop_count attribute provides the value of the spacecraft clock at the end of a time period of interest.  
- PDS4 data type: ASCII_Short_String_Collapsed  
- Valid values: N/A  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: Yes  
  
*start_orbit_number*  
Provides the the lowest revolution orbit number that contributed data to a given data product.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum value: 1  
- Maximum value: 20000  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
*stop_orbit_number*  
Provides the the highest revolution orbit number that contributed data to a given data product.  
- PDS4 data type: ASCII_NonNegative_Integer  
- Valid values: N/A  
- Minimum value: 1  
- Maximum value: 20000  
- Minimum occurrences: 0  
- Maximum occurrences: 1  
- Nillable: No  
  
# Examples  
  
Example PDS4 label snippet for a Magellan F-MIDR data product:  
  
```

    <Mission_Area>
      <mgn:Magellan_Parameters>
        <mgn:product_type>F-MIDR</mgn:product_type>
        <mgn:product_version_id>201</mgn:product_version_id>
        <mgn:mapping_cycle>2</mgn:mapping_cycle>
        <mgn:mission_phase_name>Mapping Cycle 2</mgn:mission_phase_name>
        <mgn:radar_look_direction>Left</mgn:radar_look_direction>
        <mgn:original_pds_volume_id>mg_0062</mgn:original_pds_volume_id>
      </mgn:Magellan_Parameters>
    </Mission_Area>

```  
Example PDS4 label snippet from urn:nasa:pds:magellan_bsr_calibrated:prt:4156194b:  
```
<Mission_Area>
  <mgn:Magellan_Parameters>
    <mgn:band_name>S</mgn:band_name>
    <mgn:dsn_station_number>63</mgn:dsn_station_number>
    <mgn:organization_id>SUE</mgn:organization_id>
    <mgn:received_polarization_type>right circular</mgn:received_polarization_type>
    <mgn:product_type>BSR</mgn:product_type>
  </mgn:Magellan_Parameters>
</Mission_Area>
```  
