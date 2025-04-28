# Ex.05 Design a Website for Server Side Processing
# Date: 28.04.2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
### math.html
```
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Power Of a Lamp Filament</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: #fff;
}
.edge {
    width: 100%;
    padding-top: 200px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed #ff9800;
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: #fff8e1;
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 10px;
}
h1 {
    color: black;
    padding-top: 10px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>POWER OF A LAMP FILAMENT</h1>
        <h3>BAUDHIGAN D(212223230028)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                INTENSITY: <input type="text" name="intensity" value="{{i}}">m<br/>
            </div>
            <div class="formelt">
                RESISTANCE: <input type="text" name="resistance" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                POWER: <input type="text" name="power" value="{{power}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```

### views.py
```
from django.shortcuts import render
def power_calculator(request):
        power = None 
        intensity = None
        resistance = None 
        if request.method == 'POST':
            print("POST method is used")
            intensity = request.POST.get('intensity','0')
            resistance = request.POST.get('resistance','0')
            if intensity and resistance:
                try:
                    I = float(intensity)
                    R = float(resistance)
                    power = I**2 * R
                    print('request=',request)
                    print('intensity=',I)
                    print('resistance=',R)
                    print('power=',power)  
                except ValueError:
                    power = "Invalid input. Please enter numerical values."
        return render(request, 'mathapp/math.html', {'power': power, 'intensity': intensity, 'resistance': resistance})
```

### urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.power_calculator, name='power_calculator'),
]
```
# SERVER SIDE PROCESSING:
![Alt text](<Screenshot 2025-04-28 131934.png>)
# HOMEPAGE:
![Alt text](<Screenshot 2025-04-28 131855.png>)
# RESULT:
The program for performing server side processing is completed successfully.
