# HelloID-Conn-SA-Full-Exchange-On-Premises-SharedMailbox-Manage-SendOnBehalf-Permissions

| :information_source: Information                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This repository contains the connector and configuration code only. The implementer is responsible for acquiring the connection details such as username, password, certificate, etc. You might even need to sign a contract or agreement with the supplier before implementing this connector. Please contact the client's application manager to coordinate the connector requirements. |

## Description

_HelloID-Conn-SA-Full-Exchange-On-Premises-SharedMailbox-Manage-SendOnBehalf-Permissions_ is a template designed for use with HelloID Service Automation (SA) Delegated Forms. It can be imported into HelloID and customized according to your requirements.

By using this delegated form, you can grant SendOnBehalf permissions to users for Exchange On-Premises shared mailboxes. The following options are available:

1.  Search and select the shared mailbox by name or alias
2.  Search and select the user account that should receive SendOnBehalf permissions
3.  The selected user and mailbox are validated
4.  SendOnBehalf permission is granted to the user for the selected shared mailbox
5.  Audit logging tracks all actions and results

## Getting started

### Requirements

- **Exchange On-Premises Environment**:<br>
  An Exchange On-Premises server with remote PowerShell access enabled is required.
- **Exchange Management Shell Access**:<br>
  The service account must have permissions to connect to Exchange using remote PowerShell and execute the Set-Mailbox cmdlet.
- **PowerShell Remoting**:<br>
  PowerShell remoting must be enabled on the Exchange server, and the HelloID Service Automation agent must be able to establish remote PowerShell sessions.

### Connection settings

The following user-defined variables are used by the connector.

| Setting               | Description                                                | Mandatory |
| --------------------- | ---------------------------------------------------------- | --------- |
| ExchangeConnectionUri | The URI to connect to Exchange On-Premises via PowerShell  | Yes       |
| ExchangeAdminUsername | The username to connect to Exchange with admin permissions | Yes       |
| ExchangeAdminPassword | The password to connect to Exchange (stored as secret)     | Yes       |

## Remarks

### Shared Mailbox Focus

The datasources are specifically designed to work with shared mailboxes (RecipientTypeDetails = 'SharedMailbox'). If you need to manage SendOnBehalf permissions for user mailboxes or other mailbox types, you will need to modify the filter in the datasource.

### Filter-Based Search

This connector uses filter-based queries instead of OrganizationalUnit-based searches. This provides more flexibility and better performance for searching mailboxes and users across the entire Exchange organization.

### Authentication Method

The connector uses 'Default' authentication. If your Exchange environment requires a different authentication method (such as Kerberos or Basic), you will need to modify the sessionParams in the datasources and task.

### Audit Logging

All actions are logged using the HelloID audit logging format with the Action type set to "GrantMembership". This allows for proper tracking and reporting of permission grants in HelloID.

## Development resources

### API endpoints

The following Exchange PowerShell cmdlets are used by the connector:

| Cmdlet      | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| Get-Mailbox | Retrieve mailbox information                                 |
| Get-User    | Retrieve user information                                    |
| Set-Mailbox | Update mailbox properties including SendOnBehalf permissions |

### API documentation

https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-servers-using-remote-powershell

## Getting help

> :bulb: **Tip:**  
> _For more information on Delegated Forms, please refer to our [documentation](https://docs.helloid.com/en/service-automation/delegated-forms.html) pages_.

## HelloID docs

The official HelloID documentation can be found at: https://docs.helloid.com/
