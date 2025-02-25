# shippingapi - the C# library for the Shipping API

Shipping API Sample

This C# SDK is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: 1.0.0
- SDK version: 2.0.0
- Build package: org.openapitools.codegen.languages.CSharpClientCodegen

## Frameworks supported
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fmaxmckone7%2Fpitneybowes-shipping-api-csharp-openapi.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fmaxmckone7%2Fpitneybowes-shipping-api-csharp-openapi?ref=badge_shield)



- .NET 4.0 or later
- Windows Phone 7.1 (Mango)

## Dependencies


- [RestSharp](https://www.nuget.org/packages/RestSharp) - 105.1.0 or later
- [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/) - 7.0.0 or later
- [JsonSubTypes](https://www.nuget.org/packages/JsonSubTypes/) - 1.2.0 or later

The DLLs included in the package may not be the latest version. We recommend using [NuGet](https://docs.nuget.org/consume/installing-nuget) to obtain the latest version of the packages:

```
Install-Package RestSharp
Install-Package Newtonsoft.Json
Install-Package JsonSubTypes
```

NOTE: RestSharp versions greater than 105.1.0 have a bug which causes file uploads to fail. See [RestSharp#742](https://github.com/restsharp/RestSharp/issues/742)

## Installation

Run the following command to generate the DLL

- [Mac/Linux] `/bin/sh build.sh`
- [Windows] `build.bat`

Then include the DLL (under the `bin` folder) in the C# project, and use the namespaces:

```csharp
using shippingapi.Api;
using shippingapi.Client;
using shippingapi.Model;

```


## Packaging

A `.nuspec` is included with the project. You can follow the Nuget quickstart to [create](https://docs.microsoft.com/en-us/nuget/quickstart/create-and-publish-a-package#create-the-package) and [publish](https://docs.microsoft.com/en-us/nuget/quickstart/create-and-publish-a-package#publish-the-package) packages.

This `.nuspec` uses placeholders from the `.csproj`, so build the `.csproj` directly:

```
nuget pack -Build -OutputDirectory out shippingapi.csproj
```

Then, publish to a [local feed](https://docs.microsoft.com/en-us/nuget/hosting-packages/local-feeds) or [other host](https://docs.microsoft.com/en-us/nuget/hosting-packages/overview) and consume the new package via Nuget as usual.


## Getting Started

```csharp
using System.Collections.Generic;
using System.Diagnostics;
using shippingapi.Api;
using shippingapi.Client;
using shippingapi.Model;

namespace Example
{
    public class Example
    {
        public static void Main()
        {

            Configuration.Default.BasePath = "https://shipping-api-sandbox.pitneybowes.com/shippingservices";
            // Configure OAuth2 access token for authorization: oAuth2ClientCredentials
            Configuration.Default.AccessToken = "YOUR_ACCESS_TOKEN";

            var apiInstance = new AddressValidationApi(Configuration.Default);
            var address = new Address(); // Address | Address object that needs to be validated.
            var xPBUnifiedErrorStructure = true;  // bool? | Set this to true to use the standard [error object](https://shipping.pitneybowes.com/reference/error-object.html#standard-error-object) if an error occurs. (optional)  (default to true)
            var minimalAddressValidation = true;  // bool? | When set to true, the complete address (delivery line and last line) is validated but only the last line (city, state, and postal code) would be changed by the validation check. (optional) 

            try
            {
                // Address validation
                Address result = apiInstance.VerifyAddress(address, xPBUnifiedErrorStructure, minimalAddressValidation);
                Debug.WriteLine(result);
            }
            catch (ApiException e)
            {
                Debug.Print("Exception when calling AddressValidationApi.VerifyAddress: " + e.Message );
                Debug.Print("Status Code: "+ e.ErrorCode);
                Debug.Print(e.StackTrace);
            }

        }
    }
}
```

## Documentation for API Endpoints

All URIs are relative to *https://shipping-api-sandbox.pitneybowes.com/shippingservices*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AddressValidationApi* | [**VerifyAddress**](docs/AddressValidationApi.md#verifyaddress) | **POST** /v1/addresses/verify | Address validation
*AddressValidationApi* | [**VerifyAndSuggestAddress**](docs/AddressValidationApi.md#verifyandsuggestaddress) | **POST** /v1/addresses/verify-suggest | Address Suggestion
*CarrierInfoApi* | [**GetCarrierFacilities**](docs/CarrierInfoApi.md#getcarrierfacilities) | **POST** /v1/carrier-facility | Find Carrier Facilities
*CarrierInfoApi* | [**GetCarrierLicenseAgreement**](docs/CarrierInfoApi.md#getcarrierlicenseagreement) | **GET** /v1/carrier/license-agreements | This operation retrieves a carrier's license agreement.
*CarrierInfoApi* | [**GetCarrierServiceRules**](docs/CarrierInfoApi.md#getcarrierservicerules) | **GET** /v1/information/rules/rating-services | Retrieves the rules governing the carrier's services.
*CarrierInfoApi* | [**GetCarrierSupportedDestination**](docs/CarrierInfoApi.md#getcarriersupporteddestination) | **GET** /v1/countries | This operation returns a list of supported destination countries to which the carrier offers international shipping services.
*ContainerApi* | [**GetContainerizedParcelsLabels**](docs/ContainerApi.md#getcontainerizedparcelslabels) | **POST** /v1/container-manifest | Create Container Manifest Label
*CrossBorderQuotesApi* | [**GetCrossBorderQuotes**](docs/CrossBorderQuotesApi.md#getcrossborderquotes) | **POST** /v1/crossborder/checkout/quotes | Cross-Border Quotes
*CrossBorderQuotesApi* | [**PredictedHSCode**](docs/CrossBorderQuotesApi.md#predictedhscode) | **POST** /v1/crossborder/hs-classification/items | Predicts the HS Code for a parcel
*ManifestsApi* | [**CreateManifest**](docs/ManifestsApi.md#createmanifest) | **POST** /v1/manifests | This operation creates an end-of-day manifest
*ManifestsApi* | [**ReprintManifest**](docs/ManifestsApi.md#reprintmanifest) | **GET** /v1/manifests/{manifestId} | reprintManifest
*ManifestsApi* | [**RetryManifest**](docs/ManifestsApi.md#retrymanifest) | **GET** /v1/manifests | retryManifest
*ParcelProtectionApi* | [**CancelParcelProtection**](docs/ParcelProtectionApi.md#cancelparcelprotection) | **POST** /v1/parcel-protection/void | Parcel Protection Coverage
*ParcelProtectionApi* | [**GetParcelProtectionCoverage**](docs/ParcelProtectionApi.md#getparcelprotectioncoverage) | **POST** /v1/parcel-protection/create | Parcel Protection Coverage
*ParcelProtectionApi* | [**GetParcelProtectionQuote**](docs/ParcelProtectionApi.md#getparcelprotectionquote) | **POST** /v1/parcel-protection/quote | Parcel Protection Quote
*ParcelProtectionApi* | [**GetParcelProtectionReports**](docs/ParcelProtectionApi.md#getparcelprotectionreports) | **GET** /v1/parcel-protection/{developerId}/policies | Parcel Protection Reports
*PickupApi* | [**CancelPickup**](docs/PickupApi.md#cancelpickup) | **POST** /v1/pickups/{pickupId}/cancel | Cancel Pickup
*PickupApi* | [**GetPickupschedule**](docs/PickupApi.md#getpickupschedule) | **POST** /v1/pickups/schedule | Address validation
*RateParcelsApi* | [**RateParcel**](docs/RateParcelsApi.md#rateparcel) | **POST** /v1/rates | Use this operation to rate a parcel before you print and purchase a shipment label. You can rate a parcel for multiple services and multiple parcel types with a single API request.
*ShipmentApi* | [**CancelShipment**](docs/ShipmentApi.md#cancelshipment) | **DELETE** /v1/shipments/{shipmentId} | cancelShipment
*ShipmentApi* | [**CreateShipmentLabel**](docs/ShipmentApi.md#createshipmentlabel) | **POST** /v1/shipments | This operation creates a shipment and purchases a shipment label.
*ShipmentApi* | [**ReprintShipment**](docs/ShipmentApi.md#reprintshipment) | **GET** /v1/shipments/{shipmentId} | reprintShipment
*ShipmentApi* | [**RetryShipment**](docs/ShipmentApi.md#retryshipment) | **GET** /v1/shipments | retryShipment
*TrackingApi* | [**AddTrackingEvents**](docs/TrackingApi.md#addtrackingevents) | **POST** /v2/track/events | getTrackingDetails
*TrackingApi* | [**GetTrackingDetails**](docs/TrackingApi.md#gettrackingdetails) | **GET** /v1/tracking/{trackingNumber} | getTrackingDetails
*TransactionReportsApi* | [**GetTransactionReport**](docs/TransactionReportsApi.md#gettransactionreport) | **GET** /v4/ledger/developers/{developerId}/transactions/reports | This operation retrieves all transactions for a specified period of time.


## Documentation for Models

 - [Model.AddTrackingEvents](docs/AddTrackingEvents.md)
 - [Model.AddTrackingEventsEvents](docs/AddTrackingEventsEvents.md)
 - [Model.AddTrackingEventsReferences](docs/AddTrackingEventsReferences.md)
 - [Model.AdditionalAddress](docs/AdditionalAddress.md)
 - [Model.Address](docs/Address.md)
 - [Model.AddressSuggestionResponse](docs/AddressSuggestionResponse.md)
 - [Model.AddressSuggestionResponseSuggestions](docs/AddressSuggestionResponseSuggestions.md)
 - [Model.AddressVerifySuggest](docs/AddressVerifySuggest.md)
 - [Model.BatteryDetails](docs/BatteryDetails.md)
 - [Model.CancelShipment](docs/CancelShipment.md)
 - [Model.Carrier](docs/Carrier.md)
 - [Model.CarrierFacilityRequest](docs/CarrierFacilityRequest.md)
 - [Model.CarrierFacilityRequestAddress](docs/CarrierFacilityRequestAddress.md)
 - [Model.CarrierFacilityResponse](docs/CarrierFacilityResponse.md)
 - [Model.CarrierFacilityResponseCarrierFacilityOptions](docs/CarrierFacilityResponseCarrierFacilityOptions.md)
 - [Model.CarrierFacilityResponseCarrierFacilitySuggestions](docs/CarrierFacilityResponseCarrierFacilitySuggestions.md)
 - [Model.CarrierFacilityResponseFacilityHours](docs/CarrierFacilityResponseFacilityHours.md)
 - [Model.CarrierFacilityResponseFacilityTimings](docs/CarrierFacilityResponseFacilityTimings.md)
 - [Model.CarrierPayment](docs/CarrierPayment.md)
 - [Model.CarrierRule](docs/CarrierRule.md)
 - [Model.CommodityInfo](docs/CommodityInfo.md)
 - [Model.ContainerDetails](docs/ContainerDetails.md)
 - [Model.ContainerManifestResponse](docs/ContainerManifestResponse.md)
 - [Model.ContainerManifestResponseData](docs/ContainerManifestResponseData.md)
 - [Model.CrossBorderQuotesErrors](docs/CrossBorderQuotesErrors.md)
 - [Model.CrossBorderQuotesErrorsErrors](docs/CrossBorderQuotesErrorsErrors.md)
 - [Model.CrossBorderQuotesErrorsErrorsErrors](docs/CrossBorderQuotesErrorsErrorsErrors.md)
 - [Model.CrossBorderQuotesErrorsQuote](docs/CrossBorderQuotesErrorsQuote.md)
 - [Model.CrossBorderQuotesErrorsQuoteLines](docs/CrossBorderQuotesErrorsQuoteLines.md)
 - [Model.CrossBorderQuotesErrorsUnitErrors](docs/CrossBorderQuotesErrorsUnitErrors.md)
 - [Model.CrossBorderQuotesRequest](docs/CrossBorderQuotesRequest.md)
 - [Model.CrossBorderQuotesRequestAttributes](docs/CrossBorderQuotesRequestAttributes.md)
 - [Model.CrossBorderQuotesRequestBasketItems](docs/CrossBorderQuotesRequestBasketItems.md)
 - [Model.CrossBorderQuotesRequestCategories](docs/CrossBorderQuotesRequestCategories.md)
 - [Model.CrossBorderQuotesRequestDescriptions](docs/CrossBorderQuotesRequestDescriptions.md)
 - [Model.CrossBorderQuotesRequestIdentifiers](docs/CrossBorderQuotesRequestIdentifiers.md)
 - [Model.CrossBorderQuotesRequestItemDimension](docs/CrossBorderQuotesRequestItemDimension.md)
 - [Model.CrossBorderQuotesRequestPricing](docs/CrossBorderQuotesRequestPricing.md)
 - [Model.CrossBorderQuotesRequestPricingCodPrice](docs/CrossBorderQuotesRequestPricingCodPrice.md)
 - [Model.CrossBorderQuotesRequestRates](docs/CrossBorderQuotesRequestRates.md)
 - [Model.CrossBorderQuotesRequestUnitWeight](docs/CrossBorderQuotesRequestUnitWeight.md)
 - [Model.CrossBorderQuotesResponse](docs/CrossBorderQuotesResponse.md)
 - [Model.CrossBorderQuotesResponseLineRates](docs/CrossBorderQuotesResponseLineRates.md)
 - [Model.CrossBorderQuotesResponseQuote](docs/CrossBorderQuotesResponseQuote.md)
 - [Model.CrossBorderQuotesResponseQuoteLines](docs/CrossBorderQuotesResponseQuoteLines.md)
 - [Model.CrossBorderQuotesResponseTotalRates](docs/CrossBorderQuotesResponseTotalRates.md)
 - [Model.CrossBorderQuotesResponseUnitRates](docs/CrossBorderQuotesResponseUnitRates.md)
 - [Model.CrossBorderQuotesResponseUnitRatesDeliveryCommitment](docs/CrossBorderQuotesResponseUnitRatesDeliveryCommitment.md)
 - [Model.Customs](docs/Customs.md)
 - [Model.CustomsInfo](docs/CustomsInfo.md)
 - [Model.CustomsItem](docs/CustomsItem.md)
 - [Model.DeliveryCommitment](docs/DeliveryCommitment.md)
 - [Model.DimensionRules](docs/DimensionRules.md)
 - [Model.DimensionRulesMaxParcelDimensions](docs/DimensionRulesMaxParcelDimensions.md)
 - [Model.DimensionRulesMinParcelDimensions](docs/DimensionRulesMinParcelDimensions.md)
 - [Model.Discount](docs/Discount.md)
 - [Model.DocTabItem](docs/DocTabItem.md)
 - [Model.Document](docs/Document.md)
 - [Model.DocumentPage](docs/DocumentPage.md)
 - [Model.Errors](docs/Errors.md)
 - [Model.HazmatDetails](docs/HazmatDetails.md)
 - [Model.ISOCountryCode](docs/ISOCountryCode.md)
 - [Model.InfectiousSubstanceContact](docs/InfectiousSubstanceContact.md)
 - [Model.InlineResponse200](docs/InlineResponse200.md)
 - [Model.InlineResponse2001](docs/InlineResponse2001.md)
 - [Model.InlineResponse2002](docs/InlineResponse2002.md)
 - [Model.Manifest](docs/Manifest.md)
 - [Model.PageRealTransactionDetailReport](docs/PageRealTransactionDetailReport.md)
 - [Model.Parameter](docs/Parameter.md)
 - [Model.Parcel](docs/Parcel.md)
 - [Model.ParcelDimension](docs/ParcelDimension.md)
 - [Model.ParcelProtectionCreateRequest](docs/ParcelProtectionCreateRequest.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfo](docs/ParcelProtectionCreateRequestShipmentInfo.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfoConsigneeInfo](docs/ParcelProtectionCreateRequestShipmentInfoConsigneeInfo.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfoParcelInfo](docs/ParcelProtectionCreateRequestShipmentInfoParcelInfo.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfoParcelInfoCommodityList](docs/ParcelProtectionCreateRequestShipmentInfoParcelInfoCommodityList.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfoShipperInfo](docs/ParcelProtectionCreateRequestShipmentInfoShipperInfo.md)
 - [Model.ParcelProtectionCreateRequestShipmentInfoShipperInfoAddress](docs/ParcelProtectionCreateRequestShipmentInfoShipperInfoAddress.md)
 - [Model.ParcelProtectionCreateResponse](docs/ParcelProtectionCreateResponse.md)
 - [Model.ParcelProtectionCreateResponseParcelProtectionFeesBreakup](docs/ParcelProtectionCreateResponseParcelProtectionFeesBreakup.md)
 - [Model.ParcelProtectionPolicyResponse](docs/ParcelProtectionPolicyResponse.md)
 - [Model.ParcelProtectionPolicyResponseContent](docs/ParcelProtectionPolicyResponseContent.md)
 - [Model.ParcelProtectionPolicyResponsePolicyDetails](docs/ParcelProtectionPolicyResponsePolicyDetails.md)
 - [Model.ParcelProtectionPolicyResponseShipmentDetails](docs/ParcelProtectionPolicyResponseShipmentDetails.md)
 - [Model.ParcelProtectionPolicyResponseShipperInfo](docs/ParcelProtectionPolicyResponseShipperInfo.md)
 - [Model.ParcelProtectionPolicyResponseShipperInfoAddress](docs/ParcelProtectionPolicyResponseShipperInfoAddress.md)
 - [Model.ParcelProtectionPolicyResponseSort](docs/ParcelProtectionPolicyResponseSort.md)
 - [Model.ParcelProtectionQuoteRequest](docs/ParcelProtectionQuoteRequest.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfo](docs/ParcelProtectionQuoteRequestShipmentInfo.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfoConsigneeInfo](docs/ParcelProtectionQuoteRequestShipmentInfoConsigneeInfo.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfoParcelInfo](docs/ParcelProtectionQuoteRequestShipmentInfoParcelInfo.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfoParcelInfoCommodityList](docs/ParcelProtectionQuoteRequestShipmentInfoParcelInfoCommodityList.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfoShipperInfo](docs/ParcelProtectionQuoteRequestShipmentInfoShipperInfo.md)
 - [Model.ParcelProtectionQuoteRequestShipmentInfoShipperInfoAddress](docs/ParcelProtectionQuoteRequestShipmentInfoShipperInfoAddress.md)
 - [Model.ParcelProtectionQuoteResponse](docs/ParcelProtectionQuoteResponse.md)
 - [Model.ParcelProtectionQuoteResponseParcelProtectionFeesBreakup](docs/ParcelProtectionQuoteResponseParcelProtectionFeesBreakup.md)
 - [Model.ParcelType](docs/ParcelType.md)
 - [Model.ParcelTypeRules](docs/ParcelTypeRules.md)
 - [Model.ParcelWeight](docs/ParcelWeight.md)
 - [Model.PrerequisiteRules](docs/PrerequisiteRules.md)
 - [Model.RadioActiveParcelDimension](docs/RadioActiveParcelDimension.md)
 - [Model.RadioActivityDetail](docs/RadioActivityDetail.md)
 - [Model.RadioNuclideDetail](docs/RadioNuclideDetail.md)
 - [Model.Rate](docs/Rate.md)
 - [Model.RealTransactionDetailReport](docs/RealTransactionDetailReport.md)
 - [Model.SchedulePickup](docs/SchedulePickup.md)
 - [Model.SchedulePickupPickupSummary](docs/SchedulePickupPickupSummary.md)
 - [Model.SchedulePickupResponse](docs/SchedulePickupResponse.md)
 - [Model.SchedulePickupTotalWeight](docs/SchedulePickupTotalWeight.md)
 - [Model.SearchCriteria](docs/SearchCriteria.md)
 - [Model.Services](docs/Services.md)
 - [Model.ServicesParameterRule](docs/ServicesParameterRule.md)
 - [Model.Shipment](docs/Shipment.md)
 - [Model.Signatory](docs/Signatory.md)
 - [Model.SpecialService](docs/SpecialService.md)
 - [Model.SpecialServiceCodes](docs/SpecialServiceCodes.md)
 - [Model.SpecialServicesRule](docs/SpecialServicesRule.md)
 - [Model.Surcharge](docs/Surcharge.md)
 - [Model.Tax](docs/Tax.md)
 - [Model.Trackable](docs/Trackable.md)
 - [Model.TrackingAddress](docs/TrackingAddress.md)
 - [Model.TrackingResponse](docs/TrackingResponse.md)
 - [Model.TrackingResponseScanDetailsList](docs/TrackingResponseScanDetailsList.md)
 - [Model.UnitOfDimension](docs/UnitOfDimension.md)
 - [Model.UnitOfWeight](docs/UnitOfWeight.md)
 - [Model.VoidParcelProtectionRequest](docs/VoidParcelProtectionRequest.md)
 - [Model.VoidParcelProtectionResponse](docs/VoidParcelProtectionResponse.md)
 - [Model.WeightRules](docs/WeightRules.md)


## Documentation for Authorization


### oAuth2ClientCredentials


- **Type**: OAuth
- **Flow**: application
- **Authorization URL**: 
- **Scopes**: N/A



## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fmaxmckone7%2Fpitneybowes-shipping-api-csharp-openapi.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fmaxmckone7%2Fpitneybowes-shipping-api-csharp-openapi?ref=badge_large)