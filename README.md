# cyrus-ldap-sync
Maintain mailboxes in cyrus imap in sync with LDAP directory.

Purpose of this script is to create or delete mailboxes in cyrus imap according to existing user accounts in LDAP and also manage mailbox quota.
Current version is intended to work with Active Directory. Older versions worked fine with openldap.

## Requirements

Script uses [python-cyrus](https://github.com/reinaldoc/python-cyrus).

## How it works

1. Get all LDAP entries with *mail* attribute.
1. Query cyrus for mailbox of each user.
1. Create mailbox if it doesn't exsist and also set default quota for it.
1. Build list of all mailboxes and delete ones which doesn't have corresponding LDAP entries.

## Setting quota mode

This script also can be used for setting individual mailbox quota.
```
python cyrus-ldap-sync -s 10240 -u test
```
