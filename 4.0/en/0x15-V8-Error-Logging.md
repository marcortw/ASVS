# V8: Error Handling and Logging Verification Requirements

## Control Objective

The primary objective of error handling and logging is to provide useful information for the user, administrators, and incident response teams. The objective is not to create massive amounts of logs, but high quality logs, with more signal than discarded noise.

High quality logs will often contain sensitive data, and must be protected as per local data privacy laws or directives. This should include:

* Not collecting or logging sensitive information unless specifically required.
* Ensuring all logged information is handled securely and protected as per its data classification.
* Ensuring that logs are not stored forever, but have an absolute lifetime that is as short as possible.

If logs contain private or sensitive data, the definition of which varies from country to country, the logs become some of the most sensitive information held by the application and thus very attractive to attackers in their own right.

It is also important to ensure that the application fails securely and that errors do not disclose unnecessary information.

### 8.1 Log Content Requirements

Logging sensitive information is dangerous - the logs become classified themselves, which means they need to be encrypted, become subject to retention policies, and must be disclosed in security audits. Ensure only necessary information is kept in logs, and certainly no payment, credentials (including session tokens), sensitive or personally identifiable information.

| # | Description | L1 | L2 | L3 | CWE | CWSS |
| :---: | :--- | :---: | :---:| :---: | :---: | :---: |
| **8.1.1** | Verify that the application does not log credentials, session tokens or payment details. | ✓ | ✓ | ✓ | tbd | tbd |
| **8.1.2** | Verify that the application does not log other sensitive data as defined under local privacy laws or relevant security policy. |  | ✓ | ✓ | tbd | tbd |
| **8.1.3** | Verify that the application logs security relevant events including successful and failed authentication events, access control failures, deserialization failures and input validation failures. | ✓ | ✓ | ✓ | tbd | tbd |
| **8.1.4** | Verify that each log event includes necessary information that would allow for a detailed investigation of the timeline when an event happens. |  | ✓ | ✓ | tbd | tbd |

### 8.2 Log Processing Requirements

Timely logging is critical for audit events, triage, and escalation. Ensure that the application's logs are clear and can be easily monitored and analyzed either in situ, or log shipped to a remote monitoring system. 

| # | Description | L1 | L2 | L3 | CWE | CWSS |
| :---: | :--- | :---: | :---:| :---: | :---: | :---: |
| **8.2.1** | Verify that all authentication decisions are logged, without storing sensitive session identifiers or memorized secrets. This should include requests with relevant metadata needed for security investigations.  | ✓ | ✓ | ✓ | tbd | tbd |
| **8.2.2** | Verify that all access control decisions can be logged and all failed decisions are logged. This should include requests with relevant metadata needed for security investigations. | ✓ | ✓ | ✓ | 285 | tbd |
| **8.2.3** | Verify that a common logging format and approach is used across the system.  | ✓ | ✓ | ✓ | tbd | tbd |

### 8.3 Log Protection Requirements

Logs that can be trivially modified or deleted are useless for investigations and prosecutions. Disclosure of logs can expose inner details about the application or the data it containts. Care must be taken when protecting logs from unauthorized disclosure, modification or deletion.

| # | Description | L1 | L2 | L3 | CWE | CWSS |
| :---: | :--- | :---: | :---:| :---: | :---: | :---: |
| **8.3.1** | Verify that all events are protected from injection when viewed in log viewing software. |  | ✓ | ✓ | tbd | tbd |
| **8.3.2** | Verify that security logs are protected from unauthorized access and modification. |  | ✓ | ✓ | tbd | tbd |
| **8.3.3** | Verify that the application appropriately encodes user-supplied data to prevent log injection. | ✓ | ✓ | ✓ | tbd | tbd |
| **8.3.4** | Verify that logs are transmitted to a remote system for analysis, detection, alerting, and escalation. |  |  | ✓ | tbd | tbd |
| **8.3.5** | Verify that time sources are synchronized to the correct time and time zone. | ✓ | ✓ | ✓ | tbd | tbd |

### 8.2 Error Handling

The purpose of error handling is to allow the application to provide security relevant events for monitoring, triage and escalation. The purpose is not to create logs. When logging security related events, ensure that there is a purpose to the log, and that it can be distinguished by SIEM or analysis software.  

| # | Description | L1 | L2 | L3 | CWE | CWSS |
| :---: | :--- | :---: | :---:| :---: | :---: | :---: |
| **8.2.1** | Verify that a generic message is shown when an unexpected or security sensitive error occurs, potentially with a unique ID which support personnel can use to investigate.  | ✓ | ✓ | ✓ | tbd | tbd |
| **8.3.2** | Verify that exception handling is used across the codebase to account for expected and unexpected error conditions.  | ✓ | ✓ | ✓ | tbd | tbd |
| **8.3.3** | Verify that a "last resort" error handler is defined which will catch all unhandled exceptions.  | | ✓ | ✓ | tbd | tbd |

## References

For more information, see also:

* [OWASP Testing Guide 4.0 content: Testing for Error Handling](https://www.owasp.org/index.php/Testing_for_Error_Handling)
