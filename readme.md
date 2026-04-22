# CapMonster Cloud PHP client

Official PHP SDK for the CapMonster Cloud API.

## Links

- Package: [zennolab/capmonstercloud.client on Packagist](https://packagist.org/packages/zennolab/capmonstercloud.client)
- Documentation: [docs.capmonster.cloud](https://docs.capmonster.cloud/)
- Dashboard / API key: [dash.capmonster.cloud](https://dash.capmonster.cloud/)

💵 Want to test before depositing? Contact support and we’ll add trial credits to your account.

## Minimal example

```php
    include './client/Client.php';
    include './client/src/captcha/ImageToText.php';
    include './client/src/captcha/RecaptchaV2.php';
    $client = new Client("your_client_key");

    //solve image captcha
    $body = "base64_captcha_image";
    $imageRequest = new ImageToTextRequest($body);
    $imageResult = $client->solve($imageRequest);
    
    //solve Recaptcha 2 (without proxy)
    $websiteURL = "https://lessons.zennolab.com/captchas/recaptcha/v2_simple.php?level=high";
    $websiteKey = "6Lcg7CMUAAAAANphynKgn9YAgA4tQ2KI_iqRyTwd";
    $recaptchaV2Request = new RecaptchaV2Request($websiteURL, $websiteKey);
    $recaptchaV2Result = $client->solve($recaptchaV2Request);
    
```

Supported task families include reCAPTCHA, GeeTest, image-to-text, and additional task types documented in the public docs.

## Response format
 The result of the solve method always contains two fields: bool result, a request success indicator, and a mixed message field containing a text description of the error or an object of a successful response from the server.

## Supported request classes

- [GeeTestProxylessRequest](https://zenno.link/doc-geetest-en)
- [GeeTestRequest](https://zenno.link/doc-geetest-proxy-en)
- [ImageToTextRequest](https://zenno.link/doc-ImageToTextTask-en)
- [RecaptchaV2ProxylessRequest](https://zenno.link/doc-recaptcha2-en)
- [RecaptchaV2Request](https://zenno.link/doc-recaptcha2-proxy-en)
- [RecaptchaV3ProxylessRequest](https://zenno.link/doc-recaptcha3-en)
- [RecaptchaV2EnterpriseProxylessRequest](https://zenno.link/doc-recaptcha2e-en)
- [RecaptchaV2EnterpriseRequest](https://zenno.link/doc-recaptcha2e-proxy-en)
- [TurnstileProxylessRequest](https://zenno.link/doc-turnstile-en)
- [TurnstileRequest](https://zenno.link/doc-turnstile-proxy-en)
- [RecaptchaComplexImageTaskRequest](https://zenno.link/doc-complextask-rc-en)
