# Haribo Tariff Analysis

**Repository Name**: `Haribo-Tariff-Insights`

Welcome to the **Haribo Tariff Analysis** project, an interactive R Shiny application that unravels how Haribo, the iconic gummy bear manufacturer, navigated EU tariffs through its US operations. Crafted with low-code/no-code methods and powered by AI tools from xAI and OpenAI, this project blends economic analysis with supply chain expertise to make complex trade dynamics accessible to all.

Whether you're a data enthusiast, a business leader, or simply curious about Haribo’s global strategy, this app offers intuitive visualizations and insights into plant locations, tariff exemptions, ingredient sourcing, product differences, and more.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [How It Was Built](#how-it-was-built)
- [Installation](#installation)
- [Usage](#usage)
- [Code](#code)
- [Why This Matters](#why-this-matters)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Project Overview

As a Senior Economist and Supply Chain Expert, I developed this project to demystify Haribo’s strategic tariff exemption, achieved through its Wisconsin plant. The app explores why Haribo avoided EU tariffs, how ingredient sourcing impacts trade, and what differentiates US and German Goldbears. It’s designed for both technical users (data scientists, analysts) and non-technical audiences (business stakeholders, curious learners) to engage with trade policy and supply chain dynamics interactively.

**Key Highlights**:
- **Low-Code/No-Code Approach**: Built using R Shiny’s drag-and-drop-like simplicity, requiring minimal coding expertise.
- **AI-Powered Development**: Leveraged xAI’s Grok and OpenAI’s ChatGPT for code generation, data simulation, and iterative refinement, showcasing AI’s role in democratizing app creation.
- **Comprehensive Visualizations**: Includes maps, line graphs, bar charts, and tables to explore global operations, tariff factors, and product insights.

This project demonstrates how AI-driven tools can empower anyone to create sophisticated apps, making economic and supply chain analysis accessible without deep technical skills.

---

## Features

- **Global Plant Map**: A 2D interactive map showing Haribo’s 14 production and distribution facilities worldwide.
- **Tariff Exemption Insights**: Line graphs analyzing Rules of Origin Compliance, Trade Policy Leverage, and Market Proximity from 2020–2023.
- **Sourcing Scenarios**: Bar charts comparing ingredient sourcing (Local US, Brazil Mix, EU Mix) and tariff risks, alongside raw materials vs. finished goods duties.
- **Product Differences**: Visual comparison of US and German Goldbears’ ingredients (e.g., corn syrup vs. glucose syrup).
- **Regulatory Drivers**: Bar charts highlighting US vs. EU regulatory strictness for food additives.
- **Quality & Perception**: Line graphs of taste test preferences (2020–2023), showing German Goldbears’ edge.
- **Strategic Insights**: Trends in jobs, market share, and trade resilience over time.
- **Financial Metrics**: UK-specific turnover, growth, and profit data for 2022–2023.
- **Facility Info**: Detailed table of Haribo’s US operations, including plant size and staffing.
- **Beautiful Landing Page**: A visually engaging entry point with the Haribo logo, inviting users to explore the dashboard.

---

## How It Was Built

This app was created using **low-code/no-code principles**, harnessing the power of **R Shiny** and **AI tools** to simplify development. Here’s the tech stack and process:

- **R Shiny**: The core framework for building the interactive web app, offering a user-friendly interface for visualizations without complex coding.
- **Packages**:
  - `plotly`: For interactive line and bar charts.
  - `leaflet`: For the global plant map.
  - `dplyr` and `tidyr`: For data manipulation.
  - `bslib`: For modern, Haribo-branded styling (dark theme, gold accents).
  - `shinyjs`: For smooth landing page transitions.
- **AI Assistance**:
  - **xAI’s Grok**: Guided dataset creation, code debugging, and visualization design, ensuring economic and supply chain accuracy.
  - **OpenAI’s ChatGPT**: Assisted with code structure, UI layout, and iterative refinements, making development accessible to non-coders.
- **Data**: Simulated datasets for proprietary Haribo metrics (e.g., tariff factors, sourcing), supplemented by real-world-inspired facility and financial data.
- **Design**: A custom landing page with a Haribo logo (`www/haribo-logo.png`) and a candy-themed background, built with `bslib` for responsiveness.

The AI tools acted as virtual co-developers, generating code snippets, suggesting visualizations, and troubleshooting errors, proving that anyone can build a professional app with minimal technical expertise.

---

## Installation

To run the app locally, follow these steps:

1. **Prerequisites**:
   - Install [R](https://www.r-project.org/) (version 4.0 or higher).
   - Install [RStudio](https://www.rstudio.com/) for an optimal development environment.

2. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Haribo-Tariff-Insights.git
   cd Haribo-Tariff-Insights
   ```

3. **Install Dependencies**:
   Open `app.R` in RStudio and run the package installation section, or use:
   ```R
   install.packages(c("shiny", "plotly", "leaflet", "dplyr", "tidyr", "bslib", "shinyjs"))
   ```

4. **Add Logo**:
   - Place `haribo-logo.png` in a `www/` folder within the project directory (`Haribo-Tariff-Insights/www/`).

5. **Run the App**:
   In RStudio, open `app.R` and click "Run App," or use:
   ```R
   shiny::runApp()
   ```

The app will launch in your browser, starting with the landing page.

---

## Usage

1. **Landing Page**: Upon opening, you’ll see a vibrant landing page with the Haribo logo, a brief intro, and an "Enter Dashboard" button.
2. **Dashboard Navigation**:
   - Use the tabset to explore nine sections: Plant Locations, Tariff Exemption Factors, Sourcing Scenarios, Product Differences, Regulatory Drivers, Quality & Perception, Strategic Insights, Haribo Metrics, and Facility Info.
   - Interact with dropdowns (e.g., tariff factors, sourcing scenarios) to customize visualizations.
   - Hover over charts for detailed data points, or click map markers for plant details.
3. **Non-Technical Users**: Focus on the intuitive visuals and descriptions below each tab to understand Haribo’s tariff strategy.
4. **Technical Users**: Dive into the code for customization, or extend the datasets with real-world data.

---

## Code

Below is the complete `app.R` file, ensuring transparency and reproducibility:

```R
# app.R

# Install required packages if not already installed
if (!require("shiny")) install.packages("shiny")
if (!require("plotly")) install.packages("plotly")
if (!require("leaflet")) install.packages("leaflet")
if (!require("dplyr")) install.packages("dplyr")
if (!require("tidyr")) install.packages("tidyr")
if (!require("bslib")) install.packages("bslib")
if (!require("shinyjs")) install.packages("shinyjs")

library(shiny)
library(plotly)
library(leaflet)
library(dplyr)
library(tidyr)
library(bslib)
library(shinyjs)

# Simulated datasets
plants_data <- data.frame(
  name = c("Bonn, Germany", "Grafschaft, Germany", "Solingen, Germany", "Cobern, Germany",
           "Kenosha, WI, USA", "Castelldefels, Spain", "Nørre Snede, Denmark", "Fagernes, Norway",
           "Pontefract, UK", "Uzès, France", "Brixen, Italy", "Neuss, Germany",
           "Pleasant Prairie, WI, USA (Dist.)", "Dunhagen, Ireland"),
  lat = c(50.7374, 50.5874, 51.1657, 50.3167, 42.5847, 41.2800, 55.9667, 60.9858,
          53.6919, 44.0122, 46.7150, 51.2042, 42.5531, 53.6333),
  lon = c(7.0982, 7.0674, 7.0066, 7.4667, -87.8212, 1.9768, 9.4000, 9.2324,
          -1.3127, 4.4197, 11.6550, 6.6877, -87.9334, -6.7667)
)

haribo_metrics <- data.frame(
  Year = c(2022, 2023),
  Turnover_Million_GBP = c(218, 270),
  Export_Growth_Percent = c(0, 20),
  Domestic_Growth_Percent = c(0, 24),
  PreTax_Profit_Million_GBP = c(35, 31)
)

haribo_facility_info <- data.frame(
  attribute = c(
    "Global Production Sites", "Global Employees", "Pleasant Prairie Plant Size (sq ft)",
    "Pleasant Prairie Warehouse (sq ft)", "Goldbears Daily Output", "Future Plant Size (sq ft)",
    "Pleasant Prairie Production Staff", "Warehouse Staff", "Part-time Staff",
    "Investment in Phase 1 (USD Million)", "Planned Expansion (Bristol, WI)", "US Facility Type",
    "New Manufacturing Lines", "Jobs in Phase 1", "Phase 2 Jobs Planned",
    "Current Wisconsin Direct Employees", "Third-party Shipping Staff",
    "Remaining Jobs to Fill (Phase 1)", "Total Tax Credits Awarded (USD Million)", "Tax Credits Released"
  ),
  value = c(
    "16 sites in 10 countries", "~7,000", "500,000", "87,866", "60 million", "2,000,000",
    "450 full-time", "44 full-time", "20 part-time", "148.5", "Tripling warehouse capacity",
    "Goldbears-focused", "Twin Snakes planned", "400", "400",
    "187", "60", "220", "22.5", "8.6"
  )
)

tariff_factors_data <- data.frame(
  year = 2020:2023,
  rules_compliance = c(7.5, 8.0, 8.2, 8.4),
  trade_leverage = c(6.5, 7.0, 7.2, 7.5),
  market_proximity = c(8.1, 8.3, 8.5, 8.6)
)

sourcing_data <- data.frame(
  scenario = c("Local US", "Brazil Mix", "EU Mix"),
  gelatin = c(0.7, 0.5, 0.4),
  corn_syrup = c(0.8, 0.6, 0.5),
  sugar = c(0.9, 0.7, 0.8),
  citric_acid = c(0.6, 0.5, 0.7),
  cost = c(9.5, 8.0, 8.5),
  tariff_risk = c(2.0, 3.0, 1.5)
)

tariff_duties_data <- data.frame(
  year = 2020:2023,
  raw_materials = c(5.0, 5.2, 5.1, 4.9),
  finished_goods = c(7.0, 6.8, 6.5, 6.2)
)

product_diff_data <- data.frame(
  ingredient = rep(c("Gelatin", "Corn Syrup", "Sugar"), 2),
  proportion = c(0.35, 0.25, 0.40, 0.30, 0.20, 0.50),
  region = rep(c("US", "Germany"), each = 3)
)

regulatory_data <- data.frame(
  regulation = rep(c("Food Color", "Preservatives", "Sweeteners"), 2),
  strictness = c(7, 8, 6, 9, 9, 7),
  region = rep(c("US", "EU"), each = 3)
)

taste_test_data <- data.frame(
  year = rep(2020:2023, 2),
  region = rep(c("US", "Germany"), each = 4),
  preference = c(6.8, 7.0, 7.2, 7.1, 8.0, 8.2, 8.1, 8.3)
)

strategic_data <- data.frame(
  year = 2020:2023,
  jobs = c(500, 520, 540, 580),
  market_share = c(15, 16, 17, 18),
  trade_resilience = c(6.0, 6.5, 6.7, 7.0)
)

# UI
ui <- fluidPage(
  theme = bs_theme(
    bg = "#121212",
    fg = "#f0f0f0",
    primary = "#fdd835",
    base_font = font_google("Inter")
  ),
  useShinyjs(),
  tags$head(
    tags$link(
      rel = "icon",
      href = "haribo-logo.png",
      type = "image/png"
    ),
    tags$style(HTML("
      .landing-page { 
        text-align: center; 
        padding: 50px; 
        background: url('https://images.unsplash.com/photo-1626284054396-6fd9436b4e1c') no-repeat center center; 
        background-size: cover; 
        min-height: 100vh; 
        display: flex; 
        flex-direction: column; 
        justify-content: center; 
        color: #f0f0f0; 
      }
      .landing-page h1 { 
        font-size: 3em; 
        margin-bottom: 20px; 
        text-shadow: 2px 2px 4px rgba(0,0,0,0.5); 
      }
      .landing-page p { 
        font-size: 1.2em; 
        max-width: 600px; 
        margin: 0 auto 30px; 
      }
      .landing-page .btn-enter { 
        font-size: 1.5em; 
        padding: 15px 30px; 
        background-color: #fdd835; 
        color: #121212; 
        border: none; 
        border-radius: 25px; 
        cursor: pointer; 
        transition: background-color 0.3s; 
      }
      .landing-page .btn-enter:hover { 
        background-color: #e6c200; 
      }
      .dashboard { 
        padding: 20px; 
      }
      .logo-img {
        width: 200px;
        margin-bottom: 20px;
      }
    "))
  ),
  uiOutput("page")
)

# Server
server <- function(input, output, session) {
  # Reactive value to track page state
  rv <- reactiveValues(page = "landing")

  # Render UI based on page state
  output$page <- renderUI({
    if (rv$page == "landing") {
      div(
        class = "landing-page",
        img(src = "haribo-logo.png", class = "logo-img"),
        h1("Explore Haribo’s Tariff Triumph"),
        p("Dive into an interactive analysis of how Haribo dodged EU tariffs with its US operations. Discover global plant locations, ingredient sourcing, product differences, and strategic insights behind the gummy giant’s success."),
        actionButton("enter_dashboard", "Enter Dashboard", class = "btn-enter")
      )
    } else {
      div(
        class = "dashboard",
        titlePanel("Haribo Tariff Exemption Analysis"),
        tabsetPanel(
          tabPanel(
            "Plant Locations",
            leafletOutput("map", height = 400),
            p("Global map of Haribo's 14 production and distribution facilities.")
          ),
          tabPanel(
            "Tariff Exemption Factors",
            selectInput(
              "tariff_factor",
              "Select Factor:",
              choices = c(
                "Rules Compliance" = "rules_compliance",
                "Trade Leverage" = "trade_leverage",
                "Market Proximity" = "market_proximity"
              )
            ),
            plotlyOutput("tariff_plot", height = 400),
            p("Trends in factors contributing to tariff exemption.")
          ),
          tabPanel(
            "Sourcing Scenarios",
            selectInput(
              "sourcing_scenario",
              "Select Scenario:",
              choices = c("Local US", "Brazil Mix", "EU Mix")
            ),
            plotlyOutput("sourcing_plot", height = 400),
            plotlyOutput("tariff_duties_plot", height = 400),
            p("Ingredient sourcing proportions and tariff duties comparison.")
          ),
          tabPanel(
            "Product Differences",
            plotlyOutput("product_diff_plot", height = 400),
            p("Comparison of US vs. German Goldbears ingredients.")
          ),
          tabPanel(
            "Regulatory Drivers",
            plotlyOutput("regulatory_plot", height = 400),
            p("US vs. EU regulatory strictness for confectionery.")
          ),
          tabPanel(
            "Quality & Perception",
            plotlyOutput("taste_test_plot", height = 400),
            p("Taste test preference trends for US and German Goldbears.")
          ),
          tabPanel(
            "Strategic Insights",
            plotlyOutput("strategic_plot", height = 400),
            p("Trends in jobs, market share, and trade resilience.")
          ),
          tabPanel(
            "Haribo Metrics",
            plotlyOutput("metrics_plot", height = 400),
            p("Financial and growth metrics for Haribo UK operations.")
          ),
          tabPanel(
            "Facility Info",
            tableOutput("facility_table"),
            p("Key attributes of Haribo’s US operations.")
          )
        )
      )
    }
  })

  # Switch to dashboard on button click
  observeEvent(input$enter_dashboard, {
    rv$page <- "dashboard"
  })

  # Plant locations map
  output$map <- renderLeaflet({
    leaflet(plants_data) %>%
      addTiles() %>%
      addMarkers(~lon, ~lat, popup = ~name, label = ~name) %>%
      setView(lng = 0, lat = 20, zoom = 2)
  })

  # Tariff factors line graph
  output$tariff_plot <- renderPlotly({
    req(input$tariff_factor)
    plot_ly(tariff_factors_data, x = ~year, y = ~get(input$tariff_factor), type = "scatter", mode = "lines+markers") %>%
      layout(
        title = paste(input$tariff_factor, "Over Time"),
        xaxis = list(title = "Year"),
        yaxis = list(title = "Score")
      )
  })

  # Sourcing scenarios bar graph
  output$sourcing_plot <- renderPlotly({
    req(input$sourcing_scenario)
    data <- sourcing_data %>% filter(scenario == input$sourcing_scenario)
    plot_ly(data) %>%
      add_trace(
        x = c("Gelatin", "Corn Syrup", "Sugar", "Citric Acid"),
        y = c(data$gelatin, data$corn_syrup, data$sugar, data$citric_acid),
        type = "bar",
        name = "Proportion"
      ) %>%
      add_trace(
        x = c("Cost", "Tariff Risk"),
        y = c(data$cost, data$tariff_risk),
        type = "bar",
        name = "Metrics"
      ) %>%
      layout(
        title = paste("Sourcing:", input$sourcing_scenario),
        xaxis = list(title = "Component"),
        yaxis = list(title = "Value")
      )
  })

  # Tariff duties line graph
  output$tariff_duties_plot <- renderPlotly({
    plot_ly(tariff_duties_data) %>%
      add_trace(x = ~year, y = ~raw_materials, name = "Raw Materials", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~year, y = ~finished_goods, name = "Finished Goods", type = "scatter", mode = "lines+markers") %>%
      layout(
        title = "Tariff Duties Comparison",
        xaxis = list(title = "Year"),
        yaxis = list(title = "Duty (%)")
      )
  })

  # Product differences bar graph
  output$product_diff_plot <- renderPlotly({
    plot_ly(product_diff_data, x = ~ingredient, y = ~proportion, color = ~region, type = "bar", barmode = "group") %>%
      layout(
        title = "US vs. German Goldbears Ingredients",
        xaxis = list(title = "Ingredient"),
        yaxis = list(title = "Proportion")
      )
  })

  # Regulatory drivers bar graph
  output$regulatory_plot <- renderPlotly({
    plot_ly(regulatory_data, x = ~regulation, y = ~strictness, color = ~region, type = "bar", barmode = "group") %>%
      layout(
        title = "Regulatory Strictness: US vs. EU",
        xaxis = list(title = "Regulation"),
        yaxis = list(title = "Strictness")
      )
  })

  # Taste test line graph
  output$taste_test_plot <- renderPlotly({
    plot_ly(taste_test_data) %>%
      add_trace(x = ~year, y = ~preference, color = ~region, type = "scatter", mode = "lines+markers") %>%
      layout(
        title = "Taste Test Preference",
        xaxis = list(title = "Year"),
        yaxis = list(title = "Preference")
      )
  })

  # Strategic insights line graph
  output$strategic_plot <- renderPlotly({
    plot_ly(strategic_data) %>%
      add_trace(x = ~year, y = ~jobs, name = "Jobs", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~year, y = ~market_share, name = "Market Share", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~year, y = ~trade_resilience, name = "Trade Resilience", type = "scatter", mode = "lines+markers") %>%
      layout(
        title = "Strategic Insights",
        xaxis = list(title = "Year"),
        yaxis = list(title = "Value")
      )
  })

  # Haribo metrics line graph
  output$metrics_plot <- renderPlotly({
    plot_ly(haribo_metrics) %>%
      add_trace(x = ~Year, y = ~Turnover_Million_GBP, name = "Turnover (M GBP)", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~Year, y = ~Export_Growth_Percent, name = "Export Growth (%)", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~Year, y = ~Domestic_Growth_Percent, name = "Domestic Growth (%)", type = "scatter", mode = "lines+markers") %>%
      add_trace(x = ~Year, y = ~PreTax_Profit_Million_GBP, name = "Pre-Tax Profit (M GBP)", type = "scatter", mode = "lines+markers") %>%
      layout(
        title = "Haribo UK Financial Metrics",
        xaxis = list(title = "Year"),
        yaxis = list(title = "Value")
      )
  })

  # Facility info table
  output$facility_table <- renderTable({
    haribo_facility_info
  })
}

# Run the app
shinyApp(ui = ui, server = server)
```

**Note**: Ensure `haribo-logo.png` is in the `www/` folder of your project directory.

---

## Why This Matters

In an era of escalating trade wars and supply chain disruptions, understanding how global companies like Haribo navigate tariffs is critical. As a Senior Economist and Supply Chain Expert, I see this project as more than an analysis—it’s a blueprint for resilience. Haribo’s tariff exemption through its US plant showcases strategic localization, a model for businesses facing similar pressures. For communities, it means jobs (400 in Wisconsin alone) and economic stability. For consumers, it ensures affordable gummy bears despite trade tensions.

Beyond economics, this project highlights a transformative trend: **democratized innovation**. By using low-code/no-code tools and AI (xAI’s Grok, OpenAI’s ChatGPT), I built a sophisticated app without years of coding expertise. This empowers non-technical professionals—economists, managers, educators—to create impactful tools, bridging the gap between complex data and actionable insights. In a world where trade policies shape markets overnight, such accessibility can drive informed decisions, foster collaboration, and spark curiosity across industries.

---

## Contributing

Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a branch (`git checkout -b feature/your-feature`).
3. Commit changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a Pull Request.

Please include tests and documentation for new features.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **xAI**: For Grok’s invaluable assistance in code generation and economic insights.
- **OpenAI**: For ChatGPT’s support in UI design and iterative development.
- **Haribo**: For inspiring this analysis with their global supply chain strategy.
- **R Shiny Community**: For robust tools that make data visualization accessible.

---

Explore the app, share your feedback, and let’s uncover the sweet success of Haribo’s tariff strategy together!
