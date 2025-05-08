# 📊 Census and Presidential Elections Dashboard

This interactive dashboard, built using **R**, **Shiny**, and **Flexdashboard**, explores U.S. census data (2008–2023) alongside presidential election data (2000–2020). The application presents an integrated view of social indicators and voting trends at the state level.

---

## 🚀 Features

- **Census Data Visualization**: Analyze poverty levels, income distribution, and social wealth classifications across states.
- **Election Results**: Explore voting patterns over five presidential election cycles.
- **Dynamic Interactivity**: Built with Shiny for responsive charts and user-driven filtering.
- **Visual Enhancements**: Uses `ggplot2`, `plotly`, `gt`, `flextable`, and `magick` for polished visualizations.

---

## 📁 Data Sources

- U.S. Census Data:  
  [Link](https://raw.githubusercontent.com/dilernia/STA418-518/main/Data/census_data_state_2008-2023.csv)

- Presidential Elections Data:  
  `countypres_2000-2020.csv` (uploaded to repository or read locally)

---

## 🛠 Technologies Used

- **R** and **RMarkdown**
- **Flexdashboard** for layout
- **Shiny** for interactivity
- **Packages**:  
  `tidyverse`, `ggplot2`, `plotly`, `lubridate`, `skimr`, `mice`, `naniar`, `gt`, `gtExtras`, `maps`, `scales`, `magick`, `grid`, `flextable`

---

## 📦 Installation and Deployment

### To Run Locally:

1. Clone the repository.
2. Open `dashboard.Rmd` in RStudio.
3. Click **"Run Document"** or use:

```r
rmarkdown::run("dashboard.Rmd")
```

### To Deploy on GitHub Pages:

1. Render the dashboard:

```r
rmarkdown::render("dashboard.Rmd")
```

2. Move the `.html` file to `/docs` folder (or root).
3. Enable GitHub Pages in repository settings (source = `main`, folder = `/docs` or `/`).
4. Access your dashboard at:  
   `https://yourusername.github.io/your-repo-name/`

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 👤 Author

**Obadiah Kiptoo**  
_MSc in Data Science and Analytics | Applied Statistics graduate | Passionate about data visualization and policy insights_

For inquiries or collaboration, feel free to reach out!
