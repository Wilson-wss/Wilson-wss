import pandas as pd
from gmplot import gmplot

# Ler a planilha do Excel

df = pd.read_excel(r'C:\Users\wilso\PycharmProjects\mapploter\venv\Pasta1.xlsx')


# Extrair as coordenadas geográficas (latitude e longitude) da planilha
latitudes = df['Latitude']
longitudes = df['Longitude']


# Criar um mapa com base nas coordenadas geográficas
gmap = gmplot.GoogleMapPlotter(latitudes[0], longitudes[0], 5)  # Use a primeira coordenada como o ponto central

# Adicionar marcadores para cada coordenada na lista
for lat, lon in zip(latitudes, longitudes):
    gmap.marker(lat, lon)

# Salvar o mapa em um arquivo HTML
output_file = 'mapa.html'
gmap.draw(output_file)

print(f"Mapa gerado com sucesso! Salvo em '{output_file}'")
