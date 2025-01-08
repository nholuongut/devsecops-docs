# Kakit config

The above configuration customizations like Phases, ENV, etc. can be saved in the repository in a config file called `katkitconfig.js` Following is an example of one such file

{% code title="katkitconfig.js" %}
```javascript
[
    {
        "EnvName": "default",
        "LocalFleet": "true",
        "WorkFlow": [
            {
                "Name": "PRE_DEPLOY_BUILD",
                "PhaseType": 4,
                "BuildParams": "PHASE=PRE_DEPLOY_BUILD, FOO=BAR",
                "Order": 0,
                "Parallelism": 1,
                "ContinerImage": "nholuongut/zbuilder:v7"
            },
            {
                "Name": "DEPLOY",
                "PhaseType": 1,
                "BuildParams": "PHASE=DEPLOY",
                "Order": 1,
                "Parallelism": 1,
                "ContinerImage": null
            }
        ]
    }
]
```
{% endcode %}
