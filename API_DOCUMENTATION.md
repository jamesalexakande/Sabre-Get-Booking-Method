# Sabre Booking Management API: Get Booking Method

## Introduction
The **Get Booking** method is a Booking endpoint in Sabre’s Booking Management API that allows easy retrieval and display of booking details or reservations already existing in other internal Sabre domains.

It provides a single response overview by combining details from Passenger Name Records (PNRs) and Orders stored in the Sabre system - displaying passenger information, itineraries, pricing, ticketing status, and payment time limits.

## Why Use the Get Booking Method?

Developers should use the **Get Booking** method for the following reasons:
- Retrieves complete customer booking details for customer-facing applications. travel agency systems  
- Provides a simplified reservation overview by drawing from different content sources (PNR and Order).
- Streamlines the booking retrieval process, eliminating the need to call multiple APIs.
- Facilitates automated workflows for booking management and modifications.
- Includes additional details and retrieves data not stored in the Sabre PNR (e.g., ticket details, fare rates).
- Retrieves reservation details independently, without the need for previous requests or session data.

## Process Flow

Here's a simplified process flow for the Get Booking Method

![Get Booking API_EDITED](https://github.com/user-attachments/assets/49056121-7bb5-4eec-aa8a-4aff1b7e6902)

---
## Authentication
To interact with the Sabre Booking Management API, all requests must include a valid authentication token in the request headers. This ensures secure access and proper authorization for API operations.

**Obtaining a Token**
To retrieve a token, follow the authentication guide in this repository:
[AUTHENTICATION.md](AUTHENTICATION.md)

## Example Requests and Responses

### 1. Display Complete Booking

`POST: baseURL/getBooking`

**BaseURL**: `api.cert.platform.sabre.com/v1/trip/orders`

#### **Request**
```json
{
  "confirmationId": "GLEBNY",
  "bookingSource": "SABRE",
  "targetPcc": "G7HE",
  "givenName": "John",
  "middleName": "W",
  "surname": "Smith",
  "returnOnly": [ "FLIGHTS" ]
}
```

#### **Response**
```json
{
  "bookingId": "1SXXX1A2B3C4D",
  "startDate": "2024-07-09",
  "endDate": "2024-07-19",
  "isCancelable": false,
  "isTicketed": false,
  "agencyCustomerNumber": "1234567",
  "creationDetails": {
    "creationUserSine": "A12",
    "creationDate": "2024-01-09",
    "creationTime": "15:00",
    "purchaseDeadlineDate": "2024-01-09",
    "purchaseDeadlineTime": "15:00",
    "agencyIataNumber": "99119911",
    "userWorkPcc": "AB12",
    "userHomePcc": "CD34",
    "primeHostId": "1S"
  },
  "contactInfo": {
    "emails": [
      "travel@sabre.com"
    ],
    "phones": [
      "+1-555-123-4567"
    ],
    "faxes": [
      "+1-555-123-4567"
    ],
    "emergencyPhones": [
      "+1-555-123-4567"
    ]
  },
  "travelers": [
    {
      "givenName": "John",
      "middleName": "W",
      "surname": "Smith",
      "birthDate": "2024-01-23",
      "gender": "FEMALE",
      "type": "ADULT",
      "passengerCode": "ADT",
      "nameAssociationId": "3",
      "nameReferenceCode": "C05",
      "isGrouped": true,
      "emails": [
        "john@smith.family.priv"
      ],
      "phones": [
        {
          "number": "+1-555-123-4567",
          "label": "M"
        }
      ],
      "remarks": [
        {
          "type": "GENERAL",
          "alphaCode": "T",
          "text": "XXATW/"
        }
      ],
      "address": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      },
      "identityDocuments": [
        {
          "documentNumber": "0123456789",
          "documentType": "PASSPORT",
          "documentSubType": "RUC",
          "expiryDate": "2024-07-09",
          "issuingCountryCode": "US",
          "residenceCountryCode": "US",
          "placeOfIssue": "ROME",
          "placeOfBirth": "KOSZALIN",
          "hostCountryCode": "US",
          "issueDate": "2024-07-09",
          "givenName": "John",
          "middleName": "Jack",
          "surname": "Smith",
          "birthDate": "2024-12-02",
          "gender": "FEMALE",
          "isPrimaryDocumentHolder": true,
          "isLapChildDocument": true,
          "residenceDestinationAddress": {
            "street": "1230 Ellen Ave, apt 10",
            "city": "Dallas",
            "stateProvince": "TX",
            "postalCode": "75063",
            "countryCode": "US"
          },
          "flightIndices": [
            1
          ],
          "itemId": "76c2817b178cc264fa44cf85df1da5fb9e1b963006b2339aa5edc09129415bba5fcf5bf91a5f"
        }
      ],
      "loyaltyPrograms": [
        {
          "supplierCode": "AA",
          "programType": "FREQUENT_FLYER",
          "programNumber": "987654321",
          "tierLevel": 3,
          "receiverCode": "UA"
        }
      ],
      "ancillaries": [
        {
          "itemId": "12",
          "commercialName": "UPTO33LB 15KG BAGGAGE",
          "numberOfItems": 1,
          "reasonForIssuanceCode": "C",
          "reasonForIssuanceName": "BAGGAGE",
          "subcode": "05Z",
          "airlineCode": "EY",
          "vendorCode": "EY",
          "source": "ATPCO",
          "electronicMiscellaneousDocumentNumber": "6074333222111",
          "isRefundable": true,
          "isCommissionable": false,
          "flightApplicabilityType": "Single",
          "flights": [
            {
              "itemId": "12"
            }
          ],
          "statusCode": "HD",
          "statusName": "Confirmed",
          "totals": {
            "subtotal": "100.00",
            "taxes": "8.00",
            "fees": "20.00",
            "total": "128.00",
            "currencyCode": "USD",
            "netRemit": "110.00"
          }
        }
      ],
      "formOfPaymentIndices": [
        1
      ],
      "employerIndex": 1
    }
  ],
  "travelersGroup": {
    "itemId": "3",
    "name": "GROUP ONE",
    "numberOfTravelers": 1,
    "numberOfTravelersRemaining": 1
  },
  "flights": [
    {
      "itemId": "12",
      "confirmationId": "NIEBNY",
      "sourceType": "NDC",
      "flightNumber": 123,
      "airlineCode": "AA",
      "airlineName": "AMERICAN AIRLINES",
      "operatingFlightNumber": 321,
      "operatingAirlineCode": "UA",
      "operatingAirlineName": "UNITED AIRLINES",
      "fromAirportCode": "DFW",
      "toAirportCode": "HNL",
      "departureDate": "2024-07-09",
      "departureTime": "09:15",
      "updatedDepartureDate": "2024-07-09",
      "updatedDepartureTime": "09:25",
      "departureTerminalName": "Terminal D",
      "departureGate": "D",
      "arrivalDate": "2024-07-09",
      "arrivalTime": "12:28",
      "updatedArrivalDate": "2024-07-09",
      "updatedArrivalTime": "12:38",
      "arrivalTerminalName": "Terminal 1",
      "arrivalGate": "1",
      "seats": [
        {
          "number": "13A",
          "characteristics": [
            "K"
          ],
          "statusCode": "AF",
          "statusName": "Confirmed"
        }
      ],
      "numberOfSeats": 1,
      "cabinTypeName": "Coach",
      "cabinTypeCode": "C",
      "aircraftTypeCode": "E90",
      "aircraftTypeName": "EMBRAER EMB E90",
      "bookingClass": "Y",
      "meals": [
        {
          "code": "H",
          "description": "Hot meal"
        }
      ],
      "flightStatusCode": "AF",
      "flightStatusName": "Confirmed",
      "durationInMinutes": 590,
      "distanceInMiles": 5143,
      "hiddenStopAircraftTypeCode": "E90",
      "hiddenStopAircraftTypeName": "EMBRAER EMB E90",
      "hiddenStopAirportCode": "HAV",
      "hiddenStopArrivalDate": "2024-07-09",
      "hiddenStopArrivalTime": "09:15",
      "hiddenStopDepartureDate": "2024-07-09",
      "hiddenStopDepartureTime": "09:15",
      "hiddenStops": [
        {
          "airportCode": "DFW",
          "departureDate": "2024-07-09",
          "departureTime": "09:15",
          "arrivalDate": "2024-07-09",
          "arrivalTime": "12:28",
          "aircraftTypeCode": "E90",
          "aircraftTypeName": "EMBRAER EMB E90",
          "durationInMinutes": 300
        }
      ],
      "travelerIndices": [
        1
      ],
      "identityDocuments": [
        {
          "itemId": "76c2817b178cc264fa44cf85df1da5fb9e1b963006b2339aa5edc09129415bba5fcf5bf91a5f",
          "status": "Confirmed"
        }
      ],
      "isPast": false
    }
  ],
  "journeys": [
    {
      "firstAirportCode": "DFW",
      "departureDate": "2024-07-09",
      "departureTime": "09:15",
      "lastAirportCode": "HNL",
      "numberOfFlights": 1
    }
  ],
  "fareRules": [
    {
      "originAirportCode": "DFW",
      "destinationAirportCode": "ATL",
      "owningAirlineCode": "AA",
      "passengerCode": "ADT",
      "isRefundable": true,
      "refundPenalties": [
        {
          "applicability": "BEFORE_DEPARTURE",
          "conditionsApply": false,
          "penalty": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ],
      "isChangeable": true,
      "exchangePenalties": [
        {
          "applicability": "BEFORE_DEPARTURE",
          "conditionsApply": false,
          "penalty": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ]
    }
  ],
  "fareOffers": [
    {
      "travelerIndices": [
        1
      ],
      "flights": [
        {
          "itemId": "12"
        }
      ],
      "cabinBaggageAllowance": {
        "maximumPieces": 1,
        "totalWeightInPounds": 50,
        "totalWeightInKilograms": 23,
        "baggagePieces": [
          {
            "maximumSizeInInches": 46,
            "maximumSizeInCentimeters": 118,
            "maximumWeightInPounds": 50,
            "maximumWeightInKilograms": 23,
            "numberOfPieces": 1,
            "specialItemDescription": "SKI EQUIPMENT",
            "isCheckInOnly": true,
            "fee": {
              "amount": "100.00",
              "currencyCode": "USD"
            }
          }
        ]
      },
      "checkedBaggageAllowance": {
        "maximumPieces": 1,
        "totalWeightInPounds": 50,
        "totalWeightInKilograms": 23,
        "baggagePieces": [
          {
            "maximumSizeInInches": 46,
            "maximumSizeInCentimeters": 118,
            "maximumWeightInPounds": 50,
            "maximumWeightInKilograms": 23,
            "numberOfPieces": 1,
            "specialItemDescription": "SKI EQUIPMENT",
            "isCheckInOnly": true,
            "fee": {
              "amount": "100.00",
              "currencyCode": "USD"
            }
          }
        ]
      },
      "cabinBaggageCharges": [
        {
          "maximumSizeInInches": 46,
          "maximumSizeInCentimeters": 118,
          "maximumWeightInPounds": 50,
          "maximumWeightInKilograms": 23,
          "numberOfPieces": 1,
          "specialItemDescription": "SKI EQUIPMENT",
          "isCheckInOnly": true,
          "fee": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ],
      "checkedBaggageCharges": [
        {
          "maximumSizeInInches": 46,
          "maximumSizeInCentimeters": 118,
          "maximumWeightInPounds": 50,
          "maximumWeightInKilograms": 23,
          "numberOfPieces": 1,
          "specialItemDescription": "SKI EQUIPMENT",
          "isCheckInOnly": true,
          "fee": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ]
    }
  ],
  "fares": [
    {
      "creationDetails": {
        "creationUserSine": "A12",
        "creationDate": "2024-01-09",
        "creationTime": "15:00",
        "purchaseDeadlineDate": "2024-01-09",
        "purchaseDeadlineTime": "15:00",
        "agencyIataNumber": "99119911",
        "userWorkPcc": "AB12",
        "userHomePcc": "CD34",
        "primeHostId": "1S"
      },
      "airlineCode": "AA",
      "fareCalculationLine": "BUE AA DFW Q430.00 5740.00NUC6170.00END ROE1.00 XT175.50TQ175.50QO315.90US96.50YC122.90XY69.50XA",
      "tourCode": "123456789ABCDE",
      "isNegotiatedFare": true,
      "travelerIndices": [
        1
      ],
      "commission": {
        "commissionAmount": "25.00",
        "currencyCode": "USD",
        "commissionPercentage": "5.00"
      },
      "fareConstruction": [
        {
          "flights": [
            {
              "itemId": "12"
            }
          ],
          "flightIndices": [
            1
          ],
          "fareBasisCode": "ABCDE10",
          "baseRate": {
            "amount": "100.00",
            "currencyCode": "USD"
          },
          "brandFareCode": "ECOFLEX",
          "brandFareName": "ECO FLEX",
          "brandProgramCode": "CFFLH",
          "brandProgramName": "LH BRANDED FARES INTERCONT",
          "brandAttributes": [
            {
              "itemId": "SABRE_NDCC_ID_1",
              "description": "Qantas Points"
            }
          ],
          "isCurrentItinerary": false,
          "checkedBaggageAllowance": {
            "maximumPieces": 1,
            "totalWeightInPounds": 50,
            "totalWeightInKilograms": 23,
            "baggagePieces": [
              {
                "maximumSizeInInches": 46,
                "maximumSizeInCentimeters": 118,
                "maximumWeightInPounds": 50,
                "maximumWeightInKilograms": 23,
                "numberOfPieces": 1,
                "specialItemDescription": "SKI EQUIPMENT",
                "isCheckInOnly": true,
                "fee": {
                  "amount": "100.00",
                  "currencyCode": "USD"
                }
              }
            ]
          }
        }
      ],
      "taxBreakdown": [
        {
          "taxCode": "XY",
          "taxAmount": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ],
      "totals": {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      },
      "pricingTypeCode": "S",
      "pricingTypeName": "Manual",
      "pricingStatusCode": "A",
      "pricingStatusName": "Active",
      "hasValidPricing": false,
      "requestedTravelerType": "C08",
      "pricedTravelerType": "C08",
      "recordTypeCode": "PQ",
      "recordTypeName": "Price Quote",
      "recordId": "12"
    }
  ],
  "remarks": [
    {
      "type": "GENERAL",
      "alphaCode": "T",
      "text": "XXATW/"
    }
  ],
  "hotels": [
    {
      "itemId": "12",
      "confirmationId": "23428937429074",
      "hotelName": "Ilia Hotel and Luxury Suites",
      "address": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n",
        "cityCode": "DFW"
      },
      "checkInDate": "2024-07-09",
      "checkInTime": "15:00",
      "checkOutDate": "2024-07-19",
      "checkOutTime": "11:00",
      "corporateDiscountCode": 6878700,
      "leadTravelerIndex": 1,
      "room": {
        "roomType": "2 double beds",
        "quantity": 1,
        "description": "Deluxe Room, 2 Double Beds",
        "roomTypeCode": "100144834",
        "productCode": "SM3A00",
        "roomRate": {
          "amount": "100.00",
          "currencyCode": "USD"
        },
        "travelerIndices": [
          1
        ],
        "agencyCommission": {
          "commissionAmount": "25.00",
          "currencyCode": "USD",
          "commissionPercentage": "5.00"
        }
      },
      "isRefundable": false,
      "refundPenalties": [
        {
          "applicableFromDate": "2024-07-07T16:00:00Z",
          "applicableToDate": "2024-07-09T16:00:00Z",
          "penalty": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ],
      "refundPenaltyPolicyCode": "01D",
      "hotelStatusCode": "HK",
      "hotelStatusName": "Confirmed",
      "chainCode": "BY",
      "chainName": "Banyan Tree Hotels and Resorts",
      "propertyId": "100144834",
      "sabrePropertyId": "7678",
      "contactInfo": {
        "emails": [
          "travel@sabre.com"
        ],
        "phones": [
          "+1-555-123-4567"
        ],
        "faxes": [
          "+1-555-123-4567"
        ],
        "emergencyPhones": [
          "+1-555-123-4567"
        ]
      },
      "specialInstructions": "Need a wi-fi in the room.",
      "guaranteeTypeCode": 5,
      "guaranteeTypeName": "Credit card",
      "guaranteePaymentNote": "GVI4XXXXXXXXXXX1111EXP 01 25-HOTEL",
      "paymentPolicy": "DEPOSIT",
      "payment": {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      },
      "numberOfGuests": 1,
      "associatedFlightDetails": {
        "arrivalAirlineCode": "AA",
        "arrivalFlightNumber": 123,
        "arrivalTime": "12:28",
        "departureAirlineCode": "AA",
        "departureFlightNumber": 123,
        "departureTime": "09:15"
      },
      "sourceTypeCode": 100,
      "sourceTypeName": "Sabre GDS"
    }
  ],
  "cars": [
    {
      "itemId": "12",
      "confirmationId": "843296421",
      "travelerIndex": 1,
      "vendorName": "National",
      "vendorCode": "ZE",
      "pickUpLocationCode": "DFW",
      "pickUpAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      },
      "pickUpDate": "2024-07-09",
      "pickUpTime": "13:00",
      "pickUpContactInfo": {
        "emails": [
          "travel@sabre.com"
        ],
        "phones": [
          "+1-555-123-4567"
        ],
        "faxes": [
          "+1-555-123-4567"
        ],
        "emergencyPhones": [
          "+1-555-123-4567"
        ]
      },
      "dropOffLocationCode": "DEN",
      "dropOffAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      },
      "dropOffDate": "2024-07-19",
      "dropOffTime": "12:00",
      "dropOffContactInfo": {
        "emails": [
          "travel@sabre.com"
        ],
        "phones": [
          "+1-555-123-4567"
        ],
        "faxes": [
          "+1-555-123-4567"
        ],
        "emergencyPhones": [
          "+1-555-123-4567"
        ]
      },
      "collectionAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US"
      },
      "collectionSite": {
        "id": "ABC123",
        "name": "TEST LOCATION",
        "phone": "8175551212"
      },
      "deliveryAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US"
      },
      "deliverySite": {
        "id": "ABC123",
        "name": "TEST LOCATION",
        "phone": "8175551212"
      },
      "isRefundable": false,
      "refundPenalties": [
        {
          "applicableFromDate": "2024-07-07T16:00:00Z",
          "applicableToDate": "2024-07-09T16:00:00Z",
          "penalty": {
            "amount": "100.00",
            "currencyCode": "USD"
          }
        }
      ],
      "carStatusCode": "HK",
      "carStatusName": "Confirmed",
      "vehicleTypeCode": "MBMR",
      "vehicleTypeName": "Two/Three Door",
      "numberOfVehicles": 1,
      "rateCode": "RCUD1",
      "distanceAllowance": "UNL",
      "guaranteePaymentNote": "GVI4XXXXXXXXXXX0008EXP 03 22-TEST CAR",
      "specialInstructions": "NON-SMOKING CAR PLEASE",
      "payment": {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    }
  ],
  "trains": [
    {
      "itemId": "12",
      "confirmationId": "76E220",
      "trainNumber": "822",
      "trainName": "Heartland Flyer",
      "vendorCode": "2V",
      "vendorName": "Amtrak",
      "operatingVendorCode": "2V",
      "operatingVendorName": "Amtrak",
      "fromStationCode": "FTW",
      "fromStationName": "Central Station",
      "toStationCode": "ATL",
      "toStationName": "Peachtree Station",
      "departureDate": "2024-07-10",
      "departureTime": "19:15",
      "arrivalDate": "2024-07-10",
      "arrivalTime": "23:10",
      "isRefundable": true,
      "trainStatusCode": "HK",
      "trainStatusName": "Confirmed",
      "payment": {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    }
  ],
  "cruises": [
    {
      "itemId": "12",
      "confirmationId": "XPCD8Q",
      "vendorCode": "PC",
      "shipCode": "RP",
      "shipName": "Royal Princess",
      "fromPortCode": "ANC",
      "toPortCode": "YVR",
      "departureDate": "2024-07-12",
      "departureTime": "16:00",
      "arrivalDate": "2024-07-15",
      "arrivalTime": "09:00",
      "numberOfGuests": 2,
      "cabinNumber": "C101",
      "cruiseStatusCode": "GK",
      "cruiseStatusName": "Confirmed"
    }
  ],
  "allSegments": [
    {
      "id": "12",
      "type": "FLIGHT",
      "text": "123",
      "vendorCode": "AA",
      "date": "2024-07-09",
      "time": "09:15",
      "locationCode": "ATL",
      "address": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      },
      "startDate": "2024-07-09",
      "startTime": "09:15",
      "startLocationCode": "DFW",
      "startAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      },
      "endDate": "2024-07-09",
      "endTime": "12:28",
      "endLocationCode": "HNL",
      "endAddress": {
        "street": "1230 Ellen Ave, apt 10",
        "city": "Dallas",
        "stateProvince": "TX",
        "postalCode": "75063",
        "countryCode": "US",
        "name": "John Smith",
        "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
      }
    }
  ],
  "flightTickets": [
    {
      "number": "0167489825830",
      "date": "2024-07-01",
      "agencyIataNumber": "12344321",
      "airlineCode": "AA",
      "travelerIndex": 1,
      "flightCoupons": [
        {
          "itemId": "12",
          "couponStatus": "Printed",
          "couponStatusCode": "PR"
        }
      ],
      "allCoupons": [
        {
          "couponStatus": "Printed",
          "couponStatusCode": "PR",
          "itemId": "12"
        }
      ],
      "payment": {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      },
      "isBundledTicket": true,
      "ticketStatusName": "Issued",
      "ticketStatusCode": "TE",
      "ticketingPcc": "G7HE",
      "commission": {
        "commissionAmount": "25.00",
        "currencyCode": "USD",
        "commissionPercentage": "5.00"
      }
    }
  ],
  "payments": {
    "flightTotals": [
      {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    ],
    "flightCurrentTotals": [
      {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    ],
    "hotelTotals": [
      {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    ],
    "carTotals": [
      {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    ],
    "trainTotals": [
      {
        "subtotal": "100.00",
        "taxes": "8.00",
        "fees": "20.00",
        "total": "128.00",
        "currencyCode": "USD",
        "netRemit": "110.00"
      }
    ],
    "formsOfPayment": [
      {
        "cardTypeCode": "VI",
        "cardNumber": "4537156488578956",
        "cardSecurityCode": "123",
        "expiryDate": "2024-07",
        "extendedPayment": 12,
        "miscellaneousCreditCode": "PL189947",
        "numberOfInstallments": 4,
        "airlinePlanCode": "RG065",
        "installmentAmount": "100",
        "type": "CHECK",
        "cardHolder": {
          "givenName": "John",
          "surname": "Smith",
          "email": "john@smith.family.priv",
          "phone": "+1-555-123-4567",
          "address": {
            "street": "1230 Ellen Ave, apt 10",
            "city": "Dallas",
            "stateProvince": "TX",
            "postalCode": "75063",
            "countryCode": "US"
          }
        },
        "manualApproval": {
          "code": "12345",
          "requestDateTime": "2024-07-09T09:15:00Z",
          "expiryDateTime": "2024-07-09T09:15:00Z",
          "airlineCode": "AA",
          "amount": "100.00",
          "currencyCode": "USD"
        },
        "authentications": [
          {
            "secureAuthenticationValue": "ABC123455533533444455555678",
            "secureTransactionId": "ABCDEFGHI123456789012!.1234567890123",
            "issueCode": "AO",
            "resultCode": "OK",
            "cardNumberCollectionCode": "K",
            "channelCode": "MO",
            "electronicCommerceIndicator": "12",
            "exemptionTypeCode": "SC",
            "updatedDateTime": "2024-07-07T16:00:00Z",
            "mandateTypeCode": "NA",
            "merchantName": "TEST CREDIT CARD",
            "originalPaymentReference": "1234547839012345",
            "amount": "1234.56",
            "currencyCode": "USD",
            "tokenAuthenticationValue": "ABC3434334343556677487312567",
            "verificationResultCode": "PASS",
            "version": "120"
          }
        ],
        "virtualCard": {
          "customerAccountCode": "John",
          "agencyEmail": "john@smith.family.priv",
          "hotelFax": "+1-555-123-4567",
          "hotelName": "Ilia Hotel and Luxury Suites",
          "roomType": "2 double beds",
          "roomDescription": "Deluxe Room, 2 Double Beds",
          "rateAmount": {
            "amount": "100.00",
            "currencyCode": "USD"
          },
          "virtualCardCharges": [
            "Breakfast"
          ]
        },
        "agencyIataNumber": "129345738",
        "agencyAddress": {
          "street": "1230 Ellen Ave, apt 10",
          "city": "Dallas",
          "stateProvince": "TX",
          "postalCode": "75063",
          "countryCode": "US",
          "name": "John Smith",
          "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
        },
        "corporateId": "CC006",
        "companyAddress": {
          "street": "1230 Ellen Ave, apt 10",
          "city": "Dallas",
          "stateProvince": "TX",
          "postalCode": "75063",
          "countryCode": "US",
          "name": "John Smith",
          "freeText": "John Smith\n1230 Ellen Ave, Apt 10\nDallas, TX 75063\nUS\n"
        },
        "voucher": {
          "billingNumber": "1234567",
          "type": "FC"
        },
        "netBalance": "300.20",
        "docketPrefix": "AGT*V",
        "docketNumber": "654456",
        "docketIssuingAgentInitials": "LS",
        "docketDescription": "DOCKET NUM 0123456",
        "governmentTravelRequestDescription": "REQ-123456",
        "invoiceDescription": "AGT INVOICE",
        "useType": "Unknown",
        "tripType": "Unknown",
        "useTypes": [
          "Unknown"
        ],
        "tripTypes": [
          "Unknown"
        ],
        "isAgencyPaymentCard": false
      }
    ]
  },
  "otherServices": [
    {
      "airlineCode": "AA",
      "chainCode": "BY",
      "vendorCode": "ZE",
      "travelerIndex": 1,
      "serviceMessage": "/CX-J674A0957C0"
    }
  ],
  "futureTicketingPolicy": {
    "ticketingPcc": "G7RE",
    "queueNumber": "55",
    "ticketingDate": "2024-07-09",
    "ticketingTime": "11:00",
    "comment": "TICKET BEFORE TUES"
  },
  "specialServices": [
    {
      "travelerIndices": [
        1
      ],
      "flights": [
        {
          "itemId": "12"
        }
      ],
      "code": "WCHR",
      "name": "Wheelchair/Passenger can walk up stairs",
      "message": "/PREPAID",
      "statusCode": "HK",
      "statusName": "Confirmed"
    }
  ],
  "retentionEndDate": "2024-01-30",
  "retentionLabel": "RETENTION DATE",
  "accountingItems": [
    {
      "fareApplicationType": "Single Traveler",
      "formOfPaymentType": "Cash",
      "creationType": "Exchange",
      "airlineCode": "AA",
      "ticketNumber": "2200011234567",
      "commission": {
        "commissionAmount": "25.00",
        "currencyCode": "USD",
        "commissionPercentage": "5.00"
      },
      "fareAmount": "520.00",
      "taxAmount": "123.00",
      "travelerIndices": [
        1
      ],
      "tariffBasisType": "Foreign",
      "cardNumber": "4537156488578956",
      "cardTypeCode": "VI",
      "currencyCode": "USD"
    }
  ],
  "nonElectronicTickets": [
    {
      "ticketStatus": "Active",
      "ticketNumber": "0011234567899",
      "travelerIndex": 1,
      "ticketingUserCode": "A12",
      "ticketingPcc": "G7HE",
      "date": "2024-07-01",
      "time": "09:15"
    }
  ],
  "travelersEmployers": [
    {
      "street": "1230 Ellen Ave, apt 10",
      "city": "Dallas",
      "stateProvince": "TX",
      "postalCode": "75063",
      "countryCode": "US",
      "idType": "GST",
      "employerId": "22AAAAA0000A1Z5",
      "employerName": "Sabre",
      "phones": [
        {
          "number": "+1-555-123-4567",
          "label": "M"
        }
      ],
      "emails": [
        "john@gst.company.com"
      ]
    }
  ],
  "timestamp": "2024-10-28T11:11:21Z",
  "bookingSignature": "76c2817b178cc264fa44cf85df1da5fb9e1b963006b2339aa5edc09129415bba5fcf5bf91a5f",
  "request": {
    "confirmationId": "GLEBNY",
    "bookingSource": "SABRE",
    "targetPcc": "G7HE",
    "givenName": "John",
    "middleName": "W",
    "surname": "Smith",
    "returnOnly": [
      "FLIGHTS"
    ],
    "extraFeatures": {
      "returnFrequentRenter": false,
      "returnWalletFormsOfPayment": false,
      "returnFiscalId": false,
      "returnEmptySeatObjects": true
    },
    "unmaskPaymentCardNumbers": false
  },
  "errors": [
    {
      "category": "BAD_REQUEST",
      "type": "REQUIRED_FIELD_MISSING",
      "description": "may not be null",
      "fieldPath": "someObject.someFieldName",
      "fieldName": "someName",
      "fieldValue": "field value"
    }
  ]
}
```


---

### 2. Display Booking and Validate Surname

#### **Request**
```json
{
  "confirmationId": "XXXX",
  "surname": "SMITH"
}
```

#### **Response**
Returns booking information if the surname matches; otherwise, a validation error is returned.

---

### 3. Display Selected Booking Elements

#### **Request**
```json
{
    "confirmationId": "XXXX",
    "returnOnly": [ "TICKETS" ]
}
```

#### **Response**
```json
{
    "flightTickets": [{
        "number": "1609786952746",
        "date": "2023-03-20",
        "travelerIndex": 1,
        "ticketStatusName": "Refunded/Exchanged",
        "ticketStatusCode": "TR"
    }]
}
```
## Request Parameters

### Headers

| **Header**	| **Type**	| **Description** |
|----------------|----------------|-------------|
| Authorization	| String |	Bearer token for authentication|
| Content-Type	| String | Must be application/json|

### Request Body
| **Field**         | **Type**          | **Description** |
|----------------|----------------|-------------|
| `confirmationId` | `string` | The booking reference ID as shown in the supplier/vendor system. |
| `bookingSource` | `string` | Identifies the source of the booking (default: `SABRE`). |
| `targetPcc` | `string` | The pseudo city code where booking retrieval is requested. |
| `givenName` | `string` | The traveler's first name. |
| `middleName` | `string` | The traveler's middle name or initial. |
| `surname` | `string` | The traveler's last name. |
| `returnOnly` | `array` | Lists response sections returned by the service. |

## Response Parameters
| **Field**                 | **Type**            | **Description**  |
|--------------------------|----------------------|----------------|
| **bookingId**            |  `string`           | The booking reference ID from the supplier/vendor system. For SABRE, this is the PNR Locator or NDC orderId value, depending on content type. |
| **startDate**            | `string`             | The start date of the booking. |
| **endDate**              | `string`          | The end date of the booking. |
| **isCancelable**         | `boolean`   | If `true`, the booking is cancelable in full or in segments. Refer to `refundPenalties` for more details. |
| **isTicketed**           | `boolean`   | If `true`, a ticket(s) was issued for the booking. |
| **agencyCustomerNumber** | `string`    | The travel agency customer identifier, also known as the customer number or DK number. |
| **creationDetails**      | `object`    | Contains user, date, and time details regarding the creation of the booking. |
| **contactInfo**          | `array`     | Lists all contact information associated with the booking. |
| **travelers**            | `array`     | Lists all traveler(s) associated with the booking. |
| **emails**               | `array`     | Lists all email addresses of the traveler. |
| **phones**               | `array`     | Lists all phone numbers associated with the traveler. |
| **remarks**              | `array`     | Lists all remarks associated with the booking. |
| **address**              | `object`    | Contains the traveler’s address information. |
| **identityDocuments**    | `array`     | Lists all documents associated with the traveler. |
| **loyaltyPrograms**      | `array`     | Lists all loyalty programs like frequent flyer programs associated with the traveler. |
| **ancillaries**          | `array`     | Lists details of ancillary services. |
| **travelersGroup**       | `object`    | Contains information about the group the travelers belong to. |
| **flights**              | `array`     | Lists all flights associated with the booking in chronological order. |
| **journeys**             | `array`     | Lists all journeys associated with the booking. One-way bookings contain a single journey, round-trips contain two, and multi-destination bookings contain more than two. |
| **fareRules**            | `array`     | Lists fare rule information displayed at the time of purchase. |
| **fareOffers**           | `array`     | Lists ancillary offers for selected flights identified by `itemId` flight references. |
| **fares**                | `array`     | Lists fare details information based on active price quotes in the booking. |
| **hotels**               | `array`     | Lists all hotel reservations associated with the booking. |
| **cars**                 | `array`     | Lists all car rentals associated with the booking. |
| **trains**               | `array`     | Lists all train reservations associated with the booking. |
| **cruises**              | `array`     | Lists all cruise reservations associated with the booking. |
| **allSegments**          | `array`     | Lists all segments in the reservation using a generic model. |
| **flightTickets**        | `array`     | Lists all flight tickets associated with the booking. |
| **futureTicketingPolicy**| `object`    | Contains detailed ticket arrangements for a future date. |
| **retentionEndDate**     | `string`    | The retention date of the booking. |
| **retentionLabel**       | `string`    | The label associated with the retention date. |
| **bookingSignature**     | `string`    | The unique ID of the Get Booking response. |

---

## Error Handling 

This section provides a list of potential errors that may occur when retrieving booking detail.
| **HTTP Status** | **Error Code** | **Description** |
|------------|------------|-------------|
| INVALID_MESSAGE | APPLICATION_ERROR | Incorrect booking request |
| UNAUTHORIZED_ACCESS | UNAUTHORIZED | Expired or invalid security token |
| UNAUTHORIZED_ACCESS | UNAUTHORIZED | Invalid security token. |
| UNAUTHORIZED_ACCESS | UNAUTHORIZED | Booking cannot be retrieved due to authorization issues in the security systems. Please verify the used credentials with your account manager. |
| UNAUTHORIZED_ACCESS | RESOURCE_RESTRICTED | Access to selected booking is restricted. Verify the used credentials and Travel Journal Record settings with your account manager. |
| FORBIDDEN_ACCESS | FORBIDDEN | Booking details could not be retrieved. The downline service returned a forbidden access. Please retry or verify the used credentials with your account manager. |
| INTERNAL_SERVER_TIMEOUT | APPLICATION_ERROR | Call to internal service timed out. |
| BOOKING_NOT_FOUND | RESOURCE_NOT_FOUND | Booking cannot be found |
| RESOURCE_UNAVAILABLE | WARNING | Some resource cannot be populated for given reservation. Details are returned in fieldName, fieldPath and fieldValue. |
| RESOURCE_UNAVAILABLE | WARNING | Resource cannot be populated. Details not available for manually generated pricing information saved in the booking. |
| RESOURCE_UNAVAILABLE | WARNING | Details for ticket with number: %s cannot be populated. |
| RESOURCE_UNAVAILABLE | WARNING | Cannot populate some data for flight. |
| RESOURCE_UNAVAILABLE | WARNING | Unable to populate additional data for %s: %s |
| JOURNEY_DATA_MISSING | WARNING | Journey details cannot be determined due to Leg Detection service failure. |
| BOOKING_RETRIEVAL | APPLICATION_ERROR | Booking cannot be retrieved |
| INVALID_VALUE | BAD_REQUEST | Invalid filtering option. Available options are: |
| INVALID_VALUE | BAD_REQUEST | Validation Failed: |
| UNPARSEABLE_REQUEST | BAD_REQUEST | Invalid Syntax |
| DOWNLINE_SERVICE_FAILURE | APPLICATION_ERROR | Cannot connect to underlying system |
| FAULT_RESPONSE | APPLICATION_ERROR | The underlying system cannot process request at this time. |
| INTERNAL_PROCESSING_TIMEOUT | APPLICATION_ERROR | Penalty information was not obtained due to the unexpectedly long processing time of the %s service. |
| TRANSACTION_PROCESSING_TIMEOUT | APPLICATION_ERROR | Unable to initiate a stateful transaction due to the unexpectedly long processing time of the %v service. |

## References
- [Booking Management API - Reference Documentation](https://developer.sabre.com/docs/rest_apis/trip/orders/booking_management/reference-documentation)
- [Get Booking - Examples](https://developer.sabre.com/get-booking-examples)
- [Booking Management API - Get Booking (Error List)](https://developer.sabre.com/docs/rest_apis/trip/orders/booking_management/help?page=get-booking-error-list)

### License
This API documentation is provided under the MIT License.
