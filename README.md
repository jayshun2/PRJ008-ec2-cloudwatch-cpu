# Project Title

Use CloudTrail to Track AWS API Activity in Your Account

## Overview

This project demonstrates how to enable and use **AWS CloudTrail** to record all API activity in your AWS account. CloudTrail acts like a security camera for your cloud environment, keeping track of who did what, when, and from where. By storing these records in Amazon S3 and optionally streaming them to CloudWatch or analyzing them with Athena, you gain visibility and accountability that is essential for troubleshooting, compliance, and security.

## Architecture

The core of this project is **AWS CloudTrail**, which records account activity and generates logs. These logs are stored in **Amazon S3** for durable, long-term storage. For real-time monitoring and alerting, CloudTrail can stream events into **Amazon CloudWatch Logs**. For querying and analysis, the logs can be accessed using **Amazon Athena** or CloudTrail Lake. Together, these services provide a complete view of activity in your account.

## Getting Started

1. Sign in to the **AWS Management Console** with an admin-level account.
2. Navigate to **CloudTrail** and create a new trail.

   * Name it something recognizable, such as `acct-main-trail`.
   * Apply it to all regions to ensure full coverage.
   * Enable management events (read and write).
3. Choose **Create new S3 bucket** to store logs.

   * Use a globally unique name like `ct-logs-youraccountid-region`.
   * Keep “Block all public access” enabled.
4. (Optional) Enable **log file validation** and **SSE-KMS encryption** for stronger security.
5. (Optional) Stream logs to a **CloudWatch Logs** group for real-time alerts.
6. Review and create the trail.

## Usage

* Perform any action in your AWS account (for example, create and delete a test S3 bucket).
* In **CloudTrail → Event history**, you should see the recorded events within minutes.
* Check the S3 bucket for `.gz` log files stored in a structured folder format.
* If CloudWatch Logs was enabled, confirm that log streams are receiving new events.

## Cleanup

To avoid unexpected costs, delete resources if this project was created for testing:

1. Delete the CloudTrail trail from the **CloudTrail console**.
2. Delete the **CloudWatch Logs group** if you created one.
3. Empty and delete the **S3 log bucket**.
4. Schedule deletion of the **KMS key** if you created one specifically for this project.

## Optional Enhancements

* Add **data events** for specific S3 buckets or Lambda functions.
* Enable **CloudTrail Insights** to automatically detect unusual API activity.
* Use **Athena** or **CloudTrail Lake** for advanced querying and reporting.
* Set up **CloudWatch alarms** for high-risk actions (such as IAM policy changes).
* Apply **S3 lifecycle policies** to transition older logs into Glacier for cost optimization.

## License

MIT License
