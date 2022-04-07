# Snapshots Explorer for cheqd networks

Simple browser-based app to display contents of an S3-compatible object storage bucket. Used for [snapshots.cheqd.net](https://snapshots.cheqd.net).

This repo is forked from [awslabs/aws-js-s3-explorer](https://github.com/awslabs/aws-js-s3-explorer) to utilise [DigitalOcean's Spaces object-storage offering](https://www.digitalocean.com/products/spaces) instead of AWS S3.

## Usage

To retarget this repo to a different DigitalOcean Spaces storage, change the following lines to your own endpoint using the examples below.

Line 185:

```javascript
var endpoint = 'nyc1.cdn.digitaloceanspaces.com'
```

Line 482:

```javascript
AWS.config.region = 'nyc1';
```

Line 658-659:

```javascript
s3exp_config.Bucket = '<space-name>';
s3exp_config.Region = 'nyc1';
```

## Deploy

The [snapshots.cheqd.net](snapshots.cheqd.net) microsite is auto-deployed using [Cloudflare Pages](https://developers.cloudflare.com/pages/platform/github-integration) using its GitHub integration. No configuration is required besides connecting your repository to Cloudflare.

### CORS Settings

CORS settings need to be specified to allow the file explorer front-end to fetch and list file details.

These steps assume that the deployment has been done to Cloudflare Pages. Follow [DigitalOcean's guide on defining CORS settings](https://docs.digitalocean.com/products/spaces/how-to/configure-cors/) to set the following:

1. **Origin** to `https://<subdomain>.pages.dev`
2. **Allowed Methods** to `GET` and `HEAD`
3. **Allowed Headers** to `*`
4. (optional )**Access Control Max Age** to 7200
