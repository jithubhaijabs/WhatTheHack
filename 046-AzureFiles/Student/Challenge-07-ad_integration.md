# Challenge 7: Integrate Azure File share with Active Directory (AD DS)

[< Previous Challenge](./Challenge-06-monitor_file_share.md) - **[Home](../README.md)**

## Pre-requisites

- Deployment of environment described in [Challenge 0](./Challenge-00-lab_setup.md) should be completed and validated.
- Azure Files deployed in Challenge 1 should be deployed and have some files.

## Introduction

In this challenge you will be enabling identity-based authentication over SMB using Active Directory Domain Services (AD DS). This will enable seamless access for end-users to access their Azure file shares similar to how they do it on-prem with traditional file servers. Each user uses their current identity to get access based on share permissions and ACLs on file and folder level.

Share-level permission assignment can be performed using RBAC model and Azure Active Directory (Azure AD) users/groups, which requires user identities synced to Azure AD. For example, you can assign Azure built-in roles like 'Storage File Data SMB Share Reader' to users or groups in Azure AD to grant read access to an Azure file share.

The alternate approach (which we will use for this lab) is to use default share-level permission. This will enable all authenticated users and groups the same permission based on your choice (Reader|Contributor|Elevated_Contributor).

At the directory/file level, Azure Files supports preserving, inheriting, and enforcing Windows-style DACLs just like any Windows file servers. You can choose to keep Windows DACLs when copying/migrating data from existing file servers to Azure Files over SMB (eg. robocopy with /COPY:DATSO) or use Azure File Sync which automatically preserves full fidelity. Whether you plan to enforce authorization or not, you can use Azure file shares to back up ACLs along with your data.This offers seamless integration with your enterprise AD DS environment. As you replace on-prem file servers with Azure file shares, existing users can access Azure file shares from their current clients with a single sign-on experience, without any change to the credentials in use.

Azure Files also support other identity-based authentication/authorization like Azure AD. You can refer [here](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-planning#identity) for more info.

## Description

Before starting the steps to configure ADDS authentication for Azure files SMB, review the [supported scenarios and restrictions](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-identity-auth-active-directory-enable#supported-scenarios-and-restrictions).

**Need to expand the scenarios - add details, with specific examples, context for participants**

1. Enable AD DS authentication on your Azure storage account
1. Assign share-level permissions to all authenticated users (No Azure AD Sync). The permissions should give all users Read & Change on share-level.
1. Mount Azure file share from a domain-joined VM
1. Review directory/file level permissions on Azure file share and compare with on-prem file server
1. Modify ACLs of particular department share on HQ file server (what to change??) and verify then verify on Azure File share.

https://docs.microsoft.com/en-us/azure/storage/files/storage-files-identity-ad-ds-assign-permissions?tabs=azure-powershell#share-level-permissions-for-all-authenticated-identities

## Success Criteria

At the end of this challenge you should have...

## Learning Resources

- [Assign Share-level permissions - options, use case and more info](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-identity-ad-ds-assign-permissions?tabs=azure-portal)

## Tips

- Azure File...
- [Tools for file copy/migration](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-migration-overview#file-copy-tools)