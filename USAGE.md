<!-- Start SDK Example Usage [usage] -->
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
<!-- End SDK Example Usage [usage] -->