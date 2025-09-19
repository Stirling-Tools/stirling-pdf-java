# Filter
(*filter()*)

## Overview

Document content filtering and search operations for information discovery and organization.

This endpoint group enables intelligent content discovery and organization within
document collections for content-based processing and information extraction.

Common use cases:
• Legal discovery, research organization, and compliance auditing
• Content moderation, academic research, and business intelligence
• Quality assurance and content validation workflows

Business applications:
• Contract analysis, financial review, and healthcare records organization
• Government processing, educational curation, and IP protection

Workflow scenarios:
• Large-scale processing, automated classification, and information extraction
• Document preparation for further processing or analysis

Target users: Legal professionals, researchers, compliance officers, and
organizations requiring intelligent document content discovery and organization.


### Available Operations

* [pageSize](#pagesize) - Checks if a PDF is of a certain size
* [pageRotation](#pagerotation) - Checks if a PDF is of a certain rotation
* [pageCount](#pagecount) - Checks if a PDF is greater, less or equal to a setPageCount
* [fileSize](#filesize) - Checks if a PDF is a set file size
* [containsText](#containstext) - Checks if a PDF contains set text, returns true if does
* [containsImage](#containsimage) - Checks if a PDF contains an image

## pageSize

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pageSize" method="post" path="/api/v1/filter/filter-page-size" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PageSizeRequest;
import org.openapis.openapi.models.components.PageSizeRequestComparator;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.PageSizeResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PageSizeRequest req = PageSizeRequest.builder()
                .comparator(PageSizeRequestComparator.EQUAL)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PageSizeResponse res = sdk.filter().pageSize()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [PageSizeRequest](../../models/shared/PageSizeRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[PageSizeResponse](../../models/operations/PageSizeResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## pageRotation

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pageRotation" method="post" path="/api/v1/filter/filter-page-rotation" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PageRotationRequest;
import org.openapis.openapi.models.components.PageRotationRequestComparator;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.PageRotationResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PageRotationRequest req = PageRotationRequest.builder()
                .comparator(PageRotationRequestComparator.EQUAL)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PageRotationResponse res = sdk.filter().pageRotation()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [PageRotationRequest](../../models/shared/PageRotationRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[PageRotationResponse](../../models/operations/PageRotationResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## pageCount

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pageCount" method="post" path="/api/v1/filter/filter-page-count" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFComparisonAndCount;
import org.openapis.openapi.models.components.PDFComparisonAndCountComparator;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.PageCountResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFComparisonAndCount req = PDFComparisonAndCount.builder()
                .comparator(PDFComparisonAndCountComparator.GREATER)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PageCountResponse res = sdk.filter().pageCount()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [PDFComparisonAndCount](../../models/shared/PDFComparisonAndCount.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |

### Response

**[PageCountResponse](../../models/operations/PageCountResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## fileSize

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="fileSize" method="post" path="/api/v1/filter/filter-file-size" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.FileSizeRequest;
import org.openapis.openapi.models.components.FileSizeRequestComparator;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.FileSizeResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        FileSizeRequest req = FileSizeRequest.builder()
                .comparator(FileSizeRequestComparator.GREATER)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        FileSizeResponse res = sdk.filter().fileSize()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [FileSizeRequest](../../models/shared/FileSizeRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[FileSizeResponse](../../models/operations/FileSizeResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## containsText

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="containsText" method="post" path="/api/v1/filter/filter-contains-text" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.ContainsTextRequest;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.ContainsTextResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ContainsTextRequest req = ContainsTextRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ContainsTextResponse res = sdk.filter().containsText()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [ContainsTextRequest](../../models/shared/ContainsTextRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[ContainsTextResponse](../../models/operations/ContainsTextResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## containsImage

Input:PDF Output:Boolean Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="containsImage" method="post" path="/api/v1/filter/filter-contains-image" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFWithPageNums;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.ContainsImageResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFWithPageNums req = PDFWithPageNums.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ContainsImageResponse res = sdk.filter().containsImage()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [PDFWithPageNums](../../models/shared/PDFWithPageNums.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[ContainsImageResponse](../../models/operations/ContainsImageResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |