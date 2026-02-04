# Notes

## Class labs: npm blocked by execution policy (Windows)

If you get an error when running `npm` (e.g. "running scripts is disabled on this system"), PowerShell’s execution policy is blocking scripts.

**Fix:** In PowerShell, run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Confirm with `Y` when prompted. Then try `npm` again.

**Note:** You may need to close and reopen the terminal (or VS Code) after changing the policy.
