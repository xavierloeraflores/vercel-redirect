# Vercel Redirect Template

A minimal **Vercel project template** for domain redirects.  
Deploy it with one click, change the destination domain, and your Vercel domain will forward all traffic.


---

## One-Click Deploy

Click the button below to deploy your own copy to Vercel.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fxavierloeraflores%2Fvercel-redirect)

After deployment, redirect to your domain by updating the `vercel.json` file.

---

## How It Works

The template uses **`vercel.json` redirects** to forward all traffic to another domain while preserving the path.

Example: `example.com/pricing` redirects to `yourdomain.com/pricing`


---

## Setup

1. Deploy the template using the **Deploy with Vercel** button.
2. Open `vercel.json`.
3. Replace `https://vercel.com` with the domain you want to redirect to.
4. Redeploy (or push changes).

Example configuration:

```json
{
  "redirects": [
    { 
      "source": "/",
      "destination": "https://yourdomain.com",
      "permanent": true
    },
    {
      "source": "/:path*",
      "destination": "https://yourdomain.com/:path*",
      "permanent": true
    }
  ]
}
```

This configuration preserves URL paths when redirecting.


---

## Optional: Redirect Everything to One Page

If you want all URLs to redirect to a single destination (without preserving paths), use this alternative configuration:

```json
{
  "redirects": [
    { 
      "source": "/(.*)",
      "destination": "https://yourdomain.com",
      "permanent": true
    }
  ]
}
```
Example:
```
example.com/pricing
example.com/blog/post
example.com/anything
```
All redirect to: `yourdomain.com`


---

## Notes

`permanent: true` creates a 301 redirect, which is recommended for SEO and long-term redirects.

No app code or pages are required — Vercel handles the redirect using `vercel.json`.


---

## Demo

Example redirect:

**Source:**  
https://vercel-domain-redirect-demo.vercel.app  

**Destination:**  
https://vercel.com  

Paths are preserved, e.g.:

- https://vercel-domain-redirect-demo.vercel.app/docs → https://vercel.com/docs

## License

MIT
