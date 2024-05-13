# dnac-helper

import requests
from requests.auth import HTTPBasicAuth

requests.packages.urllib3.disable_warnings()
url = "https://10.10.10.50/dna/system/api/v1/auth/token"

response = requests.request(
    "POST",
    url,
    auth=HTTPBasicAuth("admin", "1234QWer"),
    verify=False,
)

print(response.json())
