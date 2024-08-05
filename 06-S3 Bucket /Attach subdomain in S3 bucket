# 🌐 Adding a Subdomain for Your Static Website on S3 and Connecting with GitHub Actions

## Step 1: Create a Subdomain in GoDaddy 🏠

1. Log in to your GoDaddy account.
2. Navigate to **My Products** and click **DNS** next to your domain `payvista.net`.
3. Add a CNAME record:
   - **Type**: CNAME
   - **Name**: `staging` (This will create `staging.payvista.net`)
   - **Value**: `staging-payvista-ui.s3-website.ap-south-1.amazonaws.com`
   - **TTL**: Default (usually 1 hour)

## Step 2: Create a CloudFront Distribution 🚀

1. Log in to your AWS Management Console.
2. Navigate to **CloudFront** and click **Create Distribution**.
3. Select **Web** as the delivery method.
4. **Origin Settings**:
   - **Origin Domain Name**: `staging-payvista-ui.s3-website.ap-south-1.amazonaws.com`
   - **Origin Path**: Leave it blank
   - **Name**: Leave it default
5. **Default Cache Behavior Settings**:
   - **Viewer Protocol Policy**: Redirect HTTP to HTTPS
6. **Distribution Settings**:
   - **Alternate Domain Names (CNAMEs)**: `staging.payvista.net`
   - **SSL Certificate**: Choose the custom SSL certificate from ACM (`*.payvista.net`)
7. Leave the other settings as default and click **Create Distribution**.

## Step 3: Update DNS Settings in GoDaddy 🔄

1. Return to **GoDaddy DNS settings** for `payvista.net`.
2. Add or Update a CNAME record:
   - **Type**: CNAME
   - **Name**: `staging`
   - **Value**: `<CloudFront Distribution Domain Name>` (found in the CloudFront console under your new distribution)
   - **TTL**: Default (usually 1 hour)

## Step 4: Configure S3 Bucket for Static Website Hosting 📦

1. Navigate to your S3 bucket (`staging-payvista-ui`).
2. Go to **Properties** and enable **Static website hosting**.
   - **Index document**: `index.html`
   - **Error document**: `error.html` (if you have one)

## Step 5: Update GitHub Actions for CI/CD 🚀

Ensure your GitHub Actions workflow updates the S3 bucket and invalidates the CloudFront cache after each deployment. Here’s a sample `main.yml` for your GitHub Actions:

```yaml
name: Deploy React Ui App to S3 and Invalidate CloudFront

on:
  push:
    branches:
      - payvista_staging_ui

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install dependencies
        run: npm install

      - name: Build project
        run: npm run build

      - name: Deploy to S3
        uses: jakejarvis/s3-sync-action@v0.5.1
        with:
          args: --follow-symlinks --delete
        env:
          AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          SOURCE_DIR: 'build'

      - name: Invalidate CloudFront Cache
        uses: chetan/invalidate-cloudfront-action@v2
        env:
          DISTRIBUTION: ${{ secrets.CLOUDFRONT_DISTRIBUTION_ID }}
          PATHS: '/*'
          AWS_REGION: 'ap-south-1'
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
