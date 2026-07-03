# picsforyou.cloud — Java Client SDK

Standalone Java client library for the [picsforyou.cloud](https://github.com/guidoinit/picsforyou-cloud) REST API.

## Requirements

- Java 21+
- Maven 3.8+

## Usage

### Maven

Add to your `pom.xml`:

```xml
<dependency>
    <groupId>com.picsforyou.cloud</groupId>
    <artifactId>picsforyou-cloud-client</artifactId>
    <version>1.0.0</version>
</dependency>
```

### Quick start

```java
var client = new PicsForYouCloudClient("http://localhost:3000");

// Signup
client.signup("user@example.com", "mypassword");

// Login
AuthResponse login = client.login("user@example.com", "mypassword");

// List plans
List<Plan> plans = client.listPlans();

// Get token for storage API
TokenResponse token = client.requestToken("client-id", "client-secret");

// Upload a file
UploadedFile file = client.uploadFile(
    token.getAccessToken(), "photo.jpg",
    "image/jpeg", 2048, base64Data);

// List files
List<UploadedFile> files = client.listFiles(token.getAccessToken());

// Download
byte[] data = client.downloadFile(token.getAccessToken(), file.getId());

// Delete
client.deleteFile(token.getAccessToken(), file.getId());
```

## API Coverage

| Group | Methods |
|---|---|
| **Auth** | signup, verify, login, me, logout |
| **Credentials** | registerClient, requestToken |
| **Plans** | listPlans, assignPlan, selectPlan, createCheckoutSession, getCheckoutSuccessHtml, customPlanRequest |
| **Storage** | listFiles, uploadFile, downloadFile, deleteFile |
| **Internal** | debugState |

## Build

```bash
mvn clean package
```

## License

This project is licensed under the terms of the Apache License 2.0.
