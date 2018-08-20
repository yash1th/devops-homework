# Autoscaled Web Service Deployment

We want you to automate the deployment of a dashboard to AWS, Azure, or GCP which shows the availability of different hardware profiles. We would also like for you to:

1. Figure out how to autoscale this application based on the number of incoming requests.
1. Propose a workaround to the performance issue.

There are two different Flask applications that need to be deployed:

* `portal.py` is a public facing app that renders out the dashboard.
* `hardware.py` is an internal service that calculates the availability of the different hardware profiles available on the platform. This service must not be available to the public internet.

Assume that calculating the hardware availability is a slow and CPU-intensive process. The `slow_process_to_calculate_availability` function in `hardware.py` contains an artificial sleep statement to simulate this. You should NOT change this.

However, you _should_ feel free to otherwise modify the python files, requirements.txt, and/or database to improve performance.

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

## Deliverables

Create a new repo with your Github account and send us the link. Please use a different repo name and do not fork this one.

Your submission should include:
1. Updated application source files
1. Scripts to deploy the two autoscaled web applications to AWS/Azure/GCP. Remember that `portal.py` should be publically accessible and `hardware.py` should be a private internal service.
1. Include a README.md file with details on how to run everything. In your writeup, you should discuss:
  * Things to consider if this was a true production deployment. For example, how would a developer deploy new versions of these applications?
  * Suggestions for dealing with the dashboard performance issue.

The requirements are intentionally vague so feel free to ask questions along the way. There is no deadline for this but we do ask that you keep track of the amount of time you spend working on this.
