---
title: Элемент&gt; подписи &lt;(развертывание ClickOnce) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295080"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>Элемент&gt; подписи &lt;(развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Содержит сведения, необходимые для того, чтобы подписать этот манифест развертывания с помощью цифровой подписи.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Заметки  
 Подпись манифеста развертывания с помощью подписи конверта является необязательной, но рекомендуется. Дополнительные сведения о подписывании XML-файлов см. в разделе консорциум W3C рекомендации «синтаксис XML-подписи и обработка», описанная в разделе [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/).  
  
 Если вы хотите подписать манифест, необходимо предоставить хэши для всех файлов. Манифест с файлами, которые не хэшируются, не может быть подписан, так как пользователи не могут проверить содержимое нехэшированных файлов.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан элемент `Signature` в манифесте развертывания, который используется в развертывании [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
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
