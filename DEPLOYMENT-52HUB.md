# 52HUB Admin Frontend Deployment Notes

## Project

- Project: 52HUB admin frontend
- Upstream baseline: dujiao-next/admin v1.0.2
- Local branch: 52hub/v1.0.2-admin-hardening
- Build command: `npm run build`
- Production deploy directory: `/opt/dujiao-next/web/admin`
- Production container mount: `./web/admin:/usr/share/nginx/html:ro`

## Source-Hardened Content

1. 52Hub Admin branding.
2. favicon / logo / icon public assets.
3. `52hub-hotfixes.css`.
4. Admin title changed to `52Hub Admin`.
5. AdminLayout / Login branding updates.
6. `image.ts` path normalization fix.
7. Admin keeps `zh-TW` for backend content management compatibility.

## Known Residuals

1. `Dujiao-Next` / `GitHub` residual text may still exist and should be checked against actual pages later.

## Operational Notes

- Do not push directly to upstream `origin`.
- Rollback: restore the `/opt/dujiao-next/web` backup or redeploy the previous `dist` version.
