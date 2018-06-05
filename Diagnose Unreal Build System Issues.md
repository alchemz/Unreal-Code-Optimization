# Diagnose Unreal Build System Issues
- fail to generate the project files warning

How Does The Unreal's Build System work:
*.xcodeproj, *.sln define how to build the binaries, and Unreal Engine created a independent a system to generate the project files to have the project work under difference operating system.
The Unreal Build System uses *.Target.cs, *.Build.cs file to generate the project files, which goes to *.xcodeproj, *.sln, and then be translated to the Binaries file.

The reason for the "fail to generate the project files warning" issue, is because the 4.18 changes setting for the generate the files step.

Solution: in BuildingEscape.uproject file, update the UnrealAssociation:4.12 to 4.18 or newer version

- Warning: Failed to find object 'Class /Script/BuildEscape.BuildEscapeGameMode'
Unreal 4.17 made the update for including header files to get better performance,
so in the newer version, we need to include header files manually, such as 
include "BuildEscape.h", include "GameFramework/Actor.h"