# Login, accounts and the menu

Problems with logging in, staying logged in, roles, datasets and the menu of `signcollect.nl`.

!!! note "No self-service password reset"
    SignCollect has no "forgot password" link. An administrator sets a new password for you.

### "Ongeldige gebruikersnaam of wachtwoord." {#login-wrong-password}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** the username or password does not match exactly. Capitals and spaces count.

**Try this:**

1. Type the username again. Check for a space at the start or end.
2. Check that Caps Lock is off.
3. If your browser filled in the password, type it by hand instead.
4. If it still fails, ask an administrator to set a new password.

**Still stuck?** Send your username (never your password) and the time.

### My password worked yesterday, but not after I used the TYD API admin page {#login-tyd-hash}

**Type:** system error · **Who can fix:** administrator

**Likely cause:** the TYD API admin page changes how your password is stored the first time you log in there. After that, the normal SignCollect login no longer accepts it. This is a known bug.

**Try this:**

1. Ask an administrator to set your password again in the Users page.
2. Until the bug is fixed, avoid logging in on the TYD API admin page with the same account.

**Still stuck?** Send your username and the time you last used the TYD API admin page.

### "Uw account is geblokkeerd. Neem contact op met een beheerder." {#login-blocked}

**Type:** both · **Who can fix:** administrator

**Likely cause:** an administrator blocked your account, or it was blocked automatically after more than 60 days without login or activity.

**Try this:**

1. Ask an administrator to unblock your account in the Users page.

**Still stuck?** Send your username and when you last logged in.

### I forgot my password {#login-forgot}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** there is no self-service reset.

**Try this:**

1. Ask an administrator for a new password.
2. The administrator uses **Edit** in the Users page and fills in a new password.

**Still stuck?** Send your username.

### "Er is een fout opgetreden. Probeer het opnieuw." on the login page {#login-generic-error}

**Type:** system error · **Who can fix:** you / administrator

**Likely cause:** the login request itself failed, because of your network or the server.

**Try this:**

1. Check your network and try again.
2. Check whether other pages load. If not, see [Server and system](system.md).

**Still stuck?** Send the time and the message.

### I keep getting sent back to the login page {#login-loop}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** your session is missing or expired, your browser blocks the cookie, or your account was blocked in the meantime.

**Try this:**

1. Log in again. You return to the page you came from.
2. Allow cookies for `signcollect.nl`.
3. Close private or incognito windows and try a normal window.
4. If it loops right after logging in, see [account blocked](#login-blocked).

**Still stuck?** Send the page address, your browser name and the time.

### I logged out, but I am still logged in {#login-logout}

**Type:** user error · **Who can fix:** you

**Likely cause:** closing the tab does not log you out. The session lasts up to a year.

**Try this:**

1. Use the **Logout** link in the menu. It clears the login on every SignCollect address.
2. If you still appear logged in, clear the cookies for `signcollect.nl`.
3. Always log out on shared computers.

**Still stuck?** Send your browser name.

### A page says "Geen toegang" or "Unauthorized" {#login-no-access}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** the page is for administrators only, for example the Users page, the activity log and the Signbank admin page. Your role is checked on the server each time.

**Try this:**

1. Check whether you need this page for your work.
2. If so, ask an administrator to change your role.

**Still stuck?** Send the page address and your username.

### The dataset (NGT/LSM) or the Signbank/Signio switch gives an error {#login-dataset}

**Type:** user error · **Who can fix:** you / administrator

**Likely cause:** your browser remembers the last dataset or view you chose. If you are no longer allowed to use it, the server refuses it.

**Try this:**

1. Pick another dataset or view in the menu.
2. If you need that dataset, ask an administrator to allow it for your account.

**Still stuck?** Send your username and the dataset you need.

### The menu is in the wrong language {#login-language}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** the language comes from your user settings.

**Try this:**

1. Ask an administrator to change your language in the Users page.

**Still stuck?** Send your username and the language you want.

### A menu link opens an error page {#login-menu}

**Type:** both · **Who can fix:** you / administrator

**Likely cause:** you opened a bookmarked folder address without a start page, or the component behind the link is not installed on this host. On a demo host some tools do not exist.

**Try this:**

1. Go back to the menu on `signcollect.nl` and click the link from there.
2. Replace old bookmarks with the address the menu opens now. Several tools were renamed.
3. If the menu link itself fails, report it.

**Still stuck?** Send the menu item, the address it opened and the error text.

### Adding a user fails {#login-add-user}

**Type:** user error · **Who can fix:** administrator

**Likely cause:** the form names the problem: "Username already exists", "Username and password are required", "At least one dataset must be allowed", or the default dataset is not one of the allowed ones.

**Try this:**

1. Choose a username that is not in use.
2. Tick at least one dataset and one view.
3. Make the default one of the ticked options.

**Still stuck?** Send the exact message.
