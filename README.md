# MVI56E-DNPNET
Programs and Sample Ladder for use with the MVI56E-DNPNET.  All of these routines are stored as raw text, rather than L5X files.  This makes it easier to study, and examine and use as samples.  At the top of the code in the flower box are any tags that need to be created for these routines to work.  Make sure you create all the listed tags, or the routine will not compile!

## DNP CROB Handler Routine
CROBOutputRoutine.txt

## DNP Database Size Control
DNPDatabaseSizeEnforcer.tx

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
