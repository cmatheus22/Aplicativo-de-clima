# Aplicativo-de-clima
 Um aplicativo de previsão do tempo em Python que utiliza a API de previsão do tempo para fornecer informações precisas sobre o clima em diferentes cidades ao redor do mundo.

import requests

def get_weather(city):
    api_key = 'sua_chave_de_api'
    base_url = 'https://api.weather.com'
    endpoint = '/data/2.5/weather'
    params = {
        'q': city,
        'appid': api_key,
        'units': 'metric'  # Altere para 'imperial' para Fahrenheit
    }

    response = requests.get(base_url + endpoint, params=params)
    data = response.json()

    if response.status_code == 200:
        temperature = data['main']['temp']
        weather_desc = data['weather'][0]['description']
        return f'Temperatura em {city}: {temperature}°C, {weather_desc}'
    else:
        return 'Não foi possível obter a previsão do tempo.'

def main():
    city = input('Digite o nome da cidade: ')
    weather = get_weather(city)
    print(weather)

if __name__ == '__main__':
    main()
