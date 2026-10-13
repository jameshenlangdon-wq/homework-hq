# Homework HQ

A one-page homework planner. Type assignments like a text, get one clear "do this next", run a focus timer. When you connect Google, it also:

- pulls your Canvas assignments in from the Canvas calendar in Google Calendar every time you open it
- backs your list up to a private file in your own Google Drive, so your phone and laptop match

Everything is in `index.html`. There's no server and no database.

## 1. Put it online (GitHub Pages)

1. Create a **public** GitHub repository, for example `homework-hq`, and add `index.html` to it.
2. In the repository, go to **Settings → Pages**. Set **Source** to "Deploy from a branch", **Branch** to `main` and the folder to `/ (root)`, then click **Save**.
3. After a minute the site is live at `https://<your-github-username>.github.io/homework-hq/`.

## 2. Let it read Google Calendar (one-time, about 10 minutes)

1. Go to https://console.cloud.google.com/ and create a project called "Homework HQ".
2. **APIs & Services → Library**: enable **Google Calendar API** and **Google Drive API**.
3. **APIs & Services → OAuth consent screen** (also called "Google Auth Platform"): choose **External**, set the app name to "Homework HQ" and use your email for the contacts. Under **Audience → Test users**, add the Google account your Canvas calendar is in.
4. **APIs & Services → Credentials → Create credentials → OAuth client ID**:
   - Application type: **Web application**
   - Authorized JavaScript origins: `https://<your-github-username>.github.io`
5. Copy the **Client ID**. It ends in `.apps.googleusercontent.com`.
6. Paste it into `index.html` on the line `const GOOGLE_CLIENT_ID = "";` and commit.

Open the site and tap **Connect Google**. Google will warn that the app isn't verified. That's expected for a personal app: click **Continue**.

### If Google says access is blocked

School Google accounts (like `@student.yourschool.com`) are often set up to block apps the school hasn't approved. If you see "Access blocked" or "admin_policy_enforced":

- Add your Canvas calendar feed to a **personal** Gmail account's Google Calendar (Other calendars → From URL), and connect that account instead.
- Or keep using the **Connect Canvas** panel in the app to import the Canvas `.ics` file by hand.

## Notes

- Your homework is saved in your browser first, so the site works offline and without Google.
- The Drive file sits in Drive's hidden app-data folder. Only this app can see it, and it doesn't show up in your Drive file list.
- Canvas doesn't share what you've submitted, so check things off in the app.
