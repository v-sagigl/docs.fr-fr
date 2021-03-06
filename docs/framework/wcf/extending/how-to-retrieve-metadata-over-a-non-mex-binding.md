---
title: 'Procédure : récupérer des métadonnées sur une liaison non-MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 4a127e3e2283050018705c85606bd7c03c36de8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766777"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Procédure : récupérer des métadonnées sur une liaison non-MEX
Cette rubrique décrit comment récupérer les métadonnées d'un point de terminaison MEX sur une liaison non-MEX. Le code dans cet exemple est basé sur le [personnalisé sécuriser les métadonnées de point de terminaison](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemple.  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Pour récupérer des métadonnées sur une liaison non-MEX  
  
1. Déterminez la liaison utilisée par le point de terminaison MEX. Pour les services Windows Communication Foundation (WCF), vous pouvez déterminer la liaison MEX en accédant au fichier de configuration du service. Dans ce cas, la liaison MEX est définie dans la configuration de service suivante :  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. Dans le fichier de configuration client, configurez la même liaison personnalisée. Dans ce cas, le client définit également un comportement `clientCredentials` pour fournir un certificat permettant d'authentifier auprès du service lors de la demande des métadonnées provenant du point de terminaison MEX. Lorsque vous utilisez Svcutil.exe pour demander les métadonnées sur une liaison personnalisée, vous devez ajouter la configuration du point de terminaison MEX au fichier de configuration de Svcutil.exe (Svcutil.exe.config), et le nom de la configuration du point de terminaison doit correspondre au schéma d’URI de l’adresse du point de terminaison MEX, comme indiqué dans le code suivant.  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3. Créez un `MetadataExchangeClient` et appelez `GetMetadata`. Cette opération peut s'effectuer de deux manières différentes : vous pouvez spécifier la liaison personnalisée dans la configuration ou dans le code, comme indiqué dans l'exemple suivant.  
  
    ```  
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. Créez un `WsdlImporter`, puis appelez `ImportAllEndpoints`, comme illustré dans le code suivant.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. À ce stade, vous disposez d’une collection de points de terminaison de service. Pour plus d’informations sur l’importation de métadonnées, consultez [Comment : Importer des métadonnées dans les points de terminaison de Service](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Voir aussi

- [Métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md)
