# Ex.04 Design a Website for Server Side Processing
## Date:20-12-2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

math.html

```
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: rgba(133, 240, 235, 1);
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed hsla(266, 59%, 31%, 1.00);
    width: 550px;
    min-height: 250px;
    font-size: 20px;
    background-color: #b576e4ff;
}
.formelt {
    color: rgb(9, 10, 11);
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: rgba(15, 2, 28, 1);
    padding-top: 20px;
}

</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h2>Surface area of a Right Cylinder</h2>
   <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```

views.py

```
from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    
    if request.method == 'POST':
        print("POST method is used")
        
        print('request.POST:', request.POST)
        
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html', context)
```

urls.py

```
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofsurface/',views.surfacearea,name="areaofsurface"),
    path('',views.surfacearea,name="areaofsurfaceroot")
]
```


## SERVER SIDE PROCESSING:

<img width="1457" height="274" alt="Screenshot 2025-12-20 084809" src="https://github.com/user-attachments/assets/30a00031-d92b-4e81-b84f-30b7e634324a" />


## HOMEPAGE:

<img width="1920" height="1080" alt="Screenshot (93)" src="https://github.com/user-attachments/assets/da0618da-b7b3-40b5-a425-bbfb83992a9c" />


## RESULT:
The program for performing server side processing is completed successfully.
