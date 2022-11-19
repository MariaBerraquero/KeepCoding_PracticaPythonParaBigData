Práctica Bootcamp @ KeepCoding - Python para Big Data
======

## Preparación

#### Importar librerías necesarias


```python

import pandas as pd
import numpy as np
from IPython.display import display, HTML
from functools import reduce

```

#### Cargar datos


```python

df = pd.read_csv('dataset_final.csv')

with pd.option_context('display.max_rows', 10):
    display(df)

```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
      <th>Total</th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
      <th>Generation</th>
      <th>Legendary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Bulbasaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>318</td>
      <td>45</td>
      <td>49</td>
      <td>49</td>
      <td>65</td>
      <td>65</td>
      <td>45</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Ivysaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>405</td>
      <td>60</td>
      <td>62</td>
      <td>63</td>
      <td>80</td>
      <td>80</td>
      <td>60</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Venusaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>525</td>
      <td>80</td>
      <td>82</td>
      <td>83</td>
      <td>100</td>
      <td>100</td>
      <td>80</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>VenusaurMega Venusaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>625</td>
      <td>80</td>
      <td>100</td>
      <td>123</td>
      <td>122</td>
      <td>120</td>
      <td>80</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Charmander</td>
      <td>Fire</td>
      <td>NaN</td>
      <td>309</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>60</td>
      <td>50</td>
      <td>65</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>795</th>
      <td>719</td>
      <td>Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>600</td>
      <td>50</td>
      <td>100</td>
      <td>150</td>
      <td>100</td>
      <td>150</td>
      <td>50</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>796</th>
      <td>719</td>
      <td>DiancieMega Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>700</td>
      <td>50</td>
      <td>160</td>
      <td>110</td>
      <td>160</td>
      <td>110</td>
      <td>110</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>797</th>
      <td>720</td>
      <td>HoopaHoopa Confined</td>
      <td>Psychic</td>
      <td>Ghost</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>60</td>
      <td>150</td>
      <td>130</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>798</th>
      <td>720</td>
      <td>HoopaHoopa Unbound</td>
      <td>Psychic</td>
      <td>Dark</td>
      <td>680</td>
      <td>80</td>
      <td>160</td>
      <td>60</td>
      <td>170</td>
      <td>130</td>
      <td>80</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>799</th>
      <td>721</td>
      <td>Volcanion</td>
      <td>Fire</td>
      <td>Water</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>120</td>
      <td>130</td>
      <td>90</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>800 rows × 13 columns</p>
</div>


##  Preguntas


### 1. ¿Cuántos pokémon hay en el dataset?



```python

n_row = df.shape[0]
print(f'En el dataset hay {n_row} pokémon.')

```

    En el dataset hay 800 pokémon.
    

### 2. ¿Cuántos pokémon hay de tipo Poison? (Type 1)


```python

df_poison1 = (df[df['Type 1'] == 'Poison']).shape[0]
print(f'Hay {df_poison1} pokémon cuyo Type 1 es Poison.' )

```

    Hay 28 pokémon cuyo Type 1 es Poison.
    

### 3. ¿Cuántos tipos diferentes de pokémon hay? (Type 1)


```python

n_types1 = df['Type 1'].nunique()
print(f'Hay {n_types1} diferentes tipos de pokémon.')

```

    Hay 18 diferentes tipos de pokémon.
    

### 4. ¿Cuántos pokémon hay de cada tipo? (Type 1)


```python

n_types1 = df.groupby('Type 1')['Name'].count().rename('Frecuencia')

with pd.option_context('display.max_rows', None):
   display(HTML(n_types1.to_frame().to_html()))

```


<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Frecuencia</th>
    </tr>
    <tr>
      <th>Type 1</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bug</th>
      <td>69</td>
    </tr>
    <tr>
      <th>Dark</th>
      <td>31</td>
    </tr>
    <tr>
      <th>Dragon</th>
      <td>32</td>
    </tr>
    <tr>
      <th>Electric</th>
      <td>44</td>
    </tr>
    <tr>
      <th>Fairy</th>
      <td>17</td>
    </tr>
    <tr>
      <th>Fighting</th>
      <td>27</td>
    </tr>
    <tr>
      <th>Fire</th>
      <td>52</td>
    </tr>
    <tr>
      <th>Flying</th>
      <td>4</td>
    </tr>
    <tr>
      <th>Ghost</th>
      <td>32</td>
    </tr>
    <tr>
      <th>Grass</th>
      <td>70</td>
    </tr>
    <tr>
      <th>Ground</th>
      <td>32</td>
    </tr>
    <tr>
      <th>Ice</th>
      <td>24</td>
    </tr>
    <tr>
      <th>Normal</th>
      <td>98</td>
    </tr>
    <tr>
      <th>Poison</th>
      <td>28</td>
    </tr>
    <tr>
      <th>Psychic</th>
      <td>57</td>
    </tr>
    <tr>
      <th>Rock</th>
      <td>44</td>
    </tr>
    <tr>
      <th>Steel</th>
      <td>27</td>
    </tr>
    <tr>
      <th>Water</th>
      <td>112</td>
    </tr>
  </tbody>
</table>


##### 4.1 ¿Cuál es el tipo de pokémon con más pokémon? (Type 1)


```python

n_types1 = n_types1.sort_values(ascending = False)
print(f'El tipo más frecuente en Type 1 es: {n_types1.keys()[0]}')

```

    El tipo más frecuente en Type 1 es: Water
    

### 5. ¿Cuál es el pokémon más rápido?



```python

df_sort_speed = df.sort_values('Speed', ascending = False)
print(f'El pokemon más rápido es: {df_sort_speed["Name"].values[0]}.')

```

    El pokemon más rápido es: DeoxysSpeed Forme.
    

### 6. ¿Cuántos pokemon tiene una defensa superior a 100?


```python

pokemon_def_100 = df[df['Defense'] > 100]
print(f'Hay {len(pokemon_def_100)} pokémon con una defensa superior a 100.')

```

    Hay 123 pokémon con una defensa superior a 100.
    

### 7. ¿Cuántos pokemons tienen una defensa superior a 100 y una velocidad superior a 100?


```python

pokemon_def_sp_100 = df[(df['Defense'] > 100) & (df['Speed'] > 100)]
print(f'Hay {len(pokemon_def_sp_100)} pokémon con una defensa y una velocidad superior a 100.')

```

    Hay 9 pokémon con una defensa y una velocidad superior a 100.
    

### 8. Ordena el dataset por el tipo 1 y por el tipo 2


```python

with pd.option_context('display.max_rows', 10):
    display(df.sort_values(['Type 1', 'Type 2']))
    
```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
      <th>Total</th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
      <th>Generation</th>
      <th>Legendary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>656</th>
      <td>595</td>
      <td>Joltik</td>
      <td>Bug</td>
      <td>Electric</td>
      <td>319</td>
      <td>50</td>
      <td>47</td>
      <td>50</td>
      <td>57</td>
      <td>50</td>
      <td>65</td>
      <td>5</td>
      <td>False</td>
    </tr>
    <tr>
      <th>657</th>
      <td>596</td>
      <td>Galvantula</td>
      <td>Bug</td>
      <td>Electric</td>
      <td>472</td>
      <td>70</td>
      <td>77</td>
      <td>60</td>
      <td>97</td>
      <td>60</td>
      <td>108</td>
      <td>5</td>
      <td>False</td>
    </tr>
    <tr>
      <th>231</th>
      <td>214</td>
      <td>Heracross</td>
      <td>Bug</td>
      <td>Fighting</td>
      <td>500</td>
      <td>80</td>
      <td>125</td>
      <td>75</td>
      <td>40</td>
      <td>95</td>
      <td>85</td>
      <td>2</td>
      <td>False</td>
    </tr>
    <tr>
      <th>232</th>
      <td>214</td>
      <td>HeracrossMega Heracross</td>
      <td>Bug</td>
      <td>Fighting</td>
      <td>600</td>
      <td>80</td>
      <td>185</td>
      <td>115</td>
      <td>40</td>
      <td>105</td>
      <td>75</td>
      <td>2</td>
      <td>False</td>
    </tr>
    <tr>
      <th>697</th>
      <td>636</td>
      <td>Larvesta</td>
      <td>Bug</td>
      <td>Fire</td>
      <td>360</td>
      <td>55</td>
      <td>85</td>
      <td>55</td>
      <td>50</td>
      <td>55</td>
      <td>60</td>
      <td>5</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>655</th>
      <td>594</td>
      <td>Alomomola</td>
      <td>Water</td>
      <td>NaN</td>
      <td>470</td>
      <td>165</td>
      <td>75</td>
      <td>80</td>
      <td>40</td>
      <td>45</td>
      <td>65</td>
      <td>5</td>
      <td>False</td>
    </tr>
    <tr>
      <th>724</th>
      <td>656</td>
      <td>Froakie</td>
      <td>Water</td>
      <td>NaN</td>
      <td>314</td>
      <td>41</td>
      <td>56</td>
      <td>40</td>
      <td>62</td>
      <td>44</td>
      <td>71</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>725</th>
      <td>657</td>
      <td>Frogadier</td>
      <td>Water</td>
      <td>NaN</td>
      <td>405</td>
      <td>54</td>
      <td>63</td>
      <td>52</td>
      <td>83</td>
      <td>56</td>
      <td>97</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>762</th>
      <td>692</td>
      <td>Clauncher</td>
      <td>Water</td>
      <td>NaN</td>
      <td>330</td>
      <td>50</td>
      <td>53</td>
      <td>62</td>
      <td>58</td>
      <td>63</td>
      <td>44</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>763</th>
      <td>693</td>
      <td>Clawitzer</td>
      <td>Water</td>
      <td>NaN</td>
      <td>500</td>
      <td>71</td>
      <td>73</td>
      <td>88</td>
      <td>120</td>
      <td>89</td>
      <td>59</td>
      <td>6</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>800 rows × 13 columns</p>
</div>


### 9. Crea un nuevo dataset con los pokémon de tipo Water y Fire como primer tipo



```python

pokemon_type_water_or_fire = df[(df['Type 1'] == 'Water') | (df['Type 1'] == 'Fire')]
with pd.option_context('display.max_rows', 10):
    display(pokemon_type_water_or_fire)

```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
      <th>Total</th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
      <th>Generation</th>
      <th>Legendary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Charmander</td>
      <td>Fire</td>
      <td>NaN</td>
      <td>309</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>60</td>
      <td>50</td>
      <td>65</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Charmeleon</td>
      <td>Fire</td>
      <td>NaN</td>
      <td>405</td>
      <td>58</td>
      <td>64</td>
      <td>58</td>
      <td>80</td>
      <td>65</td>
      <td>80</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Charizard</td>
      <td>Fire</td>
      <td>Flying</td>
      <td>534</td>
      <td>78</td>
      <td>84</td>
      <td>78</td>
      <td>109</td>
      <td>85</td>
      <td>100</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>CharizardMega Charizard X</td>
      <td>Fire</td>
      <td>Dragon</td>
      <td>634</td>
      <td>78</td>
      <td>130</td>
      <td>111</td>
      <td>130</td>
      <td>85</td>
      <td>100</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>6</td>
      <td>CharizardMega Charizard Y</td>
      <td>Fire</td>
      <td>Flying</td>
      <td>634</td>
      <td>78</td>
      <td>104</td>
      <td>78</td>
      <td>159</td>
      <td>115</td>
      <td>100</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>735</th>
      <td>667</td>
      <td>Litleo</td>
      <td>Fire</td>
      <td>Normal</td>
      <td>369</td>
      <td>62</td>
      <td>50</td>
      <td>58</td>
      <td>73</td>
      <td>54</td>
      <td>72</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>736</th>
      <td>668</td>
      <td>Pyroar</td>
      <td>Fire</td>
      <td>Normal</td>
      <td>507</td>
      <td>86</td>
      <td>68</td>
      <td>72</td>
      <td>109</td>
      <td>66</td>
      <td>106</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>762</th>
      <td>692</td>
      <td>Clauncher</td>
      <td>Water</td>
      <td>NaN</td>
      <td>330</td>
      <td>50</td>
      <td>53</td>
      <td>62</td>
      <td>58</td>
      <td>63</td>
      <td>44</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>763</th>
      <td>693</td>
      <td>Clawitzer</td>
      <td>Water</td>
      <td>NaN</td>
      <td>500</td>
      <td>71</td>
      <td>73</td>
      <td>88</td>
      <td>120</td>
      <td>89</td>
      <td>59</td>
      <td>6</td>
      <td>False</td>
    </tr>
    <tr>
      <th>799</th>
      <td>721</td>
      <td>Volcanion</td>
      <td>Fire</td>
      <td>Water</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>120</td>
      <td>130</td>
      <td>90</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>164 rows × 13 columns</p>
</div>


### 10. Crea un nuevo dataset con los pokemon Legendary



```python

df_legendary = df[df['Legendary'] == True]
with pd.option_context('display.max_rows', 10):
    display(df_legendary)
    
```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
      <th>Total</th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
      <th>Generation</th>
      <th>Legendary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>156</th>
      <td>144</td>
      <td>Articuno</td>
      <td>Ice</td>
      <td>Flying</td>
      <td>580</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>125</td>
      <td>85</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>157</th>
      <td>145</td>
      <td>Zapdos</td>
      <td>Electric</td>
      <td>Flying</td>
      <td>580</td>
      <td>90</td>
      <td>90</td>
      <td>85</td>
      <td>125</td>
      <td>90</td>
      <td>100</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>158</th>
      <td>146</td>
      <td>Moltres</td>
      <td>Fire</td>
      <td>Flying</td>
      <td>580</td>
      <td>90</td>
      <td>100</td>
      <td>90</td>
      <td>125</td>
      <td>85</td>
      <td>90</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>162</th>
      <td>150</td>
      <td>Mewtwo</td>
      <td>Psychic</td>
      <td>NaN</td>
      <td>680</td>
      <td>106</td>
      <td>110</td>
      <td>90</td>
      <td>154</td>
      <td>90</td>
      <td>130</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>163</th>
      <td>150</td>
      <td>MewtwoMega Mewtwo X</td>
      <td>Psychic</td>
      <td>Fighting</td>
      <td>780</td>
      <td>106</td>
      <td>190</td>
      <td>100</td>
      <td>154</td>
      <td>100</td>
      <td>130</td>
      <td>1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>795</th>
      <td>719</td>
      <td>Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>600</td>
      <td>50</td>
      <td>100</td>
      <td>150</td>
      <td>100</td>
      <td>150</td>
      <td>50</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>796</th>
      <td>719</td>
      <td>DiancieMega Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>700</td>
      <td>50</td>
      <td>160</td>
      <td>110</td>
      <td>160</td>
      <td>110</td>
      <td>110</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>797</th>
      <td>720</td>
      <td>HoopaHoopa Confined</td>
      <td>Psychic</td>
      <td>Ghost</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>60</td>
      <td>150</td>
      <td>130</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>798</th>
      <td>720</td>
      <td>HoopaHoopa Unbound</td>
      <td>Psychic</td>
      <td>Dark</td>
      <td>680</td>
      <td>80</td>
      <td>160</td>
      <td>60</td>
      <td>170</td>
      <td>130</td>
      <td>80</td>
      <td>6</td>
      <td>True</td>
    </tr>
    <tr>
      <th>799</th>
      <td>721</td>
      <td>Volcanion</td>
      <td>Fire</td>
      <td>Water</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>120</td>
      <td>130</td>
      <td>90</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>65 rows × 13 columns</p>
</div>


### 11. Calcula el promedio de stats de los pokemon Legendary (HP, Attack, Defense, Sp. Atk, Sp. Def, Speed) y los no Legendary


```python

stats = ['HP', 'Attack', 'Defense', 'Sp. Atk', 'Sp. Def', 'Speed']

df_legendary = df[df['Legendary'] == True]
df_legendary_stats = df_legendary[stats].mean().rename('Promedio').to_frame()

print("El promedio de las estadísticas para los pokémon de tipo Legendario es:")
with pd.option_context('display.max_rows', None, 'display.precision', 2):
    display(df_legendary_stats)


df_no_legendary = df[df['Legendary'] == False]
df_no_legendary_stats = df_no_legendary[stats].mean().rename('Promedio').to_frame()

print("El promedio de las estadísticas para los pokémon de tipo No Legendario es:")
with pd.option_context('display.max_rows', None, 'display.precision', 2):
    display(df_no_legendary_stats)
    
```

    El promedio de las estadísticas para los pokémon de tipo Legendario es:
    


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Promedio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>HP</th>
      <td>92.74</td>
    </tr>
    <tr>
      <th>Attack</th>
      <td>116.68</td>
    </tr>
    <tr>
      <th>Defense</th>
      <td>99.66</td>
    </tr>
    <tr>
      <th>Sp. Atk</th>
      <td>122.18</td>
    </tr>
    <tr>
      <th>Sp. Def</th>
      <td>105.94</td>
    </tr>
    <tr>
      <th>Speed</th>
      <td>100.18</td>
    </tr>
  </tbody>
</table>
</div>


    El promedio de las estadísticas para los pokémon de tipo No Legendario es:
    


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Promedio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>HP</th>
      <td>67.18</td>
    </tr>
    <tr>
      <th>Attack</th>
      <td>75.67</td>
    </tr>
    <tr>
      <th>Defense</th>
      <td>71.56</td>
    </tr>
    <tr>
      <th>Sp. Atk</th>
      <td>68.45</td>
    </tr>
    <tr>
      <th>Sp. Def</th>
      <td>68.89</td>
    </tr>
    <tr>
      <th>Speed</th>
      <td>65.46</td>
    </tr>
  </tbody>
</table>
</div>


### 12. Crea un nuevo dataframe con el resultado del anterior ejercicio comparando ambos promedios

```
    Ejemplo:
                    HP  Attack  Defense  Sp. Atk  Sp. Def  Speed
    Legendary       99      90       89       91       94     90
    No Legendary    80      95       75       12       43     87
```


```python

df_pokemon_compare = df_legendary_stats.compare(df_no_legendary_stats, align_axis = 1, keep_shape = True, keep_equal = True)
dict = {'self' : 'Legendario', 'other' : 'No Legendario'}
df_pokemon_compare = df_pokemon_compare.rename(columns=dict)

with pd.option_context('display.max_rows', None, 'display.precision', 2):
    display(df_pokemon_compare.transpose())
    
```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">Promedio</th>
      <th>Legendario</th>
      <td>92.74</td>
      <td>116.68</td>
      <td>99.66</td>
      <td>122.18</td>
      <td>105.94</td>
      <td>100.18</td>
    </tr>
    <tr>
      <th>No Legendario</th>
      <td>67.18</td>
      <td>75.67</td>
      <td>71.56</td>
      <td>68.45</td>
      <td>68.89</td>
      <td>65.46</td>
    </tr>
  </tbody>
</table>
</div>


### 13. Añade una nueva columna ['Doble tipo'] al dataframe inicial que indique si el pokemon tiene dos tipos o no


```python

df['Doble tipo'] = np.where(df['Type 2'].isnull(), False, True)
with pd.option_context('display.max_rows', 10):
    display(df)
    
```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
      <th>Total</th>
      <th>HP</th>
      <th>Attack</th>
      <th>Defense</th>
      <th>Sp. Atk</th>
      <th>Sp. Def</th>
      <th>Speed</th>
      <th>Generation</th>
      <th>Legendary</th>
      <th>Doble tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Bulbasaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>318</td>
      <td>45</td>
      <td>49</td>
      <td>49</td>
      <td>65</td>
      <td>65</td>
      <td>45</td>
      <td>1</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Ivysaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>405</td>
      <td>60</td>
      <td>62</td>
      <td>63</td>
      <td>80</td>
      <td>80</td>
      <td>60</td>
      <td>1</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Venusaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>525</td>
      <td>80</td>
      <td>82</td>
      <td>83</td>
      <td>100</td>
      <td>100</td>
      <td>80</td>
      <td>1</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>VenusaurMega Venusaur</td>
      <td>Grass</td>
      <td>Poison</td>
      <td>625</td>
      <td>80</td>
      <td>100</td>
      <td>123</td>
      <td>122</td>
      <td>120</td>
      <td>80</td>
      <td>1</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Charmander</td>
      <td>Fire</td>
      <td>NaN</td>
      <td>309</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>60</td>
      <td>50</td>
      <td>65</td>
      <td>1</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>795</th>
      <td>719</td>
      <td>Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>600</td>
      <td>50</td>
      <td>100</td>
      <td>150</td>
      <td>100</td>
      <td>150</td>
      <td>50</td>
      <td>6</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>796</th>
      <td>719</td>
      <td>DiancieMega Diancie</td>
      <td>Rock</td>
      <td>Fairy</td>
      <td>700</td>
      <td>50</td>
      <td>160</td>
      <td>110</td>
      <td>160</td>
      <td>110</td>
      <td>110</td>
      <td>6</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>797</th>
      <td>720</td>
      <td>HoopaHoopa Confined</td>
      <td>Psychic</td>
      <td>Ghost</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>60</td>
      <td>150</td>
      <td>130</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>798</th>
      <td>720</td>
      <td>HoopaHoopa Unbound</td>
      <td>Psychic</td>
      <td>Dark</td>
      <td>680</td>
      <td>80</td>
      <td>160</td>
      <td>60</td>
      <td>170</td>
      <td>130</td>
      <td>80</td>
      <td>6</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>799</th>
      <td>721</td>
      <td>Volcanion</td>
      <td>Fire</td>
      <td>Water</td>
      <td>600</td>
      <td>80</td>
      <td>110</td>
      <td>120</td>
      <td>130</td>
      <td>90</td>
      <td>70</td>
      <td>6</td>
      <td>True</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
<p>800 rows × 14 columns</p>
</div>


### 14. Muestra las columas Name, Type 1, Type 2 de los pokémon que tienen dos tipos y ordenalos por Type 1, Type 2 y Name


```python

df_pok_doble_tipo = (df[['Name', 'Type 1', 'Type 2']] [df['Doble tipo'] == True]).sort_values(['Type 1', 'Type 2', 'Name'])
with pd.option_context('display.max_rows', 10):
    display(df_pok_doble_tipo)
    
```


<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Type 1</th>
      <th>Type 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>657</th>
      <td>Galvantula</td>
      <td>Bug</td>
      <td>Electric</td>
    </tr>
    <tr>
      <th>656</th>
      <td>Joltik</td>
      <td>Bug</td>
      <td>Electric</td>
    </tr>
    <tr>
      <th>231</th>
      <td>Heracross</td>
      <td>Bug</td>
      <td>Fighting</td>
    </tr>
    <tr>
      <th>232</th>
      <td>HeracrossMega Heracross</td>
      <td>Bug</td>
      <td>Fighting</td>
    </tr>
    <tr>
      <th>697</th>
      <td>Larvesta</td>
      <td>Bug</td>
      <td>Fire</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>626</th>
      <td>Carracosta</td>
      <td>Water</td>
      <td>Rock</td>
    </tr>
    <tr>
      <th>240</th>
      <td>Corsola</td>
      <td>Water</td>
      <td>Rock</td>
    </tr>
    <tr>
      <th>404</th>
      <td>Relicanth</td>
      <td>Water</td>
      <td>Rock</td>
    </tr>
    <tr>
      <th>625</th>
      <td>Tirtouga</td>
      <td>Water</td>
      <td>Rock</td>
    </tr>
    <tr>
      <th>440</th>
      <td>Empoleon</td>
      <td>Water</td>
      <td>Steel</td>
    </tr>
  </tbody>
</table>
<p>414 rows × 3 columns</p>
</div>


### 15. Dada una lista de Artículos con sus precios. Define las siguientes funciones:
>Puedes definir más funciones si lo consideras necesario.


```python

articulos = {
    'Camisa': 20,
    'Pantalón': 30,
    'Calcetines': 5,
    'Zapatos': 50,
    'Gorra': 10,
    'Bufanda': 15,
    'Gafas': 25,
    'Reloj': 35,
    'Corbata': 40,
}

compra = ['Camisa', 'Pantalón', 'Pantalón', 'Gorra', 'Gafas', 'Corbata']

```

#### 15.A Una función que calcule el precio total de la compra


```python

def total_compra(articulos, compra):
    return reduce(lambda a, b: a + articulos[b], compra, 0)

print(f'El total de la compra es: {total_compra(articulos, compra)}')

```

    El total de la compra es: 155
    

#### 15.B Una función que calcule el precio total de la compra con un descuento del 10 %



```python

def total_compra_descuento(articulos, compra, porcentaje_descuento = 10):
    return (total_compra(articulos, compra) * (100 - porcentaje_descuento)) / 100

print(f'El total de la compra con un descuento del 10 % es: {total_compra_descuento(articulos, compra)}')

```

    El total de la compra con un descuento del 10 % es: 139.5
    

#### 15.C Una función que calcule el precio total de la compra con un descuento del 10 % si la compra supera los 100 €



```python

def total_compra_descuento_supera_100(articulos, compra, porcentaje_descuento = 10):
    total = total_compra(articulos, compra)
    if total > 100:
        total = total * (100 - porcentaje_descuento) / 100
    return total

print(f'El total de la compra con un descuento del 10 % (si el total supera los 100 €) es: {total_compra_descuento_supera_100(articulos, compra)}')

```

    El total de la compra con un descuento del 10 % (si el total supera los 100 €) es: 139.5
    

#### 15.D Una función que calcule el precio total aplicando el IVA (21 %)



```python

def total_compra_iva(articulos, compra, iva = 21):
    total = total_compra(articulos, compra)
    total += total * (iva/100)
    return total

print(f'El total de la compra con IVA del 21 % aplicado es: {total_compra_iva(articulos, compra)}')
```

    El total de la compra con IVA del 21 % aplicado es: 187.55
    

#### 15.E Lista los artículos cuyo precio es superior a 20 €


```python

def filtro_articulos_precio_superior(articulos, precio_superior = 20):  
    return list(filter(lambda x: articulos[x] > precio_superior, articulos))

print(f'Los artículos con precio superior a 20 € son: {filtro_articulos_precio_superior(articulos)}')
```

    Los artículos con precio superior a 20 € son: ['Pantalón', 'Zapatos', 'Gafas', 'Reloj', 'Corbata']
    

### 16. Dada una lista de tuplas con el nombre de un alumno, apellidos, curso y sus notas. 


```python

alumnos = [('Juan', 'Pérez', '1', [5, 6, 7, 8, 9]),
            ('Ana', 'García', '2', [5, 6, 7, 8, 9]),
            ('Luis', 'González', '1', [5, 6, 7, 8, 9]),
            ('María', 'Martínez', '2', [5, 6, 7, 8, 9]),
            ('Pedro', 'Rodríguez', '1', [5, 6, 7, 8, 9]),
            ('Lucía', 'Hernández', '2', [5, 6, 7, 8, 9]),
            ('Marta', 'López', '1', [5, 6, 7, 8, 9]),
            ('Sara', 'Díaz', '2', [5, 6, 7, 8, 9]),
            ('Javier', 'Sánchez', '1', [5, 6, 7, 8, 9]),
            ('Miguel', 'Fernández', '2', [5, 6, 7, 8, 9]),
            ('Sergio', 'Jiménez', '1', [5, 6, 7, 8, 9]),
            ('Sandra', 'Ruiz', '2', [5, 6, 7, 8, 9]),
            ('Pablo', 'Álvarez', '1', [5, 6, 7, 8, 9]),
            ('María', 'Gómez', '2', [5, 6, 7, 8, 9]),
]

```


 Define una funcion que reciba el curso y saque una lista en la que aparezca el nombre y apellidos y el promedio de sus notas.
 > Puedes definir más funciones si lo consideras necesario.


```python

def get_notas_medias_alumnos(alumnos, curso):
    df_alumnos = pd.DataFrame(alumnos).rename(columns={0:'Nombre', 1:'Apellido', 2:'Curso', 3:'Notas'})
    
    df_alumnos_filtered = df_alumnos[df_alumnos['Curso'] == str(curso)]
    df_alumnos_filtered = df_alumnos_filtered.drop(columns=['Curso'])
    
    df_alumnos_filtered['Notas Medias'] = df_alumnos_filtered['Notas'].apply(np.mean)
    df_alumnos_filtered = df_alumnos_filtered.drop(columns=['Notas'])

    return df_alumnos_filtered.values.tolist()

print('La lista de alumnos de 1er curso junto a sus notas medias es:')
display(get_notas_medias_alumnos(alumnos, '1'))

```

    La lista de alumnos de 1er curso junto a sus notas medias es:
    


    [['Juan', 'Pérez', 7.0],
     ['Luis', 'González', 7.0],
     ['Pedro', 'Rodríguez', 7.0],
     ['Marta', 'López', 7.0],
     ['Javier', 'Sánchez', 7.0],
     ['Sergio', 'Jiménez', 7.0],
     ['Pablo', 'Álvarez', 7.0]]

