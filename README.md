# Micro "microservices" Deployment

We want you to automate the deployment of a dashboard to AWS, Azure, or GCP which shows the availability of different hardware profiles.

There are two different Flask applications that need to be deployed:

* `portal.py` is a public facing app that renders out the dashboard.
* `hardware.py` is an internal service that calculates the availability of the different hardware profiles available on the platform. This service must not be available to the public internet.


## Running Locally
The provided source code is setup to run on Python 3+

First, you should create and source your virtual environment.

```
pip install -r requirements.txt
sqlite3 database.db < database.sql
python portal.py
python hardware.py
```

Once the two Flask applications are running, visiting http://localhost:5000 will render out the hardware availability dashboard. Note that this will take ~10 seconds to load in its current state.

## Requirements

1. Create a new repo with your Github account and send us the link. *Please use a different repo name and do not fork this one.*
1. Modify the provided Flask applications to use a RDBMS like MySQL or PostgreSQL instead of sqlite. Using a managed service like RDS for this is encouraged. This database should not be accessible from the public internet.
1. The creation of the virtual networks used to host the public `portal` UI and the private `hardware` service should be scripted.
1. You should also include a script to deploy new builds of the `portal` and `hardware` applications. Feel free to use VMs, containers, or serverless for this.
1. Please include a README.md file with details on how to run everything and how new versions of the services should be deployed.

The requirements are intentionally vague so feel free to ask questions along the way. Please keep track of the amount of time you spend working on this.


## Extra Credit

1. Figure out how to autoscale this application based on the number of incoming requests.
1. Come up with a workaround to the performance issue with loading the `portal` UI. Assume that calculating the hardware availability is a slow and CPU-intensive process. The `slow_process_to_calculate_availability` function in `hardware.py` contains an artificial sleep statement to simulate this. You should NOT change this this function.
