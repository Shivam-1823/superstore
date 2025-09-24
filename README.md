# Superstore Sales Dashboard

A comprehensive Power BI dashboard analyzing retail sales data from a fictional superstore, providing insights into sales performance, customer behavior, and product trends.

## Project Overview and Objectives

This project demonstrates advanced data visualization and business intelligence capabilities using Power BI. The dashboard analyzes retail sales data to:

- **Track Key Performance Indicators (KPIs)** including total sales, profit, and quantity sold
- **Analyze Sales Trends** across different time periods and geographical regions
- **Identify Top Performing Products** and categories
- **Understand Customer Segments** and their purchasing behaviors
- **Monitor Regional Performance** across different states and cities
- **Evaluate Shipping Modes** and delivery performance

The primary objective is to provide actionable insights for business decision-making, helping stakeholders understand sales patterns, identify growth opportunities, and optimize business operations.

## Files Included

### Core Files
- **`Dashboards.pbix`** - Main Power BI dashboard file containing all visualizations, data models, and DAX calculations
- **`Sample - Superstore.csv`** - Raw dataset containing sales transactions, customer information, and product details

### Screenshots
Dashboard screenshots should be added to a `/screenshots` folder in the repository to showcase the various views and insights:
- Executive Summary Dashboard
- Sales Performance Analysis
- Product Category Breakdown
- Regional Sales Maps
- Customer Segment Analysis
- Time Series Trends

## Dashboard Features

### Main KPIs
- **Total Sales**: $2.3M+ in revenue tracking
- **Total Profit**: Profit margin analysis and trends
- **Quantity Sold**: Volume metrics across product categories
- **Average Order Value**: Customer spending patterns
- **Profit Ratio**: Profitability percentage by various dimensions

### Key Views and Insights

#### 1. Executive Summary
- High-level KPI cards with year-over-year comparisons
- Sales trend visualization with monthly/quarterly breakdowns
- Top-performing metrics at a glance

#### 2. Sales Performance Analysis
- Interactive time series charts showing sales trends
- Regional performance maps with state-level drilling
- Category-wise sales distribution (Technology, Office Supplies, Furniture)
- Sub-category performance rankings

#### 3. Customer Segment Analysis
- Customer segmentation (Consumer, Corporate, Home Office)
- Customer purchasing behavior patterns
- Loyalty and retention metrics

#### 4. Product Performance
- Best and worst-selling products identification
- Category and sub-category profitability analysis
- Product-level margin analysis

#### 5. Geographic Insights
- State and city-wise sales distribution
- Regional profitability comparison
- Shipping performance by geography

#### 6. Operational Metrics
- Shipping mode analysis (Standard, Second Class, First Class, Same Day)
- Delivery performance tracking
- Order size distribution

## How to Use/Open the Dashboard

### Prerequisites
- **Microsoft Power BI Desktop** (Latest version recommended)
- **Power BI Pro/Premium license** (for sharing and collaboration features)

### Opening the Dashboard
1. **Download the repository** files to your local machine
2. **Open Power BI Desktop** application
3. **Open the `Dashboards.pbix` file** by:
   - File → Open → Browse to the downloaded file
   - Or double-click the `.pbix` file (if Power BI is set as default)
4. **Data Refresh**: The dashboard should load with the embedded data from `Sample - Superstore.csv`
5. **Interactive Exploration**: Use filters, slicers, and drill-down capabilities to explore data

### Navigation Tips
- Use the **page tabs** at the bottom to navigate between different dashboard views
- **Click on charts** to cross-filter related visualizations
- **Use slicers** (dropdown filters) to focus on specific time periods, regions, or categories
- **Drill-down** capabilities available on hierarchical charts (Year → Quarter → Month)

## Scripts/DAX Examples

The dashboard utilizes several advanced DAX (Data Analysis Expressions) formulas for calculated measures:

### Key Measures

```dax
// Total Sales Measure
Total Sales = SUM(Orders[Sales])

// Total Profit Measure  
Total Profit = SUM(Orders[Profit])

// Profit Ratio Calculation
Profit Ratio = DIVIDE([Total Profit], [Total Sales], 0)

// Year-over-Year Sales Growth
Sales YoY Growth = 
VAR CurrentYearSales = [Total Sales]
VAR PreviousYearSales = 
    CALCULATE(
        [Total Sales],
        DATEADD('Calendar'[Date], -1, YEAR)
    )
RETURN
    DIVIDE(CurrentYearSales - PreviousYearSales, PreviousYearSales, 0)

// Running Total Sales
Running Total Sales = 
CALCULATE(
    [Total Sales],
    FILTER(
        ALLSELECTED(Orders[Order Date]),
        Orders[Order Date] <= MAX(Orders[Order Date])
    )
)

// Top N Products by Sales
Top N Products = 
VAR RankingValue = RANKX(ALL(Orders[Product Name]), [Total Sales], , DESC)
RETURN
    IF(RankingValue <= 10, [Total Sales], BLANK())
```

### Time Intelligence Functions
```dax
// Previous Month Sales
Previous Month Sales = 
CALCULATE(
    [Total Sales],
    DATEADD('Calendar'[Date], -1, MONTH)
)

// Monthly Growth Rate
Monthly Growth = 
VAR CurrentMonth = [Total Sales]
VAR PreviousMonth = [Previous Month Sales]
RETURN
    DIVIDE(CurrentMonth - PreviousMonth, PreviousMonth, 0)
```

## Project Structure
```
superstore/
│
├── Dashboards.pbix           # Main Power BI dashboard file
├── Sample - Superstore.csv   # Source dataset
├── README.md                 # Project documentation
└── screenshots/              # Dashboard screenshots (to be added)
    ├── executive-summary.png
    ├── sales-analysis.png
    ├── product-performance.png
    ├── regional-analysis.png
    └── customer-segments.png
```

## Technical Details

- **Data Source**: CSV file with 9,994+ rows of sales transactions
- **Time Range**: 2020-2023 sales data
- **Geographic Coverage**: United States (48 states)
- **Product Categories**: Technology, Office Supplies, Furniture
- **Customer Segments**: Consumer, Corporate, Home Office
- **Key Metrics**: Sales, Profit, Quantity, Discount, Shipping Cost

## Future Enhancements

- Integration with live data sources (SQL Server, Azure, etc.)
- Advanced predictive analytics using machine learning
- Real-time dashboard updates
- Mobile-responsive design optimization
- Additional customer lifetime value analysis

## Credits and Contact Information

### Project Author
**Shivam**  
- GitHub: [@Shivam-1823](https://github.com/Shivam-1823)
- Repository: [superstore](https://github.com/Shivam-1823/superstore)

### Data Source
- **Dataset**: Sample Superstore Sales Data
- **Original Source**: Fictional retail dataset for educational and demonstration purposes

### Tools and Technologies
- **Microsoft Power BI Desktop** - Data visualization and dashboard creation
- **DAX (Data Analysis Expressions)** - Advanced calculations and measures
- **Power Query** - Data transformation and preparation

### Acknowledgments
- Power BI community for inspiration and best practices
- Microsoft documentation and learning resources

---

## Getting Started

1. **Clone this repository**:
   ```bash
   git clone https://github.com/Shivam-1823/superstore.git
   ```

2. **Open the dashboard**:
   - Install Power BI Desktop if not already installed
   - Open `Dashboards.pbix` file
   - Explore the interactive visualizations

3. **Add Screenshots**:
   - Create a `/screenshots` folder
   - Add PNG/JPG files showcasing different dashboard views
   - Update this README with specific screenshot references

4. **Customize and Extend**:
   - Modify visualizations to meet specific requirements
   - Add new measures using DAX
   - Integrate with your own data sources

---

*This project demonstrates practical Power BI skills including data modeling, DAX calculations, interactive visualizations, and business intelligence best practices.*

**Last Updated**: September 2025![Screenshot-2025-09-24-195623](https://github.com/user-attachments/assets/21a01539-bb6e-4ae8-8105-eb40ca71943a)
