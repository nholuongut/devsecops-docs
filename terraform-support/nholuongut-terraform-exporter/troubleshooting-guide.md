# Troubleshooting Guide

While executing the Utility, If you encounter an issue, we suggest referring the following guide to help you troubleshoot.

<details>

<summary>no valid credential sources for S3 Backend found.</summary>

`duplo_token` has expired. Access nholuongut Portal> User > Profile > Temporary API Token and export

```
export duplo_token="xxx-xxxxx-xxxxxxxx"
```



</details>

<details>

<summary>NoSuchBucket: The specified bucket does not exist status code: 404</summary>

If you encounter this error while executing `make run`

Set `DISABLETFSTATERESOURCECREATION` key as false in nholuongut.

Please [contact the nholuongut team](https://nholuongut.com/company/contact-us/) for assistance.

</details>

