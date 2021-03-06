
------------------------------------------------------------------------------
v 1.4.1			Jul 15, 2013
------------------------------------------------------------------------------

*	Added the ability to manipulate UFS (Steam cloud) files with UFSClient.
*	Added SteamScreenshots handler for interacting with user screenshots.
*	Added an optional parameter to SteamID.Render() to render SteamIDs to their Steam3 representations.
*	Added the ability to specify the timeout of WebAPI requests with Interface.Timeout.
*	The RSACrypto and KeyDictionary utility classes are now accessible to consumers.
*	Updated EMsg list.
*	Updated game related GC messages.


------------------------------------------------------------------------------
v 1.4.0			Jun 08, 2013
------------------------------------------------------------------------------

*	KeyValues now correctly writes out strings in UTF8.
*	Fixed an exception that could occur with an invalid string passed to SteamID's constructor.
*	Added SteamFriends.ClanStateCallback.
*	Added EPersonaStateFlag. This value is now exposed in SteamFriends.PersonaStateCallback.
*	Added MsgClientCreateChat and MsgClientCreateChatResponse messages.
*	Added GlobalID base class for globally unique values (such as JobIDs, UGCHandles) in Steam.
*	Updated EMsg list.
*	Updated game related GC messages.
*	Added initial support for the Steam Cloud file system with UFSClient. This feature should be considered unstable and may
	have breaking changes in the future.

BREAKING CHANGES
*	STATIC_CALLBACKS builds of SteamKit have now been completely removed.
*	Message classes for unified messages have moved namespaces from SteamKit2.Steamworks to SteamKit2.Unified.Internal.


------------------------------------------------------------------------------
v 1.3.1			Mar 10, 2013
------------------------------------------------------------------------------

*	Fixed issue where the avatar hash of a clan was always null.
*	Introduced better handling of networking related cryptographic exceptions.
*	Updated EMsg list.
*	Exposed SteamClient.JobCallback<T> for external consumers.
*	STATIC_CALLBACK builds of SteamKit and related code has been obsoleted and will be removed in the next version.
*	Implemented GameID.ToString().
*	Implemented game pass sending and recieving with SteamApps.SendGuestPass(), SteamApps.GuestPassListCallback, and
	SteamApps.SendGuestPassCallback.
*	Implemented requesting Steam community profile info with SteamFriends.RequestProfileInfo(), and SteamFriends.ProfileInfoCallback
*	CMClient now exposes a ConnectionTimeout field to control the timeout when connecting to Steam. The default timeout is 5 seconds.
*	Updated the internal list of CM servers to help alleviate some issues with connecting to dead servers.
*	Implemented SteamClient.CMListCallback to retrieve the current list of CM servers.
*	Implemented initial support for unified messages through the SteamUnifiedMessages handler.

BREAKING CHANGES
*	CMClient.Connect has been refactored significantly. It is no longer possible to use unencrypted connections. The Connect function
	now accepts an IPEndPoint to allow consumers to specify which Steam server they wish to connect to. Along with this,
	CMClient.Servers is now exposed as a collection of IPEndPoints, instead of IPAddresses.
*	SteamApps.PackageInfoCallback now exposes the immediate child KeyValue for the data, to be more consistent with
	SteamApps.AppInfoCallback.


------------------------------------------------------------------------------
v 1.3.0			Jan 16, 2013
------------------------------------------------------------------------------

*	Fixed case where friend and chat messages were incorrectly trimming the last character.
*	Steam2 ServerClient now exposes a IsConnected property.
*	Steam2 ContentServerClient can now optionally not perform a server handshake when opening a storage session.
*	Added various enums: EClanPermission, EMarketingMessageFlags, ENewsUpdateType, ESystemIMType, EChatFlags,
	ERemoteStoragePlatform, EDRMBlobDownloadType, EDRMBlobDownloadErrorDetail, EClientStat, EClientStatAggregateMethod,
	ELeaderboardDataRequest, ELeaderboardSortMethod, ELeaderboardUploadScoreMethod, and EChatPermission.
*	Fixed case where SteamKit was throwing an unhandled exception during Steam3 tcp connection teardown.
*	Added PICS support to the SteamApps handler: PICSGetAccessTokens, PICSGetChangesSince, and PICSGetProductInfo.
*	Added anonymous download support to CDNClient.
*	Updated the following enums: EMsg, EUniverse, EChatEntryType, EPersonaState, EFriendRelationship, EFriendFlags,
	EClientPersonaStateFlag, ELicenseFlags, ELicenseType, EPaymentMethod, EIntroducerRouting, EClanRank, EClanRelationship,
	EAppInfoSection, EContentDownloadSourceType, EOSType, EServerType, ECurrencyCode, EDepotFileFlag, EEconTradeResponse,
	ESystemIMType, ERemoteStoragePlatform, and EResult.
*	Exposed the following properties in SteamUser.LoggedOnCallback: CellIDPingThreshold, UsePICS, WebAPIUserNonce, and 
	IPCountryCode.
*	Fixed case where SteamKit was incorrectly handling certain logoff messages during Steam server unavailability.
*	Fixed potential crash in Steam2 ContentServerClient when opening a storage session.
*	Updated to latest protobuf-net.

BREAKING CHANGES
*	DepotManifest.ChunkData.CRC is now named DepotManifest.ChunkData.Checksum.


------------------------------------------------------------------------------
v 1.2.2			Nov 11, 2012
------------------------------------------------------------------------------

*	Fixed critical issue that occured while serializing protobuf messages.


------------------------------------------------------------------------------
v 1.2.1			Nov 11, 2012
------------------------------------------------------------------------------

*	Added EPersonaState.LookingToTrade and EPersonaState.LookingToPlay.
*	Added SteamFriends.UnbanChatMember.
*	Removed GeneralDSClient.GetAuthServerList as Steam2 auth servers no longer exist.
*	Removed dependency on Classless.Hasher.
*	Updated to latest protobuf-net.


------------------------------------------------------------------------------
v 1.2.0			Nov 04, 2012
------------------------------------------------------------------------------

*	Fixed issue where LoginKeyCallback was being passed incorrect data.
*	Fixed ClientGCMsg PacketMessage constructor.
*	WebAPI list and array parameters are now accepted and flattened to x[n]=y format.
*	Fixed KeyValue issue when multiple duplicate children exist.
*	Updated protobuf definitions for internal message classes to their latest definitions.
*	Updated EMsgs.
*	Fixed critical MsgMulti handling.
*	Added EEconTradeResponse.
*	Added SteamTrading client message handler.
*	Modified Steam3 TCP socket shutdown to play well with Mono.
*	Modified CMClient.Connect method to be properly async.
*	Implemented friend blocking/unblocking with SteamFriends.IgnoreFriend and SteamFriends.IgnoreFriendCallback.
*	Fixed gameserver logon.
*	Local user is now given the persona name [unassigned] before SteamUser.AccountInfoCallback comes in.
*	Updated SteamKit2's bootstrap CM list, this should reduce how often SK2 will connect to an offline/dead server.
*	Steam2 ServerClient's now expose a ConnectionTimeout member.

BREAKING CHANGES
*	Dota GC EMsgs are now longer located in SteamKit2.GC.Dota.EGCMsg, they are now in SteamKit2.Gc.Dota.Internal.EDOTAGCMsg.
*	Base GC EMsgs are now longer located in SyteamKit2.GC.EGCMsgBase, they are now in multiple enums in the SteamKit2.GC.Internal namespace:
	EGCBaseMsg, EGCSystemMsg, EGCSharedMsg, ESOMsg, EGCItemMsg
*	SteamApps.AppInfoCallback now exposes the immediate child KeyValue for every Section, instead of an empty root parent.


------------------------------------------------------------------------------
v 1.1.0			May 14, 2012
------------------------------------------------------------------------------

*	Added SteamWorkshop for enumerating and requesting details of published workshop files.
*	Large overhaul of SteamGameCoordinator to support the sending and receiving of GC messages.
*	Added SteamFriends ChatInviteCallback.
*	Added SteamFriends KickChatMember and BanChatMember.
*	Fixed invalid handling of PackageInfoCallback response.
*	Updated protobuf definitions for internal message classes to their latest definitions.

BREAKING CHANGES
*	Consumers of SteamClient.JobCallback<T> will have to change their handler functions to take a "JobID" parameter instead of a "ulong".
	These are functionally equivalent, and JobIDs can be implicitly casted to and from ulongs.


------------------------------------------------------------------------------
v 1.0.0			Feb 26, 2012
------------------------------------------------------------------------------

*	Initial release.
