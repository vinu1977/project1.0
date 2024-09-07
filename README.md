# project1.0
import requests

# Function to get weather data
def get_weather(city, api_key):
    base_url = "http://api.openweathermap.org/data/2.5/weather?"
    
    # Complete URL for the request
    complete_url = base_url + "q=" + city + "&appid=" + api_key + "&units=metric"
    
    # Send request to OpenWeatherMap API
    response = requests.get(complete_url)
    
    # Check the status code (200 means success)
    if response.status_code == 200:
        data = response.json()
        
        # Extracting and displaying key information
        main = data['main']
        temperature = main['temp']
        pressure = main['pressure']
        humidity = main['humidity']
        weather_desc = data['weather'][0]['description']
        
        print(f"City: {city}")
        print(f"Temperature: {temperature}°C")
        print(f"Weather: {weather_desc}")
        print(f"Pressure: {pressure} hPa")
        print(f"Humidity: {humidity}%")
        
    else:
        # If city is not found
        print("City not found, please check the name and try again.")

# Main function
def main():
    api_key = "your_api_key_here"  # Replace with your OpenWeatherMap API key
    city = input("Enter the city name: ")
    get_weather(city, api_key)

# Run the main function
if __name__ == "__main__":
    main()
