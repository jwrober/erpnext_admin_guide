## 1.4 Typography

To make things easier to follow in the book, there are a few typographical conventions used. This section contains some examples of the typographical format used throughout the ERPNext Administrator's Guide.

### 1.4.1 Code / Command Line
The following example shows commands to be typed in at a command line, or other pre-formatted text form logs, error messages:

    bench use [site name]
    bench backup --with-files
    bench upgrade --upgrade


### 1.4.2 Replaceable Text

Any text that is expected to be replaced by something site specific is contained inside of square brackets. In this example the user should place the name of the site (e.g. site1.local) as a replacement for [site name].

    bench use [site name]

### 1.4.3 Important

Anything that is important to note to the reader is prefaced with **NOTE**:

### 1.4.4 Actions

When describing actions to take in a set of instructions, button clicks are in **bold** font. It is assumed that the word "click" is synonymous with "tap" for touch sensitive interfaces.

1. Login to ERPNext with Administrator account
1. Click the **Login** button
1. Click **Setup** on the Desk

### 1.4.5 Names of Programs / Utilities

The names of programs or utilities that are referenced in regular text will be in fixed width font, such as `sudo`, `su`, `cd`, or `bench`.

## 1.4.6 Path Navigation

When working inside of ERPNext, the Administrators guide will give a click path to get to a particular document. The format will look like this:

> Explore > Setup > Users > User

In this example, the user clicks the Explore icon on the Desktop, navigates to the Setup module, looks for the Users header and clicks on the User document list.<br /><br />

Previous: [1.3 Prerequisites](prerequisites.md "Prerequisites") | Next: [2.1 Overview of ERPNext](../introduction/overview.md "Introduction")
