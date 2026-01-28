# Reflection: What Clicked and What Didn’t (Active Directory Foundations)

## What confused me at first
When I first started this lab, I thought most of my issues were related to credentials or permissions. If something didn’t work, my instinct was to assume I typed something wrong or didn’t have the right access.

## What actually caused most of the problems
As I worked through the setup and troubleshooting, it became clear that most of the issues weren’t user-related at all — they were DNS-related. Once DNS was misconfigured, everything else downstream started failing in ways that weren’t always obvious.

## What finally clicked
The biggest realization for me was that Active Directory doesn’t really exist without DNS. If name resolution isn’t working correctly, authentication, domain joins, and logins all break — sometimes in ways that look completely unrelated.

## How this changed how I think about troubleshooting
Instead of jumping straight to credentials or permissions, I now think more about the underlying services first. I’ve started asking myself: *Can the client even find the domain controller?* before assuming anything else is wrong.

## What I still want to get better at
I still want to improve at reading error messages more critically and trusting diagnostic tools instead of assuming something didn’t run just because I didn’t immediately see output.
