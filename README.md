# Task-4
Setup and use Firewall
PS C:\WINDOWS\system32> New-NetFirewallRule -DisplayName "Block TCP 4444" -Direction Inbound -LocalPort 4444 -Protocol TCP -Action Block -Profile Any -Enabled True                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Name                          : {e13ebd4d-b3c2-469b-9d10-c75539cae1f1}                                                                                                                                             DisplayName                   : Block TCP 4444                                                                                                                                                                     Description                   :                                                                                                                                                                                    DisplayGroup                  :                                                                                                                                                                                    Group                         :                                                                                                                                                                                    Enabled                       : True                                                                                                                                                                               Profile                       : Any                                                                                                                                                                                Platform                      : {}                                                                                                                                                                                 Direction                     : Inbound                                                                                                                                                                            Action                        : Block
EdgeTraversalPolicy           : Block
LooseSourceMapping            : False
LocalOnlyMapping              : False
Owner                         :
PrimaryStatus                 : OK
Status                        : The rule was parsed successfully from the store. (65536)
EnforcementStatus             : NotApplicable
PolicyStoreSource             : PersistentStore
PolicyStoreSourceType         : Local
RemoteDynamicKeywordAddresses : {}
PolicyAppId                   :
PackageFamilyName             :



PS C:\WINDOWS\system32> Get-NetFirewallRule -DisplayName "Block TCP 4444" | Format-Table Name, DisplayName, Enabled, Direction, Action, Profile
>>

Name                                   DisplayName    Enabled Direction Action Profile
----                                   -----------    ------- --------- ------ -------
{e13ebd4d-b3c2-469b-9d10-c75539cae1f1} Block TCP 4444    True   Inbound  Block     Any


PS C:\WINDOWS\system32> Test-NetConnection -ComputerName 192.168.1.107 -Port 4444
WARNING: TCP connect to (192.168.1.107 : 4444) failed


ComputerName           : 192.168.1.107
RemoteAddress          : 192.168.1.107
RemotePort             : 4444
InterfaceAlias         : Wi-Fi
SourceAddress          : 192.168.1.107
PingSucceeded          : True
PingReplyDetails (RTT) : 0 ms
TcpTestSucceeded       : False

Removing the Test Block:

PS C:\WINDOWS\system32> Remove-NetFirewallRule -DisplayName "Block TCP 4444"
PS C:\WINDOWS\system32> Get-NetFirewallRule -DisplayName "Block TCP 4444"
Get-NetFirewallRule : No MSFT_NetFirewallRule objects found with property 'DisplayName' equal to 'Block TCP 4444'.  Verify the value of the property and retry.
At line:1 char:1
+ Get-NetFirewallRule -DisplayName "Block TCP 4444"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Block TCP 4444:String) [Get-NetFirewallRule], CimJobException
    + FullyQualifiedErrorId : CmdletizationQuery_NotFound_DisplayName,Get-NetFirewallRule

