# Roblox Account Utils

**By 1kakeden · v1.1.1 · Windows 10/11 x64**

I built Roblox Account Utils to organize separate Roblox sign-in sessions, launch selected accounts in sequence, and hand off to Swordburst 2 Controller. Version 1.1.1 adds custom input controls and saved account-to-window assignments; existing account profiles are preserved.

## Download and start

Download **Roblox_Account_Utils_v1.1.1_win-x64.zip** from the [latest release](https://github.com/kakedent/roblox-account-utils-releases/releases/latest). Extract the entire ZIP and run **RobloxAccountUtils.exe**. Keep the included folders and DLLs beside the executable. The Microsoft Edge WebView2 Runtime is required for embedded sign-in windows.

Add or select account profiles, sign in through each profile's browser window, and choose the accounts to launch. **Settings** contains launch delays, verification, themes, optional cleanup, and the path to Swordburst 2 Controller. Select **Swordburst2Controller.exe** if upgrading from the earlier controller name.

## Features

- Separate, persistent WebView2 browser profiles for Roblox sign-ins.
- A selected-account launch queue with delay, cancellation, and client checks.
- Optional handoff to Swordburst 2 Controller after launching.
- Violet, Midnight, Emerald, and Slate themes.
- Experimental multi-instance compatibility and process monitoring.
- Optional cleanup of tracked clients whose previously visible game windows have closed.

## Accounts and privacy

Profiles remain in **%LOCALAPPDATA%\1kakeden\SessionLauncher** for compatibility with earlier releases. Browser sessions stay on the computer and are not included in downloads or source packages. The app does not extract or export Roblox passwords, cookies, or session tokens.

## Cleanup and exit

Automatic cleanup starts off. It considers only new clients tracked during a verified launch queue, and waits 25 seconds after a previously observed game window disappears. **Close selected hidden PID** asks for confirmation before attempting to close a selected client.

Window visibility is a heuristic, so cleanup can affect a loading or background client. Test it with the intended setup before enabling it. Exiting the app cancels the remaining queue and does not intentionally close Roblox clients or the controller; releasing the experimental multi-instance guard may still affect compatibility.

This is an unofficial, unsigned Windows utility, not affiliated with Roblox. Multi-instance behavior depends on the installed Roblox version. Game and server rules apply.

## Updates and trusted launches

The app checks the public GitHub release feed at startup. **Updates** runs a manual check. New releases open in the browser for manual installation; settings and sign-in profiles remain local.

Account Utils handles the registered **roblox-player** protocol only after a launch request from a trusted HTTPS Roblox game page. This avoids the embedded browser's repeated launch confirmation without changing Windows security settings or allowing unrelated websites and protocols. Roblox must already be installed.

The legacy external browser executable field has been removed. Layout spacing, wrapping, and minimum sizes have been adjusted to keep headers and buttons separate.

## Building from source

The source repository is private. Contributors with access can install the .NET 8 SDK or newer and run **build-windows.cmd** from the project root. The script publishes **publish\RobloxAccountUtils.exe** and packages the complete distribution in **dist**.

## Version 1.1.1

Startup and manual update checks use the same GitHub stable-release approach as Swordburst 2 Controller. Trusted, intentional Roblox launches from the embedded browser are handed to the registered Roblox app; other external protocols retain the browser prompt. The legacy browser.exe setting has been removed. Headers and action rows have more space, and the client list shows RAM use per process. Close sign-in browser windows when finished to release their browser resources.

## Custom controls

Launch delay and verification use themed number steppers, the theme picker uses a custom dropdown, and account selection uses drawn switches. Buttons, fields, and list borders follow the selected theme.

## Saved window assignments

Select an account, click **Assign window…**, and choose its Roblox game window by PID and window handle. Verify the signed-in Roblox account before saving: window titles alone cannot identify it. A window can belong to only one account. The assignment appears in the account list and is saved locally for both apps in **%LOCALAPPDATA%\RobloxController\account-window-assignments.json**. No browser session data or credentials are sent.

Use the refreshed Swordburst 2 Controller v1.1.2 on the same Windows user account. Stop automation, then select **Scan / Arrange** or **Start** to load assignments. Linked live windows are ordered by the Account Utils account list, ahead of unassigned windows. Controller account cards show the saved account nickname. Changes made during a run take effect after stopping and scanning or starting again.

Assignments survive restarting the apps while the same Roblox windows remain open. When Roblox closes or restarts, select its new window again; old process/window identities are never automatically reused. Removing an account also removes its saved assignment. Controller combat settings remain session-specific.
