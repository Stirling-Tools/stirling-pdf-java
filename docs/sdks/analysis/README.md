# Analysis
(*analysis()*)

## Overview

Document analysis and information extraction services for content intelligence and insights.

This endpoint group provides analytical capabilities to understand document structure,
extract information, and generate insights from PDF content for automated processing.

Common use cases:
• Document inventory management and content audit for compliance verification
• Quality assurance workflows and business intelligence analytics
• Migration planning, accessibility evaluation, and document forensics

Business applications:
• Legal discovery, financial document review, and healthcare records analysis
• Academic research, government processing, and publishing optimization

Operational scenarios:
• Large-scale profiling, migration assessment, and performance optimization
• Automated quality control and content strategy development

Target users: Data analysts, QA teams, administrators, and business intelligence
professionals requiring detailed document insights.


### Available Operations

* [getSecurityInfo](#getsecurityinfo) - Get security information
* [getPageDimensions](#getpagedimensions) - Get page dimensions for all pages
* [getPageCount](#getpagecount) - Get PDF page count
* [getFormFields](#getformfields) - Get form field information
* [getFontInfo](#getfontinfo) - Get font information
* [getDocumentProperties](#getdocumentproperties) - Get PDF document properties
* [getBasicInfo](#getbasicinfo) - Get basic PDF information
* [getAnnotationInfo](#getannotationinfo) - Get annotation information

## getSecurityInfo

Returns encryption and permission details. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getSecurityInfo" method="post" path="/api/v1/analysis/security-info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetSecurityInfoResponse;

public class Application {

    public static void main(String[] args) throws GetSecurityInfoBadRequestException, GetSecurityInfoRequestEntityTooLargeException, GetSecurityInfoUnprocessableEntityException, GetSecurityInfoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetSecurityInfoResponse res = sdk.analysis().getSecurityInfo()
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

**[GetSecurityInfoResponse](../../models/operations/GetSecurityInfoResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/GetSecurityInfoBadRequestException            | 400                                                         | application/json                                            |
| models/errors/GetSecurityInfoRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/GetSecurityInfoUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/GetSecurityInfoInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |

## getPageDimensions

Returns width and height of each page. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getPageDimensions" method="post" path="/api/v1/analysis/page-dimensions" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetPageDimensionsResponse;

public class Application {

    public static void main(String[] args) throws GetPageDimensionsBadRequestException, GetPageDimensionsRequestEntityTooLargeException, GetPageDimensionsUnprocessableEntityException, GetPageDimensionsInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetPageDimensionsResponse res = sdk.analysis().getPageDimensions()
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

**[GetPageDimensionsResponse](../../models/operations/GetPageDimensionsResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/GetPageDimensionsBadRequestException            | 400                                                           | application/json                                              |
| models/errors/GetPageDimensionsRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/GetPageDimensionsUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/GetPageDimensionsInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |

## getPageCount

Returns total number of pages in PDF. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getPageCount" method="post" path="/api/v1/analysis/page-count" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetPageCountResponse;

public class Application {

    public static void main(String[] args) throws GetPageCountBadRequestException, GetPageCountRequestEntityTooLargeException, GetPageCountUnprocessableEntityException, GetPageCountInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetPageCountResponse res = sdk.analysis().getPageCount()
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

**[GetPageCountResponse](../../models/operations/GetPageCountResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/GetPageCountBadRequestException            | 400                                                      | application/json                                         |
| models/errors/GetPageCountRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/GetPageCountUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/GetPageCountInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## getFormFields

Returns count and details of form fields. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getFormFields" method="post" path="/api/v1/analysis/form-fields" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetFormFieldsResponse;

public class Application {

    public static void main(String[] args) throws GetFormFieldsBadRequestException, GetFormFieldsRequestEntityTooLargeException, GetFormFieldsUnprocessableEntityException, GetFormFieldsInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetFormFieldsResponse res = sdk.analysis().getFormFields()
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

**[GetFormFieldsResponse](../../models/operations/GetFormFieldsResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/GetFormFieldsBadRequestException            | 400                                                       | application/json                                          |
| models/errors/GetFormFieldsRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/GetFormFieldsUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/GetFormFieldsInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## getFontInfo

Returns list of fonts used in the document. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getFontInfo" method="post" path="/api/v1/analysis/font-info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetFontInfoResponse;

public class Application {

    public static void main(String[] args) throws GetFontInfoBadRequestException, GetFontInfoRequestEntityTooLargeException, GetFontInfoUnprocessableEntityException, GetFontInfoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetFontInfoResponse res = sdk.analysis().getFontInfo()
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

**[GetFontInfoResponse](../../models/operations/GetFontInfoResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/GetFontInfoBadRequestException            | 400                                                     | application/json                                        |
| models/errors/GetFontInfoRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/GetFontInfoUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/GetFontInfoInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |

## getDocumentProperties

Returns title, author, subject, etc. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getDocumentProperties" method="post" path="/api/v1/analysis/document-properties" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetDocumentPropertiesResponse;

public class Application {

    public static void main(String[] args) throws GetDocumentPropertiesBadRequestException, GetDocumentPropertiesRequestEntityTooLargeException, GetDocumentPropertiesUnprocessableEntityException, GetDocumentPropertiesInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetDocumentPropertiesResponse res = sdk.analysis().getDocumentProperties()
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

**[GetDocumentPropertiesResponse](../../models/operations/GetDocumentPropertiesResponse.md)**

### Errors

| Error Type                                                        | Status Code                                                       | Content Type                                                      |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| models/errors/GetDocumentPropertiesBadRequestException            | 400                                                               | application/json                                                  |
| models/errors/GetDocumentPropertiesRequestEntityTooLargeException | 413                                                               | application/json                                                  |
| models/errors/GetDocumentPropertiesUnprocessableEntityException   | 422                                                               | application/json                                                  |
| models/errors/GetDocumentPropertiesInternalServerError            | 500                                                               | application/json                                                  |
| models/errors/APIException                                        | 4XX, 5XX                                                          | \*/\*                                                             |

## getBasicInfo

Returns page count, version, file size. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getBasicInfo" method="post" path="/api/v1/analysis/basic-info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetBasicInfoResponse;

public class Application {

    public static void main(String[] args) throws GetBasicInfoBadRequestException, GetBasicInfoRequestEntityTooLargeException, GetBasicInfoUnprocessableEntityException, GetBasicInfoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetBasicInfoResponse res = sdk.analysis().getBasicInfo()
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

**[GetBasicInfoResponse](../../models/operations/GetBasicInfoResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/GetBasicInfoBadRequestException            | 400                                                      | application/json                                         |
| models/errors/GetBasicInfoRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/GetBasicInfoUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/GetBasicInfoInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## getAnnotationInfo

Returns count and types of annotations. Input:PDF Output:JSON Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="getAnnotationInfo" method="post" path="/api/v1/analysis/annotation-info" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.GetAnnotationInfoResponse;

public class Application {

    public static void main(String[] args) throws GetAnnotationInfoBadRequestException, GetAnnotationInfoRequestEntityTooLargeException, GetAnnotationInfoUnprocessableEntityException, GetAnnotationInfoInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        GetAnnotationInfoResponse res = sdk.analysis().getAnnotationInfo()
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

**[GetAnnotationInfoResponse](../../models/operations/GetAnnotationInfoResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/GetAnnotationInfoBadRequestException            | 400                                                           | application/json                                              |
| models/errors/GetAnnotationInfoRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/GetAnnotationInfoUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/GetAnnotationInfoInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |