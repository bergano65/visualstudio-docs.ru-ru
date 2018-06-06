---
title: '&lt;Подпись&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02a7fb2ab17d5a8f8a8e141814be432a119bf82
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814964"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Подпись&gt; элемент (развертывание ClickOnce)
Содержит сведения, необходимые для того, чтобы подписать этот манифест развертывания с помощью цифровой подписи.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Примечания  
 Подписывать манифест развертывания с помощью подписи конверт является необязательным, но рекомендуется. Дополнительные сведения о подписи XML-файлов см. World Wide Web рекомендации консорциума, «XML-синтаксис и обработка подписи,», описанную в [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Если требуется подписать манифест, необходимо создать хэши для всех файлов. Не удалось подписать манифест с файлами, которые не были хэшированы, поскольку пользователи не могут проверить содержимое нехэшированных файлов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `Signature` элемента в манифесте развертывания, используемых в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания.  
  
```xml  
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
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)