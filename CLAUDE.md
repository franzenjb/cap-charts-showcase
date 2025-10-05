# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a data visualization showcase for Coalition Assistance Program (CAP) metrics. The project demonstrates various ways to visualize quarterly performance data using Wall Street-quality charts with American Red Cross branding.

## Key Data Points Being Visualized

The client provided 5 specific quarterly metrics for 2024:
1. **Coalitions Formed**: Q1(32), Q2(41), Q3(38), Q4(36) - Total: 147
2. **Volunteers Recruited**: Q1(842), Q2(1,021), Q3(956), Q4(1,023) - Total: 3,842  
3. **Services Delivered**: Q1(2,456), Q2(3,123), Q3(3,342), Q4(3,536) - Total: 12,457
4. **Communities Served**: Q1(178), Q2(234), Q3(256), Q4(224) - Total: 892
5. **Response Time (hours)**: Q1(3.2), Q2(2.8), Q3(2.3), Q4(2.4) - Average: 2.7

## Architecture & File Structure

### Core Visualization Pages
- `index.html` - Unified dashboard with 8 tabs containing all visualization types
- `data-analysis.html` - Point-by-point breakdown showing 3 visualization options per metric
- `wall-street-redcross.html` - Premium Wall Street-style visualizations with Red Cross branding
- `simple-metrics.html` - Basic KPI cards and simple charts
- `advanced-analytics.html` - 3D surfaces, heatmaps, Sankey diagrams

### Technologies & Libraries
- **Chart.js** - Primary charting library (line, bar, pie, doughnut, radar, bubble)
- **Plotly.js** - Advanced visualizations (3D surfaces, waterfalls, sunbursts, heatmaps)
- **TailwindCSS** - Utility-first CSS framework for styling
- **D3.js** - Included but not actively used yet

### Design System
- **Primary Color**: `#ED1B2E` (Red Cross Red)
- **Secondary Colors**: `#00A0DF` (Accent Blue), `#6D6E70` (Gray), `#231F20` (Dark)
- **Font**: Open Sans (Google Fonts)
- **Chart Height**: Fixed at 400px using `.chart-wrapper` divs

## Common Development Tasks

### Testing Locally
```bash
# Start local server
python3 -m http.server 8080
# Open http://localhost:8080
```

### Deployment
The site automatically deploys to GitHub Pages on push to main branch via GitHub Actions.
Live URL: https://franzenjb.github.io/cap-charts-showcase/

### Adding New Visualizations
1. Charts must be wrapped in `.chart-wrapper` divs to prevent stretching
2. Canvas elements should not have height classes directly applied
3. Use Red Cross color palette for consistency
4. Include watermark divs for professional appearance

## Chart Implementation Patterns

### Chart.js Setup
```javascript
Chart.defaults.color = '#6D6E70';
Chart.defaults.font.family = 'Open Sans';

new Chart(ctx, {
    options: {
        responsive: true,
        maintainAspectRatio: false
    }
});
```

### Plotly Setup
```javascript
Plotly.newPlot('elementId', data, {
    paper_bgcolor: 'transparent',
    font: {family: 'Open Sans'}
});
```

## Important Notes

- The `index.html` uses lazy loading for charts - they initialize only when their tab is first clicked
- All charts are responsive but maintain a fixed 400px height
- The site is optimized for presenting to clients, focusing on clear data communication
- Each visualization option includes a recommendation explaining when/why to use it