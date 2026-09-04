# Taf-Taf

Taf-Taf is a local-only Android utility for reviewing and migrating Gambian phone numbers in your Contacts.

## Migration rules

Taf-Taf only proposes changes for old 7-digit Gambian numbers whose first digit is 2, 3, 6, 7, or 9. It also recognizes the same numbers when stored with `+220` or `00220`.

| Old local number | New local number | International result |
| --- | --- | --- |
| `2xxxxxx` | `872xxxxxx` | `+220872xxxxxx` |
| `7xxxxxx` | `877xxxxxx` | `+220877xxxxxx` |
| `3xxxxxx` | `833xxxxxx` | `+220833xxxxxx` |
| `6xxxxxx` | `836xxxxxx` | `+220836xxxxxx` |
| `9xxxxxx` | `899xxxxxx` | `+220899xxxxxx` |

Already-migrated 9-digit Gambian numbers beginning with `87`, `83`, or `89` are not migrated again.

## Safety and privacy

- Taf-Taf requests Android `READ_CONTACTS` and `WRITE_CONTACTS` permissions because those are necessary to scan and update contacts.
- The app does **not** request the Internet permission.
- Proposed changes are shown before they are applied.
- Each successful change is recorded locally for later review and rollback.
- Individual changes can be restored.
- A wholesale undo option is available for active changes.
- Before restoring a number, Taf-Taf verifies that the current number still matches the value written by the app. If the number was edited afterwards, the app avoids overwriting the newer edit.

## Build the APK in GitHub — no Android Studio required

1. Sign in to GitHub and create a new **private** repository, for example `Taf-Taf`.
2. On the new repository page, choose **uploading an existing file**.
3. Unzip the Taf-Taf source package on your computer and upload the **contents of the project folder**. The `.github` folder must be included. Do not upload only the ZIP file.
4. Commit the uploaded files to the `main` branch.
5. Open the repository's **Actions** tab.
6. Select **Build Taf-Taf APK**.
7. Click **Run workflow**, keep the `main` branch selected, and click **Run workflow** again.
8. When the run finishes successfully, open it and scroll to **Artifacts**.
9. Download **Taf-Taf-APK**. GitHub downloads a ZIP containing `Taf-Taf.apk`.
10. Extract `Taf-Taf.apk`, transfer it to your Android phone, and install it. Android may ask you to allow installation from the app you used to open the APK (for example Files or your browser).

The GitHub workflow uses JDK 17 and Gradle 8.9, which are compatible with the Android Gradle Plugin 8.7.x used by this project.

## First-use recommendation

Before applying changes to your whole address book, create a few test contacts representing each of the five migration rules and run Taf-Taf against those first. Review the preview, apply the changes, then test both an individual restore and the wholesale undo function.
