# openapi

Developer-friendly & type-safe Java SDK specifically catered to leverage *openapi* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=openapi&utm_campaign=java"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20Speakeasy-212015?style=for-the-badge&logoColor=FBE331&logo=speakeasy&labelColor=545454" /></a>
    <a href="https://mit-license.org/">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/stirling-pdf/stirling). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Stirling PDF - Processing API: API documentation for PDF processing operations including conversion, manipulation, security, and utilities.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [openapi](#openapi)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Asynchronous Support](#asynchronous-support)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

### Getting started

JDK 11 or later is required.

The samples below show how a published SDK artifact is used:

Gradle:
```groovy
implementation 'com.stirling:openapi:0.2.4'
```

Maven:
```xml
<dependency>
    <groupId>com.stirling</groupId>
    <artifactId>openapi</artifactId>
    <version>0.2.4</version>
</dependency>
```

### How to build
After cloning the git repository to your file system you can build the SDK artifact from source to the `build` directory by running `./gradlew build` on *nix systems or `gradlew.bat` on Windows systems.

If you wish to build from source and publish the SDK artifact to your local Maven repository (on your filesystem) then use the following command (after cloning the git repo locally):

On *nix:
```bash
./gradlew publishToMavenLocal -Pskip.signing
```
On Windows:
```bash
gradlew.bat publishToMavenLocal -Pskip.signing
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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
#### Asynchronous Call
An asynchronous SDK client is also available that returns a [`CompletableFuture<T>`][comp-fut]. See [Asynchronous Support](#asynchronous-support) for more details on async benefits and reactive library integration.
```java
package hello.world;

import java.util.concurrent.CompletableFuture;
import org.openapis.openapi.AsyncStirling;
import org.openapis.openapi.Stirling;
import org.openapis.openapi.models.components.SignatureValidationRequest;
import org.openapis.openapi.models.operations.async.ValidateSignatureResponse;

public class Application {

    public static void main(String[] args) {

        AsyncStirling sdk = Stirling.builder()
            .build()
            .async();

        SignatureValidationRequest req = SignatureValidationRequest.builder()
                .fileId("a1b2c3d4-5678-90ab-cdef-ghijklmnopqr")
                .build();

        CompletableFuture<ValidateSignatureResponse> resFut = sdk.security().validateSignature()
                .request(req)
                .call();

    }
}
```

[comp-fut]: https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletableFuture.html
<!-- End SDK Example Usage [usage] -->

<!-- Start Asynchronous Support [async-support] -->
## Asynchronous Support

The SDK provides comprehensive asynchronous support using Java's [`CompletableFuture<T>`][comp-fut] and [Reactive Streams `Publisher<T>`][reactive-streams] APIs. This design makes no assumptions about your choice of reactive toolkit, allowing seamless integration with any reactive library.

<details>
<summary>Why Use Async?</summary>

Asynchronous operations provide several key benefits:

- **Non-blocking I/O**: Your threads stay free for other work while operations are in flight
- **Better resource utilization**: Handle more concurrent operations with fewer threads
- **Improved scalability**: Build highly responsive applications that can handle thousands of concurrent requests
- **Reactive integration**: Works seamlessly with reactive streams and backpressure handling

</details>

<details>
<summary>Reactive Library Integration</summary>

The SDK returns [Reactive Streams `Publisher<T>`][reactive-streams] instances for operations dealing with streams involving multiple I/O interactions. We use Reactive Streams instead of JDK Flow API to provide broader compatibility with the reactive ecosystem, as most reactive libraries natively support Reactive Streams.

**Why Reactive Streams over JDK Flow?**
- **Broader ecosystem compatibility**: Most reactive libraries (Project Reactor, RxJava, Akka Streams, etc.) natively support Reactive Streams
- **Industry standard**: Reactive Streams is the de facto standard for reactive programming in Java
- **Better interoperability**: Seamless integration without additional adapters for most use cases

**Integration with Popular Libraries:**
- **Project Reactor**: Use `Flux.from(publisher)` to convert to Reactor types
- **RxJava**: Use `Flowable.fromPublisher(publisher)` for RxJava integration
- **Akka Streams**: Use `Source.fromPublisher(publisher)` for Akka Streams integration
- **Vert.x**: Use `ReadStream.fromPublisher(vertx, publisher)` for Vert.x reactive streams
- **Mutiny**: Use `Multi.createFrom().publisher(publisher)` for Quarkus Mutiny integration

**For JDK Flow API Integration:**
If you need JDK Flow API compatibility (e.g., for Quarkus/Mutiny 2), you can use adapters:
```java
// Convert Reactive Streams Publisher to Flow Publisher
Flow.Publisher<T> flowPublisher = FlowAdapters.toFlowPublisher(reactiveStreamsPublisher);

// Convert Flow Publisher to Reactive Streams Publisher
Publisher<T> reactiveStreamsPublisher = FlowAdapters.toPublisher(flowPublisher);
```

For standard single-response operations, the SDK returns `CompletableFuture<T>` for straightforward async execution.

</details>

<details>
<summary>Supported Operations</summary>

Async support is available for:

- **[Server-sent Events](#server-sent-event-streaming)**: Stream real-time events with Reactive Streams `Publisher<T>`
- **[JSONL Streaming](#jsonl-streaming)**: Process streaming JSON lines asynchronously
- **[Pagination](#pagination)**: Iterate through paginated results using `callAsPublisher()` and `callAsPublisherUnwrapped()`
- **[File Uploads](#file-uploads)**: Upload files asynchronously with progress tracking
- **[File Downloads](#file-downloads)**: Download files asynchronously with streaming support
- **[Standard Operations](#example)**: All regular API calls return `CompletableFuture<T>` for async execution

</details>

[comp-fut]: https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CompletableFuture.html
[reactive-streams]: https://www.reactive-streams.org/
<!-- End Asynchronous Support [async-support] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [analysis()](docs/sdks/analysis/README.md)

* [getSecurityInfo](docs/sdks/analysis/README.md#getsecurityinfo) - Get security information
* [getPageDimensions](docs/sdks/analysis/README.md#getpagedimensions) - Get page dimensions for all pages
* [getPageCount](docs/sdks/analysis/README.md#getpagecount) - Get PDF page count
* [getFormFields](docs/sdks/analysis/README.md#getformfields) - Get form field information
* [getFontInfo](docs/sdks/analysis/README.md#getfontinfo) - Get font information
* [getDocumentProperties](docs/sdks/analysis/README.md#getdocumentproperties) - Get PDF document properties
* [getBasicInfo](docs/sdks/analysis/README.md#getbasicinfo) - Get basic PDF information
* [getAnnotationInfo](docs/sdks/analysis/README.md#getannotationinfo) - Get annotation information

### [convert()](docs/sdks/convert/README.md)

* [urlToPdf](docs/sdks/convert/README.md#urltopdf) - Convert a URL to a PDF
* [processPdfToXML](docs/sdks/convert/README.md#processpdftoxml) - Convert PDF to XML
* [processPdfToWord](docs/sdks/convert/README.md#processpdftoword) - Convert PDF to Word document
* [processPdfToRTForTXT](docs/sdks/convert/README.md#processpdftortfortxt) - Convert PDF to Text or RTF format
* [processPdfToPresentation](docs/sdks/convert/README.md#processpdftopresentation) - Convert PDF to Presentation format
* [pdfToPdfA](docs/sdks/convert/README.md#pdftopdfa) - Convert a PDF to a PDF/A
* [processPdfToMarkdown](docs/sdks/convert/README.md#processpdftomarkdown) - Convert PDF to Markdown
* [convertToImage](docs/sdks/convert/README.md#converttoimage) - Convert PDF to image(s)
* [processPdfToHTML](docs/sdks/convert/README.md#processpdftohtml) - Convert PDF to HTML
* [pdfToCsv](docs/sdks/convert/README.md#pdftocsv) - Extracts a CSV document from a PDF
* [markdownToPdf](docs/sdks/convert/README.md#markdowntopdf) - Convert a Markdown file to PDF
* [convertToPdf](docs/sdks/convert/README.md#converttopdf) - Convert images to a PDF file
* [htmlToPdf](docs/sdks/convert/README.md#htmltopdf) - Convert an HTML or ZIP (containing HTML and CSS) to PDF
* [processFileToPDF](docs/sdks/convert/README.md#processfiletopdf) - Convert a file to a PDF using LibreOffice
* [convertEmlToPdf](docs/sdks/convert/README.md#convertemltopdf) - Convert EML to PDF

### [filter()](docs/sdks/filter/README.md)

* [pageSize](docs/sdks/filter/README.md#pagesize) - Checks if a PDF is of a certain size
* [pageRotation](docs/sdks/filter/README.md#pagerotation) - Checks if a PDF is of a certain rotation
* [pageCount](docs/sdks/filter/README.md#pagecount) - Checks if a PDF is greater, less or equal to a setPageCount
* [fileSize](docs/sdks/filter/README.md#filesize) - Checks if a PDF is a set file size
* [containsText](docs/sdks/filter/README.md#containstext) - Checks if a PDF contains set text, returns true if does
* [containsImage](docs/sdks/filter/README.md#containsimage) - Checks if a PDF contains an image

### [general()](docs/sdks/general/README.md)

* [splitPdf](docs/sdks/general/README.md#splitpdf) - Split PDF pages into smaller sections
* [splitPdf1](docs/sdks/general/README.md#splitpdf1) - Split PDFs by Chapters
* [splitPdf2](docs/sdks/general/README.md#splitpdf2) - Split a PDF file into separate documents
* [autoSplitPdf1](docs/sdks/general/README.md#autosplitpdf1) - Auto split PDF pages into separate documents based on size or count
* [scalePages](docs/sdks/general/README.md#scalepages) - Change the size of a PDF page/document
* [rotatePDF](docs/sdks/general/README.md#rotatepdf) - Rotate a PDF file
* [deletePages](docs/sdks/general/README.md#deletepages) - Remove pages from a PDF file
* [removeImages](docs/sdks/general/README.md#removeimages) - Remove images from file to reduce the file size.
* [rearrangePages](docs/sdks/general/README.md#rearrangepages) - Rearrange pages in a PDF file
* [pdfToSinglePage](docs/sdks/general/README.md#pdftosinglepage) - Convert a multi-page PDF into a single long page PDF
* [overlayPdfs](docs/sdks/general/README.md#overlaypdfs) - Overlay PDF files in various modes
* [mergeMultiplePagesIntoOne](docs/sdks/general/README.md#mergemultiplepagesintoone) - Merge multiple pages of a PDF document into a single page
* [mergePdfs](docs/sdks/general/README.md#mergepdfs) - Merge multiple PDF files into one
* [extractBookmarks](docs/sdks/general/README.md#extractbookmarks) - Extract PDF Bookmarks
* [editTableOfContents](docs/sdks/general/README.md#edittableofcontents) - Edit Table of Contents
* [cropPdf](docs/sdks/general/README.md#croppdf) - Crops a PDF document
* [createBookletImposition](docs/sdks/general/README.md#createbookletimposition) - Create a booklet with proper page imposition

### [misc()](docs/sdks/misc/README.md)

* [metadata](docs/sdks/misc/README.md#metadata) - Update metadata of a PDF file
* [unlockPDFForms](docs/sdks/misc/README.md#unlockpdfforms) - Remove read-only property from form fields
* [extractHeader](docs/sdks/misc/README.md#extractheader) - Grabs all JS from a PDF and returns a single JS file with all code
* [scannerEffect](docs/sdks/misc/README.md#scannereffect) - Apply scanner effect to PDF
* [replaceAndInvertColor](docs/sdks/misc/README.md#replaceandinvertcolor) - Replace-Invert Color PDF
* [repairPdf](docs/sdks/misc/README.md#repairpdf) - Repair a PDF file
* [removeBlankPages](docs/sdks/misc/README.md#removeblankpages) - Remove blank pages from a PDF file
* [processPdfWithOCR](docs/sdks/misc/README.md#processpdfwithocr) - Process a PDF file with OCR
* [flatten](docs/sdks/misc/README.md#flatten) - Flatten PDF form fields or full page
* [extractImages](docs/sdks/misc/README.md#extractimages) - Extract images from a PDF file
* [extractImageScans](docs/sdks/misc/README.md#extractimagescans) - Extract image scans from an input file
* [decompressPdf](docs/sdks/misc/README.md#decompresspdf) - Decompress PDF streams
* [optimizePdf](docs/sdks/misc/README.md#optimizepdf) - Optimize PDF file
* [autoSplitPdf](docs/sdks/misc/README.md#autosplitpdf) - Auto split PDF pages into separate documents
* [extractHeader1](docs/sdks/misc/README.md#extractheader1) - Extract header from PDF file
* [addStamp](docs/sdks/misc/README.md#addstamp) - Add stamp to a PDF file
* [addPageNumbers](docs/sdks/misc/README.md#addpagenumbers) - Add page numbers to a PDF document
* [overlayImage](docs/sdks/misc/README.md#overlayimage) - Overlay image onto a PDF file
* [addAttachments](docs/sdks/misc/README.md#addattachments) - Add attachments to PDF

### [pipeline()](docs/sdks/pipeline/README.md)

* [handleData](docs/sdks/pipeline/README.md#handledata) - Execute automated PDF processing pipeline

### [security()](docs/sdks/security/README.md)

* [validateSignature](docs/sdks/security/README.md#validatesignature) - Validate PDF Digital Signature
* [sanitizePDF](docs/sdks/security/README.md#sanitizepdf) - Sanitize a PDF file
* [removePassword](docs/sdks/security/README.md#removepassword) - Remove password from a PDF file
* [removeCertSignPDF](docs/sdks/security/README.md#removecertsignpdf) - Remove digital signature from PDF
* [redactPdfManual](docs/sdks/security/README.md#redactpdfmanual) - Redacts areas and pages in a PDF document
* [getPdfInfo](docs/sdks/security/README.md#getpdfinfo) - Summary here
* [signPDFWithCert](docs/sdks/security/README.md#signpdfwithcert) - Sign PDF with a Digital Certificate
* [redactPdfAuto](docs/sdks/security/README.md#redactpdfauto) - Redacts listOfText in a PDF document
* [addWatermark](docs/sdks/security/README.md#addwatermark) - Add watermark to a PDF file
* [addPassword](docs/sdks/security/README.md#addpassword) - Add password to a PDF file


</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or raise an exception.

By default, an API error will throw a `models/errors/APIException` exception. When custom error responses are specified for an operation, the SDK may also throw their associated exception. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `validateSignature` method throws the following exceptions:

| Error Type                                                    | Status Code | Content Type     |
| ------------------------------------------------------------- | ----------- | ---------------- |
| models/errors/ValidateSignatureBadRequestException            | 400         | application/json |
| models/errors/ValidateSignatureRequestEntityTooLargeException | 413         | application/json |
| models/errors/ValidateSignatureUnprocessableEntityException   | 422         | application/json |
| models/errors/ValidateSignatureInternalServerError            | 500         | application/json |
| models/errors/APIException                                    | 4XX, 5XX    | \*/\*            |

### Example

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
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `.serverURL(String serverUrl)` builder method when initializing the SDK client instance. For example:
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
                .serverURL("http://localhost:8080")
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
<!-- End Server Selection [server] -->

<!-- Start Debugging [debug] -->
## Debugging

### Debug
You can setup your SDK to emit debug logs for SDK requests and responses.

For request and response logging (especially json bodies), call `enableHTTPDebugLogging(boolean)` on the SDK builder like so:
```java
SDK.builder()
    .enableHTTPDebugLogging(true)
    .build();
```
Example output:
```
Sending request: http://localhost:35123/bearer#global GET
Request headers: {Accept=[application/json], Authorization=[******], Client-Level-Header=[added by client], Idempotency-Key=[some-key], x-speakeasy-user-agent=[speakeasy-sdk/java 0.0.1 internal 0.1.0 org.openapis.openapi]}
Received response: (GET http://localhost:35123/bearer#global) 200
Response headers: {access-control-allow-credentials=[true], access-control-allow-origin=[*], connection=[keep-alive], content-length=[50], content-type=[application/json], date=[Wed, 09 Apr 2025 01:43:29 GMT], server=[gunicorn/19.9.0]}
Response body:
{
  "authenticated": true, 
  "token": "global"
}
```
__WARNING__: This should only used for temporary debugging purposes. Leaving this option on in a production system could expose credentials/secrets in logs. <i>Authorization</i> headers are redacted by default and there is the ability to specify redacted header names via `SpeakeasyHTTPClient.setRedactedHeaders`.

__NOTE__: This is a convenience method that calls `HTTPClient.enableDebugLogging()`. The `SpeakeasyHTTPClient` honors this setting. If you are using a custom HTTP client, it is up to the custom client to honor this setting.

Another option is to set the System property `-Djdk.httpclient.HttpClient.log=all`. However, this second option does not log bodies.
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=openapi&utm_campaign=java)
