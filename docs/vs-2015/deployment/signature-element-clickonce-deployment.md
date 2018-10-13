---
title: '&lt;Подпись&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fe93a951fdde4a1aa4ad6d2c300551988e42c82b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266959"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Подпись&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Содержит сведения, необходимые для того, чтобы подписать этот манифест развертывания с помощью цифровой подписи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Примечания  
 Подписи манифеста развертывания с помощью подписи конверт является необязательным, но рекомендуется. Дополнительные сведения о подписи XML файлов см. в разделе World Wide Web консорциума W3c «XML-Signature Syntax and Processing,» описано в статье [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Если требуется подписать манифест, необходимо создать хэши для всех файлов. Не удалось подписать манифест с файлами, которые не хэшируются, потому, что пользователи не могут проверить содержимое нехэшированных файлов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `Signature` элемента в манифесте развертывания, используемые в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания.  
  
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
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)



