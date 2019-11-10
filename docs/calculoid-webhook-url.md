#
# calculoid webhook
#

Calculoid send results to specified webhook URL in last step. In results are details about API call on payment system and customer order details.
Webook URL is configurable in admin web UI. Data are in JSON format, see below.

CC server has to parse this data and check. After CC server has to run particular job in jenkins server.

```
{
  "calculatorId": "63671",
  "email": "pavera.jan@gmail.com",
  "comment": "",
  "url": "https://app.calculoid.com/#/calculator/63671",
  "id": "51190",
  "name": "Pricing test cestadocloudu.cz",
  "description": "",
  "userId": "18446",
  "webhook": "https://webhook.site/66cee174-efff-4c2c-b698-57b042f2ae1a",
  "params": {
    "newInputDesign": "1",
    "isNewCalc": "1",
    "easyredmineCrmItemControlField": "amount",
    "easyredmineCrmItemCount": "1",
    "calcualoidPreview": "0",
    "calcualoidPreviewType": "desktop",
    "shadows": "0",
    "calcAlign": "0",
    "FontSize": "1",
    "transparentBackground": "1",
    "labelAlign": "left",
    "contentAlign": "left",
    "InputAlign": "left",
    "helpTextAlign": "left",
    "formulaAlign": "left",
    "fieldBackgroundColor": "#E3E8F8",
    "colorScheme": "dark-purple",
    "showFormulaError": "0",
    "separatorThousand": "espace",
    "easyredminePriceBookQuoteActive": "1"
  },
  "userSignature": "Jan Pavera",
  "fromEmail": "jan.pavera@easysoftware.com",
  "fields": {
    "340672": {
      "calculatorFieldId": "340672",
      "value": "2",
      "id": "340672",
      "name": "Výběr programu",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "0",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0",
        "optionType": "table",
        "table": {
          "id": "202",
          "nameColumn": "2",
          "valueColumn": "0",
          "filter": {
            "1": "{F340678}"
          }
        }
      },
      "field_id": "12"
    },
    "340673": {
      "calculatorFieldId": "340673",
      "value": "0",
      "id": "340673",
      "name": "Rozšíření uživatelů",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "0",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0",
        "optionType": "table",
        "table": {
          "id": "203",
          "nameColumn": "3",
          "valueColumn": "0",
          "filter": {
            "1": "{F340678}",
            "2": "{F340672}"
          }
        }
      },
      "field_id": "12"
    },
    "340674": {
      "calculatorFieldId": "340674",
      "value": "3",
      "id": "340674",
      "name": "Výběr licence",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "1",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0",
        "optionType": "table",
        "table": {
          "id": "204",
          "nameColumn": "2",
          "valueColumn": "0",
          "filter": {
            "1": "{F340678}"
          }
        }
      },
      "field_id": "12"
    },
    "340678": {
      "calculatorFieldId": "340678",
      "value": "3",
      "id": "340678",
      "name": "Výběr konfigurace",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "0",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0",
        "optionType": "table",
        "table": {
          "id": "201",
          "nameColumn": "1",
          "valueColumn": "0"
        }
      },
      "field_id": "12"
    },
    "340730": {
      "calculatorFieldId": "340730",
      "value": "200",
      "id": "340730",
      "name": "Cena za měsíc",
      "prefix": "",
      "postfix": "Kč",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "1",
        "minHeight": "2",
        "formulaAlign": "left",
        "transparentBackground": "2",
        "oneLineField": "0",
        "invoiceEmailMessage": "",
        "emailMessage": ""
      },
      "field_id": "4"
    },
    "340736": {
      "calculatorFieldId": "340736",
      "value": "{\"country\":\"CZ\",\"checkbox\":{\"0\":true},\"oac\":false,\"email\":\"pavera.jan@gmail.com\",\"firstname\":\"Jan\",\"lastname\":\"Pavera\",\"companyName\":\"Bc. Jan Pavera\",\"address\":\"moje adresa\",\"city\":\"Praha 10\",\"zip\":\"10000\",\"paymentStatus\":\"Saving order ...\",\"price\":\"340737\"}",
      "id": "340736",
      "name": "Platební udaje",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "currency": "CZK",
        "paypalGate": "https://www.paypal.com/cgi-bin/webscr",
        "recurrentEnabled": "0",
        "recurrentEnabledField": "",
        "recurrentCycle": "M",
        "recurrentCycleField": "",
        "recurrentPeriod": "1",
        "recurrentPeriodField": "",
        "emailMessage": "<p>Hello,</p>\r\n<p></p>\r\n<p>Thank you for your order at {calculatorName}!</p>\r\n<p>{description}</p>\r\n<h3>Recapitulation of your order</h3>\r\n<p>Price: {price} {currency}</p>\r\n<p>Payment status: {status}</p>\r\n{fields}\r\n<p>Sent from: {sourceUrl}</p>\r\n<p>Best regards,<br />\r\n{userName}</p>",
        "stripeEnabled": "0",
        "stripeGate": "sandbox",
        "paypalEnabled": "1",
        "paymentGate": "invoice",
        "invoiceEnabled": "1",
        "invoiceEmailMessage": "<p>Hello,</p>\r\n<p></p>\r\n<p>Thank you for your order at {calculatorName}!</p>\r\n<p>{description}</p>\r\n<h3>Payment information</h3>\r\n<p>Price: {price} {currency}</p>\r\n<p>Reference number: {SubmissionId}</p>\r\n<p>Please send the payment to our bank account. Do not forget to include the reference number.</p>\r\n\r\n<p>Best regards,<br />\r\n{userName}</p>\r\n",
        "gaEnabled": "0",
        "gaEcommerceEnabled": "0",
        "gaAddItemToTransaction": "0",
        "fieldShow": "1",
        "minHeight": "11",
        "transparentBackground": "2",
        "oneLineField": "0",
        "showBilling": "1",
        "billingLabels": {
          "email": "E-mail",
          "firstname": "Jméno",
          "lastname": "Příjmení",
          "address": "Adresa",
          "city": "Město",
          "zip": "PSČ",
          "country": "Země",
          "companyName": "Název firmy",
          "vatid": "DIČ"
        },
        "countryPrefillGeoIP": "1",
        "countryDef": "USA",
        "pricingLabelSize": "16",
        "priceField": "340737",
        "currencyOverride": "0",
        "sendEmail": "1",
        "orderAsCompany": "1",
        "vatidRequired": "1",
        "oacLabel": "Objednat na firmu",
        "vatidViesValidation": "0",
        "viesValidationInfo": "For EU companies - please enter your VAT ID otherwise you will be charged VAT.",
        "viesValidationYes": "VAT ID is valid according to EU VIES database.",
        "viesValidationNo": "VAT ID is NOT valid due to EU VIES database.",
        "buttonText": "Pokračovat k platbě {amount} Kč",
        "checkboxes": [
          {
            "text": "Souhlasím s obchodními podmínkami",
            "url": "https://www.cestadocloudu.cz/test",
            "isRequired": "1"
          }
        ]
      },
      "field_id": "7"
    },
    "340737": {
      "calculatorFieldId": "340737",
      "value": "2280",
      "id": "340737",
      "name": "Celková cena",
      "prefix": "",
      "postfix": "Kč",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "1",
        "minHeight": "2",
        "formulaAlign": "left",
        "transparentBackground": "2",
        "oneLineField": "0"
      },
      "field_id": "4"
    },
    "340738": {
      "calculatorFieldId": "340738",
      "value": "5",
      "id": "340738",
      "name": "Sleva z celkové ceny",
      "prefix": "",
      "postfix": "%",
      "hint": "",
      "decimalPlaces": "2",
      "params": {
        "fieldShow": "1",
        "minHeight": "2",
        "formulaAlign": "left",
        "transparentBackground": "2",
        "oneLineField": "0"
      },
      "field_id": "4"
    },
    "346150": {
      "calculatorFieldId": "346150",
      "value": "0 | Uživatel",
      "id": "346150",
      "name": "Konfigurace",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "1",
        "columns": "3",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0"
      },
      "field_id": "2"
    },
    "349147": {
      "calculatorFieldId": "349147",
      "value": "1 | Jen pár dokumentů - potřebuji 20 GB",
      "id": "349147",
      "name": "Výběr programu",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "fieldShow": "1",
        "columns": "3",
        "minHeight": "2",
        "transparentBackground": "2",
        "oneLineField": "0"
      },
      "field_id": "2"
    },
    "349149": {
      "calculatorFieldId": "349149",
      "value": "1",
      "id": "349149",
      "name": "Počet uživatelů",
      "prefix": "",
      "postfix": "",
      "hint": "",
      "decimalPlaces": "0",
      "params": {
        "valueMin": "1",
        "valueMax": "10",
        "step": "1",
        "fieldShow": "1",
        "minHeight": "2",
        "InputAlign": "left",
        "transparentBackground": "2",
        "oneLineField": "0"
      },
      "field_id": "1"
    }
  },
  "payment": {
    "id": "3260",
    "status": "Pending",
    "paypalEmail": "",
    "currency": "CZK",
    "paymentGate": "invoice",
    "info": "",
    "price": "2280",
    "recurrentSettings": {
      "enabled": "0",
      "cycle": "M",
      "period": "1"
    },
    "recurrentPaidUntil": "0000-00-00",
    "gaPayload": "",
    "gaEcommercePayload": "",
    "gaItemPayload": ""
  }
}
```
