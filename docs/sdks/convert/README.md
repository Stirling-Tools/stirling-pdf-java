# Convert
(*convert()*)

## Overview

Document format transformation services for cross-platform compatibility and workflow integration.

This endpoint group enables transformation between various formats, supporting
diverse business workflows and system integrations for mixed document ecosystems.

Common use cases:
• Legacy system integration, document migration, and cross-platform sharing
• Archive standardization, publishing preparation, and content adaptation
• Accessibility compliance and mobile-friendly document preparation

Business applications:
• Enterprise content management, digital publishing, and educational platforms
• Legal document processing, healthcare interoperability, and government standardization

Integration scenarios:
• API-driven pipelines, automated workflow preparation, and batch conversions
• Real-time format adaptation for user requests

Target users: System integrators, content managers, digital archivists, and
organizations requiring flexible document format interoperability.


### Available Operations

* [urlToPdf](#urltopdf) - Convert a URL to a PDF
* [processPdfToXML](#processpdftoxml) - Convert PDF to XML
* [processPdfToWord](#processpdftoword) - Convert PDF to Word document
* [processPdfToRTForTXT](#processpdftortfortxt) - Convert PDF to Text or RTF format
* [processPdfToPresentation](#processpdftopresentation) - Convert PDF to Presentation format
* [pdfToPdfA](#pdftopdfa) - Convert a PDF to a PDF/A
* [processPdfToMarkdown](#processpdftomarkdown) - Convert PDF to Markdown
* [convertToImage](#converttoimage) - Convert PDF to image(s)
* [processPdfToHTML](#processpdftohtml) - Convert PDF to HTML
* [pdfToCsv](#pdftocsv) - Extracts a CSV document from a PDF
* [markdownToPdf](#markdowntopdf) - Convert a Markdown file to PDF
* [convertToPdf](#converttopdf) - Convert images to a PDF file
* [htmlToPdf](#htmltopdf) - Convert an HTML or ZIP (containing HTML and CSS) to PDF
* [processFileToPDF](#processfiletopdf) - Convert a file to a PDF using LibreOffice
* [convertEmlToPdf](#convertemltopdf) - Convert EML to PDF

## urlToPdf

This endpoint fetches content from a URL and converts it to a PDF format. Input:N/A Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="urlToPdf" method="post" path="/api/v1/convert/url/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.UrlToPdfResponse;

public class Application {

    public static void main(String[] args) throws UrlToPdfBadRequestException, UrlToPdfRequestEntityTooLargeException, UrlToPdfUnprocessableEntityException, UrlToPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        UrlToPdfResponse res = sdk.convert().urlToPdf()
                .call();

        if (res.responseStream().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [UrlToPdfRequest](../../models/shared/UrlToPdfRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[UrlToPdfResponse](../../models/operations/UrlToPdfResponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| models/errors/UrlToPdfBadRequestException            | 400                                                  | application/json                                     |
| models/errors/UrlToPdfRequestEntityTooLargeException | 413                                                  | application/json                                     |
| models/errors/UrlToPdfUnprocessableEntityException   | 422                                                  | application/json                                     |
| models/errors/UrlToPdfInternalServerError            | 500                                                  | application/json                                     |
| models/errors/APIException                           | 4XX, 5XX                                             | \*/\*                                                |

## processPdfToXML

This endpoint converts a PDF file to an XML file. Input:PDF Output:XML Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToXML" method="post" path="/api/v1/convert/pdf/xml" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ProcessPdfToXMLResponse;

public class Application {

    public static void main(String[] args) throws ProcessPdfToXMLBadRequestException, ProcessPdfToXMLRequestEntityTooLargeException, ProcessPdfToXMLUnprocessableEntityException, ProcessPdfToXMLInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToXMLResponse res = sdk.convert().processPdfToXML()
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

**[ProcessPdfToXMLResponse](../../models/operations/ProcessPdfToXMLResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/ProcessPdfToXMLBadRequestException            | 400                                                         | application/json                                            |
| models/errors/ProcessPdfToXMLRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/ProcessPdfToXMLUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/ProcessPdfToXMLInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |

## processPdfToWord

This endpoint converts a given PDF file to a Word document format. Input:PDF Output:WORD Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToWord" method="post" path="/api/v1/convert/pdf/word" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PdfToWordRequest;
import org.openapis.openapi.models.components.PdfToWordRequestOutputFormat;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.ProcessPdfToWordResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PdfToWordRequest req = PdfToWordRequest.builder()
                .outputFormat(PdfToWordRequestOutputFormat.ODT)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToWordResponse res = sdk.convert().processPdfToWord()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [PdfToWordRequest](../../models/shared/PdfToWordRequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[ProcessPdfToWordResponse](../../models/operations/ProcessPdfToWordResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## processPdfToRTForTXT

This endpoint converts a given PDF file to Text or RTF format. Input:PDF Output:TXT Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToRTForTXT" method="post" path="/api/v1/convert/pdf/text" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PdfToTextOrRTFRequest;
import org.openapis.openapi.models.components.PdfToTextOrRTFRequestOutputFormat;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.ProcessPdfToRTForTXTResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PdfToTextOrRTFRequest req = PdfToTextOrRTFRequest.builder()
                .outputFormat(PdfToTextOrRTFRequestOutputFormat.RTF)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToRTForTXTResponse res = sdk.convert().processPdfToRTForTXT()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [PdfToTextOrRTFRequest](../../models/shared/PdfToTextOrRTFRequest.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |

### Response

**[ProcessPdfToRTForTXTResponse](../../models/operations/ProcessPdfToRTForTXTResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## processPdfToPresentation

This endpoint converts a given PDF file to a Presentation format. Input:PDF Output:PPT Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToPresentation" method="post" path="/api/v1/convert/pdf/presentation" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PdfToPresentationRequest;
import org.openapis.openapi.models.components.PdfToPresentationRequestOutputFormat;
import org.openapis.openapi.models.errors.ErrorResponse;
import org.openapis.openapi.models.operations.ProcessPdfToPresentationResponse;

public class Application {

    public static void main(String[] args) throws ErrorResponse, ErrorResponse, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PdfToPresentationRequest req = PdfToPresentationRequest.builder()
                .outputFormat(PdfToPresentationRequestOutputFormat.PPTX)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToPresentationResponse res = sdk.convert().processPdfToPresentation()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [PdfToPresentationRequest](../../models/shared/PdfToPresentationRequest.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |

### Response

**[ProcessPdfToPresentationResponse](../../models/operations/ProcessPdfToPresentationResponse.md)**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| models/errors/ErrorResponse | 400, 413, 422               | application/json            |
| models/errors/ErrorResponse | 500                         | application/json            |
| models/errors/APIException  | 4XX, 5XX                    | \*/\*                       |

## pdfToPdfA

This endpoint converts a PDF file to a PDF/A file using LibreOffice. PDF/A is a format designed for long-term archiving of digital documents. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pdfToPdfA" method="post" path="/api/v1/convert/pdf/pdfa" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PdfToPdfARequest;
import org.openapis.openapi.models.components.PdfToPdfARequestOutputFormat;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.PdfToPdfAResponse;

public class Application {

    public static void main(String[] args) throws PdfToPdfABadRequestException, PdfToPdfARequestEntityTooLargeException, PdfToPdfAUnprocessableEntityException, PdfToPdfAInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PdfToPdfARequest req = PdfToPdfARequest.builder()
                .outputFormat(PdfToPdfARequestOutputFormat.PDFA)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PdfToPdfAResponse res = sdk.convert().pdfToPdfA()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [PdfToPdfARequest](../../models/shared/PdfToPdfARequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[PdfToPdfAResponse](../../models/operations/PdfToPdfAResponse.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/PdfToPdfABadRequestException            | 400                                                   | application/json                                      |
| models/errors/PdfToPdfARequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/PdfToPdfAUnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/PdfToPdfAInternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## processPdfToMarkdown

This endpoint converts a PDF file to Markdown format. Input:PDF Output:Markdown Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToMarkdown" method="post" path="/api/v1/convert/pdf/markdown" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ProcessPdfToMarkdownResponse;

public class Application {

    public static void main(String[] args) throws ProcessPdfToMarkdownBadRequestException, ProcessPdfToMarkdownRequestEntityTooLargeException, ProcessPdfToMarkdownUnprocessableEntityException, ProcessPdfToMarkdownInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToMarkdownResponse res = sdk.convert().processPdfToMarkdown()
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

**[ProcessPdfToMarkdownResponse](../../models/operations/ProcessPdfToMarkdownResponse.md)**

### Errors

| Error Type                                                       | Status Code                                                      | Content Type                                                     |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| models/errors/ProcessPdfToMarkdownBadRequestException            | 400                                                              | application/json                                                 |
| models/errors/ProcessPdfToMarkdownRequestEntityTooLargeException | 413                                                              | application/json                                                 |
| models/errors/ProcessPdfToMarkdownUnprocessableEntityException   | 422                                                              | application/json                                                 |
| models/errors/ProcessPdfToMarkdownInternalServerError            | 500                                                              | application/json                                                 |
| models/errors/APIException                                       | 4XX, 5XX                                                         | \*/\*                                                            |

## convertToImage

This endpoint converts a PDF file to image(s) with the specified image format, color type, and DPI. Users can choose to get a single image or multiple images.  Input:PDF Output:Image Type:SI-Conditional

### Example Usage

<!-- UsageSnippet language="java" operationID="convertToImage" method="post" path="/api/v1/convert/pdf/img" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.ConvertToImageRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ConvertToImageResponse;

public class Application {

    public static void main(String[] args) throws ConvertToImageBadRequestException, ConvertToImageRequestEntityTooLargeException, ConvertToImageUnprocessableEntityException, ConvertToImageInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ConvertToImageRequest req = ConvertToImageRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ConvertToImageResponse res = sdk.convert().convertToImage()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [ConvertToImageRequest](../../models/shared/ConvertToImageRequest.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |

### Response

**[ConvertToImageResponse](../../models/operations/ConvertToImageResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/ConvertToImageBadRequestException            | 400                                                        | application/json                                           |
| models/errors/ConvertToImageRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/ConvertToImageUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/ConvertToImageInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## processPdfToHTML

This endpoint converts a PDF file to HTML format. Input:PDF Output:HTML Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfToHTML" method="post" path="/api/v1/convert/pdf/html" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ProcessPdfToHTMLResponse;

public class Application {

    public static void main(String[] args) throws ProcessPdfToHTMLBadRequestException, ProcessPdfToHTMLRequestEntityTooLargeException, ProcessPdfToHTMLUnprocessableEntityException, ProcessPdfToHTMLInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfToHTMLResponse res = sdk.convert().processPdfToHTML()
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

**[ProcessPdfToHTMLResponse](../../models/operations/ProcessPdfToHTMLResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| models/errors/ProcessPdfToHTMLBadRequestException            | 400                                                          | application/json                                             |
| models/errors/ProcessPdfToHTMLRequestEntityTooLargeException | 413                                                          | application/json                                             |
| models/errors/ProcessPdfToHTMLUnprocessableEntityException   | 422                                                          | application/json                                             |
| models/errors/ProcessPdfToHTMLInternalServerError            | 500                                                          | application/json                                             |
| models/errors/APIException                                   | 4XX, 5XX                                                     | \*/\*                                                        |

## pdfToCsv

This operation takes an input PDF file and returns CSV file of whole page. Input:PDF Output:CSV Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pdfToCsv" method="post" path="/api/v1/convert/pdf/csv" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFWithPageNums;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.PdfToCsvResponse;

public class Application {

    public static void main(String[] args) throws PdfToCsvBadRequestException, PdfToCsvRequestEntityTooLargeException, PdfToCsvUnprocessableEntityException, PdfToCsvInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFWithPageNums req = PDFWithPageNums.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PdfToCsvResponse res = sdk.convert().pdfToCsv()
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

**[PdfToCsvResponse](../../models/operations/PdfToCsvResponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| models/errors/PdfToCsvBadRequestException            | 400                                                  | application/json                                     |
| models/errors/PdfToCsvRequestEntityTooLargeException | 413                                                  | application/json                                     |
| models/errors/PdfToCsvUnprocessableEntityException   | 422                                                  | application/json                                     |
| models/errors/PdfToCsvInternalServerError            | 500                                                  | application/json                                     |
| models/errors/APIException                           | 4XX, 5XX                                             | \*/\*                                                |

## markdownToPdf

This endpoint takes a Markdown file input, converts it to HTML, and then to PDF format. Input:MARKDOWN Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="markdownToPdf" method="post" path="/api/v1/convert/markdown/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.MarkdownToPdfResponse;

public class Application {

    public static void main(String[] args) throws MarkdownToPdfBadRequestException, MarkdownToPdfRequestEntityTooLargeException, MarkdownToPdfUnprocessableEntityException, MarkdownToPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        MarkdownToPdfResponse res = sdk.convert().markdownToPdf()
                .call();

    }
}
```

### Parameters

| Parameter                                         | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `request`                                         | [GeneralFile](../../models/shared/GeneralFile.md) | :heavy_check_mark:                                | The request object to use for the request.        |

### Response

**[MarkdownToPdfResponse](../../models/operations/MarkdownToPdfResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/MarkdownToPdfBadRequestException            | 400                                                       | application/json                                          |
| models/errors/MarkdownToPdfRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/MarkdownToPdfUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/MarkdownToPdfInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## convertToPdf

This endpoint converts one or more images to a PDF file. Users can specify whether to stretch the images to fit the PDF page, and whether to automatically rotate the images. Input:Image Output:PDF Type:MISO

### Example Usage

<!-- UsageSnippet language="java" operationID="convertToPdf" method="post" path="/api/v1/convert/img/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ConvertToPdfResponse;

public class Application {

    public static void main(String[] args) throws ConvertToPdfBadRequestException, ConvertToPdfRequestEntityTooLargeException, ConvertToPdfUnprocessableEntityException, ConvertToPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ConvertToPdfResponse res = sdk.convert().convertToPdf()
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [ConvertToPdfRequest](../../models/shared/ConvertToPdfRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[ConvertToPdfResponse](../../models/operations/ConvertToPdfResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/ConvertToPdfBadRequestException            | 400                                                      | application/json                                         |
| models/errors/ConvertToPdfRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/ConvertToPdfUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/ConvertToPdfInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## htmlToPdf

This endpoint takes an HTML or ZIP file input and converts it to a PDF format. Input:HTML Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="HtmlToPdf" method="post" path="/api/v1/convert/html/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.HTMLToPdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.HtmlToPdfResponse;

public class Application {

    public static void main(String[] args) throws HtmlToPdfBadRequestException, HtmlToPdfRequestEntityTooLargeException, HtmlToPdfUnprocessableEntityException, HtmlToPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        HTMLToPdfRequest req = HTMLToPdfRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        HtmlToPdfResponse res = sdk.convert().htmlToPdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [HTMLToPdfRequest](../../models/shared/HTMLToPdfRequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[HtmlToPdfResponse](../../models/operations/HtmlToPdfResponse.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/HtmlToPdfBadRequestException            | 400                                                   | application/json                                      |
| models/errors/HtmlToPdfRequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/HtmlToPdfUnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/HtmlToPdfInternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## processFileToPDF

This endpoint converts a given file to a PDF using LibreOffice API  Input:ANY Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="processFileToPDF" method="post" path="/api/v1/convert/file/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ProcessFileToPDFResponse;

public class Application {

    public static void main(String[] args) throws ProcessFileToPDFBadRequestException, ProcessFileToPDFRequestEntityTooLargeException, ProcessFileToPDFUnprocessableEntityException, ProcessFileToPDFInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ProcessFileToPDFResponse res = sdk.convert().processFileToPDF()
                .call();

    }
}
```

### Parameters

| Parameter                                         | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `request`                                         | [GeneralFile](../../models/shared/GeneralFile.md) | :heavy_check_mark:                                | The request object to use for the request.        |

### Response

**[ProcessFileToPDFResponse](../../models/operations/ProcessFileToPDFResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| models/errors/ProcessFileToPDFBadRequestException            | 400                                                          | application/json                                             |
| models/errors/ProcessFileToPDFRequestEntityTooLargeException | 413                                                          | application/json                                             |
| models/errors/ProcessFileToPDFUnprocessableEntityException   | 422                                                          | application/json                                             |
| models/errors/ProcessFileToPDFInternalServerError            | 500                                                          | application/json                                             |
| models/errors/APIException                                   | 4XX, 5XX                                                     | \*/\*                                                        |

## convertEmlToPdf

This endpoint converts EML (email) files to PDF format with extensive customization options. Features include font settings, image constraints, display modes, attachment handling, and HTML debug output. Input: EML file, Output: PDF or HTML file. Type: SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="convertEmlToPdf" method="post" path="/api/v1/convert/eml/pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.EmlToPdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ConvertEmlToPdfResponse;

public class Application {

    public static void main(String[] args) throws ConvertEmlToPdfBadRequestException, ConvertEmlToPdfRequestEntityTooLargeException, ConvertEmlToPdfUnprocessableEntityException, ConvertEmlToPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        EmlToPdfRequest req = EmlToPdfRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .includeAttachments(false)
                .maxAttachmentSizeMB(10)
                .downloadHtml(false)
                .includeAllRecipients(true)
                .build();

        ConvertEmlToPdfResponse res = sdk.convert().convertEmlToPdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [EmlToPdfRequest](../../models/shared/EmlToPdfRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[ConvertEmlToPdfResponse](../../models/operations/ConvertEmlToPdfResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/ConvertEmlToPdfBadRequestException            | 400                                                         | application/json                                            |
| models/errors/ConvertEmlToPdfRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/ConvertEmlToPdfUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/ConvertEmlToPdfInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |