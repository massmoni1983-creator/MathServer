# Ex.04 Design a Website for Server Side Processing
## Date:29-05-2026

## AIM:
To create a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts.

## FORMULA:
Bill = P + (P * GST / 100)
<br> P --> Price (in Rupees)
<br> GST --> GST (in Percentage)
<br> Bill --> Total Bill Amount (in Rupees)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the total bill amount (including GST).

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
## math.html
```
<!DOCTYPE html>
<html>
<head>
    <title>GST Calculator</title>
</head>
<body>

    <form method="post">
    <h2>GST Calculator</h2>

        {% csrf_token %}
        <label for="price">Price :</label>
        <input type="text" name="price" required><br><br>

        <label for="gst">GST (%):</label>
        <input type="text" name="gst" required><br><br>

        <button type="submit">Calculate</button>
    </form>

    {% if gst_amt is not None %}
        <h2>Result:</h2>
        {% if "Error" in gst_amt|stringformat:"s" %}
            <p style="color: red;">{{ gst_amt }}</p>
        {% else %}
            <p>GST: {{ gst_amt|stringformat:".2f" }}</p>
        {% endif %}
    {% endif %}
</body>
</html>
```
## views.py
```
from django.shortcuts import render

def home(request):

    total = None
    price = None
    gst = None

    if request.method == 'POST':

        price = float(request.POST['price'])
        gst = float(request.POST['gst'])

        total = price + (price * gst / 100)

    return render(request, 'math.html',
                  {'total': total,
                   'price': price,
                   'gst': gst})
```
## urls.py
```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('gstapp.urls')),
]

```



## OUTPUT - SERVER SIDE:

<img width="1855" height="350" alt="image" src="https://github.com/user-attachments/assets/cc7091d8-ea26-45a0-a6c7-a4aab6e4ae79" />

## OUTPUT - WEBPAGE:

<img width="920" height="411" alt="image" src="https://github.com/user-attachments/assets/e5ecf169-a1cf-4ca7-8b9e-b55f19b6b47e" />


## RESULT:
The a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts is created successfully.
