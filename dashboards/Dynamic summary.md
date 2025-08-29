Selection Summary = 
VAR SelCountryCount = COUNTROWS(VALUES('Data'[Country Name]))
VAR TotalCountryCount = COUNTROWS(ALL('Data'[Country Name]))
VAR SelCountry =
    IF(
        SelCountryCount = TotalCountryCount,
        "All Countries",
        CONCATENATEX(VALUES('Data'[Country Name]), 'Data'[Country Name], ", ")
    )

VAR SelYearCount = COUNTROWS(VALUES('Data'[Year]))
VAR TotalYearCount = COUNTROWS(ALL('Data'[Year]))
VAR SelYear =
    IF(
        SelYearCount = TotalYearCount,
        "All Years",
        CONCATENATEX(VALUES('Data'[Year]), 'Data'[Year], ", ")
    )

VAR SelRegionCount = COUNTROWS(VALUES('Metadata - Countries'[Region]))
VAR TotalRegionCount = COUNTROWS(ALL('Metadata - Countries'[Region]))
VAR SelRegion =
    IF(
        SelRegionCount = TotalRegionCount,
        "All Regions",
        CONCATENATEX(VALUES('Metadata - Countries'[Region]), 'Metadata - Countries'[Region], ", ")
    )

RETURN
"Selected: " &
IF(SelCountry <> BLANK(), "Country: " & SelCountry & " ", "") &
IF(SelYear <> BLANK(), "Year: " & SelYear & " ", "") &
IF(SelRegion <> BLANK(), "Region: " & SelRegion, "")

