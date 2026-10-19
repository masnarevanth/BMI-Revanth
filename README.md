# FitCheck by Revanth — BMI Calculator

A responsive, browser-based adult BMI calculator built with HTML, CSS, and JavaScript. Branded as “FitCheck by Revanth,” it includes an optional name field, gender selection, weight and height inputs, BMI classification, standard adult BMI ranges, an estimated healthy-weight range, and personalized supportive messages based on the result.

## Run locally

Open `index.html` in any modern browser. No build step, framework, API, database, or server-side runtime is required.

## Calculation and privacy notes

- BMI = weight in kilograms ÷ (height in metres × height in metres).
- Standard adult categories: underweight < 18.5; healthy weight 18.5–24.9; overweight 25.0–29.9; obesity ≥ 30.0.
- Standard adult cut-offs do not change based on gender. Children and teens need age- and sex-specific interpretation, which this adult calculator does not provide.
- All calculation happens in the visitor's browser. The entered name and measurements are not transmitted to a backend or stored by this page.
- Personalized messages are general wellness guidance, not medical advice. BMI does not directly measure muscle mass.
- BMI is a screening measure, not a medical diagnosis.

## AWS deployment option: Amazon S3 + CloudFront

Recommended architecture for a public HTTPS website:

1. Create an S3 bucket in your AWS account and upload `index.html` (keep **Block Public Access enabled**).
2. Create a CloudFront distribution using the S3 bucket as the origin. Use Origin Access Control (OAC) so CloudFront can read the private bucket.
3. Allow the CloudFront distribution access to the bucket using the S3 bucket policy generated/recommended by the CloudFront setup flow. Do not make the bucket public just to publish the site.
4. Set the default root object to `index.html`.
5. Wait for the distribution to deploy, then open its CloudFront domain name. The site should be reachable publicly over HTTPS.
6. After an update, upload the changed file and create a CloudFront invalidation for `/index.html` if the old version remains cached.

AWS console labels can change. Follow the current AWS CloudFront/S3 documentation during setup. AWS services may incur charges, although traffic for a small demo may be very low. Review the AWS pricing page and set a billing alert before publishing.

## Alternative: AWS Amplify Hosting

For the easiest beginner workflow, push this folder to a GitHub repository, then create an Amplify Hosting app and connect the repository. Amplify builds/deploys the static site and provides a public HTTPS URL. No backend is needed for this calculator.

## Suggested LinkedIn project summary


### Calculation interaction and troubleshooting
The Calculate button now runs the calculation directly and the form also supports Enter-key submission. A visible status line confirms when JavaScript has initialized; validation problems and unexpected runtime errors are shown on the page. On narrow screens, FitCheck scrolls to the result card after a successful calculation, respecting reduced-motion preferences.

If the status line remains on “Loading calculator…”, the environment displaying the HTML may be blocking JavaScript. Download the ZIP, extract it, and open the extracted `index.html` in a normal browser such as Chrome or Firefox, rather than relying on a file preview.
