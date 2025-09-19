# General
(*general()*)

## Overview

Core PDF processing operations for fundamental document manipulation workflows.

This endpoint group provides essential PDF functionality that forms the foundation
of most document processing workflows across various industries.

Common use cases:
• Document preparation for archival systems and content organization
• File preparation for distribution, accessibility compliance, and batch processing
• Document consolidation for reporting and legal compliance workflows

Typical applications:
• Content management, publishing workflows, and educational content distribution
• Business process automation and archive management

Target users: Content managers, document processors, and organizations requiring
reliable foundational PDF manipulation capabilities.


### Available Operations

* [splitPdf](#splitpdf) - Split PDF pages into smaller sections
* [splitPdf1](#splitpdf1) - Split PDFs by Chapters
* [splitPdf2](#splitpdf2) - Split a PDF file into separate documents
* [autoSplitPdf1](#autosplitpdf1) - Auto split PDF pages into separate documents based on size or count
* [scalePages](#scalepages) - Change the size of a PDF page/document
* [rotatePDF](#rotatepdf) - Rotate a PDF file
* [deletePages](#deletepages) - Remove pages from a PDF file
* [removeImages](#removeimages) - Remove images from file to reduce the file size.
* [rearrangePages](#rearrangepages) - Rearrange pages in a PDF file
* [pdfToSinglePage](#pdftosinglepage) - Convert a multi-page PDF into a single long page PDF
* [overlayPdfs](#overlaypdfs) - Overlay PDF files in various modes
* [mergeMultiplePagesIntoOne](#mergemultiplepagesintoone) - Merge multiple pages of a PDF document into a single page
* [mergePdfs](#mergepdfs) - Merge multiple PDF files into one
* [extractBookmarks](#extractbookmarks) - Extract PDF Bookmarks
* [editTableOfContents](#edittableofcontents) - Edit Table of Contents
* [cropPdf](#croppdf) - Crops a PDF document
* [createBookletImposition](#createbookletimposition) - Create a booklet with proper page imposition

## splitPdf

Split each page of a PDF into smaller sections based on the user's choice (halves, thirds, quarters, etc.), both vertically and horizontally. Input:PDF Output:ZIP-PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="splitPdf" method="post" path="/api/v1/general/split-pdf-by-sections" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SplitPdfBySectionsRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SplitPdfResponse;

public class Application {

    public static void main(String[] args) throws SplitPdfBadRequestException, SplitPdfRequestEntityTooLargeException, SplitPdfUnprocessableEntityException, SplitPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SplitPdfBySectionsRequest req = SplitPdfBySectionsRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        SplitPdfResponse res = sdk.general().splitPdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [SplitPdfBySectionsRequest](../../models/shared/SplitPdfBySectionsRequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |

### Response

**[SplitPdfResponse](../../models/operations/SplitPdfResponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| models/errors/SplitPdfBadRequestException            | 400                                                  | application/json                                     |
| models/errors/SplitPdfRequestEntityTooLargeException | 413                                                  | application/json                                     |
| models/errors/SplitPdfUnprocessableEntityException   | 422                                                  | application/json                                     |
| models/errors/SplitPdfInternalServerError            | 500                                                  | application/json                                     |
| models/errors/APIException                           | 4XX, 5XX                                             | \*/\*                                                |

## splitPdf1

Splits a PDF into chapters and returns a ZIP file.

### Example Usage

<!-- UsageSnippet language="java" operationID="splitPdf_1" method="post" path="/api/v1/general/split-pdf-by-chapters" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SplitPdfByChaptersRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SplitPdf1Response;

public class Application {

    public static void main(String[] args) throws SplitPdf1BadRequestException, SplitPdf1RequestEntityTooLargeException, SplitPdf1UnprocessableEntityException, SplitPdf1InternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SplitPdfByChaptersRequest req = SplitPdfByChaptersRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        SplitPdf1Response res = sdk.general().splitPdf1()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [SplitPdfByChaptersRequest](../../models/shared/SplitPdfByChaptersRequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |

### Response

**[SplitPdf1Response](../../models/operations/SplitPdf1Response.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/SplitPdf1BadRequestException            | 400                                                   | application/json                                      |
| models/errors/SplitPdf1RequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/SplitPdf1UnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/SplitPdf1InternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## splitPdf2

This endpoint splits a given PDF file into separate documents based on the specified page numbers or ranges. Users can specify pages using individual numbers, ranges, or 'all' for every page. Input:PDF Output:PDF Type:SIMO

### Example Usage

<!-- UsageSnippet language="java" operationID="splitPdf_2" method="post" path="/api/v1/general/split-pages" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFWithPageNums;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.SplitPdf2Response;

public class Application {

    public static void main(String[] args) throws SplitPdf2BadRequestException, SplitPdf2RequestEntityTooLargeException, SplitPdf2UnprocessableEntityException, SplitPdf2InternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFWithPageNums req = PDFWithPageNums.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        SplitPdf2Response res = sdk.general().splitPdf2()
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

**[SplitPdf2Response](../../models/operations/SplitPdf2Response.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/SplitPdf2BadRequestException            | 400                                                   | application/json                                      |
| models/errors/SplitPdf2RequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/SplitPdf2UnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/SplitPdf2InternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## autoSplitPdf1

split PDF into multiple paged documents based on size/count, ie if 20 pages and split into 5, it does 5 documents each 4 pages
 if 10MB and each page is 1MB and you enter 2MB then 5 docs each 2MB (rounded so that it accepts 1.9MB but not 2.1MB) Input:PDF Output:ZIP-PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="autoSplitPdf_1" method="post" path="/api/v1/general/split-by-size-or-count" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SplitPdfBySizeOrCountRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AutoSplitPdf1Response;

public class Application {

    public static void main(String[] args) throws AutoSplitPdf1BadRequestException, AutoSplitPdf1RequestEntityTooLargeException, AutoSplitPdf1UnprocessableEntityException, AutoSplitPdf1InternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        SplitPdfBySizeOrCountRequest req = SplitPdfBySizeOrCountRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AutoSplitPdf1Response res = sdk.general().autoSplitPdf1()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `request`                                                                           | [SplitPdfBySizeOrCountRequest](../../models/shared/SplitPdfBySizeOrCountRequest.md) | :heavy_check_mark:                                                                  | The request object to use for the request.                                          |

### Response

**[AutoSplitPdf1Response](../../models/operations/AutoSplitPdf1Response.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/AutoSplitPdf1BadRequestException            | 400                                                       | application/json                                          |
| models/errors/AutoSplitPdf1RequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/AutoSplitPdf1UnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/AutoSplitPdf1InternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## scalePages

This operation takes an input PDF file and the size to scale the pages to in the output PDF file. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="scalePages" method="post" path="/api/v1/general/scale-pages" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PageSize;
import org.openapis.openapi.models.components.ScalePagesRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ScalePagesResponse;

public class Application {

    public static void main(String[] args) throws ScalePagesBadRequestException, ScalePagesRequestEntityTooLargeException, ScalePagesUnprocessableEntityException, ScalePagesInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ScalePagesRequest req = ScalePagesRequest.builder()
                .pageSize(PageSize.LEGAL)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ScalePagesResponse res = sdk.general().scalePages()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                     | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `request`                                                     | [ScalePagesRequest](../../models/shared/ScalePagesRequest.md) | :heavy_check_mark:                                            | The request object to use for the request.                    |

### Response

**[ScalePagesResponse](../../models/operations/ScalePagesResponse.md)**

### Errors

| Error Type                                             | Status Code                                            | Content Type                                           |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| models/errors/ScalePagesBadRequestException            | 400                                                    | application/json                                       |
| models/errors/ScalePagesRequestEntityTooLargeException | 413                                                    | application/json                                       |
| models/errors/ScalePagesUnprocessableEntityException   | 422                                                    | application/json                                       |
| models/errors/ScalePagesInternalServerError            | 500                                                    | application/json                                       |
| models/errors/APIException                             | 4XX, 5XX                                               | \*/\*                                                  |

## rotatePDF

This endpoint rotates a given PDF file by a specified angle. The angle must be a multiple of 90. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="rotatePDF" method="post" path="/api/v1/general/rotate-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.Angle;
import org.openapis.openapi.models.components.RotatePDFRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RotatePDFResponse;

public class Application {

    public static void main(String[] args) throws RotatePDFBadRequestException, RotatePDFRequestEntityTooLargeException, RotatePDFUnprocessableEntityException, RotatePDFInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        RotatePDFRequest req = RotatePDFRequest.builder()
                .angle(Angle.NINETY)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RotatePDFResponse res = sdk.general().rotatePDF()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [RotatePDFRequest](../../models/shared/RotatePDFRequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[RotatePDFResponse](../../models/operations/RotatePDFResponse.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/RotatePDFBadRequestException            | 400                                                   | application/json                                      |
| models/errors/RotatePDFRequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/RotatePDFUnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/RotatePDFInternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## deletePages

This endpoint removes specified pages from a given PDF file. Users can provide a comma-separated list of page numbers or ranges to delete. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="deletePages" method="post" path="/api/v1/general/remove-pages" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFWithPageNums;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DeletePagesResponse;

public class Application {

    public static void main(String[] args) throws DeletePagesBadRequestException, DeletePagesRequestEntityTooLargeException, DeletePagesUnprocessableEntityException, DeletePagesInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFWithPageNums req = PDFWithPageNums.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        DeletePagesResponse res = sdk.general().deletePages()
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

**[DeletePagesResponse](../../models/operations/DeletePagesResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/DeletePagesBadRequestException            | 400                                                     | application/json                                        |
| models/errors/DeletePagesRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/DeletePagesUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/DeletePagesInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |

## removeImages

This endpoint remove images from file to reduce the file size.Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="removeImages" method="post" path="/api/v1/general/remove-image-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RemoveImagesResponse;

public class Application {

    public static void main(String[] args) throws RemoveImagesBadRequestException, RemoveImagesRequestEntityTooLargeException, RemoveImagesUnprocessableEntityException, RemoveImagesInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RemoveImagesResponse res = sdk.general().removeImages()
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

**[RemoveImagesResponse](../../models/operations/RemoveImagesResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/RemoveImagesBadRequestException            | 400                                                      | application/json                                         |
| models/errors/RemoveImagesRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/RemoveImagesUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/RemoveImagesInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## rearrangePages

This endpoint rearranges pages in a given PDF file based on the specified page order or custom mode. Users can provide a page order as a comma-separated list of page numbers or page ranges, or a custom mode. Input:PDF Output:PDF

### Example Usage

<!-- UsageSnippet language="java" operationID="rearrangePages" method="post" path="/api/v1/general/rearrange-pages" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.RearrangePagesRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RearrangePagesResponse;

public class Application {

    public static void main(String[] args) throws RearrangePagesBadRequestException, RearrangePagesRequestEntityTooLargeException, RearrangePagesUnprocessableEntityException, RearrangePagesInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        RearrangePagesRequest req = RearrangePagesRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RearrangePagesResponse res = sdk.general().rearrangePages()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [RearrangePagesRequest](../../models/shared/RearrangePagesRequest.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |

### Response

**[RearrangePagesResponse](../../models/operations/RearrangePagesResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/RearrangePagesBadRequestException            | 400                                                        | application/json                                           |
| models/errors/RearrangePagesRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/RearrangePagesUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/RearrangePagesInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## pdfToSinglePage

This endpoint converts a multi-page PDF document into a single paged PDF document. The width of the single page will be same as the input's width, but the height will be the sum of all the pages' heights. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="pdfToSinglePage" method="post" path="/api/v1/general/pdf-to-single-page" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.PdfToSinglePageResponse;

public class Application {

    public static void main(String[] args) throws PdfToSinglePageBadRequestException, PdfToSinglePageRequestEntityTooLargeException, PdfToSinglePageUnprocessableEntityException, PdfToSinglePageInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        PdfToSinglePageResponse res = sdk.general().pdfToSinglePage()
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

**[PdfToSinglePageResponse](../../models/operations/PdfToSinglePageResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| models/errors/PdfToSinglePageBadRequestException            | 400                                                         | application/json                                            |
| models/errors/PdfToSinglePageRequestEntityTooLargeException | 413                                                         | application/json                                            |
| models/errors/PdfToSinglePageUnprocessableEntityException   | 422                                                         | application/json                                            |
| models/errors/PdfToSinglePageInternalServerError            | 500                                                         | application/json                                            |
| models/errors/APIException                                  | 4XX, 5XX                                                    | \*/\*                                                       |

## overlayPdfs

Overlay PDF files onto a base PDF with different modes: Sequential, Interleaved, or Fixed Repeat. Input:PDF Output:PDF Type:MIMO

### Example Usage

<!-- UsageSnippet language="java" operationID="overlayPdfs" method="post" path="/api/v1/general/overlay-pdfs" -->
```java
package hello.world;

import java.io.FileInputStream;
import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.OverlayPdfsResponse;
import org.openapis.openapi.utils.Utils;

public class Application {

    public static void main(String[] args) throws OverlayPdfsBadRequestException, OverlayPdfsRequestEntityTooLargeException, OverlayPdfsUnprocessableEntityException, OverlayPdfsInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        OverlayPdfsRequest req = OverlayPdfsRequest.builder()
                .overlayFiles(List.of(
                    OverlayFile.builder()
                        .fileName("example.file")
                        .content(Utils.readBytesAndClose(new FileInputStream("example.file")))
                        .build()))
                .overlayMode(OverlayMode.SEQUENTIAL_OVERLAY)
                .overlayPosition(543.74)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        OverlayPdfsResponse res = sdk.general().overlayPdfs()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | [OverlayPdfsRequest](../../models/shared/OverlayPdfsRequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[OverlayPdfsResponse](../../models/operations/OverlayPdfsResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/OverlayPdfsBadRequestException            | 400                                                     | application/json                                        |
| models/errors/OverlayPdfsRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/OverlayPdfsUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/OverlayPdfsInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |

## mergeMultiplePagesIntoOne

This operation takes an input PDF file and the number of pages to merge into a single sheet in the output PDF file. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="mergeMultiplePagesIntoOne" method="post" path="/api/v1/general/multi-page-layout" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.MergeMultiplePagesRequest;
import org.openapis.openapi.models.components.MergeMultiplePagesRequestPagesPerSheet;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.MergeMultiplePagesIntoOneResponse;

public class Application {

    public static void main(String[] args) throws MergeMultiplePagesIntoOneBadRequestException, MergeMultiplePagesIntoOneRequestEntityTooLargeException, MergeMultiplePagesIntoOneUnprocessableEntityException, MergeMultiplePagesIntoOneInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        MergeMultiplePagesRequest req = MergeMultiplePagesRequest.builder()
                .pagesPerSheet(MergeMultiplePagesRequestPagesPerSheet.TWO)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        MergeMultiplePagesIntoOneResponse res = sdk.general().mergeMultiplePagesIntoOne()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [MergeMultiplePagesRequest](../../models/shared/MergeMultiplePagesRequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |

### Response

**[MergeMultiplePagesIntoOneResponse](../../models/operations/MergeMultiplePagesIntoOneResponse.md)**

### Errors

| Error Type                                                            | Status Code                                                           | Content Type                                                          |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| models/errors/MergeMultiplePagesIntoOneBadRequestException            | 400                                                                   | application/json                                                      |
| models/errors/MergeMultiplePagesIntoOneRequestEntityTooLargeException | 413                                                                   | application/json                                                      |
| models/errors/MergeMultiplePagesIntoOneUnprocessableEntityException   | 422                                                                   | application/json                                                      |
| models/errors/MergeMultiplePagesIntoOneInternalServerError            | 500                                                                   | application/json                                                      |
| models/errors/APIException                                            | 4XX, 5XX                                                              | \*/\*                                                                 |

## mergePdfs

This endpoint merges multiple PDF files into a single PDF file. The merged file will contain all pages from the input files in the order they were provided. Input:PDF Output:PDF Type:MISO

### Example Usage

<!-- UsageSnippet language="java" operationID="mergePdfs" method="post" path="/api/v1/general/merge-pdfs" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.MergePdfsResponse;

public class Application {

    public static void main(String[] args) throws MergePdfsBadRequestException, MergePdfsRequestEntityTooLargeException, MergePdfsUnprocessableEntityException, MergePdfsInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        MergePdfsResponse res = sdk.general().mergePdfs()
                .call();

    }
}
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [MergePdfsRequest](../../models/shared/MergePdfsRequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[MergePdfsResponse](../../models/operations/MergePdfsResponse.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/MergePdfsBadRequestException            | 400                                                   | application/json                                      |
| models/errors/MergePdfsRequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/MergePdfsUnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/MergePdfsInternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## extractBookmarks

Extracts bookmarks/table of contents from a PDF document as JSON.

### Example Usage

<!-- UsageSnippet language="java" operationID="extractBookmarks" method="post" path="/api/v1/general/extract-bookmarks" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ExtractBookmarksResponse;

public class Application {

    public static void main(String[] args) throws ExtractBookmarksBadRequestException, ExtractBookmarksRequestEntityTooLargeException, ExtractBookmarksUnprocessableEntityException, ExtractBookmarksInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        ExtractBookmarksResponse res = sdk.general().extractBookmarks()
                .call();

    }
}
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [ExtractBookmarksRequest](../../models/operations/ExtractBookmarksRequest.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |

### Response

**[ExtractBookmarksResponse](../../models/operations/ExtractBookmarksResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| models/errors/ExtractBookmarksBadRequestException            | 400                                                          | application/json                                             |
| models/errors/ExtractBookmarksRequestEntityTooLargeException | 413                                                          | application/json                                             |
| models/errors/ExtractBookmarksUnprocessableEntityException   | 422                                                          | application/json                                             |
| models/errors/ExtractBookmarksInternalServerError            | 500                                                          | application/json                                             |
| models/errors/APIException                                   | 4XX, 5XX                                                     | \*/\*                                                        |

## editTableOfContents

Add or edit bookmarks/table of contents in a PDF document.

### Example Usage

<!-- UsageSnippet language="java" operationID="editTableOfContents" method="post" path="/api/v1/general/edit-table-of-contents" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.EditTableOfContentsRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.EditTableOfContentsResponse;

public class Application {

    public static void main(String[] args) throws EditTableOfContentsBadRequestException, EditTableOfContentsRequestEntityTooLargeException, EditTableOfContentsUnprocessableEntityException, EditTableOfContentsInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        EditTableOfContentsRequest req = EditTableOfContentsRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .bookmarkData("[{\\"title\\":\\"Chapter 1\\",\\"pageNumber\\":1,\\"children\\":[{\\"title\\":\\"Section 1.1\\",\\"pageNumber\\":2}]}]")
                .replaceExisting(true)
                .build();

        EditTableOfContentsResponse res = sdk.general().editTableOfContents()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `request`                                                                       | [EditTableOfContentsRequest](../../models/shared/EditTableOfContentsRequest.md) | :heavy_check_mark:                                                              | The request object to use for the request.                                      |

### Response

**[EditTableOfContentsResponse](../../models/operations/EditTableOfContentsResponse.md)**

### Errors

| Error Type                                                      | Status Code                                                     | Content Type                                                    |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| models/errors/EditTableOfContentsBadRequestException            | 400                                                             | application/json                                                |
| models/errors/EditTableOfContentsRequestEntityTooLargeException | 413                                                             | application/json                                                |
| models/errors/EditTableOfContentsUnprocessableEntityException   | 422                                                             | application/json                                                |
| models/errors/EditTableOfContentsInternalServerError            | 500                                                             | application/json                                                |
| models/errors/APIException                                      | 4XX, 5XX                                                        | \*/\*                                                           |

## cropPdf

This operation takes an input PDF file and crops it according to the given coordinates. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="cropPdf" method="post" path="/api/v1/general/crop" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.CropPdfForm;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.CropPdfResponse;

public class Application {

    public static void main(String[] args) throws CropPdfBadRequestException, CropPdfRequestEntityTooLargeException, CropPdfUnprocessableEntityException, CropPdfInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        CropPdfForm req = CropPdfForm.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        CropPdfResponse res = sdk.general().cropPdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                         | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `request`                                         | [CropPdfForm](../../models/shared/CropPdfForm.md) | :heavy_check_mark:                                | The request object to use for the request.        |

### Response

**[CropPdfResponse](../../models/operations/CropPdfResponse.md)**

### Errors

| Error Type                                          | Status Code                                         | Content Type                                        |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| models/errors/CropPdfBadRequestException            | 400                                                 | application/json                                    |
| models/errors/CropPdfRequestEntityTooLargeException | 413                                                 | application/json                                    |
| models/errors/CropPdfUnprocessableEntityException   | 422                                                 | application/json                                    |
| models/errors/CropPdfInternalServerError            | 500                                                 | application/json                                    |
| models/errors/APIException                          | 4XX, 5XX                                            | \*/\*                                               |

## createBookletImposition

This operation combines page reordering for booklet printing with multi-page layout. It rearranges pages in the correct order for booklet printing and places multiple pages on each sheet for proper folding and binding. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="createBookletImposition" method="post" path="/api/v1/general/booklet-imposition" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.BookletImpositionRequest;
import org.openapis.openapi.models.components.BookletImpositionRequestPagesPerSheet;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.CreateBookletImpositionResponse;

public class Application {

    public static void main(String[] args) throws CreateBookletImpositionBadRequestException, CreateBookletImpositionRequestEntityTooLargeException, CreateBookletImpositionUnprocessableEntityException, CreateBookletImpositionInternalServerError, Exception {

        Stirling sdk = Stirling.builder()
            .build();

        BookletImpositionRequest req = BookletImpositionRequest.builder()
                .pagesPerSheet(BookletImpositionRequestPagesPerSheet.TWO)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        CreateBookletImpositionResponse res = sdk.general().createBookletImposition()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [BookletImpositionRequest](../../models/shared/BookletImpositionRequest.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |

### Response

**[CreateBookletImpositionResponse](../../models/operations/CreateBookletImpositionResponse.md)**

### Errors

| Error Type                                                          | Status Code                                                         | Content Type                                                        |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| models/errors/CreateBookletImpositionBadRequestException            | 400                                                                 | application/json                                                    |
| models/errors/CreateBookletImpositionRequestEntityTooLargeException | 413                                                                 | application/json                                                    |
| models/errors/CreateBookletImpositionUnprocessableEntityException   | 422                                                                 | application/json                                                    |
| models/errors/CreateBookletImpositionInternalServerError            | 500                                                                 | application/json                                                    |
| models/errors/APIException                                          | 4XX, 5XX                                                            | \*/\*                                                               |