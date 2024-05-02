```python
import pandas as pd
import matplotlib.pyplot as plt
```


```python
#Nessa parte do código a visualização do dados foi organizadas
#Filtrar apenas os dados A203
df_A203 = pd.read_csv (r'C:\Users\luizs\OneDrive\Documentos\Aprendendo Python\aulinha luketa\concatenados_mensal.csv', sep =';', decimal = ',')
df_A203 = df_A203[df_A203['Estacao'] == 'A203']
df_A203['Precipitacao_(mm)'] = df_A203['Precipitacao_(mm)'].round(2)
df_A203['Tmax_C'] = df_A203['Tmax_C'].round(2)
df_A203
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mes</th>
      <th>Estacao</th>
      <th>Precipitacao_(mm)</th>
      <th>Tmax_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>A203</td>
      <td>135.43</td>
      <td>31.12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>A203</td>
      <td>215.99</td>
      <td>31.56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>A203</td>
      <td>339.89</td>
      <td>31.33</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>A203</td>
      <td>377.20</td>
      <td>33.25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>A203</td>
      <td>290.02</td>
      <td>31.34</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>A203</td>
      <td>153.68</td>
      <td>30.87</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>A203</td>
      <td>84.06</td>
      <td>30.70</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>A203</td>
      <td>19.65</td>
      <td>31.02</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>A203</td>
      <td>2.00</td>
      <td>32.71</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>A203</td>
      <td>0.75</td>
      <td>31.63</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>A203</td>
      <td>4.52</td>
      <td>32.20</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>A203</td>
      <td>37.26</td>
      <td>32.28</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Nessa etapa já foi feita a plotagem, juntamente com a personalização do gráfico
prec = df_A203['Precipitacao_(mm)']
temp = df_A203['Tmax_C']
mes = df_A203['mes']
fig, ax1 = plt.subplots()
plt.grid(True, linestyle = '--', alpha = 0.7)

#Plotando a primeira variável no subplot com eixo y à esquerda
plt.xlabel ('Meses')
plt.xticks(mes) #serve pra colocar os meses no eixo x sem pular os numeros 
plt.xticks(rotation=45)
#Plotagem de duas variaveis dois y em função de um x
ax1.bar(mes, prec, color='blue')
ax1.set_ylabel('Precipitação (mm)', color='blue')
ax2 = ax1.twinx() #comando chave para criar doisos dois eixos 'y'
ax2.plot(mes, temp, color='red', marker='o', markersize=4)
ax2.set_ylabel('Temperatura (°C)', color='red')
plt.title ('Prec - Temp')
#Como aumentar o limite do eixo y
ax1.set_ylim(0 , 400)
ax2.set_ylim(20, 35)


#Modificando o tamanho da figura e cores no geral 
plt.rcParams['figure.figsize'] = (7 , 4)
plt.rcParams['figure.facecolor'] = 'azure'
plt.rcParams['axes.facecolor'] = 'azure'
```


    
<img src="Figura gerada.png">
    

