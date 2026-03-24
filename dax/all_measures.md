
## Registration Measures

### Total Registrations

Total Registrations = COUNTROWS(Fact_Registrations)

### Confirmed Registrations

Confirmed Registrations =
CALCULATE(
    COUNTROWS(Fact_Registrations),
    Fact_Registrations[Status] = "Confirmed"
)

### Pending Registrations

Pending Registrations =
CALCULATE(
    COUNTROWS(Fact_Registrations),
    Fact_Registrations[Status] = "Pending"
)

### Cancelled Registrations

Cancelled Registrations =
CALCULATE(
    COUNTROWS(Fact_Registrations),
    Fact_Registrations[Status] = "Cancelled"
)

### Total Attended

Total Attended =
CALCULATE(
    COUNTROWS(Fact_Registrations),
    Fact_Registrations[Attended] = "Yes"
)

## Rate Measures

### Confirmation Rate

Confirmation Rate % =
DIVIDE(
    [Confirmed Registrations],
    [Total Registrations],
    0
) * 100

### Attendance Rate

Attendance Rate % =
DIVIDE(
    [Total Attended],
    [Confirmed Registrations],
    0
) * 100

### Cancellation Rate

Cancellation Rate % =
DIVIDE(
    [Cancelled Registrations],
    [Total Registrations],
    0
) * 100

### Capacity Fill Rate

Capacity Fill Rate % =
DIVIDE(
    [Confirmed Registrations],
    SUM(Dim_Events[Capacity]),
    0
) * 100

##  Email Campaign Measures

### Emails Sent

Emails Sent = SUM(Dim_EmailCampaigns[EmailsSent])

### Emails Opened

Emails Opened = SUM(Dim_EmailCampaigns[Opened])

### Emails Clicked
Emails Clicked = SUM(Dim_EmailCampaigns[Clicked])

### Email Open Rate
Email Open Rate % =
DIVIDE(
    [Emails Opened],
    [Emails Sent],
    0
) * 100

### Click Through Rate

Click Through Rate % =
DIVIDE(
    [Emails Clicked],
    [Emails Opened],
    0
) * 100

## Time Intelligence Measures

### Prev Month Registrations

Prev Month Registrations =
CALCULATE(
    [Total Registrations],
    DATEADD(Dim_Date[Date], -1, MONTH)
)

### MoM Growth

MoM Growth = [Total Registrations] - [Prev Month Registrations]

### MoM Growth %

MoM Growth % =
DIVIDE(
    [MoM Growth],
    [Prev Month Registrations],
    0
) * 100

### YTD Registrations

YTD Registrations =
TOTALYTD(
    COUNTROWS(Fact_Registrations),
    Dim_Date[Date]
)

### Running Total

Running Total =
CALCULATE(
    [Total Registrations],
    FILTER(
        ALL(Dim_Date),
        Dim_Date[Date] <= MAX(Dim_Date[Date])
    )
)

## Regional & Ranking Measures

### Region Share

Region Share % =
DIVIDE(
    [Total Registrations],
    CALCULATE(
        [Total Registrations],
        ALL(Dim_Events[Region])
    ),
    0
) * 100

### Top Region

Top Region =
CALCULATE(
    SELECTEDVALUE(Dim_Events[Region]),
    TOPN(1,
        SUMMARIZE(Dim_Events, Dim_Events[Region]),
        [Total Registrations],
        DESC
    )
)

### Events Count

Events Count = COUNTROWS(Dim_Events)

