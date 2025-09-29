# miningdashboards
# Mining Dashboards

During my year and a half in the Operational Excellence Department, one of my responsibilities was to create tools that allowed the Operational Director and the Operational Excellence Team to monitor production compliance.

The main challenge was to summarize the entire operation in just a few clicks — transitioning from static tables to a more user-friendly, graphical, and dynamic interface. To achieve this, it was necessary to understand the company’s data sources and design a reliable, automated way of retrieving them. The work presented here required collaboration across multiple departments and a solid understanding of the company’s data flow.

The creation of these dashboards relied primarily on **DAX, Power Query (M), and SQL**, while their maintenance required some knowledge of **Power BI gateways**.

---

## Context and Challenges

Managers traditionally monitored daily production using **SIREP**, a local platform that tracks tonnage, flow, grades, and consumption ratios. SIREP presents this information in tabular form, comparing actuals against forecast and budget targets. Data is available daily, monthly, quarterly, and yearly — but only one date can be selected at a time.

This limitation made it impossible, for example, to directly compare two quarters. Further analysis was usually delegated to subordinates, who either exported data from SIREP or relied on on-premise systems such as SCADA.

SIREP is the **official corporate data source**, so it is regarded as the reference for reporting. While IT ensured SIREP’s availability and functionality, I was responsible for the accuracy of the data being reported to it.

*Image of SIREP here*

---

## An Improved Approach

The dashboard was designed as a **dynamic, interactive reporting tool** that presents the same official data as SIREP but with additional features:

* Daily updates with *to-date* calculations.
* Moving average vs. actual vs. target graphs.
* Adjusted production calculations to meet targets.
* Performance projections based on trends.
* A top-down navigation approach, enabled by Power BI, that lets users click graphs or values to drill down into details.

*Images showing dashboard granularity here*

### Data Sources

The dashboard queries SIREP’s SQL database for both actuals and targets (budget and forecast). Special handling was required for weighted averages: tables were pivoted and additional columns created in Power Query.

*Image of Power Query here*

### Deployment

To make the dashboard available across the organization, I created a Power BI Workspace and added all relevant users. I requested a dedicated server from IT to host the gateway, avoiding on-premise limitations. Automatic updates were scheduled twice a day at 11:30 and 12:00.

*Image of Gateway and Workspace here*

---

## Final Result

The dashboard allows users to navigate through data from the **Mine, Crushing, Processing Plant, and equipment availability**.

* The **main page** can be filtered by month or quarter. It summarizes performance across three columns:

  1. To-date compliance
  2. Trend indicators
  3. Adjustments required to meet targets

* For ounces, the dashboard shows the remaining ounces needed within the period.

* Trend indicators are represented by triangles or an equal sign:

  * ▲ Green upward triangle → last actual value > 5% higher than the previous one
  * ▼ Red downward triangle → last actual value > 5% lower
  * = Equal sign → variation within ±5%

This provides executives with a quick overview of performance. Users can click on any variable to open a detailed report page.

*Image of main page here*

Each variable’s report includes:

* A line chart with actuals, 7-day moving average, and target.
* A colored compliance ring with cumulative compliance.
* Current moving average value.
* Projected performance if the current trend continues.
* Final target for the period.
* Daily production adjustments required to reach the target.

*Image of detailed reports here*

---

## Comments

With this implementation, directors and managers can quickly see production performance, track progress toward targets, and identify adjustments needed to reach goals. The simplicity of the dashboard answers the most common executive questions without compromising data reliability, since it uses the **official corporate source**.

Although its granularity is limited compared to operational tools, this was intentional: the dashboard’s scope is focused on executive needs. More detailed operational monitoring is handled with tools such as Pi System.

👉 For real-time dashboards and analysis, see the repository on **Pi System** (*link here*).
 PiSystem. If interested you can check the work on real-time dashboards and analysis on this repository: *include the repository on pisystem 
