# Misc
(*misc()*)

## Overview

Specialized utilities and supplementary tools for enhanced document processing workflows.

This endpoint group provides utility operations that support core document processing
tasks and address specific workflow needs in real-world scenarios.

Common use cases:
• Document optimization for bandwidth-limited environments and storage cost management
• Document repair, content extraction, and validation for quality assurance
• Accessibility improvement and custom processing for specialized needs

Business applications:
• Web publishing optimization, email attachment management, and archive efficiency
• Mobile compatibility, print production, and legacy document recovery

Operational scenarios:
• Batch processing, quality control, and performance optimization
• Troubleshooting and recovery of problematic documents

Target users: System administrators, document specialists, and organizations requiring
specialized document processing and optimization tools.


### Available Operations

* [metadata](#metadata) - Update metadata of a PDF file
* [unlockPDFForms](#unlockpdfforms) - Remove read-only property from form fields
* [extractHeader](#extractheader) - Grabs all JS from a PDF and returns a single JS file with all code
* [scannerEffect](#scannereffect) - Apply scanner effect to PDF
* [replaceAndInvertColor](#replaceandinvertcolor) - Replace-Invert Color PDF
* [repairPdf](#repairpdf) - Repair a PDF file
* [removeBlankPages](#removeblankpages) - Remove blank pages from a PDF file
* [processPdfWithOCR](#processpdfwithocr) - Process a PDF file with OCR
* [flatten](#flatten) - Flatten PDF form fields or full page
* [extractImages](#extractimages) - Extract images from a PDF file
* [extractImageScans](#extractimagescans) - Extract image scans from an input file
* [decompressPdf](#decompresspdf) - Decompress PDF streams
* [optimizePdf](#optimizepdf) - Optimize PDF file
* [autoSplitPdf](#autosplitpdf) - Auto split PDF pages into separate documents
* [extractHeader1](#extractheader1) - Extract header from PDF file
* [addStamp](#addstamp) - Add stamp to a PDF file
* [addPageNumbers](#addpagenumbers) - Add page numbers to a PDF document
* [overlayImage](#overlayimage) - Overlay image onto a PDF file
* [addAttachments](#addattachments) - Add attachments to PDF

## metadata

This endpoint allows you to update the metadata of a given PDF file. You can add, modify, or delete standard and custom metadata fields. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="metadata" method="post" path="/api/v1/misc/update-metadata" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.MetadataRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.MetadataResponse;

public class Application {

    public static void main(String[] args) throws MetadataBadRequestException, MetadataRequestEntityTooLargeException, MetadataUnprocessableEntityException, MetadataInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        MetadataRequest req = MetadataRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        MetadataResponse res = sdk.misc().metadata()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [MetadataRequest](../../models/shared/MetadataRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[MetadataResponse](../../models/operations/MetadataResponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| models/errors/MetadataBadRequestException            | 400                                                  | application/json                                     |
| models/errors/MetadataRequestEntityTooLargeException | 413                                                  | application/json                                     |
| models/errors/MetadataUnprocessableEntityException   | 422                                                  | application/json                                     |
| models/errors/MetadataInternalServerError            | 500                                                  | application/json                                     |
| models/errors/APIException                           | 4XX, 5XX                                             | \*/\*                                                |

## unlockPDFForms

Removing read-only property from form fields making them fillableInput:PDF, Output:PDF. Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="unlockPDFForms" method="post" path="/api/v1/misc/unlock-pdf-forms" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.UnlockPDFFormsResponse;

public class Application {

    public static void main(String[] args) throws UnlockPDFFormsBadRequestException, UnlockPDFFormsRequestEntityTooLargeException, UnlockPDFFormsUnprocessableEntityException, UnlockPDFFormsInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        UnlockPDFFormsResponse res = sdk.misc().unlockPDFForms()
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

**[UnlockPDFFormsResponse](../../models/operations/UnlockPDFFormsResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/UnlockPDFFormsBadRequestException            | 400                                                        | application/json                                           |
| models/errors/UnlockPDFFormsRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/UnlockPDFFormsUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/UnlockPDFFormsInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## extractHeader

desc. Input:PDF Output:JS Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="extractHeader" method="post" path="/api/v1/misc/show-javascript" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ExtractHeaderResponse;

public class Application {

    public static void main(String[] args) throws ExtractHeaderBadRequestException, ExtractHeaderRequestEntityTooLargeException, ExtractHeaderUnprocessableEntityException, ExtractHeaderInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ExtractHeaderResponse res = sdk.misc().extractHeader()
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

**[ExtractHeaderResponse](../../models/operations/ExtractHeaderResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/ExtractHeaderBadRequestException            | 400                                                       | application/json                                          |
| models/errors/ExtractHeaderRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/ExtractHeaderUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/ExtractHeaderInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## scannerEffect

Applies various effects to simulate a scanned document, including rotation, noise, and edge softening. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="scannerEffect" method="post" path="/api/v1/misc/scanner-effect" -->
```java
package hello.world;

import java.io.FileInputStream;
import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ScannerEffectResponse;
import org.openapis.openapi.utils.Utils;

public class Application {

    public static void main(String[] args) throws ScannerEffectBadRequestException, ScannerEffectRequestEntityTooLargeException, ScannerEffectUnprocessableEntityException, ScannerEffectInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ScannerEffectRequest req = ScannerEffectRequest.builder()
                .fileInput(ScannerEffectRequestFileInput.builder()
                    .fileName("example.file")
                    .content(Utils.readBytesAndClose(new FileInputStream("example.file")))
                    .build())
                .quality(Quality.HIGH)
                .rotation(Rotation.NONE)
                .colorspace(Colorspace.GRAYSCALE)
                .border(20)
                .rotate(0)
                .rotateVariance(2)
                .brightness(1f)
                .contrast(1f)
                .blur(1f)
                .noise(8f)
                .yellowish(false)
                .resolution(300)
                .advancedEnabled(false)
                .build();

        ScannerEffectResponse res = sdk.misc().scannerEffect()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [ScannerEffectRequest](../../models/shared/ScannerEffectRequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |

### Response

**[ScannerEffectResponse](../../models/operations/ScannerEffectResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/ScannerEffectBadRequestException            | 400                                                       | application/json                                          |
| models/errors/ScannerEffectRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/ScannerEffectUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/ScannerEffectInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## replaceAndInvertColor

This endpoint accepts a PDF file and option of invert all colors or replace text and background colors. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="replaceAndInvertColor" method="post" path="/api/v1/misc/replace-invert-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.ReplaceAndInvertColorRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ReplaceAndInvertColorResponse;

public class Application {

    public static void main(String[] args) throws ReplaceAndInvertColorBadRequestException, ReplaceAndInvertColorRequestEntityTooLargeException, ReplaceAndInvertColorUnprocessableEntityException, ReplaceAndInvertColorInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ReplaceAndInvertColorRequest req = ReplaceAndInvertColorRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ReplaceAndInvertColorResponse res = sdk.misc().replaceAndInvertColor()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `request`                                                                           | [ReplaceAndInvertColorRequest](../../models/shared/ReplaceAndInvertColorRequest.md) | :heavy_check_mark:                                                                  | The request object to use for the request.                                          |

### Response

**[ReplaceAndInvertColorResponse](../../models/operations/ReplaceAndInvertColorResponse.md)**

### Errors

| Error Type                                                        | Status Code                                                       | Content Type                                                      |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| models/errors/ReplaceAndInvertColorBadRequestException            | 400                                                               | application/json                                                  |
| models/errors/ReplaceAndInvertColorRequestEntityTooLargeException | 413                                                               | application/json                                                  |
| models/errors/ReplaceAndInvertColorUnprocessableEntityException   | 422                                                               | application/json                                                  |
| models/errors/ReplaceAndInvertColorInternalServerError            | 500                                                               | application/json                                                  |
| models/errors/APIException                                        | 4XX, 5XX                                                          | \*/\*                                                             |

## repairPdf

This endpoint repairs a given PDF file by running Ghostscript (primary), qpdf (fallback), or PDFBox (if no external tools available). The PDF is first saved to a temporary location, repaired, read back, and then returned as a response. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="repairPdf" method="post" path="/api/v1/misc/repair" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RepairPdfResponse;

public class Application {

    public static void main(String[] args) throws RepairPdfBadRequestException, RepairPdfRequestEntityTooLargeException, RepairPdfUnprocessableEntityException, RepairPdfInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RepairPdfResponse res = sdk.misc().repairPdf()
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

**[RepairPdfResponse](../../models/operations/RepairPdfResponse.md)**

### Errors

| Error Type                                            | Status Code                                           | Content Type                                          |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| models/errors/RepairPdfBadRequestException            | 400                                                   | application/json                                      |
| models/errors/RepairPdfRequestEntityTooLargeException | 413                                                   | application/json                                      |
| models/errors/RepairPdfUnprocessableEntityException   | 422                                                   | application/json                                      |
| models/errors/RepairPdfInternalServerError            | 500                                                   | application/json                                      |
| models/errors/APIException                            | 4XX, 5XX                                              | \*/\*                                                 |

## removeBlankPages

This endpoint removes blank pages from a given PDF file. Users can specify the threshold and white percentage to tune the detection of blank pages. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="removeBlankPages" method="post" path="/api/v1/misc/remove-blanks" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.RemoveBlankPagesRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.RemoveBlankPagesResponse;

public class Application {

    public static void main(String[] args) throws RemoveBlankPagesBadRequestException, RemoveBlankPagesRequestEntityTooLargeException, RemoveBlankPagesUnprocessableEntityException, RemoveBlankPagesInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        RemoveBlankPagesRequest req = RemoveBlankPagesRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        RemoveBlankPagesResponse res = sdk.misc().removeBlankPages()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `request`                                                                 | [RemoveBlankPagesRequest](../../models/shared/RemoveBlankPagesRequest.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |

### Response

**[RemoveBlankPagesResponse](../../models/operations/RemoveBlankPagesResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| models/errors/RemoveBlankPagesBadRequestException            | 400                                                          | application/json                                             |
| models/errors/RemoveBlankPagesRequestEntityTooLargeException | 413                                                          | application/json                                             |
| models/errors/RemoveBlankPagesUnprocessableEntityException   | 422                                                          | application/json                                             |
| models/errors/RemoveBlankPagesInternalServerError            | 500                                                          | application/json                                             |
| models/errors/APIException                                   | 4XX, 5XX                                                     | \*/\*                                                        |

## processPdfWithOCR

This endpoint processes a PDF file using OCR (Optical Character Recognition). Users can specify languages, sidecar, deskew, clean, cleanFinal, ocrType, ocrRenderType, and removeImagesAfter options. Uses OCRmyPDF if available, falls back to Tesseract. Input:PDF Output:PDF Type:SI-Conditional

### Example Usage

<!-- UsageSnippet language="java" operationID="processPdfWithOCR" method="post" path="/api/v1/misc/ocr-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.OcrType;
import org.openapis.openapi.models.components.ProcessPdfWithOcrRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ProcessPdfWithOCRResponse;

public class Application {

    public static void main(String[] args) throws ProcessPdfWithOCRBadRequestException, ProcessPdfWithOCRRequestEntityTooLargeException, ProcessPdfWithOCRUnprocessableEntityException, ProcessPdfWithOCRInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ProcessPdfWithOcrRequest req = ProcessPdfWithOcrRequest.builder()
                .languages(List.of(
                    "<value 1>",
                    "<value 2>"))
                .ocrType(OcrType.FORCE_OCR)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ProcessPdfWithOCRResponse res = sdk.misc().processPdfWithOCR()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [ProcessPdfWithOcrRequest](../../models/shared/ProcessPdfWithOcrRequest.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |

### Response

**[ProcessPdfWithOCRResponse](../../models/operations/ProcessPdfWithOCRResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/ProcessPdfWithOCRBadRequestException            | 400                                                           | application/json                                              |
| models/errors/ProcessPdfWithOCRRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/ProcessPdfWithOCRUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/ProcessPdfWithOCRInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |

## flatten

Flattening just PDF form fields or converting each page to images to make text unselectable. Input:PDF, Output:PDF. Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="flatten" method="post" path="/api/v1/misc/flatten" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.FlattenRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.FlattenResponse;

public class Application {

    public static void main(String[] args) throws FlattenBadRequestException, FlattenRequestEntityTooLargeException, FlattenUnprocessableEntityException, FlattenInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        FlattenRequest req = FlattenRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        FlattenResponse res = sdk.misc().flatten()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `request`                                               | [FlattenRequest](../../models/shared/FlattenRequest.md) | :heavy_check_mark:                                      | The request object to use for the request.              |

### Response

**[FlattenResponse](../../models/operations/FlattenResponse.md)**

### Errors

| Error Type                                          | Status Code                                         | Content Type                                        |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| models/errors/FlattenBadRequestException            | 400                                                 | application/json                                    |
| models/errors/FlattenRequestEntityTooLargeException | 413                                                 | application/json                                    |
| models/errors/FlattenUnprocessableEntityException   | 422                                                 | application/json                                    |
| models/errors/FlattenInternalServerError            | 500                                                 | application/json                                    |
| models/errors/APIException                          | 4XX, 5XX                                            | \*/\*                                               |

## extractImages

This endpoint extracts images from a given PDF file and returns them in a zip file. Users can specify the output image format. Input:PDF Output:IMAGE/ZIP Type:SIMO

### Example Usage

<!-- UsageSnippet language="java" operationID="extractImages" method="post" path="/api/v1/misc/extract-images" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFExtractImagesRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ExtractImagesResponse;

public class Application {

    public static void main(String[] args) throws ExtractImagesBadRequestException, ExtractImagesRequestEntityTooLargeException, ExtractImagesUnprocessableEntityException, ExtractImagesInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFExtractImagesRequest req = PDFExtractImagesRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ExtractImagesResponse res = sdk.misc().extractImages()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `request`                                                                 | [PDFExtractImagesRequest](../../models/shared/PDFExtractImagesRequest.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |

### Response

**[ExtractImagesResponse](../../models/operations/ExtractImagesResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/ExtractImagesBadRequestException            | 400                                                       | application/json                                          |
| models/errors/ExtractImagesRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/ExtractImagesUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/ExtractImagesInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## extractImageScans

This endpoint extracts image scans from a given file based on certain parameters. Users can specify angle threshold, tolerance, minimum area, minimum contour area, and border size. Input:PDF Output:IMAGE/ZIP Type:SIMO

### Example Usage

<!-- UsageSnippet language="java" operationID="extractImageScans" method="post" path="/api/v1/misc/extract-image-scans" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ExtractImageScansResponse;

public class Application {

    public static void main(String[] args) throws ExtractImageScansBadRequestException, ExtractImageScansRequestEntityTooLargeException, ExtractImageScansUnprocessableEntityException, ExtractImageScansInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ExtractImageScansResponse res = sdk.misc().extractImageScans()
                .call();

    }
}
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [ExtractImageScansRequest](../../models/shared/ExtractImageScansRequest.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |

### Response

**[ExtractImageScansResponse](../../models/operations/ExtractImageScansResponse.md)**

### Errors

| Error Type                                                    | Status Code                                                   | Content Type                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| models/errors/ExtractImageScansBadRequestException            | 400                                                           | application/json                                              |
| models/errors/ExtractImageScansRequestEntityTooLargeException | 413                                                           | application/json                                              |
| models/errors/ExtractImageScansUnprocessableEntityException   | 422                                                           | application/json                                              |
| models/errors/ExtractImageScansInternalServerError            | 500                                                           | application/json                                              |
| models/errors/APIException                                    | 4XX, 5XX                                                      | \*/\*                                                         |

## decompressPdf

Fully decompresses all PDF streams including text content

### Example Usage

<!-- UsageSnippet language="java" operationID="decompressPdf" method="post" path="/api/v1/misc/decompress-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.PDFFile;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.DecompressPdfResponse;

public class Application {

    public static void main(String[] args) throws DecompressPdfBadRequestException, DecompressPdfRequestEntityTooLargeException, DecompressPdfUnprocessableEntityException, DecompressPdfInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        PDFFile req = PDFFile.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        DecompressPdfResponse res = sdk.misc().decompressPdf()
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

**[DecompressPdfResponse](../../models/operations/DecompressPdfResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| models/errors/DecompressPdfBadRequestException            | 400                                                       | application/json                                          |
| models/errors/DecompressPdfRequestEntityTooLargeException | 413                                                       | application/json                                          |
| models/errors/DecompressPdfUnprocessableEntityException   | 422                                                       | application/json                                          |
| models/errors/DecompressPdfInternalServerError            | 500                                                       | application/json                                          |
| models/errors/APIException                                | 4XX, 5XX                                                  | \*/\*                                                     |

## optimizePdf

This endpoint accepts a PDF file and optimizes it based on the provided parameters. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="optimizePdf" method="post" path="/api/v1/misc/compress-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.OptimizeLevel;
import org.openapis.openapi.models.components.OptimizePdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.OptimizePdfResponse;

public class Application {

    public static void main(String[] args) throws OptimizePdfBadRequestException, OptimizePdfRequestEntityTooLargeException, OptimizePdfUnprocessableEntityException, OptimizePdfInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        OptimizePdfRequest req = OptimizePdfRequest.builder()
                .optimizeLevel(OptimizeLevel.FIVE)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        OptimizePdfResponse res = sdk.misc().optimizePdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `request`                                                       | [OptimizePdfRequest](../../models/shared/OptimizePdfRequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |

### Response

**[OptimizePdfResponse](../../models/operations/OptimizePdfResponse.md)**

### Errors

| Error Type                                              | Status Code                                             | Content Type                                            |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| models/errors/OptimizePdfBadRequestException            | 400                                                     | application/json                                        |
| models/errors/OptimizePdfRequestEntityTooLargeException | 413                                                     | application/json                                        |
| models/errors/OptimizePdfUnprocessableEntityException   | 422                                                     | application/json                                        |
| models/errors/OptimizePdfInternalServerError            | 500                                                     | application/json                                        |
| models/errors/APIException                              | 4XX, 5XX                                                | \*/\*                                                   |

## autoSplitPdf

This endpoint accepts a PDF file, scans each page for a specific QR code, and splits the document at the QR code boundaries. The output is a zip file containing each separate PDF document. Input:PDF Output:ZIP-PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="autoSplitPdf" method="post" path="/api/v1/misc/auto-split-pdf" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.AutoSplitPdfRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AutoSplitPdfResponse;

public class Application {

    public static void main(String[] args) throws AutoSplitPdfBadRequestException, AutoSplitPdfRequestEntityTooLargeException, AutoSplitPdfUnprocessableEntityException, AutoSplitPdfInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        AutoSplitPdfRequest req = AutoSplitPdfRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AutoSplitPdfResponse res = sdk.misc().autoSplitPdf()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [AutoSplitPdfRequest](../../models/shared/AutoSplitPdfRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[AutoSplitPdfResponse](../../models/operations/AutoSplitPdfResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/AutoSplitPdfBadRequestException            | 400                                                      | application/json                                         |
| models/errors/AutoSplitPdfRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/AutoSplitPdfUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/AutoSplitPdfInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## extractHeader1

This endpoint accepts a PDF file and attempts to extract its title or header based on heuristics. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="extractHeader_1" method="post" path="/api/v1/misc/auto-rename" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.ExtractHeaderRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.ExtractHeader1Response;

public class Application {

    public static void main(String[] args) throws ExtractHeader1BadRequestException, ExtractHeader1RequestEntityTooLargeException, ExtractHeader1UnprocessableEntityException, ExtractHeader1InternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        ExtractHeaderRequest req = ExtractHeaderRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        ExtractHeader1Response res = sdk.misc().extractHeader1()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [ExtractHeaderRequest](../../models/shared/ExtractHeaderRequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |

### Response

**[ExtractHeader1Response](../../models/operations/ExtractHeader1Response.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/ExtractHeader1BadRequestException            | 400                                                        | application/json                                           |
| models/errors/ExtractHeader1RequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/ExtractHeader1UnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/ExtractHeader1InternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## addStamp

This endpoint adds a stamp to a given PDF file. Users can specify the stamp type (text or image), rotation, opacity, width spacer, and height spacer. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="addStamp" method="post" path="/api/v1/misc/add-stamp" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AddStampResponse;

public class Application {

    public static void main(String[] args) throws AddStampBadRequestException, AddStampRequestEntityTooLargeException, AddStampUnprocessableEntityException, AddStampInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        AddStampRequest req = AddStampRequest.builder()
                .stampType(StampType.TEXT)
                .position(AddStampRequestPosition.FIVE)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AddStampResponse res = sdk.misc().addStamp()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [AddStampRequest](../../models/shared/AddStampRequest.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[AddStampResponse](../../models/operations/AddStampResponse.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| models/errors/AddStampBadRequestException            | 400                                                  | application/json                                     |
| models/errors/AddStampRequestEntityTooLargeException | 413                                                  | application/json                                     |
| models/errors/AddStampUnprocessableEntityException   | 422                                                  | application/json                                     |
| models/errors/AddStampInternalServerError            | 500                                                  | application/json                                     |
| models/errors/APIException                           | 4XX, 5XX                                             | \*/\*                                                |

## addPageNumbers

This operation takes an input PDF file and adds page numbers to it. Input:PDF Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="addPageNumbers" method="post" path="/api/v1/misc/add-page-numbers" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.*;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AddPageNumbersResponse;

public class Application {

    public static void main(String[] args) throws AddPageNumbersBadRequestException, AddPageNumbersRequestEntityTooLargeException, AddPageNumbersUnprocessableEntityException, AddPageNumbersInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        AddPageNumbersRequest req = AddPageNumbersRequest.builder()
                .fontType(FontType.TIMES)
                .position(AddPageNumbersRequestPosition.EIGHT)
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .customText("Page {n} of {total}")
                .build();

        AddPageNumbersResponse res = sdk.misc().addPageNumbers()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `request`                                                             | [AddPageNumbersRequest](../../models/shared/AddPageNumbersRequest.md) | :heavy_check_mark:                                                    | The request object to use for the request.                            |

### Response

**[AddPageNumbersResponse](../../models/operations/AddPageNumbersResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/AddPageNumbersBadRequestException            | 400                                                        | application/json                                           |
| models/errors/AddPageNumbersRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/AddPageNumbersUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/AddPageNumbersInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |

## overlayImage

This endpoint overlays an image onto a PDF file at the specified coordinates. The image can be overlaid on every page of the PDF if specified.  Input:PDF/IMAGE Output:PDF Type:SISO

### Example Usage

<!-- UsageSnippet language="java" operationID="overlayImage" method="post" path="/api/v1/misc/add-image" -->
```java
package hello.world;

import java.io.FileInputStream;
import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.ImageFile;
import org.openapis.openapi.models.components.OverlayImageRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.OverlayImageResponse;
import org.openapis.openapi.utils.Utils;

public class Application {

    public static void main(String[] args) throws OverlayImageBadRequestException, OverlayImageRequestEntityTooLargeException, OverlayImageUnprocessableEntityException, OverlayImageInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        OverlayImageRequest req = OverlayImageRequest.builder()
                .imageFile(ImageFile.builder()
                    .fileName("example.file")
                    .content(Utils.readBytesAndClose(new FileInputStream("example.file")))
                    .build())
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        OverlayImageResponse res = sdk.misc().overlayImage()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                         | Type                                                              | Required                                                          | Description                                                       |
| ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| `request`                                                         | [OverlayImageRequest](../../models/shared/OverlayImageRequest.md) | :heavy_check_mark:                                                | The request object to use for the request.                        |

### Response

**[OverlayImageResponse](../../models/operations/OverlayImageResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| models/errors/OverlayImageBadRequestException            | 400                                                      | application/json                                         |
| models/errors/OverlayImageRequestEntityTooLargeException | 413                                                      | application/json                                         |
| models/errors/OverlayImageUnprocessableEntityException   | 422                                                      | application/json                                         |
| models/errors/OverlayImageInternalServerError            | 500                                                      | application/json                                         |
| models/errors/APIException                               | 4XX, 5XX                                                 | \*/\*                                                    |

## addAttachments

This endpoint adds attachments to a PDF. Input:PDF, Output:PDF Type:MISO

### Example Usage

<!-- UsageSnippet language="java" operationID="addAttachments" method="post" path="/api/v1/misc/add-attachments" -->
```java
package hello.world;

import java.lang.Exception;
import java.util.List;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.components.AddAttachmentRequest;
import org.openapis.openapi.models.errors.*;
import org.openapis.openapi.models.operations.AddAttachmentsResponse;

public class Application {

    public static void main(String[] args) throws AddAttachmentsBadRequestException, AddAttachmentsRequestEntityTooLargeException, AddAttachmentsUnprocessableEntityException, AddAttachmentsInternalServerError, Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        AddAttachmentRequest req = AddAttachmentRequest.builder()
                .attachments(List.of())
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        AddAttachmentsResponse res = sdk.misc().addAttachments()
                .request(req)
                .call();

    }
}
```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `request`                                                           | [AddAttachmentRequest](../../models/shared/AddAttachmentRequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |

### Response

**[AddAttachmentsResponse](../../models/operations/AddAttachmentsResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| models/errors/AddAttachmentsBadRequestException            | 400                                                        | application/json                                           |
| models/errors/AddAttachmentsRequestEntityTooLargeException | 413                                                        | application/json                                           |
| models/errors/AddAttachmentsUnprocessableEntityException   | 422                                                        | application/json                                           |
| models/errors/AddAttachmentsInternalServerError            | 500                                                        | application/json                                           |
| models/errors/APIException                                 | 4XX, 5XX                                                   | \*/\*                                                      |