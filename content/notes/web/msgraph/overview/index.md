---
title: "notes > web > msgraph > overview"
date: 2023-01-01T00:00:00-06:00
draft: false
---

# Installation
| Action | Command |
|--------|---------|
| Set execution policy | `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` |  
| Install MS Graph module | `Install-Module Microsoft.Graph -Scope CurrentUser` |  
| Verify the installation | `Get-InstalledModule Microsoft.Graph` |  
| Update the SDK | `Update-Module Microsoft.Graph` | 

# Authentication
| Action | Command |
|--------|---------|
| Get permissions required | `Find-MgGraphCommand -command command \| Select -First 1 -ExpandProperty Permissions` | 
| Sign | `Connect-MgGraph -Scopes "User.ReadWrite.All","Group.ReadWrite.All"` |
| Sign out | `Disconnect-MgGraph` |

# Guests
| Action | Command |
---------|---------|
| Send an invitation | `New-MgInvitation -InvitedUserDisplayName "John Doe" -InvitedUserEmailAddress John@contoso.com -InviteRedirectUrl "https://myapplications.microsoft.com" -SendInvitationMessage:$true` |
| Verify the user exists in directory | `Get-MgUser -Filter "Mail eq 'John@contoso.com'"` |

# Teams
| Action | Command |
|--------|---------|
| List a team's channels | `Get-MgTeamChannel -TeamId $team.Id` |
| | `$channel = Get-MgTeamChannel -TeamId ID_FROM_PREVIOUS_STEP -Filter "displayName eq 'General'"` |
| Get a user's joined Teams | `Get-MgUserJoinedTeam -UserId $user.Id` |
| Send a message to a channel | `New-MgTeamChannelMessage -TeamId $team.Id -ChannelId $channel.Id -Body @{ Content="Hello World" }` |

# Users
| Action | Command |
|--------|---------|
| Get a user list | `Get-MgUser` |
| Get a user by display name | `$user = Get-MgUser -Filter "displayName eq 'Megan Bowen'" \| $user.DisplayName` |
| Get a user's joined Teams	| `Get-MgUserJoinedTeam -UserId $user.Id` |
