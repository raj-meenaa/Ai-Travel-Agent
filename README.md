# 🤖 AI Travel Agent

A comprehensive AI-powered travel planning application that helps users find flights, hotels, and create personalized travel itineraries. Built with Streamlit for the frontend and a modular agent-based architecture for travel services.

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![Streamlit](https://img.shields.io/badge/streamlit-latest-red)
![License](https://img.shields.io/badge/license-MIT-green)

## 🚀 Features

### Core Functionality
- **✈️ Flight Search**: Real-time flight search with multiple airlines and pricing options
- **🏨 Hotel Booking**: Comprehensive hotel search with ratings, amenities, and pricing
- **📧 Email Integration**: Automated email delivery of travel recommendations
- **🤖 AI-Powered Recommendations**: Intelligent analysis of travel options using Ollama/LLM
- **📱 User-Friendly Interface**: Clean Streamlit web interface for easy interaction

### Key Capabilities
- Multi-destination flight searches (outbound and return)
- Hotel recommendations based on location, dates, and preferences
- Price comparison and optimization
- Professional email formatting with HTML content
- Real-time availability and pricing updates
- Airline logos and hotel images integration
- Booking links and direct reservations

## 🏗️ Architecture

The application follows a modular agent-based architecture:

```
┌─────────────────┐
│   Streamlit UI  │
└─────────┬───────┘
          │
┌─────────▼───────┐
│ Orchestrator    │
│    Agent        │
└─────────┬───────┘
          │
    ┌─────┼─────┐
    ▼     ▼     ▼
┌───────┐ ┌─────┐ ┌───────┐
│Flight │ │Hotel│ │ Email │
│Agent  │ │Agent│ │ Agent │
└───────┘ └─────┘ └───────┘
```

### Component Overview

#### 1. **Orchestrator Agent** (`agents/orchestrator_agent.py`)
- **Role**: Central coordinator for the entire travel planning workflow
- **Responsibilities**:
  - Manages flight searches for both outbound and return trips
  - Handles hotel searches based on destination and dates
  - Coordinates email delivery of travel recommendations
  - Analyzes and combines results for optimal suggestions
  - Tracks workflow progress and handles errors
- **Features**: 
  - Pricing optimization
  - Scheduling efficiency analysis
  - User preference consideration
  - Comprehensive travel recommendations with detailed pricing

#### 2. **Flight Agent** (`agents/flight_agent.py`)
- **Role**: Specialized flight search and analysis
- **Capabilities**:
  - Real-time flight searches using SerpAPI
  - Price comparison across multiple airlines
  - Flight duration and convenience analysis
  - Airline reputation consideration
  - Integration with airline logos and booking links
- **Output**: Detailed flight information in HTML format with pricing, schedules, and airline details

#### 3. **Hotel Agent** (`agents/hotel_agent.py`)
- **Role**: Hotel search and recommendation engine
- **Features**:
  - Location-based hotel searches
  - Price range filtering and comparison
  - Guest ratings and review analysis
  - Amenity-based recommendations
  - Hotel class and star rating considerations
- **Output**: Hotel recommendations with images, pricing, amenities, and booking information

#### 4. **Email Agent** (`agents/email_agent.py`)
- **Role**: Professional email communication
- **Functionality**:
  - Creates detailed travel itinerary emails
  - Formats content in clean, professional HTML
  - Includes flight details, hotel information, and pricing
  - Integrates images, logos, and booking links
  - Uses SendGrid for reliable email delivery
- **Template**: Professional HTML email templates with embedded travel information

#### 5. **Base Agent** (`agents/base_agent.py`)
- **Role**: Foundation class for all specialized agents
- **Provides**:
  - Common LLM integration (Ollama/OpenAI compatible)
  - JSON parsing utilities
  - Error handling mechanisms
  - System prompts for tools and email formatting
  - Standardized agent interface

## 📋 Requirements

### System Dependencies
- Python 3.8 or higher
- Internet connection for API calls

### Python Packages
- `streamlit` - Web interface framework
- `openai` - LLM integration (compatible with Ollama)
- `python-dotenv` - Environment variable management
- `sendgrid` - Email delivery service
- `google-search-results` (serpapi) - Flight and hotel search
- `requests` - HTTP client for API calls
- `asyncio` - Asynchronous programming support

### External Services Required
1. **Ollama** - Local LLM service running on `localhost:11434`
2. **SerpAPI** - Google search API for flights and hotels
3. **SendGrid** - Email delivery service

## ⚙️ Setup & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/raj-meenaa/Ai-Travel-Agent.git
cd Ai-Travel-Agent
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Environment Configuration
Create a `.env` file in the root directory:

```env
# SerpAPI for flight and hotel searches
SERPAPI_API_KEY=your_serpapi_key_here

# SendGrid for email delivery
SENDGRID_KEY=your_sendgrid_api_key_here

# Ollama Configuration (if different from default)
OLLAMA_BASE_URL=http://localhost:11434/v1
```

### 4. Setup Ollama (Local LLM)
```bash
# Install Ollama (macOS/Linux)
curl -fsSL https://ollama.ai/install.sh | sh

# Pull the required model
ollama pull llama3.2

# Start Ollama service
ollama serve
```

### 5. Get API Keys

#### SerpAPI (Required for flight/hotel searches)
1. Visit [SerpAPI](https://serpapi.com)
2. Sign up for an account
3. Get your API key from the dashboard
4. Add to `.env` file

#### SendGrid (Required for email functionality)
1. Visit [SendGrid](https://sendgrid.com)
2. Create an account
3. Generate an API key
4. Add to `.env` file

## 🎮 Usage

### Starting the Application
```bash
streamlit run main.py
```

The application will be available at `http://localhost:8501`

### Using the Interface

1. **Enter Travel Details**:
   - Origin airport code (e.g., MAD for Madrid)
   - Destination airport code (e.g., AMS for Amsterdam)
   - Departure and return dates
   - Number of adults, children, and rooms
   - Your email address

2. **Select Email Preference**:
   - Choose whether to receive results via email

3. **Get Recommendations**:
   - Click "Get Travel Information"
   - View flight and hotel options in separate tabs
   - See pricing, ratings, and booking links

4. **Review Results**:
   - **Flight Options**: Airlines, schedules, prices, booking links
   - **Hotel Options**: Properties, ratings, amenities, pricing
   - **Email Summary**: Professional itinerary sent to your inbox

### Example Usage
```
Origin: LAX (Los Angeles)
Destination: NYC (New York)
Departure: 2024-03-15
Return: 2024-03-22
Adults: 2
Children: 0
Rooms: 1
Email: your-email@example.com
```

## 🛠️ Development

### Project Structure
```
Ai-Travel-Agent/
├── main.py                 # Streamlit application entry point
├── agents/                 # Agent modules
│   ├── __init__.py
│   ├── base_agent.py      # Base class for all agents
│   ├── orchestrator_agent.py # Main coordinator
│   ├── flight_agent.py    # Flight search specialist
│   ├── hotel_agent.py     # Hotel search specialist
│   └── email_agent.py     # Email communication
├── requirements.txt        # Python dependencies
├── .env                   # Environment variables (create this)
└── README.md              # This file
```

### Key Functions

#### `main.py`
- `main()`: Streamlit UI and user interaction
- `process_travel_request()`: Async processing of travel requests

#### Agent Methods
- `run()`: Main execution method for each agent
- `_query_ollama()`: LLM integration for intelligent recommendations
- `_parse_json_safely()`: Safe JSON parsing with error handling

### Customization Options

1. **Add New Search Providers**: Extend agents to support additional APIs
2. **Modify Email Templates**: Update HTML templates in email agent
3. **Enhance Recommendations**: Improve LLM prompts for better suggestions
4. **Add New Features**: Extend the agent architecture for additional services

## 🔧 Configuration

### Ollama Model Configuration
The application uses `llama3.2` by default. To use different models:

1. Pull the desired model: `ollama pull model-name`
2. Update `base_agent.py`:
```python
model="your-preferred-model"
```

### Search Parameters
Customize search behavior in agent files:
- Flight search parameters in `flight_agent.py`
- Hotel search filters in `hotel_agent.py`
- Email templates in `email_agent.py`

## 🚨 Troubleshooting

### Common Issues

1. **Ollama Connection Error**
   - Ensure Ollama is running: `ollama serve`
   - Check the correct port (default: 11434)
   - Verify model is installed: `ollama list`

2. **API Key Errors**
   - Verify `.env` file exists and has correct keys
   - Check API key validity on respective platforms
   - Ensure sufficient API credits/quota

3. **Streamlit Issues**
   - Update Streamlit: `pip install --upgrade streamlit`
   - Clear browser cache
   - Check for port conflicts

### Error Messages
- `No module named 'streamlit'` → Install requirements: `pip install -r requirements.txt`
- `Error querying Ollama` → Check Ollama service and model availability
- `Invalid JSON format` → API response parsing issue, check API keys

## 🎯 Future Enhancements

### Planned Features
- [ ] **Car Rental Integration**: Add car rental search and booking
- [ ] **Activity Recommendations**: Suggest local activities and attractions
- [ ] **Multi-city Trips**: Support for complex itineraries
- [ ] **Price Alerts**: Monitor and notify about price changes
- [ ] **User Profiles**: Save preferences and past searches
- [ ] **Mobile App**: React Native or Flutter mobile application
- [ ] **Social Features**: Share itineraries with friends and family
- [ ] **Expense Tracking**: Budget management and expense monitoring

### Technical Improvements
- [ ] **Caching System**: Redis integration for faster responses
- [ ] **Database Integration**: PostgreSQL for user data and history
- [ ] **Microservices**: Break down agents into separate services
- [ ] **API Gateway**: RESTful API for third-party integrations
- [ ] **Load Balancing**: Handle multiple concurrent users
- [ ] **Testing Suite**: Comprehensive unit and integration tests

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Raj Meena**
- GitHub: [@raj-meenaa](https://github.com/raj-meenaa)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and test thoroughly
4. Commit your changes: `git commit -m 'Add some feature'`
5. Push to the branch: `git push origin feature-name`
6. Submit a pull request

## 📞 Support

If you encounter any issues or have questions, please:
1. Check the troubleshooting section above
2. Search existing [issues](https://github.com/raj-meenaa/Ai-Travel-Agent/issues)
3. Create a new issue with detailed information

---

**Made with ❤️ by [Raj Meena](https://github.com/raj-meenaa)**