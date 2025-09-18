# Contributing to AI Travel Agent

Thank you for your interest in contributing to the AI Travel Agent project! We welcome contributions from everyone.

## 🚀 Getting Started

### Prerequisites
- Python 3.8 or higher
- Git
- Basic knowledge of Python and Streamlit

### Setting up the Development Environment

1. **Fork the repository**
   ```bash
   git clone https://github.com/your-username/Ai-Travel-Agent.git
   cd Ai-Travel-Agent
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your API keys
   ```

4. **Start Ollama service**
   ```bash
   ollama serve
   ollama pull llama3.2
   ```

5. **Run the application**
   ```bash
   streamlit run main.py
   ```

## 🛠️ Development Guidelines

### Code Style
- Follow PEP 8 Python style guidelines
- Use meaningful variable and function names
- Add docstrings to classes and methods
- Keep functions focused and single-purpose

### Project Structure
```
agents/
├── base_agent.py       # Base class for all agents
├── orchestrator_agent.py  # Main workflow coordinator
├── flight_agent.py     # Flight search functionality
├── hotel_agent.py      # Hotel search functionality
└── email_agent.py      # Email communication
```

### Adding New Features

1. **New Agent Creation**
   - Extend `BaseAgent` class
   - Implement the `run()` method
   - Add appropriate error handling
   - Include comprehensive docstrings

2. **API Integration**
   - Add new dependencies to `requirements.txt`
   - Use environment variables for API keys
   - Add error handling for API failures
   - Include rate limiting considerations

3. **UI Changes**
   - Maintain Streamlit component consistency
   - Test responsive design elements
   - Ensure accessibility standards

### Testing

While this project doesn't have formal tests yet, please:
- Test your changes manually
- Verify API integrations work
- Check error handling scenarios
- Ensure the UI remains functional

## 📝 Pull Request Process

1. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**
   - Write clean, well-documented code
   - Test thoroughly
   - Update documentation if needed

3. **Commit your changes**
   ```bash
   git add .
   git commit -m "Add: descriptive commit message"
   ```

4. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Submit a Pull Request**
   - Provide a clear description of changes
   - Reference any related issues
   - Include screenshots for UI changes

## 🐛 Reporting Issues

When reporting bugs or requesting features:

1. **Search existing issues** to avoid duplicates
2. **Use clear, descriptive titles**
3. **Provide detailed information:**
   - Steps to reproduce
   - Expected vs actual behavior
   - System information (OS, Python version)
   - Error messages or logs
   - Screenshots if relevant

## 🎯 Areas for Contribution

### High Priority
- [ ] Add comprehensive error handling
- [ ] Implement caching for API responses
- [ ] Add user session management
- [ ] Create automated tests
- [ ] Improve API rate limiting

### Features
- [ ] Car rental integration
- [ ] Activity recommendations
- [ ] Multi-city trip planning
- [ ] Price tracking and alerts
- [ ] User preferences storage

### Documentation
- [ ] API documentation
- [ ] Deployment guides
- [ ] Video tutorials
- [ ] Code examples

### Bug Fixes
- Check the [issues page](https://github.com/raj-meenaa/Ai-Travel-Agent/issues) for reported bugs

## 🔧 Environment Variables

Required for development:
```env
SERPAPI_API_KEY=your_serpapi_key
SENDGRID_KEY=your_sendgrid_key
OLLAMA_BASE_URL=http://localhost:11434/v1
```

## 📚 Resources

- [Streamlit Documentation](https://docs.streamlit.io/)
- [SerpAPI Documentation](https://serpapi.com/google-flights-api)
- [SendGrid Documentation](https://docs.sendgrid.com/)
- [Ollama Documentation](https://ollama.ai/docs)

## ❓ Questions?

Feel free to:
- Open an issue for questions
- Join discussions in existing issues
- Contact the maintainer: [@raj-meenaa](https://github.com/raj-meenaa)

## 📄 License

By contributing, you agree that your contributions will be licensed under the same MIT License that covers the project.

---

**Thank you for contributing to AI Travel Agent! 🚀**