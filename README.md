# Snippet

This is a combination of different implementation in django


## Table of Contents

- [Example](#example)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Features](#features)
- [Deployment](#deployment)

## Example
```python
@admin.register(EmailSubscriber)
class EmailSubscriberAdmin(admin.ModelAdmin):
    list_display = ("id", "email", "created_at")
    ordering = ("-created_at",)

    def changelist_view(self, request, extra_context=None):
        # Aggregate new subscribers per day
        chart_data = (
            EmailSubscriber.objects.annotate(date=TruncDay("created_at"))
            .values("date")
            .annotate(y=Count("id"))
            .order_by("-date")
        )
```

### Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.


## Prerequisites

What things you need to install the software and how to install them

- python3 env
- some pip packages



## Installation

To get a development env running:

>clone this repo to your local machine
```
git clone https://github.com/JohnJohnsonOkah/snippet.git
```

>install requirements
```
pip install -r requirements.txt
```

>setup database
```
python manage.py makemigrations
python manage.py migrate
```

>create superuser
```
python manage.py createsuperuser
```

>run development server
```
python manage.py runserver
```
... 👯 Now development server is up and running...



## Features

- Admin chart
- 



## Deployment

Additional notes about how to deploy this on a live system