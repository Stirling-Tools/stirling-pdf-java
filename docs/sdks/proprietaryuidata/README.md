# ProprietaryUIData
(*proprietaryUIData()*)

## Overview

APIs for React UI data (Proprietary features)

### Available Operations

* [getTeamsData](#getteamsdata) - Get teams list data
* [getTeamDetailsData](#getteamdetailsdata) - Get team details data
* [getLoginData](#getlogindata) - Get login page data
* [getDatabaseData](#getdatabasedata) - Get database management data
* [getAuditDashboardData](#getauditdashboarddata) - Get audit dashboard data
* [getAdminSettingsData](#getadminsettingsdata) - Get admin settings data
* [getAccountData](#getaccountdata) - Get account page data

## getTeamsData

Get teams list data

### Example Usage

<!-- UsageSnippet language="java" operationID="getTeamsData" method="get" path="/api/v1/proprietary/ui-data/teams" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetTeamsDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetTeamsDataResponse res = sdk.proprietaryUIData().getTeamsData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetTeamsDataResponse](../../models/operations/GetTeamsDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getTeamDetailsData

Get team details data

### Example Usage

<!-- UsageSnippet language="java" operationID="getTeamDetailsData" method="get" path="/api/v1/proprietary/ui-data/teams/{id}" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetTeamDetailsDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetTeamDetailsDataResponse res = sdk.proprietaryUIData().getTeamDetailsData()
                .id(774157L)
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `id`               | *long*             | :heavy_check_mark: | N/A                |

### Response

**[GetTeamDetailsDataResponse](../../models/operations/GetTeamDetailsDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getLoginData

Get login page data

### Example Usage

<!-- UsageSnippet language="java" operationID="getLoginData" method="get" path="/api/v1/proprietary/ui-data/login" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetLoginDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetLoginDataResponse res = sdk.proprietaryUIData().getLoginData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetLoginDataResponse](../../models/operations/GetLoginDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getDatabaseData

Get database management data

### Example Usage

<!-- UsageSnippet language="java" operationID="getDatabaseData" method="get" path="/api/v1/proprietary/ui-data/database" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetDatabaseDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetDatabaseDataResponse res = sdk.proprietaryUIData().getDatabaseData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetDatabaseDataResponse](../../models/operations/GetDatabaseDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getAuditDashboardData

Get audit dashboard data

### Example Usage

<!-- UsageSnippet language="java" operationID="getAuditDashboardData" method="get" path="/api/v1/proprietary/ui-data/audit-dashboard" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetAuditDashboardDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetAuditDashboardDataResponse res = sdk.proprietaryUIData().getAuditDashboardData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetAuditDashboardDataResponse](../../models/operations/GetAuditDashboardDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getAdminSettingsData

Get admin settings data

### Example Usage

<!-- UsageSnippet language="java" operationID="getAdminSettingsData" method="get" path="/api/v1/proprietary/ui-data/admin-settings" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetAdminSettingsDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetAdminSettingsDataResponse res = sdk.proprietaryUIData().getAdminSettingsData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetAdminSettingsDataResponse](../../models/operations/GetAdminSettingsDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |

## getAccountData

Get account page data

### Example Usage

<!-- UsageSnippet language="java" operationID="getAccountData" method="get" path="/api/v1/proprietary/ui-data/account" -->
```java
package hello.world;

import java.lang.Exception;
import org.openapis.openapi.StirlingPdf;
import org.openapis.openapi.models.operations.GetAccountDataResponse;

public class Application {

    public static void main(String[] args) throws Exception {

        StirlingPdf sdk = StirlingPdf.builder()
            .build();

        GetAccountDataResponse res = sdk.proprietaryUIData().getAccountData()
                .call();

        if (res.body().isPresent()) {
            // handle response
        }
    }
}
```

### Response

**[GetAccountDataResponse](../../models/operations/GetAccountDataResponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| models/errors/APIException | 4XX, 5XX                   | \*/\*                      |