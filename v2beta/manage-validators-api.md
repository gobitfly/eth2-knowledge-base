---
description: Manage your validators via API
---

# ⚒️ Manage Validators \[API]

To modify the validator dashboard via API, make sure to have an active [Orca subscription](https://v2-beta-holesky.beaconcha.in/pricing).\
\
After creating a [validator dashboard](https://v2-beta-holesky.beaconcha.in/) and the desired [validator groups](validator-groups.md) through the User Interface, you can add and assign validators to groups using our API.

***

* For Holesky, please adjust the base URL to: `v2-beta-holesky.beaconcha.in`
* The Group ID can be found in the `Group Manage` [modal ](validator-groups.md)on the Dashboard
* During our beta the **API key** will only be visible in the [account settings](https://beaconcha.in/user/settings#api) on [https://beaconcha.in/user/settings#api](https://beaconcha.in/user/settings#api)
* Pass the API key as a parameter `api_key`
  * `https://v2-beta-holesky.beaconcha.in/api/v2/validator-dashboards/{dashboard_id}/validators?api_key=KEY`    \


{% swagger src="../.gitbook/assets/api.json" path="/api/v2/validator-dashboards/{dashboard_id}/validators" method="post" %}
[api.json](../.gitbook/assets/api.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/api.json" path="/api/v2/validator-dashboards/{dashboard_id}/validators" method="delete" %}
[api.json](../.gitbook/assets/api.json)
{% endswagger %}
