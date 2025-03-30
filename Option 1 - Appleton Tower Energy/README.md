# Appleton Tower Electricity and Heat Dataset

Provided by Alan Hughes, Energy Manager, University of Edinburgh

Licence: Copyright University of Edinburgh

## Dataset description

The spreadsheet contains two sheets:

### HH DATA 30 Mins #1

This records electricity and heat used in half hour periods in
Appleton Tower. It is collected using the University's automated
systems for recording energy consumption. The columns are as follows:

- 'H' - ignore
- 'OPTIMA Half Hourly DATA' - ID of meter
- 'Utility' - Electric or heat
- 'READING DATE' - Date of readings
- 'CHANNEL TYPE' - Essentially the same as Utility, except with units
- 'UNITS' - The units of consumption
- '00:30' - Energy used of Utility used from 00:00 to 00:30 on the date of the reading 
- '01:00' - Energy used used from 00:30 to 01:00 on the date of the reading
- ... Further columns are in the same format

There may be anomalies in this dataset, for example periods when there
is 0 energy consumption or negative energy consumption.

### Heating Degree Days

A heating degree day measures the number of degrees below a given
threshold temperature that outside temperature is on a given day. This
threshold is typically 15.5 degrees Celsius, which is the value used by Estates. Heating Degree Days can be computed in various ways; a simple method to compute the heating degree days for one day is:

`degree_days = max(15.5 - mean_daily_temperature, 0)`

Here `mean_daily_temperature` could be estimated by the mean of the max and min temperatures. For more detail see https://www.degreedays.net/introduction and https://en.wikipedia.org/wiki/Heating_degree_day.

For example, if the outside temperature is 10 degrees Celsius on a particular day, that
counts as 15.5-10 = 5.5 Heading Degree Days. Heating degree days can
be summed over periods, as has been done in this spreadsheet.

## Notes on the metering

Electricity and heat metering is complex! The notes below hopefully
give some helpful context without unnecessary details. Please let
David Sterratt know if you've questions via Piazza - he can contact
Estates department with queries about the data.

Meter 0201NE002V records the electricity used in Appleton Tower (AT),
apart from electricity used by a data centre in AT. In the summer,
there is a connection from the Tower to the Edinburgh Fringe Festival
in George Square, which is not metered separately, and so the
electricity used by the Fringe appears in this data.

The meter is in fact a "virtual" meter, which estimates the electricity
actually used in AT from a readings from a number of physical
electricity meters. For reference, there are two electricity supplies
into AT and some electricity flows out to supply other buildings in
George Square, as well as the data centre in AT. The virtual reading is
derived by subtracting the outgoing electricity from the incoming
electricity.

The heat meter 0201NH001V is also a virtual meter. Because of issues
with subtracting outgoing heat, sometimes the heat readings are
negative, but over a day the sum of the heat readings should be
correct.

# Daily Temperature data

The zip file midas-open-daily-temperature-edinburgh-botanics.zip contains data from the CEDA archive. The zip file contains a README and you can find more details here: https://catalogue.ceda.ac.uk/uuid/b7c6295b72c54fa9bcd8308fea2727e7/. The Open Government license allows us to distribute it to students. The max and min temperatures relevant for the heating degree day calculation are `max_air_temp` and `min_air_temp`.

# PV (solar panel) data

4 March 2025: Appleton Tower has some solar panels. Estates have shared some data from the PV panels, which is in the file `0201-Appleton Tower PV HHDATA_339_0001.xlsx`. We've not had a chance to curate the data yet, but Estates write: "There are three systems, two of them are
10kW each and the third system is 6kW. The data isn't included in the
calculation for the other meters already sent. It could be added in to
the virtual meter for the building, but the total generation is quite
low." 


