# Pipeline
(*pipeline()*)

## Overview

Automated document processing workflows for complex multi-stage business operations.

This endpoint group enables organizations to create sophisticated document processing
workflows that combine multiple operations into streamlined, repeatable processes.

Common use cases:
• Invoice processing, legal document review, and healthcare records standardization
• Government processing, educational content preparation, and publishing automation
• Contract lifecycle management and approval processes

Business applications:
• Automated compliance reporting, large-scale migration, and quality assurance
• Archive preparation, content delivery, and document approval workflows

Operational scenarios:
• Scheduled batch processing and event-driven document processing
• Multi-department coordination and business system integration

Target users: Business process managers, IT automation specialists, and organizations
requiring consistent, repeatable document processing workflows.


### Available Operations

* [handleData](#handledata) - Execute automated PDF processing pipeline

## handleData

This endpoint processes multiple PDF files through a configurable pipeline of operations. Users provide files and a JSON configuration defining the sequence of operations to perform. Input:PDF Output:PDF/ZIP Type:MIMO

### Example Usage

<!-- UsageSnippet language="java" operationID="handleData" method="post" path="/api/v1/pipeline/handleData" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.HandleDataRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.HandleDataResponse;

public class Application {

    public static void main(String[] args) throws HandleDataBadRequestException, HandleDataRequestEntityTooLargeException, HandleDataUnprocessableEntityException, HandleDataInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        HandleDataRequest req = HandleDataRequest.builder()
                .fileInput(List.of())
                .json("{\\"name\\":\\"Prepare-pdfs-for-email\\",\\"pipeline\\":[{\\"operation\\":\\"/api/v1/misc/repair\\",\\"parameters\\":{}},{\\"operation\\":\\"/api/v1/security/sanitize-pdf\\",\\"parameters\\":{\\"removeJavaScript\\":true,\\"removeEmbeddedFiles\\":false}},{\\"operation\\":\\"/api/v1/misc/compress-pdf\\",\\"parameters\\":{\\"optimizeLevel\\":2}}]}")
                .build();

        HandleDataResponse res = sdk.pipeline().handleData()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                     | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `request`                                                     | [HandleDataRequest](../../models/shared/HandleDataRequest.md) | :heavy_check_mark:                                            | The request object to use for the request.                    |

### Response

**[HandleDataResponse](../../models/operations/HandleDataResponse.md)**

### Errors

| Error Type                                             | Status Code                                            | Content Type                                           |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| models/errors/HandleDataBadRequestException            | 400                                                    | application/json                                       |
| models/errors/HandleDataRequestEntityTooLargeException | 413                                                    | application/json                                       |
| models/errors/HandleDataUnprocessableEntityException   | 422                                                    | application/json                                       |
| models/errors/HandleDataInternalServerError            | 500                                                    | application/json                                       |
| models/errors/APIException                             | 4XX, 5XX                                               | \*/\*                                                  |