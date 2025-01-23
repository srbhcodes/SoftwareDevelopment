### Report: Simple Weather Application

**Author**: Sourabh  
**Date**: 13 Dec
Title: Simple Weather Application
Git link: https://github.com/srbhcodes/WeatherApp

---

### **Scope of Project**

The goal of this project is to build a simple weather application that allows users to retrieve real-time weather information for any city. The application fetches data from the OpenWeatherMap API and displays details such as temperature, weather description, humidity, and wind speed. This project serves as an introduction to working with APIs and handling HTTP requests in Python.

---

### **Technologies Used**

- **Programming Language**: Python
- **Libraries**: `requests` (for HTTP requests)
- **API**: OpenWeatherMap API
- **Environment Variables**: `.bashrc` (for securely storing the API key)

---

### **Steps**

1. **Set Up Environment**:
    
    - Installed Python 3.x and the `requests` library.
2. **Create Project Directory**:
    
    - Created a folder and added the `weather.py` script file.
3. **Register on OpenWeatherMap**:
    
    - Created an account on OpenWeatherMap and obtained an API key.
4. **Write Python Script**:
    
    - Fetched weather data using the API.
    - Parsed the response to extract temperature, weather description, humidity, and wind speed.
5. **Error Handling**:
    
    - Handled scenarios like invalid API keys, city not found, and network issues.
6. **Environment Variable Setup**:
    
    - Stored the API key securely in the `.bashrc` file and accessed it using the `os` module.
7. **Test the Application**:
    
    - Verified functionality by running the script and entering different city names.
8. **Enhance Output**:
    
    - Formatted the output for better readability.

---

### **Project Outcome**

The weather application successfully retrieves and displays weather data for a given city. It provides:

- Current temperature (in °C).
- Weather description (e.g., "Clear sky").
- Humidity percentage.
- Wind speed (in m/s).

The project demonstrates how to work with APIs, handle errors, and use environment variables for secure data storage.

---

### **Issues Faced**

1. **Invalid API Key (401)**:
    
    - Cause: Incorrect or missing API key.
    - Solution: Verified the API key and set it as an environment variable.
2. **City Not Found (404)**:
    
    - Cause: Typing incorrect city names.
    - Solution: Added error handling to display meaningful messages.
3. **Network Errors**:
    
    - Cause: Temporary issues with the internet connection.
    - Solution: Added checks for unsuccessful HTTP requests.
4. **Environment Variable Not Loaded**:
    
    - Cause: `.bashrc` file not sourced properly after adding the API key.
    - Solution: Used `source ~/.bashrc` to reload environment variables.
5. **Formatting Issues**:
    
    - Cause: Initial output was unstructured and hard to read.
    - Solution: Reformatted the output for clarity and user-friendliness.

---

### Screenshots:

![[Pasted image 20250107214027.png]]