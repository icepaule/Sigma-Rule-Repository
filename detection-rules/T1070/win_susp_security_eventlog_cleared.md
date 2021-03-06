# Testing Documentation win_susp_security_eventlog_cleared

## Detection Rule
```
title: Eventlog Cleared
description: One of the Windows Eventlogs has been cleared. e.g. caused by "wevtutil cl" command execution
references:
    - https://twitter.com/deviouspolack/status/832535435960209408
    - https://www.hybrid-analysis.com/sample/027cc450ef5f8c5f653329641ec1fed91f694e0d229928963b30f6b0d7d3a745?environmentId=100
author: Florian Roth
tags:
    - attack.defense_evasion
    - attack.t1070
logsource:
    product: windows
    service: system
detection:
    selection:
        EventID: 104
        Source: Microsoft-Windows-Eventlog
    condition: selection
falsepositives:
    - Unknown
level: medium
```

## Attack Simualtion
The Windows Event logs are cleared with wevutil:
```
wevtutil cl security
```

## Result

Splunk

![](https://github.com/P4T12ICK/Sigma-Rule-Repository/blob/master/detection-rules/T1070/win_susp_security_eventlog_cleared_test.png)

## Note
- Detection Rule is tested successfully.

