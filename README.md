# MVI56E-DNPNET
Programs and Sample Ladder for use with the MVI56E-DNPNET.  All of these routines are stored as raw text, rather than L5X files.  This makes it easier to study, and examine and use as samples.  At the top of the code in the flower box are any tags that need to be created by the user for these routines to work.  Make sure you create all the listed tags, or the routine(s) will not compile.  All of the data types of the tags will be listed right after the tag name.  Below is a sample of what the flower box will look like.
```
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
//  Routine: %Routine Name%
//  Author : %Code Author%
//  Desc   : %Description of Routine%
//  Date   : %Creation Date%
//  Tags   : %Required Tag names that are not expected to exist%
//  Note   : %Important Notes related to routine% (Optional)
//
//  %Copyright Info%
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
```
Tags will be listed under the `Tags:` heading.  They will be listed in the format:

`TagName` - `Type` (`Scope: Local|Program|Controller`): `Description`

In the example below, the tag you need to create is `DNPServerDatabaseSizes`, and it will be of type `DNPNETSERVERDATABASE`, and since the scope isn't specified, you can create it as Controller or Local/Program scope.
```
//           DNPServerDatabaseSizes - (of type: DNPNETSERVERDATABASE): Contains the database size values for the desired
//                                                                     DNPNET slave database sizes.
```

## DNP CROB Handler Routine
CROBOutputRoutine.txt

## DNP Database Size Control
DNPDatabaseSizeEnforcer.txt - Small Routine that checks and enforces the DNP Server database of the MVI56E-DNPNET, regardless of what the user has configured in the DNPNET UDT's.  This provides multiple benifets.  First, it prevents the DNPNET from sending at least 1 point for data types that your master doesn't support.  For example, if you're not using o30v1 or o30v3, 32-bit Analog Inputs, then the smallest you can set the UDT size for is 1.  This will cause an AI32[*n*] to show up in a Class 0 poll, which is not always desireable.  The other benifet it provides is that you can keep your UDT sizes larger than what you're actually using.  This allows you to control your database sizes on the fly by just adjusting the `DNPServerDatabaseSizes` tag values.

**NOTE:** Is recommended that you keep the tag `DNPNET.CONFIG.DNP3_Server.Initialize_DNP_Output_Database` set to a 1 when using this routine. 

## DNP Error Handler
DNPErrors.txt

## MVI56E-DNPNET Configuration in Structured Text Form
DNPNETConfiguration.txt - This file allows you to configure a DNPNET module in structured text.  This makes it much easier to read your config, and even assure that the tags are always set accordingly when the controller goes into RUN mode.
This allows for much cleaner looking configuration code.
```
    // Start by configuring the DNPNET Client
    DNPNET.CONFIG.DNP3_Client.Internal_ID                               :=   33;
    DNPNET.CONFIG.DNP3_Client.Event_Messages_to_PLC                     :=    1;
    DNPNET.CONFIG.DNP3_Client.Initialize_IED_Input_Database             :=    0;
    DNPNET.CONFIG.DNP3_Client.Only_Time_Sync_Servers_If_Synced          :=    0;
    DNPNET.CONFIG.DNP3_Client.Use_Binary_Output_status_Data             :=    1;
    DNPNET.CONFIG.DNP3_Client.Use_Analog_Output_status_Data             :=    1;
    DNPNET.CONFIG.DNP3_Client.Dont_Process_IIN                          :=    0;
```
