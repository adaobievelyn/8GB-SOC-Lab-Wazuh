# 2. Windows 11 Endpoint Setup

## Problem
Windows 11 requires:
- Internet
- Microsoft account
- High RAM

We bypass all of that.

## Step 1: Start Installation

Boot Windows ISO


## Step 2: Bypass Internet Requirement

At the "Connect to network" screen:

Press:
Shift + F10

Type:
OOBE\BYPASSNRO

Press Enter

System restarts

## Step 3: Create Local Account

Select:
"I don't have internet."
"Continue with limited setup."


## Step 4: Optimize Performance

Search:
"Adjust performance"

Select:
Adjust for best performance

## Step 5: Reduce Unnecessary Startup Applications

Open:

Task Manager → Startup

Review unnecessary startup applications and disable only those that are not required for the lab or operating system.

## Optional Lab-Specific Resource Adjustment

During the original constrained build, some Windows services and background applications were temporarily reduced to lower resource consumption.

This was a lab-specific troubleshooting decision, not a recommended production configuration.

Do not disable security controls such as Microsoft Defender on production systems merely to reduce resource usage. If temporary changes are required in a controlled lab, document them and restore the controls after testing.

## Expected Result

Windows runs smoothly on 2GB RAM
