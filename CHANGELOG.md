# Changelog

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] - 2026-08-21

### Added

- Added TLS 1.2 enablement for secure connections
- Added try-catch-finally block for proper Exchange session cleanup
- Added detailed error messages with script line numbers for better debugging
- Added property selection in datasources to limit memory usage and improve performance
- Added filter-based mailbox and user searches for improved flexibility
- Added actionMessage variable for consistent error tracking throughout the task

### Changed

- Changed mailbox search from UserMailbox to SharedMailbox
- Changed datasource names from `Exchange-On-Premises-SendOnBehalf-List-Mailboxes` to `Exchange-On-Premises-Get-Sharedmailbox-Wildcard-Name-Alias`
- Changed datasource names from `Exchange-On-Premises-SendOnBehalf-Get-Users` to `Exchange-On-Premises-Get-Users-DisplayName-Mail-Name-UserprincipalName`
- Changed audit Action type from "UpdateAccount" to "GrantMembership" for accurate permission tracking
- Changed task name from "Exchange on-Premises - Manage SendOnBehalf Permissions" to "Exchange On-Premises - Sharedmailbox - Manage send on behalf permissions"
- Changed ExchangeAdminPassword to be marked as secret in all-in-one setup script
- Changed session parameter handling from variable-based authentication to fixed 'Default' authentication
- Improved error handling with consistent warning and audit message structure
- Improved audit logging with proper use of TargetDisplayName and TargetIdentifier fields

### Removed

- Removed $ExchangeAuthentication global variable (authentication now fixed to 'Default')
- Removed $ExchangeSendOnBehalfUserSearchOU global variable (now uses filter-based queries)
- Removed $ExchangeSendOnBehalfMailboxSearchOU global variable (now uses filter-based queries)
- Removed AllowRedirection parameter from session configuration
- Removed OrganizationalUnit-based searches in favor of filter-based queries

### Fixed

- Fixed session cleanup to use finally block ensuring proper disconnection even on errors
- Fixed inconsistent variable naming in task (from $mailboxGuid/$userGUID to $mailbox.Guid/$user.GUID)
- Fixed audit logging to use consistent session.InstanceId instead of session.GUID

## [1.0.2] - 2022-08-22

### Added

- Added version number and updated code for SA-agent and auditlogging

## [1.0.1] - 2021-11-16

### Added

- Added version number and updated all-in-one script

## [1.0.0] - 2021-04-29

Initial release of HelloID-Conn-SA-Full-Exchange-On-Premises-SharedMailbox-Manage-SendOnBehalf-Permissions.

### Added

- Initial release for managing SendOnBehalf permissions on Exchange On-Premises mailboxes
- PowerShell datasource to search for mailboxes
- PowerShell datasource to search for users
- Delegated form task to grant SendOnBehalf permissions
- All-in-one setup script for automated deployment
