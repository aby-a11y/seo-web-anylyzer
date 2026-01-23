# SEO Genius - AI-Powered SEO Analysis Tool

## Overview

SEO Genius is a professional-grade SEO analysis tool that leverages advanced AI (GPT-5.2) to provide comprehensive website audits. It analyzes on-page SEO elements, generates keyword strategies, identifies content gaps, and provides actionable 30-day improvement plans.

## Features

### 🔍 Comprehensive Website Analysis
- **On-Page SEO Audit**: Title tags, meta descriptions, heading structure (H1-H6)
- **Content Analysis**: Word count, content depth, semantic structure
- **Technical SEO**: Structured data detection, canonical URLs, Open Graph tags

### 🎯 AI-Powered Insights
- **Intelligent Issue Detection**: Prioritized SEO issues (High/Medium/Low)
- **Keyword Strategy**: Primary and long-tail keyword recommendations with intent classification
- **Competitor Analysis**: Assumptive competitive landscape and content gap identification
- **Content Recommendations**: SEO-optimized content ideas with suggested structure

### 📊 Actionable Reports
- **SEO Score**: 0-100 rating with detailed breakdown
- **30-Day Action Plan**: Week-by-week prioritized tasks with expected impact
- **Professional Presentation**: Client-ready reports with copy-to-clipboard functionality
- **Report History**: Save and manage multiple SEO analyses

## Technology Stack

### Backend
- **Framework**: FastAPI (Python)
- **Database**: MongoDB (Motor async driver)
- **AI Integration**: OpenAI GPT-5.2 via emergentintegrations
- **Web Scraping**: BeautifulSoup4 + httpx
- **API Design**: RESTful with comprehensive error handling

### Frontend
- **Framework**: React 19
- **UI Library**: Radix UI components
- **Styling**: Tailwind CSS with custom animations
- **Routing**: React Router v7
- **HTTP Client**: Axios

## API Endpoints

### SEO Analysis
```
POST /api/seo/analyze
Body: { "url": "https://example.com" }
Response: Complete SEO report object
```

### Get All Reports
```
GET /api/seo/reports
Response: Array of SEO reports (sorted by date)
```

### Get Specific Report
```
GET /api/seo/reports/{report_id}
Response: Single SEO report object
```

### Delete Report
```
DELETE /api/seo/reports/{report_id}
Response: Success message
```

## Architecture

### Data Flow
1. **User Input**: URL submitted via frontend form
2. **Web Scraping**: Backend fetches and parses HTML content
3. **AI Analysis**: Scraped data sent to GPT-5.2 for comprehensive SEO audit
4. **Report Generation**: Structured report saved to MongoDB
5. **Display**: Frontend renders professional report with all sections

### Key Components

#### Backend (`/app/backend/server.py`)
- `scrape_website()`: Extracts SEO-relevant data from websites
- `analyze_with_ai()`: Generates AI-powered SEO insights
- API routes for CRUD operations on SEO reports

#### Frontend Pages
- **HomePage**: Landing page with URL input and feature highlights
- **ReportPage**: Detailed SEO report display with multiple sections
- **HistoryPage**: List of all analyzed websites with management options

## Setup & Configuration

### Environment Variables

**Backend** (`/app/backend/.env`):
```
MONGO_URL=mongodb://localhost:27017
DB_NAME=test_database
CORS_ORIGINS=*
EMERGENT_LLM_KEY=sk-emergent-01c4d7f27C2D87cF73
```

**Frontend** (`/app/frontend/.env`):
```
REACT_APP_BACKEND_URL=https://your-domain.com
WDS_SOCKET_PORT=443
ENABLE_HEALTH_CHECK=false
```

### Installation

1. **Backend Dependencies**:
```bash
cd /app/backend
pip install -r requirements.txt
```

2. **Frontend Dependencies**:
```bash
cd /app/frontend
yarn install
```

### Running the Application

All services are managed by supervisor:

```bash
# Restart all services
sudo supervisorctl restart all

# Check status
sudo supervisorctl status

# View logs
tail -f /var/log/supervisor/backend.err.log
tail -f /var/log/supervisor/frontend.out.log
```

## SEO Report Structure

Each report includes:

1. **Website Overview**
   - SEO Score (0-100)
   - Title tag and meta description
   - H1 tags found
   - Word count
   - Analysis timestamp

2. **SEO Issues**
   - Priority level (High/Medium/Low)
   - Category (e.g., "Title Tag", "Content", "Technical")
   - Specific issue description
   - Actionable recommendation

3. **Keyword Strategy**
   - Primary keyword
   - 5-10 long-tail keywords
   - Keyword intent classification (informational/commercial/transactional)

4. **Competitor Analysis**
   - Assumed top competitors
   - Content gaps to fill
   - Opportunities to outperform

5. **Content Recommendations**
   - Suggested page types (Blog Post/Landing Page/Product Page)
   - Topics with high SEO potential
   - Target keywords for each topic
   - Ideal content structure (H1/H2/H3 hierarchy)

6. **30-Day Action Plan**
   - Week-by-week breakdown
   - Priority level for each task
   - Specific actions to take
   - Expected impact

## AI Integration

The tool uses OpenAI's GPT-5.2 model via the emergentintegrations library:

- **Model**: gpt-5.2 (latest, most capable)
- **Provider**: OpenAI
- **Key Management**: Uses Emergent universal key (EMERGENT_LLM_KEY)
- **Analysis Approach**: Senior SEO consultant persona with structured JSON output

## Best Practices

### For Users
1. **URL Format**: Always include protocol (http:// or https://)
2. **Analysis Time**: Expect 15-30 seconds for complete analysis
3. **Rate Limiting**: Respect website robots.txt and rate limits
4. **Report Storage**: Reports are stored indefinitely until manually deleted

### For Developers
1. **Error Handling**: All scraping failures gracefully handled with clear messages
2. **Timeout Management**: 30-second timeout for web requests
3. **Data Validation**: Pydantic models ensure data integrity
4. **Async Operations**: All I/O operations use async/await for performance

## Troubleshooting

### Common Issues

**Website Scraping Fails**:
- Some websites block automated requests
- Check if website requires authentication
- Verify URL is accessible

**AI Analysis Errors**:
- Ensure EMERGENT_LLM_KEY is valid
- Check API rate limits
- Verify JSON parsing in AI response

**MongoDB Connection Issues**:
- Confirm MongoDB is running: `sudo supervisorctl status mongodb`
- Check MONGO_URL in backend/.env

## Future Enhancements

Potential features for future versions:
- PDF export of reports
- Scheduled recurring audits
- Performance metrics (page speed, Core Web Vitals)
- Backlink analysis integration
- Rank tracking over time
- Multi-language support
- Team collaboration features

## License

Proprietary - SEO Genius by Emergent Agent

## Support

For issues or questions, refer to system logs or contact support.

---

**Built with ❤️ using AI-powered development**
