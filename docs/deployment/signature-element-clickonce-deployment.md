---
title: "Элемент &lt;Signature&gt; (развертывание ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> - элемент [манифест развертывания ClickOnce]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# Элемент &lt;Signature&gt; (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит сведения, необходимые для цифровой подписи данного манифеста развертывания.  
  
## Синтаксис  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Заметки  
 Подписывать манифест развертывания с помощью запечатывающей подписи не обязательно, но рекомендуется.  Дополнительную информацию о подписании файлов XML см. в рекомендательном документе консорциума W3C "Синтаксис и обработка XML\-подписей", расположенном по адресу [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/).  
  
 Если требуется подписать манифест, необходимо создать хэши для всех файлов.  Если манифест содержит файлы, которые не были хэшированы, его невозможно снабдить цифровой подписью, поскольку пользователи не могут проверить содержимое нехэшированных файлов.  
  
## Пример  
 В следующем примере кода показан элемент `Signature` в манифесте развертывания [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)