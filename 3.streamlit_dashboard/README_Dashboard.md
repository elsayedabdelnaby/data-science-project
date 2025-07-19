# Diet Program Analytics Dashboard

A comprehensive Streamlit dashboard for analyzing diet program management system data, providing insights into customer behavior, program performance, meal selections, and business metrics.

## 🚀 Features

### 📊 Overview Dashboard
- **Key Metrics**: Total customers, active subscriptions, available diet programs, and nationalities served
- **Customer Growth**: Time-series visualization of customer acquisition trends
- **Program Distribution**: Interactive pie chart showing popularity of different diet programs
- **Recent Activity**: Latest customer registrations and activities

### 👥 Customer Analytics
- **Interactive Filters**: Filter by nationality, gender, and date range
- **Demographics**: Age distribution, BMI analysis, and nationality breakdown
- **Gender Analysis**: Customer gender distribution with visualizations
- **Geographic Insights**: Top customer nationalities with horizontal bar charts

### 🍽️ Diet Programs Analysis
- **Master Plan Popularity**: Bar charts showing popularity of different master plans
- **Calories Distribution**: Histogram of calories across different programs
- **Program Details Table**: Comprehensive view of all programs with filtering options
- **Performance Metrics**: Subscription counts, completion rates, and revenue analysis

### 📈 Subscriptions Analytics
- **Subscription Metrics**: Total, active, and completed subscriptions with completion rates
- **Revenue Analysis**: Total revenue, revenue by program, and average revenue by status
- **Trend Analysis**: Subscription trends over time with interactive filters
- **Status Distribution**: Visual analysis of subscription statuses

### 🍴 Meal Analysis
- **Item Popularity**: Most popular food items across all programs
- **Meal Distribution**: Breakdown of selections by meal type (Breakfast, Lunch, Dinner, etc.)
- **Rating Analysis**: Item rating distribution and top-rated items
- **Program Day Analysis**: Item selections by program day

### 🌍 Geographic Analysis
- **World Map**: Interactive map showing customer distribution by country
- **Country Rankings**: Top countries by customer count and subscriptions
- **Regional Performance**: Revenue and completion rates by country
- **Geographic Heatmap**: Visual representation of customer density

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.8 or higher
- CSV data files from your EDA process

### 1. Install Dependencies
```bash
pip install -r requirements_dashboard.txt
```

### 2. Prepare Your Data Files
Ensure you have the following CSV files in your project directory:
- `customers_cleaned.csv` - Customer information with demographics
- `diet_programs_cleaned.csv` - Diet program details and pricing
- `customers_with_subscribers.csv` - Customer subscription data
- `df_selected_items_with_subscribers.csv` - Meal and item selection data

### 3. Run the Dashboard
```bash
streamlit run diet_dashboard.py
```

The dashboard will open in your default web browser at `http://localhost:8501`

## 📊 Data Structure Requirements

### Customers Data (`customers_cleaned.csv`)
Required columns:
- `id` - Customer ID
- `username` - Customer username
- `nationality` - Customer nationality/country
- `gender` - Customer gender
- `age` - Customer age
- `height` - Customer height
- `weight` - Customer weight
- `bmi` - Calculated BMI
- `created_at` - Customer registration date

### Diet Programs Data (`diet_programs_cleaned.csv`)
Required columns:
- `id_x` - Program ID
- `name_en_x` - Program name
- `master_plan_name` - Master plan category
- `calories_total` - Daily calorie target
- `program_days` - Program duration in days
- `total_amount` - Program price
- `valid_from` - Program start date
- `valid_to` - Program end date

### Subscriptions Data (`customers_with_subscribers.csv`)
Required columns:
- `id_program` - Subscription ID
- `customer_id` - Customer ID
- `program_id` - Program ID
- `diet_program_name` - Program name
- `status` - Subscription status (Active, Completed, Cancelled, etc.)
- `paid_amount` - Amount paid
- `delivery_start_date` - Subscription start date
- `created_at_program` - Subscription creation date

### Selected Items Data (`df_selected_items_with_subscribers.csv`)
Required columns:
- `customer_program_id` - Customer program ID
- `program_day` - Day in the program
- `calender_date` - Date of meal
- `item_id` - Food item ID
- `item_name` - Food item name
- `meal_code` - Meal type code
- `meal_name` - Meal type name (Breakfast, Lunch, Dinner, etc.)
- `rate` - Item rating (if available)
- `customer_id_y` - Customer ID
- `diet_program_name` - Program name

## 🎯 Dashboard Navigation

### Sidebar Menu
- **📊 Overview**: High-level metrics and trends
- **👥 Customer Analytics**: Detailed customer analysis and demographics
- **🍽️ Diet Programs**: Program-specific insights and performance
- **📈 Subscriptions**: Subscription tracking and revenue analysis
- **🍴 Meal Analysis**: Food item popularity and meal patterns
- **🌍 Geographic Analysis**: Regional and country-based analysis

### Interactive Features
- **Advanced Filtering**: Filter data by multiple criteria (date ranges, status, nationality, etc.)
- **Interactive Charts**: Plotly visualizations with hover details and zoom capabilities
- **Data Export**: Download filtered data to Excel format
- **Responsive Design**: Works on desktop and mobile devices
- **Real-time Updates**: Automatically refreshes with new data

## 🔧 Customization

### Adding New Visualizations
1. Create new functions for data processing
2. Add Plotly charts using `px` or `go`
3. Integrate into the appropriate page section

### Data Integration
1. Update the `load_data()` function to match your file paths
2. Modify column names in preprocessing functions if needed
3. Ensure proper data types and date formats

### Styling
- Custom CSS is included in the main app
- Modify the `st.markdown()` section for styling changes
- Use Streamlit's built-in theming options

## 📈 Key Metrics Explained

### Customer Metrics
- **Total Customers**: All registered customers in the system
- **Active Subscriptions**: Currently active diet program subscriptions
- **Customer Growth**: Monthly new customer acquisition rate

### Business Metrics
- **Total Revenue**: Sum of all paid amounts from subscriptions
- **Completion Rate**: Percentage of customers who complete their programs
- **Average Revenue**: Average revenue per subscription

### Program Metrics
- **Program Popularity**: Number of subscriptions per diet program
- **Calorie Distribution**: Range of calories across different programs
- **Master Plan Performance**: Success rates by program category

### Meal Metrics
- **Item Popularity**: Most frequently selected food items
- **Meal Distribution**: Breakdown of selections by meal type
- **Rating Analysis**: Customer satisfaction with food items

## 🚨 Troubleshooting

### Common Issues

1. **File Not Found Error**
   - Ensure all CSV files are in the same directory as the dashboard
   - Check file names match exactly (case-sensitive)
   - Verify file permissions

2. **Memory Issues with Large Datasets**
   - The dashboard automatically samples large files for performance
   - Use data sampling in the `load_data()` function
   - Implement data caching with `@st.cache_data`

3. **Missing Dependencies**
   ```bash
   pip install --upgrade -r requirements_dashboard.txt
   ```

4. **Port Already in Use**
   ```bash
   streamlit run diet_dashboard.py --server.port 8502
   ```

### Performance Optimization
- Use `@st.cache_data` for expensive computations
- Implement data sampling for large datasets
- Optimize data loading and preprocessing

## 📝 Data Processing Notes

### Data Cleaning
The dashboard expects cleaned data from your EDA process:
- No missing values in key columns
- Proper date formatting
- Consistent naming conventions
- Valid numeric values for calculations

### Data Relationships
The dashboard handles relationships between:
- Customers → Subscriptions (via customer_id)
- Programs → Subscriptions (via program_id)
- Subscriptions → Selected Items (via customer_program_id)

## 🤝 Contributing

Feel free to submit issues, feature requests, or pull requests to improve the dashboard.

## 📞 Support

For questions or support, please refer to the Streamlit documentation or create an issue in the project repository.

---

**Note**: This dashboard is designed to work with the specific data structure from your diet program management system. Modify the data loading and preprocessing functions to match your specific data schema if needed. 