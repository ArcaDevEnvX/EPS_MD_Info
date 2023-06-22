# ELENCO PARAMETRI
- `baseurl`            = URL BASE
    - default =  
- `call`               = Chiamata da effettuare
    - default = permit_get
- `refreshtoken`       = Token auth di EasyPark
    - default =  
- `parameters`         = Parametri URL
    - default = 
- `requestbodypath`    = Path file da dove leggere la request body
    - default = requestbody.txt
- `responsepath`       = Path file dove scrivere la risposta
    - default = response.txt
# ELENCO CALL IMPLEMENTATE
- "permit_create"
- "permit_get"
- "permit_findallareas"
- "permit_batch_delete"
# UTILIZZO
- modifica il file "requestparams.txt" con i parametri della richiesta e "requestbody.txt" con la richiesta da inviare in caso di chiamata POST
- da cmd esegui l'exe con i relativi parametri 

# Esempi:
Considera per gli esempi come valori fissi:
- baseurl= 
- redfreshtoken= 
- requestbodypath=requestbody.txt
- responsepath=response.txt
## PERMIT_CREATE
### Comando: 
    EasyParkService.exe -call=permit_create
### Contenuto requestbody.txt con la lista di permessi da creare:
    [{"carLicenceNumber":"CP269AW",
            "discountRate":0,
            "maxDiscount":null,
            "parkingareaNumbers":[{"areaCountryCode":"IT",
            "areaNo":22137}],
            "permitAreaName":"Zona 1 Agevolazione",
            "permitIdentifier":"USE_CARLICENCENUMBER",
            "permitName":"ROSA",
            "permitNote":null,
            "phoneNumber":null,
            "priceExclVat":null,
            "priceNotSubjectToVat":null,
            "priceTotal":0.0,
            "priceVat":null,
            "remainingParkingMinutes":null,
            "validFrom":"2022-01-28T00:00:00",
            "validTo":"2022-03-31T00:00:00",
            "visibleForEnforcement":false},
        {"carLicenceNumber":"FF550VH",
            "discountRate":0,
            "maxDiscount":null,
            "parkingareaNumbers":[{"areaCountryCode":"IT",
            "areaNo":22137}],
            "permitAreaName":"Zona 1 Agevolazione",
            "permitIdentifier":"USE_CARLICENCENUMBER",
            "permitName":"ROSA",
            "permitNote":null,
            "phoneNumber":null,
            "priceExclVat":null,
            "priceNotSubjectToVat":null,
            "priceTotal":0.0,
            "priceVat":null,
            "remainingParkingMinutes":null,
            "validFrom":"2022-10-05T00:00:00",
            "validTo":"2022-12-31T00:00:00",
            "visibleForEnforcement":false}]
### Possibili risposte:
    [{code: 200, codedescription: OK, content: [{"permitName":"ROSA","permitAreaName":"Zona 1 Agevolazione","parkingareaNo":22137,"countryCode":"IT","discountRate":0,"maxDiscount":0,"remainingParkingMinutes":0,"visibleForEnforcement":false,"carLicenceNumber":"FF550VH","phoneNumber":"","permitIdentifier":"USE_CARLICENCENUMBER","validFrom":"2022-10-05T00:00:00.000+0000","validTo":"2022-12-31T00:00:00.000+0000","priceTotal":0,"priceExclVat":0,"priceNotSubjectToVat":0,"priceVat":0,"permitNote":"","uniqueId":"997755f9-8975-4274-b2fb-df414e96bcba"}], error: },{code: 200, codedescription: OK, content: [{"permitName":"ROSA","permitAreaName":"Zona 1 Agevolazione","parkingareaNo":22137,"countryCode":"IT","discountRate":0,"maxDiscount":0,"remainingParkingMinutes":0,"visibleForEnforcement":false,"carLicenceNumber":"DP239AG","phoneNumber":"","permitIdentifier":"USE_CARLICENCENUMBER","validFrom":"2022-01-01T00:00:00.000+0000","validTo":"2022-12-31T00:00:00.000+0000","priceTotal":0,"priceExclVat":0,"priceNotSubjectToVat":0,"priceVat":0,"permitNote":"","uniqueId":"d6c409bc-5610-4177-b3dd-20001ac48e67"}], error: }]
## PERMIT_GET
### Comando: 
    EasyParkService.exe -call=permit_get -parameters={\"permitUniqueId\":\"c8228e78-b5bf-4adc-9adb-724ae35dd85b\"}
### Possibili risposte:
    - [{code: 200, codedescription: OK, content: , error: }]
    - [{code: 200, codedescription: OK, content: [{"permitName":"ROSA","permitAreaName":"Zona 1 Agevolazione","parkingareaNo":22137,"countryCode":"IT","discountRate":0,"maxDiscount":0,"remainingParkingMinutes":0,"visibleForEnforcement":false,"carLicenceNumber":"FF550VH","phoneNumber":"","permitIdentifier":"USE_CARLICENCENUMBER","validFrom":"2022-10-05T00:00:00.000+0000","validTo":"2022-12-31T00:00:00.000+0000","priceTotal":0,"priceExclVat":0,"priceNotSubjectToVat":0,"priceVat":0,"permitNote":"","uniqueId":"997755f9-8975-4274-b2fb-df414e96bcba"}], error: }]
    - [{code: 404, codedescription: Not Found, content: , error: {"timestamp":"2023-05-18T14:23:57.130+0000","status":404,"error":"Not  Found","message":"No message available","path":"/api/permit/"}}]
## PERMIT_FINDALLAREAS
### Comando: 
    EasyParkService.exe -call=permit_findallareas
## PERMIT_BATCH_DELETE
### Comando: 
    EasyParkService.exe -call=permit_batch_delete
### Contenuto requestbody.txt con la lista di permessi da creare:
        [
            {"applicationUniqueId":"IDPROVA1"},
            {"applicationUniqueId":"IDPROVA2"},
            {"applicationUniqueId":"IDPROVA3"}
        ]
