# Zikr Invite Links

Static Vercel site for universal/deep links: https://zikr-invites.vercel.app/join/<CODE>

**After first deploy:**

1. Test the files are served correctly:
   ```bash
   curl -sI https://zikr-invites.vercel.app/.well-known/apple-app-site-association | grep -i content-type
   curl -s  https://zikr-invites.vercel.app/.well-known/assetlinks.json | head -5
   ```

2. Verify with Google (takes ~24h to index):
   ```bash
   curl -s "https://digitalassetlinks.googleapis.com/v1/statements:list?source.web.site=https://zikr-invites.vercel.app&relation=delegate_permission/common.handle_all_urls"
   ```

3. Wire up your apps:
   - **iOS** (Xcode): Build Settings → INVITE_LINK_DOMAIN = zikr-invites.vercel.app
   - **Android** (Play Console): Create new release and rebuild APK
   - **Flutter main.dart**: Pass `--dart-define=INVITE_LINK_DOMAIN=zikr-invites.vercel.app` to build commands

4. Test deep link:
   ```bash
   https://zikr-invites.vercel.app/join/ABCD1234
   zikr://join/ABCD1234
   ```

**Custom Domain (optional)**

Once you own a domain, add it in Vercel project settings. Update all references above.
