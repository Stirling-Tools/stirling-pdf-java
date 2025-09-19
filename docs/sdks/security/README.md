# Security
(*security()*)

## Overview

Document security and protection services for confidential and sensitive content.

This endpoint group provides essential security operations for organizations handling
sensitive documents and materials requiring controlled access.

Common use cases:
• Legal confidentiality, healthcare privacy (HIPAA), and financial regulatory compliance
• Government classified handling, corporate IP protection, and educational privacy (FERPA)
• Contract security for business transactions

Business applications:
• Document authentication, confidential sharing, and secure archiving
• Content watermarking, access control, and privacy protection through redaction

Industry scenarios:
• Legal discovery, medical records exchange, financial audit documentation
• Enterprise policy enforcement and data governance

Target users: Legal professionals, healthcare administrators, compliance officers,
government agencies, and enterprises handling sensitive content.


### Available Operations

* [validateSignature](#validatesignature) - Validate PDF Digital Signature
* [sanitizePDF](#sanitizepdf) - Sanitize a PDF file
* [removePassword](#removepassword) - Remove password from a PDF file
* [removeCertSignPDF](#removecertsignpdf) - Remove digital signature from PDF
* [redactPdfManual](#redactpdfmanual) - Redacts areas and pages in a PDF document
* [getPdfInfo](#getpdfinfo) - Summary here
* [signPDFWithCert](#signpdfwithcert) - Sign PDF with a Digital Certificate
* [redactPdfAuto](#redactpdfauto) - Redacts listOfText in a PDF document
* [addWatermark](#addwatermark) - Add watermark to a PDF file
* [addPassword](#addpassword) - Add password to a PDF file

## validateSignature

Validates the digital signatures in a PDF file against default or custom certificates. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="validateSignature" method="post" path="/api/v1/security/validate-signature" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SignatureValidationRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ValidateSignatureResponse;

public class Application {

    public static void main(String[] args) throws ValidateSignatureBadRequestException, ValidateSignatureRequestEntityTooLargeException, ValidateSignatureUnprocessableEntityException, ValidateSignatureInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SignatureValidationRequest req = SignatureValidationRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ValidateSignatureResponse res = sdk.security().validateSignature()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `request`                                                                       | [SignatureValidationRequest](../../models/shared/SignatureValidationRequest.md) | :heavy_check_mark:                                                              | The request object to use for the request.                                      |

### Response

**[ValidateSignatureResponse](../../models/operations/ValidateSignatureResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/ValidateSignatureBadRequestException            | 400                                                           | application/json                                              |
| models/errors/ValidateSignatureRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/ValidateSignatureUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/ValidateSignatureInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |

## sanitizePDF

This endpoint processes a PDF file and removes specific elements based on the provided options. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="sanitizePDF" method="post" path="/api/v1/security/sanitize-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SanitizePdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SanitizePDFResponse;

public class Application {

    public static void main(String[] args) throws SanitizePDFBadRequestException, SanitizePDFRequestEntityTooLargeException, SanitizePDFUnprocessableEntityException, SanitizePDFInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SanitizePdfRequest req = SanitizePdfRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        SanitizePDFResponse res = sdk.security().sanitizePDF()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | [SanitizePdfRequest](../../models/shared/SanitizePdfRequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[SanitizePDFResponse](../../models/operations/SanitizePDFResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/SanitizePDFBadRequestException            | 400                                                     | application/json                                        |
| models/errors/SanitizePDFRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/SanitizePDFUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/SanitizePDFInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |

## removePassword

This endpoint removes the password from a protected PDF file. Users need to provide the existing password. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="removePassword" method="post" path="/api/v1/security/remove-password" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFPasswordRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RemovePasswordResponse;

public class Application {

    public static void main(String[] args) throws RemovePasswordBadRequestException, RemovePasswordRequestEntityTooLargeException, RemovePasswordUnprocessableEntityException, RemovePasswordInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFPasswordRequest req = PDFPasswordRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RemovePasswordResponse res = sdk.security().removePassword()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | [PDFPasswordRequest](../../models/shared/PDFPasswordRequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[RemovePasswordResponse](../../models/operations/RemovePasswordResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/RemovePasswordBadRequestException            | 400                                                        | application/json                                           |
| models/errors/RemovePasswordRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/RemovePasswordUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/RemovePasswordInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## removeCertSignPDF

This endpoint accepts a PDF file and returns the PDF file without the digital signature. Input:PDF, Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="removeCertSignPDF" method="post" path="/api/v1/security/remove-cert-sign" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RemoveCertSignPDFResponse;

public class Application {

    public static void main(String[] args) throws RemoveCertSignPDFBadRequestException, RemoveCertSignPDFRequestEntityTooLargeException, RemoveCertSignPDFUnprocessableEntityException, RemoveCertSignPDFInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RemoveCertSignPDFResponse res = sdk.security().removeCertSignPDF()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [PDFFile](../../models/shared/PDFFile.md)  | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[RemoveCertSignPDFResponse](../../models/operations/RemoveCertSignPDFResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/RemoveCertSignPDFBadRequestException            | 400                                                           | application/json                                              |
| models/errors/RemoveCertSignPDFRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/RemoveCertSignPDFUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/RemoveCertSignPDFInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |

## redactPdfManual

This operation takes an input PDF file with a list of areas, page number(s)/range(s)/function(s) to redact. Input:PDF, Output:PDF, Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="redactPdfManual" method="post" path="/api/v1/security/redact" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.ManualRedactPdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RedactPdfManualResponse;

public class Application {

    public static void main(String[] args) throws RedactPdfManualBadRequestException, RedactPdfManualRequestEntityTooLargeException, RedactPdfManualUnprocessableEntityException, RedactPdfManualInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ManualRedactPdfRequest req = ManualRedactPdfRequest.builder()
                .redactions(List.of())
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RedactPdfManualResponse res = sdk.security().redactPdfManual()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `request`                                                               | [ManualRedactPdfRequest](../../models/shared/ManualRedactPdfRequest.md) | :heavy_check_mark:                                                      | The request object to use for the request.                              |

### Response

**[RedactPdfManualResponse](../../models/operations/RedactPdfManualResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/RedactPdfManualBadRequestException            | 400                                                         | application/json                                            |
| models/errors/RedactPdfManualRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/RedactPdfManualUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/RedactPdfManualInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |

## getPdfInfo

desc. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getPdfInfo" method="post" path="/api/v1/security/get-info-on-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetPdfInfoResponse;

public class Application {

    public static void main(String[] args) throws GetPdfInfoBadRequestException, GetPdfInfoRequestEntityTooLargeException, GetPdfInfoUnprocessableEntityException, GetPdfInfoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetPdfInfoResponse res = sdk.security().getPdfInfo()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `request`                                  | [PDFFile](../../models/shared/PDFFile.md)  | :heavy_check_mark:                         | The request object to use for the request. |

### Response

**[GetPdfInfoResponse](../../models/operations/GetPdfInfoResponse.md)**

### Errors

| Error Type                                             | Status Code                                            | Content Type                                           |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| models/errors/GetPdfInfoBadRequestException            | 400                                                    | application/json                                       |
| models/errors/GetPdfInfoRequestEntityTooLargeException | 413                                                    | application/json                                       |
| models/errors/GetPdfInfoUnprocessableEntityException   | 422                                                    | application/json                                       |
| models/errors/GetPdfInfoInternalServerError            | 500                                                    | application/json                                       |
| models/errors/APIException                             | 4XX, 5XX                                               | \*/\*                                                  |

## signPDFWithCert

This endpoint accepts a PDF file, a digital certificate and related information to sign the PDF. It then returns the digitally signed PDF file. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="signPDFWithCert" method="post" path="/api/v1/security/cert-sign" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.CertType;
import org.openapis.openapi.models.components.SignPDFWithCertRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SignPDFWithCertResponse;

public class Application {

    public static void main(String[] args) throws SignPDFWithCertBadRequestException, SignPDFWithCertRequestEntityTooLargeException, SignPDFWithCertUnprocessableEntityException, SignPDFWithCertInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SignPDFWithCertRequest req = SignPDFWithCertRequest.builder()
                .certType(CertType.PKCS12)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        SignPDFWithCertResponse res = sdk.security().signPDFWithCert()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `request`                                                               | [SignPDFWithCertRequest](../../models/shared/SignPDFWithCertRequest.md) | :heavy_check_mark:                                                      | The request object to use for the request.                              |

### Response

**[SignPDFWithCertResponse](../../models/operations/SignPDFWithCertResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/SignPDFWithCertBadRequestException            | 400                                                         | application/json                                            |
| models/errors/SignPDFWithCertRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/SignPDFWithCertUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/SignPDFWithCertInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |

## redactPdfAuto

This operation takes an input PDF file and redacts the provided listOfText. Input:PDF, Output:PDF, Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="redactPdfAuto" method="post" path="/api/v1/security/auto-redact" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.RedactPdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RedactPdfAutoResponse;

public class Application {

    public static void main(String[] args) throws RedactPdfAutoBadRequestException, RedactPdfAutoRequestEntityTooLargeException, RedactPdfAutoUnprocessableEntityException, RedactPdfAutoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        RedactPdfRequest req = RedactPdfRequest.builder()
                .customPadding(4612.42)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RedactPdfAutoResponse res = sdk.security().redactPdfAuto()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [RedactPdfRequest](../../models/shared/RedactPdfRequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[RedactPdfAutoResponse](../../models/operations/RedactPdfAutoResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/RedactPdfAutoBadRequestException            | 400                                                       | application/json                                          |
| models/errors/RedactPdfAutoRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/RedactPdfAutoUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/RedactPdfAutoInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## addWatermark

This endpoint adds a watermark to a given PDF file. Users can specify the watermark type (text or image), rotation, opacity, width spacer, and height spacer. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="addWatermark" method="post" path="/api/v1/security/add-watermark" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.AddWatermarkRequest;
import org.openapis.openapi.models.components.WatermarkType;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AddWatermarkResponse;

public class Application {

    public static void main(String[] args) throws AddWatermarkBadRequestException, AddWatermarkRequestEntityTooLargeException, AddWatermarkUnprocessableEntityException, AddWatermarkInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        AddWatermarkRequest req = AddWatermarkRequest.builder()
                .watermarkType(WatermarkType.IMAGE)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AddWatermarkResponse res = sdk.security().addWatermark()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [AddWatermarkRequest](../../models/shared/AddWatermarkRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[AddWatermarkResponse](../../models/operations/AddWatermarkResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/AddWatermarkBadRequestException            | 400                                                      | application/json                                         |
| models/errors/AddWatermarkRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/AddWatermarkUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/AddWatermarkInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## addPassword

This endpoint adds password protection to a PDF file. Users can specify a set of permissions that should be applied to the file. Input:PDF Output:PDF

### Example Usage

<!-- UsageSnippet language="java" operationID="addPassword" method="post" path="/api/v1/security/add-password" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.AddPasswordRequest;
import org.openapis.openapi.models.components.KeyLength;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AddPasswordResponse;

public class Application {

    public static void main(String[] args) throws AddPasswordBadRequestException, AddPasswordRequestEntityTooLargeException, AddPasswordUnprocessableEntityException, AddPasswordInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        AddPasswordRequest req = AddPasswordRequest.builder()
                .keyLength(KeyLength.TWO_HUNDRED_AND_FIFTY_SIX)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AddPasswordResponse res = sdk.security().addPassword()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | [AddPasswordRequest](../../models/shared/AddPasswordRequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[AddPasswordResponse](../../models/operations/AddPasswordResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/AddPasswordBadRequestException            | 400                                                     | application/json                                        |
| models/errors/AddPasswordRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/AddPasswordUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/AddPasswordInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |