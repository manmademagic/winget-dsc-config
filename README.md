# What/Why
I couldn't find many examples of using resources outside of WinGet-DSC, hopefully this repo will help others looking to do something similar.

The DSC integration in [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/) can use other DSC resource providers, which allows for some neat tricks like being able to install chocolatey packages via the [cChoco](https://github.com/chocolatey/cChoco/tree/development/DSCResources/cChocoPackageInstall) provider. This can vastly simplify system bootstrapping scripts by only requiring a single tool to be used[^1], rather than having requiring a combination of different tools, scripts, utils, and config files.

[^1]: Really it's just a wrapper for those extra tools though - *or a wrapper for a wrapper* ¯\\\_(ツ)\_/¯ 

## What's Here
The repo contains the following files:
| File | Description |
|---|---|
|[setup.winget](/setup.winget)|the file I am using to configure my computer|
|[sample.winget](/sample.winget)|a stripped down and annotated sample|
|[README.md](/README.md)|this text you're reading|

### *How do I Use These Files?*
Looking through [sample.winget](/sample.winget) should be a good starting point for anyone looking to create their own .winget file, and [setup.winget](/setup.winget) can be used as a reference if some more examples are needed.

To apply the file, make a copy of `sample.winget` somewhere on your computer, then run `winget configure .\sample.winget`.
> [!WARNING]
> *Without modification, the sample will install software and run scripts on your machine.*

> [!CAUTION]
> **Seriously, please don't just run this without understanding what will happen first**.\
> I haven't (_intentionally_) included anything malicious, _but you can't trust anybody on the internet._[^2]

# What is Desired State Configuration (DSC)?

DSC is designed to be a declarative way to specify what a system's configuration should be.\
For the most part you can think of it as: \
_"I don't care what it currently looks like, or how you achieve it, but this what I want it to look like afterwards"_

1. _TEST_ a resource's **_state_**
2. If **_state_** == `false` then 
   1. perform the _SET_ steps that will make the resource's **_state_** == `true`
   2. _TEST_ the **_state_** again
3. Report if the resource was successfully applied

You can learn more about DSC here: https://learn.microsoft.com/en-us/powershell/dsc/overview?view=dsc-3.0 \
And more about WinGet's DSC here: https://learn.microsoft.com/en-us/windows/package-manager/configuration/


[^2]: ![image](https://github.com/user-attachments/assets/85738f56-680a-4545-b7a0-268dbdfb5db2)
